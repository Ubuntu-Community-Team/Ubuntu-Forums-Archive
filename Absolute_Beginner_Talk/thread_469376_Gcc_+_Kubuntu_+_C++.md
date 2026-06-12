---
title: "Gcc + Kubuntu + C++"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by rajausman on 2007-06-09
I have downloaded Kubuntu, which I feel may or may not come with Gcc compiler installed, anyway I did install it with:

sudo aptitude update
sudo aptitude install build-essential
sudo apt-get install gcc

But now the problem is how to link compile and run a program, such as **myfirstprogram.cpp** I am running Ubuntu Feisty.

Would someone please come with any suggestions as how to achieve this, possibly a good step-by-step guide would. Which might explain, whether or not I need to set up special compiler paths or links etc...

Any help towards this much appreciated.

---

### Post by taurus on 2007-06-09
```
g++ myfirstprogram.cpp
```

---

### Post by Rocket2DMn on 2007-06-09
If you are making more advanced programs that span multiple files and directories, you can use Makefiles.  There are many tutorials out there such as this [one]("http://myweb.stedwards.edu/laurab/help/makefilehelp.html").  Just google something like *C++ Makefile* and you will surely find some good ones.
If you don't really know what I'm talking about, then you probably shouldn't bother just yet :)
Have fun!

---

### Post by rajausman on 2007-06-10
> **taurus said:**
> ```
g++ myfirstprogram.cpp
```

I have done that before your suggestion, but I get error messages....

---

### Post by Eric_Jardas on 2007-06-10
Paste the error.
And...are you using ubuntu or kubuntu ?

---

### Post by bobbocanfly on 2007-06-10
to find out if its an error in your code you have to type

```
g++ -Wall myprogram.cpp -o myprogram
```

---

### Post by rajausman on 2007-06-11
> **bobbocanfly said:**
> to find out if its an error in your code you have to type

```
g++ -Wall myprogram.cpp -o myprogram
```

I tried this and get this error message.. could you maybe send a simple working program, with all the necessary libraries, which enable a successful program.

..............................................................
$ g++ -wall firstprogram.cpp -o firstprogram
g++: unrecognized option '-wall'
firstprogram.cpp:2: error: &#8216;include&#8217; does not name a type
firstprogram.cpp: In function &#8216;int main()&#8217;:
firstprogram.cpp:6: error: &#8216;cout&#8217; was not declared in this scope
---------------------------------------------------------------------

Thanks

---

### Post by rajausman on 2007-06-11
> **rajausman said:**
> I tried this and get this error message.. could you maybe send a simple working program, with all the necessary libraries, which enable a successful program.

..............................................................
$ g++ -wall firstprogram.cpp -o firstprogram
g++: unrecognized option '-wall'
firstprogram.cpp:2: error: ‘include’ does not name a type
firstprogram.cpp: In function ‘int main()’:
firstprogram.cpp:6: error: ‘cout’ was not declared in this scope
---------------------------------------------------------------------

Thanks

forget about the "wall", I know that it should be a capital "W"

---

### Post by Rocket2DMn on 2007-06-11
can you post your includes?  Sounds like it may not be taking
```
#include <stdio>
```

---

### Post by christhemonkey on 2007-06-11
Sounds like you forgot to include the line:
```
using namespace std; 
```
After your "#include"'s.

Or that your 2nd included library (Probs <iostream>) is not correctly typed or something.

---

### Post by Arwen on 2007-06-11
You do have #include <iostream.h> do you?
Maybe you should add "using namespace std;"  below all 'include' declarations
I f you are using more namespaces you have to declare it too,at least I used to add std and it worked.
Which gcc do you have??I think the "which gcc" command shows it.

---

### Post by KIAaze on 2007-06-11
> **rajausman said:**
> I tried this and get this error message.. could you maybe send a simple working program, with all the necessary libraries, which enable a successful program.

Thanks

I'm not sure how much you know and what you are looking for, but here goes the default example...:

hello.cpp:
> #include <iostream>

using namespace std;

int main()
{
	cout << "Hello World" << endl;
	return 0;
}

To compile it:
> g++ hello.cpp -o hello

some info about libraries since you asked:
The default path to headers is "/usr/include".
The default path to libraries is "/usr/lib".

To add include paths, use "-I<dir>" (big i) in the g++ command.
To add library paths, use "-L<dir>" in the g++ command. Define the libraries by also adding "-l<library base name>" (small L)

ex: "-lfoobar" will look for libfoobar.a.

more basic info:
[http://gentoo-wiki.com/StartingCPP]("http://gentoo-wiki.com/StartingCPP")

---

### Post by Rocket2DMn on 2007-06-11
get rid of the "endl" and just try 
```
cout << "Hello World\n" 
```
If the include still doesnt work, try
```
#include <iostream.h>
```
or 
```
#include <iostream>
#include <stdio>
```

---

### Post by Arwen on 2007-06-13
I think it's #include <stdio.h>
You can also use g++ -Wno-deprecated file.cpp so as not to show the warnings.

---

