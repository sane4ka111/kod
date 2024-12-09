#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>

#define MAX_SIZE 100

// Функция для проверки, содержится ли элемент в массиве
bool contains(double *arr, int size, double element) {
    for (int i = 0; i < size; i++) {
        if (arr[i] == element) {
            return true;
        }
    }
    return false;
}

// Функция для нахождения пересечения двух массивов
int array_intersection(double *arr1, int size1, double *arr2, int size2, double *result) {
    int result_size = 0;

    for (int i = 0; i < size1; i++) {
        if (contains(arr2, size2, arr1[i]) && !contains(result, result_size, arr1[i])) {
            result[result_size++] = arr1[i];
        }
    }

    return result_size;
}

int main() {
    double arr1[MAX_SIZE], arr2[MAX_SIZE], intersection[MAX_SIZE];
    int size1, size2;

    // Ввод первого массива
    printf("Введите количество элементов первого массива: ");
    scanf("%d", &size1);

    printf("Введите элементы первого массива: ");
    for (int i = 0; i < size1; i++) {
        scanf("%lf", &arr1[i]);
    }

    // Ввод второго массива
    printf("Введите количество элементов второго массива: ");
    scanf("%d", &size2);

    printf("Введите элементы второго массива: ");
    for (int i = 0; i < size2; i++) {
        scanf("%lf", &arr2[i]);
    }

    // Нахождение пересечения массивов
    int intersection_size = array_intersection(arr1, size1, arr2, size2, intersection);

    // Вывод результата
    printf("Массив-пересечение: ");
    for (int i = 0; i < intersection_size; i++) {
        printf("%.2lf ", intersection[i]);
    }
    printf("\n");

    return 0;
}
