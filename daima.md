```c++
#include<bits/stdc++.h>

using namespace std;
#define MAXLEN 100
typedef int DataType;
//定义顺序表的结构体类型 
typedef struct {
    DataType elem[MAXLEN];
    int len;
} sqList;
//定义顺序表类型变量 SL 
sqList SL;

//实现操作 InitList(L)
void InitList(sqList *L) {
    L->len = 0;
}

//实现操作CreateList(L,n)
void CreateList(sqList *L, int n) {
    printf("please input %d integers：", n);
    for (int i = 0; i < n; i++)
        cin >> L->elem[i];
    L->len = n;
}

//1.实现求线性表的长度的操作GetLength(L)
int GetLength(sqList L) {
    return L.len;
}

//2. 实现按位置查找操作GetElem(L,i,x)
int GetElem(sqList *L, int i, DataType *x) {
    if (i < 1 && i > L->len) {
        return 0;
    } else {
        *x = L->elem[i - 1];
        return 1;
    }
}

//3. 实现按值查找操作Locate(L,x)
int Locate(sqList L, DataType x) {
    int i = 0;
    while (i < L.len && L.elem[i] != x) {
        i++;
    }
    if (i >= L.len)
        return 0;
    else
        return i + 1;
}

//4. 实现插入操作InsElem(L,i,x)
int InsElem(sqList *L, int i, DataType x) {
    if (L->len >= MAXLEN) {
        cout << "已满";
        return -1;
    }
    if (i < 1 && i > L->len + 1) {
        cout << "插入位置错误";
        return 0;
    }
    if (i == L->len + 1) {//末尾插入
        L->elem[i - 1] = x;
        L->len++;
        return 1;
    }
    int j;
    for (j = L->len - 1; j >= i - 1; j--)
        L->elem[j + 1] = L->elem[j];
    L->elem[i - 1] = x;
    L->len++;
    return 1;
}

//5. 实现插入操作DelElem(L,i,x)
int DelEmen(sqList *L, int i, DataType *x) {
    int j;
    if (L->len == 0) {
        cout << "顺序表为空" << endl;
        return 0;
    }
    if (i < 1 || i > L->len) {
        cout << "删除序号有误" << endl;
        return 0;
    }
    *x = L->elem[i - 1];
    for (j = i; j < L->len; j++) {
        L->elem[j - 1] = L->elem[j];
    }
    L->len--;
    return 1;
}

//6. 实现显示操作DispList(L)
void DispList(sqList L) {
    for (int i = 0; i < L.len; i++) {
        cout << L.elem[i] << ",";
    }
}

//编写main函数，测试InitList(L)和CreateList(L,n)的功能
int main() {
    cout << "202283060116钱家龙" << endl;
    //调用InitList函数
    InitList(&SL);
    //输出线性表SL中的长度
    cout << SL.len << endl;
    //调用和CreateList函数
    int n;
    printf("please input n：");
    cin >> n;
    CreateList(&SL, n);
    //输出线性表中的每个元素值
    for (int i = 0; i < SL.len; i++) {
        cout << SL.elem[i] << ",";
    }
    cout << endl;

    //7. 输出表SL的长度（元素个数）
    int len = GetLength(SL);
    cout << "SL的长度是：" << len << endl;
    //8. 已知i=3, 输出表SL中的位置为i 的元素值
    int i = 3;
    int s = 0;
    GetElem(&SL, i, &s);
    cout << "i=3时，元素值为：" << s << endl;
    //9. 已知x=5, 输出x在表SL中的位置
    DataType x = 5;
    int index = Locate(SL, x);
    cout << "x=5时，索引为：" << index << endl;
    //10. 在表SL的位置i处插入x
    InsElem(&SL, i, x);
    //11. 输出SL中的每个元素值
    DispList(SL);

    DelEmen(&SL, 2, &x);
    cout << "\n删除的元素" << x << endl;
    DispList(SL);
    return 0;
} 
```