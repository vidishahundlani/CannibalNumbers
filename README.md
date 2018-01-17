# CannibalNumbers
#You'll be given two integers, i and j, on the first line. i indicates how many values you'll be given, and j indicates the number of #queries.

#Example: 

#7 2     
#21 9 5 8 10 1 3
#10 15

#Based on the above description, 7 is number of values that you will be given. 2 is the number of queries.

#That means -
#* Query 1 - How many numbers can have the value of at least 10
#* Query 2 - How many numbers can have the value of at least 15

#Your program should calculate and show the number of numbers which are equal to or greater than the desired number

#The result is:
#4 2

#code:-

#include<iostream>
using namespace std;
int main()
{
    int i, j, l, k, c=0, index=0;
    cin>>i>>j;
    int a[i], b[j], out[j];
  #input the array of numbers and arranged them in ascending order
    for(k=0;k<i;k++)
    {
        cin>>a[k];
        for(l=0;l<k;l++)
        {
            if(a[k]<a[l])
            {
                c=a[k];
                a[k]=a[l];
                a[l]=c;
            }
        }
    }
  #input the querries
    for(l=0;l<j;l++)
    {
       cin>>b[l];
    }
  #for each querry finding the no. of numbers equal or greater than it
    for(l=0;l<j;l++)
    {
        out[l] = 0;
        index = 0;
        for(k=i-1;k>=0;k--)
        {
            if(a[k]>=b[l])
            {
                out[l]++;
            }
            else if((b[l]-a[k])<=(k-index))
            {
                index = index + b[l] - a[k];
                out[l]++;
            }
        }                                           
        cout<<out[l];
        cout<<" ";
    }
    return 0;
}
