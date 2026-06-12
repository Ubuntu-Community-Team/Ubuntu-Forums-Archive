---
title: "programming with C++"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-11
how does one create a c++ file in Gedit and execute them in the terminal

---

### Post by putamaster on 2007-06-11
you need the gcc package installed
save your code as .cpp (to create from CLI just run "gedit FILENAME", and it will create the file if it doesn't exist)
and then compile in the terminal with the command "gcc FILENAME"


(I'm new to the whole linux thing but i believe that should work)

---

### Post by pardesi on 2007-06-11
i did this but i get an error
```
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
```
i have gcc installed

---

### Post by LaRoza on 2007-06-11
First install everything you need:
```

sudo aptitude install build-essential

```

Write your C++ program, than navigate to the programs directory.

then compile with:
```

g++ fileName.cpp -o executablesName

```

Remember: Linux is case sensitive, and you must type the extensions if there is one.

-edit I see you were invoking gcc, you must use g++ for C++.

---

### Post by pardesi on 2007-06-11
can you write down the exact procedure i.e. what thing i need tto install and how to do them in order to get going with C++

---

### Post by LaRoza on 2007-06-11
If you type along, this should work:

```

sudo aptitude install build-essential

gedit sampleProgram.cpp

```

at this point, build-essential will be installed and gedit will be open with a document named sampleProgram.cpp, the file extension is just a custom, you don't need it.

into the document, cut and paste:
```

#include <iostream>
int main()
{
   std::cout <<  "Hello world" << std::endl;
   return 0;
}

```
Now save and exit.

To compile:
```

g++ sampleProgram.cpp -o sampleProgram.bin

```

When compiling, you can use relative paths or absolute paths, to make things easier, navigate to the directory with the files to compile to keep the typing at a minimum.

I would say have fun, but it is only so exciting.

note:
To run the program, type its name in the terminal, you will get the words: "Hello world" on a new line.

---

### Post by pardesi on 2007-06-11
i did the first two steps while executing the third step i go this error
```
sampleProgram.cpp: In function ‘int main()’:
sampleProgram.cpp:4: error: expected primary-expression before ‘:’ token
sampleProgram.cpp:4: error: expected `;' before ‘:’ token

```
is everything ok

---

### Post by LaRoza on 2007-06-11
Sorry, typo, make that two colons between std and endl, 

```

#include <iostream>
int main()
{
   std::cout <<  "Hello world" << std::endl;
   return 0;
}

```

-edit I spelled typo wrong the first time, ironic ,huh?

---

### Post by LaRoza on 2007-06-11
It would seem you are interested in programming, I would hope so anyway. :D

If this is your first time programming, you could try an interpreted language, like Python. Python is a very powerful language and is easy to learn. I am learning it now after using C++, and find it a very useful language.

If you want to learn C++ in particular, [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/) has a good tutorial in case you want another reference in addition to what you have now.

---

### Post by pardesi on 2007-06-11
.when i wrote
this i get 
[B]pardesi@pardesi-desktop:~$ g++ sampleProgram.cpp -o sampleProgram.bin
pardesi@pardesi-desktop:~$ 

[/B]
seems to be discarded
thanks i after ubuntu beecame interseted in programming .i just used ubuntu found it great but i wanted to proceed like history did ....Thanks :p:p
and do you know one thing the site u referred me is exactly the site i was planning to learn from

---

### Post by LaRoza on 2007-06-11
Now run it, no errors, that is good sometimes.

-edit Try the Programming Talk forum, in Other Community Discussions, you'll get much more programmer response.

---

### Post by pardesi on 2007-06-11
should i run it again the same thing i get as my previous post (AFTER EDITING)

---

### Post by LaRoza on 2007-06-11
When you compile a program, the original text document, the source code, is preserved. A new binary file is made which the program itself, in this case, it is "sampleProgram.bin". Type it in the terminal to run it.

-edit If you compile the code again with the same executable name, it will replace the old file.

---

### Post by HotShotDJ on 2007-06-11
OMG!!  :shock:  Programming with C++ is now something BEGINNERS do??
After over 5 years as a Linux user, I've never written a single line of C++.  I feel so inadequate! :oops:

( ;) )

---

### Post by pardesi on 2007-06-11
isn't there any other simple way to compile and run C== as i do in LaTEX

---

### Post by LaRoza on 2007-06-11
Simple? You could use an IDE, but I wouldn't recommend it.

It is not all that difficult, just foreign at the moment.

The command g++ file.cpp -o file.bin just compiles and name the output file, if you have been typing it out, you can use the arrow key, "up", to choose the previous command. If you are writing console programs, you will need to use the CLI anyway, so it actually is easier to compile and run in the same shell. If you were using an IDE, you would compile by clicking on a button or using a hot-key, and then you would need to use a terminal to run the program.

If you were to use Python, you wouldn't have to compile, the equivalant program to the C++ program I gave as an example, is:

```

print "Hello world"

```

If you write this to a file, with the traditional file extension *.py, you could run it with the simple command
```

python fileName.py

```

If you are awkward with the CLI, who isn't at first, using it will make you more comfortable.

---

### Post by LaRoza on 2007-06-11
> **HotShotDJ said:**
> OMG!!  :shock:  Programming with C++ is now something BEGINNERS do??
After over 5 years as a Linux user, I've never written a single line of C++.  I feel so inadequate! :oops:

( ;) )

Beginner is a relative term, one can use Linux for years and never be a programmer, and can program in Windows for years and be a Linux beginner. Don't feel inadequate because other people are programmers. You probably have skills I do not have, in fact, I know you do, you have been using Linux longer than I have, but I don't feel inadequate (ok, just a little).

This forum was not the best place for the post, it should have been in the programming talk forum. 

note: no one starts out as an advanced programmer, everybody usually starts with the simple program I posted earlier in almost every language.

---

