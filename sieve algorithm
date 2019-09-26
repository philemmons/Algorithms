/* Title: sieve.cpp
 * Abstract: "This program will implement the sieve of Eratosthenes algorithm
 * 		that generates consecutive primes not exceeding any given integer n > 1"(Levitin, 6).
 * 		Arrays possess dynamic memory. http://www.cplusplus.com/doc/tutorial/dynamic/
 * Author: Phillip T. Emmons
 * ID: 9902
 * Date: 01/27/2017
 */

#include <iostream>
#include <new>

using namespace std;

//Input: A positive integer n > 1
//Output: Array L of all prime numbers less than or equal to n
int main(){
	int intNum= 0,//Integer value entered by user as the numArr dynamic array init +1 length.
		nonZero= 0,//Counter variable for the non zero values in the numArr and to be used with the second dynamic array outArr (L).
		i= 0, j= 0, p= 0;// Counter variables used as index values.

	//User enters an integer value from the console. An input check should be written in...
	cout<< "Enter a positive integer n > 1: ";
	cin.clear();// Clears the input stream.
	cin>> intNum;
	//Initialize an integer pointer as the memory location for the dynamic array, instantiates integer array,
	//and the nothrow keyword assigns the pointer to a null value if an memory error occurs.
	//The +1 is required due to the fact the algorithm starts A[p] ← p that is the third cell A[2].
	//eg - If n=5, an array of 5 elements 0-4 is created. The algorithm written as such will assign 2 to 5 starting at the third cell
	// and cause an out of bound error an crash the program.
	int *numArr = new (nothrow) int[ intNum +1 ]();
	if( numArr == nullptr ){
	  cout<<"Memory allocation failed to initialize intNum array."<<endl;
	}else{
		//for p ← 2 to n do
		for( p= 2; p<= intNum; p++ ){
			//A[p] ← p
			numArr[ p ]= p;
		}
		//for p ← 2 to roundedDown[sqrt(n)] do //see note before pseudo code
		for( p= 2; p*p <= intNum; p++ ){
			//if A[p] != 0 //p hasn’t been eliminated on previous passes
			if( numArr[ p ] !=0 ){
				//j ← p * p
				j= p*p;
				//while j ≤ n do
				while( j <= intNum ){
					//A[j] ← 0 //mark element as eliminated
					numArr[ j ] = 0;
					//j ← j + p
					j= j+p;
				}
			}
		}
		//copy the remaining elements of A to array L of the primes
		//nonZero variable  will be the array size of non zero values.
		for( i= 2; i<= intNum; i++ ){
			if( numArr[ i ] != 0 ){
				nonZero++;
			}
		}

		int *outArr = new (nothrow) int[ nonZero ]();
		//Informs user dynamic array is a go!
		if( numArr == nullptr ){
			  cout<<"Memory allocation failed to initialize nonZero array."<<endl;
		}else{
			//i ← 0
			i= 0;
			//for p ← 2 to n do
			for( p= 2; p<= intNum; p++ ){
				//if A[p] != 0
				if( numArr[p] != 0 ){
					//L[i] ← A[p]
					outArr[ i ] = numArr[ p ];
					//i ← i + 1
					i++;
				}
			}
			//return L
			//First element hard coded to display to console a clean output.
			//Avoids writing a conditional statement for the comma placement.
			cout<< "Prime numbers: " << outArr[ 0 ];
			for( i= 1; i< nonZero; i++ ){
				cout << ", "<< outArr[ i ] ;
			}
			//Garbage collection and resolves dangling pointers.
			delete[] outArr;
			outArr =0;
		}
		delete[] numArr;
		numArr =0;
	}
	return 0;
}
