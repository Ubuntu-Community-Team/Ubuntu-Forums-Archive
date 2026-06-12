---
title: "Missing headers after installing g++"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by Draco Houston on 2006-03-06
Hello, I'm very new to linux so I have been having troubles installing and configuring alot of things(well, everything actually).

At the moment I'm trying to get g++ working, it appears to be installed right, but the standard c/c++ headers are missing (and probly the libraries too, I don't know where to look for these things!). How would I get the rest of the files for it, I've been looking on the package manager and none of the library packages I've gotten seem to have them.

I don't know if this is the right place to put it, but it seems I'm overlooking something simple here.

---

### Post by WretchedSpawn on 2006-03-06
you might want to check on synaptic and see if you have all of the gcc and cpp files/libraries for your version of g++. also, if your trying to compile stuff you need the dev versions of the libraries in addition to the regular ones.

what kind of error messages are you getting anyway?

---

### Post by Draco Houston on 2006-03-06
dracohouston@Draco:~/CSC1401$ g++ helloworld.cpp
helloworld.cpp:9:19: error: stdio.h: No such file or directory
helloworld.cpp: In function ‘int main()’:
helloworld.cpp:13: error: ‘printf’ was not declared in this scope

trying to compile:

/********************************************************************

	Author: Jason Houston

	The hello world thing

********************************************************************/

#include <stdio.h>

int main()
{
	printf("Hello World!");
	return 0;
}

basically, it can't find the headers, nor can I, I'll try getting the other version of the libs now and post if it worked or not. I installed the gcc and g++ compilers from synaptic, hopefully it all got configured properly.

---

### Post by Draco Houston on 2006-03-06
Well, there you have it, it's working just fine now.

Thank you very much mate, you were ALOT of help(didn't think of the distinction between libs and development libs)

---

