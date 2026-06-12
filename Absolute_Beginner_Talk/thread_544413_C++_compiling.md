---
title: "C++ compiling"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by john-luck on 2007-09-06
Hello,

I want to compile c++.

Made a small code for test-run, and tried to compile using gcc, as follows:

gcc -x c++ kluis.cc

This gave me an error message of undefined references.

I'm using a small sample code I got in class, which reads as follows:
_____________________________
#include <iostream>
using namespace std;

int main ( ) {
   cout << "blabla" << endl;
   return 0;
}
_____________________________

Ofcourse, the "blabla" part was my own extremely creative addition. 
Perhaps something in the code is specific for the network at university? iostream and namespace... are they universal? (And what are they anyway?)

I was first using nedit. Thought the problem was that it said: UTF8 locale not supported. I assume this has something to do with the assignments for characters, so though that may have been the problem. 
I've now used KDevelopement and Kscope. Both offer the same result.

---

### Post by bone2006 on 2007-09-06
I think if you get build essentials it may be what your looking for.  It's in the repository

---

### Post by john-luck on 2007-09-06
Thanks for response.

I did :

sudo apt-get install build-essential

which seemed to have worked.

Still same error msg

---

### Post by BobCFC on 2007-09-06
I just compiled this ...  geez I was rusty took me a minute lol...


You need you use g++  not gcc....   

```

g++ kluis.cc   
```


works fine.

Good luck mate stick with it.  Remember google is your friend for error messages


EDIT:   Also this will produce an executable called a.out  which isn't very useful...  use the -o flag to give it a name such as

```

g++ kluis.cc   -o kluis
```

Then you can run the program from the current directory with the command:
```

./kluis  
```

---

### Post by BobCFC on 2007-09-06
Further to your other questions  iostream  is the c++ library for basic input and output using streams.  Streams can either be connected to the terminal as in the default case or they can be connected to files and networks.

So your current program will write blahblah to the terminal.. but if the stream was connected to a file it would write blahblah to a file using the same code.  You can also read from streams.


The namespace thing is just to keep code tidy.  You can insulate code inside a namespace to stop it clashing with other code that might use the same variable names etc.

So with out the namespace line at the top your code would be


```

#include <iostream>

int main () {
**std::cout** << "blabla" << **std::endl**;
return 0;
}

```



Which declares the std::   namespace explicitly every time is used... It will perform the exact same thing as your old code.   You can image this in a big file migh look messy so that is why you can declare namespace at the top and say "assume I mean namespace x for this following code"..  

There are people for and against using the shortcut.


When you start writing big projects you will create your own namespaces to keep code tidy.. it's really easy in a header file such as

```

namespace kluis
{
   int mycode()
   { }
}


// elsewhere:

int i = kluis::mycode();


```



EDIT:    here are some video tutorials on C++  [http://idealprogrammer.com/languages/cc/introduction-to-c-standford-video-tutorials-and-other-lectures/](http://idealprogrammer.com/languages/cc/introduction-to-c-standford-video-tutorials-and-other-lectures/)

---

