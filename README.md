#include <iostream>
using namespace std;

struct ngay
{
	int ng;
	int th;
	int n;
};
typedef struct ngay NGAY;
void Nhap(NGAY&);
void Xuat(NGAY);
bool KTNgayHopLe(NGAY);
int SoNgayToiDaTrongThang(NGAY);
int KTNhuan(NGAY);
int main()
{
	NGAY A;
	Nhap(A);
	cout << "Ngay Chinh Xac";
	Xuat(A);
	
	return 0;
}

void Nhap(NGAY& P)
{
	do
	{
		cout << "Nhap ngay: ";
		cin >> P.ng;
		cout << "Nhap thang: ";
		cin >> P.th;
		cout << "Nhap nam: ";
		cin >> P.n;
	} while (KTNgayHopLe(P)==0);
	
}
bool KTNgayHopLe(NGAY a)
{
	if (a.n < 1)
		return 0;
	if (a.th < 1)
		return 0;
	if (a.th > 12)
		return 0;
	if (a.ng < 1)
		return 0;
	if (a.ng > SoNgayToiDaTrongThang(a))
		return 0;
	return 1;
}
int KTNhuan(NGAY a)
{
	if(a.n % 4 == 0 && a.n % 100 != 0)
		return 1;
	if (a.n % 400 == 0)
		return 1;
	else
		return 0;

}
int SoNgayToiDaTrongThang(NGAY a)
{
	int ngaythang[12] = { 31,28,31,30,31,30,31,31,30,31,30,31 };
	if (KTNhuan(a))
	{
		ngaythang[1] = 29;
	}
	return ngaythang[a.th-1];
}
void Xuat(NGAY P)
{
	cout << "(" << P.ng << "/" << P.th <<"/" << P.n <<")" << endl;

}
