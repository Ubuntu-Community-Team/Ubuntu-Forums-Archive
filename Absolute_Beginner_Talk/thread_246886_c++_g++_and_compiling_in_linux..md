---
title: "c++ g++ and compiling in linux."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by WADemosthenes on 2006-08-29
The g++ GNU compiler claims to work, but programs that I compile using it in linux don't work (won't execute in windows).

What gives?

---

### Post by bbzbryce on 2006-08-29
Update:  I found this: [http://wiki.qgis.org/qgiswiki/BuildingWindowsBinaryOnLinux](http://wiki.qgis.org/qgiswiki/BuildingWindowsBinaryOnLinux)
So it appears that it is possible.

It is my understanding that something compiled only works on the same machine type that it is compiled on.  Meaning I don't believe you can run something in Windows which wasn't compiled in Windows.

---

### Post by reacocard on 2006-08-29
linux executables and windows executeables are not the same thing. that's why it doesn't work. you'll have to compile it explicity for windows. (or compile it in windows :))

---

### Post by WADemosthenes on 2006-08-29
Ah, but the executibles don't work on the linux box either.

---

### Post by WADemosthenes on 2006-08-30
So the linux build of g++ compiles a program that *would* on your particular machine *if* you had windows.

That sucks, what was it even ported to linux?

---

### Post by Bachstelze on 2006-08-30
Binaries compiled on Linux will wotk on Linux. Binaries compiled on Windows will work on Windows.

As simple as that.

---

### Post by WADemosthenes on 2006-08-31
it doesn't seem to run on linux when compiled in linux though.

---

### Post by IYY on 2006-08-31
What are you trying to compile? If it's short, let's have a look at the source code.

---

### Post by WADemosthenes on 2006-09-04
I'm very much a beginner, so It's extremely simple:
> #include <iostream>
using namespace std;

int main()
{
    int num1;
    int num2;
    int num3;
    cout << "Input three numbers for average" <<endl;
    cin >> num1;
    cin >> num2;
    cin >> num3;
    cout << "\nThe average is: ";
    int ave = (num1 + num2 + num3)/3;
    cout << ave << "\n";
    system("PAUSE");
    return EXIT_SUCCESS;
}


All I installed what g++ and it's dependenices, was that all I needed?

---

### Post by Ragazzo on 2006-09-04
Doesn't it give you an error message during compilation? You're a missing a semicolon but it should notify you about it. When you want to run the binary file in the current directory, you must prepend ./ to it, like: ./a.out

Edit: system() executes a shell command. PAUSE exists on Windows but not on Linux. You must use something else in its place.

---

### Post by cocteau on 2006-09-04
Here's my guess, as to why it's not working. The compiler should give an error for at least some of these things.

#include <iostream>
using namespace std;

int main()
{
int num1;
int num2;
int num3;
cout << "Input three numbers for average" <<endl; //space missing here.
cin >> num1;
cin >> num2;
cin >> num3;
cout << "\nThe average is: ";
int ave = (num1 + num2 + num3)/3; //This will be a truncated average. Not an error, just not quite right either,
cout << ave << "\n"; //Don't use \n as the final line break. Use endl as it flushes the buffer too. Otherwise you can't be certain this message is printed when the program is run.
system("PAUSE"); //This is a windows command. Doesn't work in linux.
return EXIT_SUCCESS; //Change this to return 0, instead.
}

---

### Post by WADemosthenes on 2006-09-04
> system("PAUSE"); //This is a windows command. Doesn't work in linux.

What is the linux equivalent?

---

### Post by Ragazzo on 2006-09-04
> **WADemosthenes said:**
> What is the linux equivalent?

cin.get() should work on all platforms.

---

### Post by WADemosthenes on 2006-09-04
cin.get() what?  I'm very new to c++, it's way harder than python.

---

### Post by cocteau on 2006-09-04
I don't think that you need an equivalent. The system("PAUSE") command is used in windows to prevent the window from closing after executing the binary. In linux you usually run the binary from the command line anyway and the terminal window stays open when the program terminates. I know that is true if you run from both Anjuta and Kdevelop IDEs.

On a seperate note. These pages might interest you.

[http://cplus.about.com/od/beginnerctutorial/l/blcplustut.htm](http://cplus.about.com/od/beginnerctutorial/l/blcplustut.htm)
[http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)

---

### Post by BlueEvil on 2006-09-05
working on deleting this post

---

### Post by WADemosthenes on 2006-09-10
Very usefull cocteau, I'm looking at those pages now. 

About running the programs, I just don't seem to be able to run them.  If a program is named "main.exe" I cd to the Desktop (where it is) and type "main.exe" -- nothing.  "main" gets nothing either.  I try double clicking the file on the desktop -- nothing.  Using the code (with corrections and minus the "System("PAUSE")") I think it should be working.  I'm not sure.

---

### Post by kroiz on 2006-09-10
Please paste the command you used to compile.
also do ls to see the file.
then try ./main

---

### Post by mmm guitar on 2006-09-10
Hi,  

Yeah problems as mentioned, try this:

```

//////////////////
//
// Title: Main.cpp
// Author: Your Name
// Date: 10/10/06
//  
// Description:
// A simple program that takes three numbers from user 
// input and calculates the average.
//
////////

#include <iostream>

using namespace std;

int main()
{
  double num1;      // 1st number from input
  double num2;      // 2nd number from input
  double num3;      // 3rd number from input
  double average;   // To hold average of three numbers
  
  // input numbers from console
  
  cout << "Input three numbers for average" << endl;
  cin >> num1;
  cin >> num2;
  cin >> num3;
  
  // calculate + display average in console
  
  average = (num1 + num2 + num3) / (double) 3.0;
  cout << "\nThe average is: " << average << endl; 
 
  return EXIT_SUCCESS;
}

```

I changed your numbers from ints to doubles so they can handle decimal places.  And when dividing by "3" you should tell the compiler what that 3 is, it could be seen as an int, double, float etc etc, a simple cast tells the compiler exactly how to handle it.  Also good practice to comment code.

Put it under the name of 'main.cpp'

Compile it with this command:

```
g++ ./main.cpp -o ./main
```

And execute using this command:

```
./main
```

Should not really call binaries in linux '.exe' - .exe is a windows term. Aye c++ is a little confusing at first but is straight forward once you get used to it.

Hf + gl

---

