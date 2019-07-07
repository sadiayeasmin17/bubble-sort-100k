# bubble-sort-100k

#include<iostream>
#include<fstream>
#include<cstdlib>
#include<ctime>
using namespace std;
void bubblesort(int arr[],int n)
{
    for(int i=0;i<n-1;i++)
    {
        for(int j=0;j<n-1;j++)
        {
            if(arr[j]>arr[j+1])
            {
                int temp=arr[j];
                arr[j]=arr[j+1];
                arr[j+1]=temp;
            }
        }
    }
}
int main()
{


    ofstream fileinput;
    srand(time(NULL));
    fileinput.open("10.txt");
    int n=100000;

    int*arr=new int[n];

    for(int i=0;i<n;i++)
    {
         arr[i]=rand()%7000;
        fileinput<<rand()<<endl;

    }

    fileinput.close();

    clock_t startTime=clock();
    bubblesort(arr,n);

    clock_t endTime=clock();

    ofstream fileoutput;
    fileoutput.open("10out.txt");
    for(int i=0;i<100000;i++)
    {
        fileoutput<<arr[i]<<endl;
    }

    double timelapse=double (endTime-startTime)/CLOCKS_PER_SEC;
    cout<<timelapse<<endl;

    fileoutput.close();
    delete[] arr;
}
