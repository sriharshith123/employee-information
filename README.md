#include <stdio.h>
#include <string.h>

struct employee {
    char name[50];
    int age;
    char position[50];
    char date_of_joining[20];
};

void sort_by_name(struct employee e[], int n) {
    struct employee temp;
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (strcmp(e[i].name, e[j].name) > 0) {
                temp = e[i];
                e[i] = e[j];
                e[j] = temp;
            }
        }
    }
}

void sort_by_date(struct employee e[], int n) {
    struct employee temp;
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            int d1, m1, y1, d2, m2, y2;
            sscanf(e[i].date_of_joining, "%d/%d/%d", &d1, &m1, &y1);
            sscanf(e[j].date_of_joining, "%d/%d/%d", &d2, &m2, &y2);
            if (y1 > y2 || (y1 == y2 && (m1 > m2 || (m1 == m2 && d1 > d2)))) {
                temp = e[i];
                e[i] = e[j];
                e[j] = temp;
            }
        }
    }
}

int main() {
    int n;
    printf("Enter the number of employees: ");
    scanf("%d", &n);
    struct employee emp[n];
    for (int i = 0; i < n; i++) {
        printf("Enter details of employee %d:\n", i+1);
        printf("Name: ");
        scanf("%s", emp[i].name);
        printf("Age: ");
        scanf("%d", &emp[i].age);
        printf("Position: ");
        scanf("%s", emp[i].position);
        printf("Date of joining (dd/mm/yyyy): ");
        scanf("%s", emp[i].date_of_joining);
    }
    sort_by_name(emp, n);
    printf("\nEmployee List sorted by name:\n");
    for (int i = 0; i < n; i++) {
        printf("Name: %s\n", emp[i].name);
        printf("Age: %d\n", emp[i].age);
        printf("Position: %s\n", emp[i].position);
        printf("Date of Joining: %s\n", emp[i].date_of_joining);
        printf("\n");
    }
    sort_by_date(emp, n);
    printf("\nEmployee List sorted by date of joining:\n");
    for (int i = 0; i < n; i++) {
        printf("Name: %s\n", emp[i].name);
        printf("Age: %d\n", emp[i].age);
        printf("Position: %s\n", emp[i].position);
        printf("Date of Joining: %s\n", emp[i].date_of_joining);
        printf("\n");
    }
    return 0;
}
