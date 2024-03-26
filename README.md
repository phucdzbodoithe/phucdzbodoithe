/*
Viết chương trình nhập vào 2 ma trận X (có n1 hàng, m1 cột) và Y (có n2 hàng, m2 cột) các số nguyên. Tính tích 2 ma trận X.Y và in kết quả ra màn hình. Nếu không tính được tích 2 ma trận thì in ra thông báo "Du lieu vao sai"

Input: 

+ Dòng thứ nhất nhập vào n1 và m1 là số hàng và số cột của ma trận X. 

+ Dòng tiếp theo nhập vào các phần tử của ma trận X gồm n1 hàng, m1 cột

+ Dòng tiếp theo nhập vào n2 và m2 là số hàng và số cột của ma trận Y. 

+ Dòng tiếp theo nhập vào các phần tử của ma trận Y gồm n2 hàng, m2 cột

Output:

+ Nếu tính được tích:

- Dòng thứ nhất in ra thông báo "Ma tran tich"

- Các dòng tiếp theo in ra các phần tử của ma trận cách nhau dấu cách.

+ Nếu không tính được tích:

- In ra thông báo "Du lieu vao sai"

Constranins: 1<=n, m<=100, các phần tử trong ma trận là các số nguyên.
*/
#include <stdio.h>

// Hàm nhập ma trận
void nhapMaTran(int a[][100], int n, int m) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            scanf("%d", &a[i][j]);
        }
    }
}

// Hàm tính tích của hai ma trận
int tinhTichMaTran(int X[][100], int n1, int m1, int Y[][100], int n2, int m2, int Z[][100]) {
    if (m1 != n2) // Kiểm tra điều kiện tính tích
        return 0;

    // Khởi tạo ma trận kết quả Z ban đầu
    for (int i = 0; i < n1; i++) {
        for (int j = 0; j < m2; j++) {
            Z[i][j] = 0;
        }
    }

    // Tính tích của hai ma trận
    for (int i = 0; i < n1; i++) {
        for (int j = 0; j < m2; j++) {
            for (int k = 0; k < m1; k++) {
                Z[i][j] += X[i][k] * Y[k][j];
            }
        }
    }

    return 1; // Trả về 1 nếu tích được tính
}

// Hàm in ma trận
void inMaTran(int Z[][100], int n, int m) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < m; j++) {
            printf("%d ", Z[i][j]);
        }
        printf("\n");
    }
}

int main() {
    int n1, m1, n2, m2;
    scanf("%d%d", &n1, &m1);
    int X[100][100];
    nhapMaTran(X, n1, m1);

    scanf("%d%d", &n2, &m2);
    int Y[100][100];
    nhapMaTran(Y, n2, m2);

    if (m1 != n2) {
        printf("Du lieu vao sai\n");
    } else {
        int Z[100][100];
        if (tinhTichMaTran(X, n1, m1, Y, n2, m2, Z)) {
            printf("Ma tran tich\n");
            inMaTran(Z, n1, m2);
        } else {
            printf("Du lieu vao sai\n");
        }
    }

    return 0;
}
