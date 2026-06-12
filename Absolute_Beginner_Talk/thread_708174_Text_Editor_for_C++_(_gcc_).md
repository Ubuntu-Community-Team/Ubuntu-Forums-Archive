---
title: "Text Editor for C++ ( gcc )"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by WILL_CHAN on 2008-02-26
I've just install Ubuntu 2 days ago ! And I'm absolutely beginner. I tried to learn how to program C++ on Linux but I don't know how I started. I already install gcc by following some instructions on some websites and now I don't know where should I type my code and compile. I know how to program on Windows 'cause it's much easier. So I would like to ask what's a good text editor if I want to program on Ubuntu. My Ubuntu version is 7.04. And I don't know how to build a program too. Any one could give me some instructions ! I'd appreciate that a lot. Thanks !

---

### Post by Martin Witte on 2008-02-26
The 'Programming Talk' forum in the 'Development and Programming' section of this site has a faq covering these questions, see [http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009). BTW: if your fresh to programming I wouldn't start with C++, languages like Python or Java are more appropriate languages to learn the concepts of programming, once your familiar with those I would continue with C++

---

### Post by mali2297 on 2008-02-26
Install the package **build-essential**, then you will also get g++. the GNU C++ compiler.

To compile example.cc in the terminal, type
```

g++ example.cc -o example

```
To execute the compiled program,
```

./example

```

There are several editors that you can try: gedit, vim, emacs et cetera.

There are also integrated development environments (IDEs) available, like Eclipse and Anjuta.

---

### Post by sayakb on 2008-02-26
@OP

gcc is a C-Compiler, while g++ is a C++ compiler. To compile a C program, write your code with .c extension, and save it. Then at a terminal:

```
gcc myprog.c -o myprog
```

I personally prefer g++ to gcc.

---

### Post by ramjet_1953 on 2008-02-26
If you want a full-blown graphical C and C++ development environment, just go into the Synaptic Package Manger, do a search for kdevelop and download it.

One word of warning, though, it is a KDE application, so it will also flag the KDE base files needed to run it.

This doesn't mean you will be running the KDE desktop, but any necessary files needed to run the package will also be loaded at execution.

Regards,
Roger :)

P.S. I run it on my GNOME desktop without any problems

---

### Post by WILL_CHAN on 2008-02-26
Thanks a lot guys ! I tried exactly the same like you said :
> 
chan@MrChan:~$ g++ example.cc -o example
example.cc: In function &#8216;int main()&#8217;:
example.cc:6: error: statement cannot resolve address of overloaded function
 And this one is the statement that my terminal told me. How can I fix it ? Or did I miss something ? Sorry for my poor English.
One more question about terminal commands ? Where can I download on the terminal commands, I think I should print a copy to practice with them so I can remember !
About gcc, I'm sorry I've not installed it yet, the one that I install from one command line that I read from one website is g++ I think. I've already printed out a whole bunch of documentation about Gcc but I read through it for more than a day. It totally freaked me out. I learned C++ and C for a year. I'm think I'm ok with C++, I just want to work with it on Ubuntu 'cause I simply don't want to depend on Window. Any help would be appreciated that. I wait for this day for more than 1 year and a half. I really love Linux T_T !
Any my program is :
```

#include <iostream>

int main()
{
	std::cout << "Hello world";
	std::endl;
	return 0;
}
```
I used gdit, I just read in one thread and I think this one is good enough for me.

---

### Post by WILL_CHAN on 2008-02-26
> The 'Programming Talk' forum in the 'Development and Programming' section of this site has a faq covering these questions, see [http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009). BTW: if your fresh to programming I wouldn't start with C++, languages like Python or Java are more appropriate languages to learn the concepts of programming, once your familiar with those I would continue with C++ Just follow this link, I just run my first program on Linux in my life. ^_^ ! So happy. I will read more to figure out how to use code in C++. Btw, is there any thread show how to use gcc 4.2.3 on Ubuntu ? I've just download the file gcc-4.2.3.tar . And I don't know how to work with it ? Could you guys give me some instructions ! Thanks !

---

### Post by mali2297 on 2008-02-26
> **WILL_CHAN said:**
> 
Any my program is :
```

#include <iostream>

int main()
{
	std::cout << "Hello world";
	std::endl;
	return 0;
}
```


Make it
```

#include <iostream>

int main()
{
  std::cout << "Hello world" << std::endl;
  return 0;
}

```

---

### Post by WILL_CHAN on 2008-02-26
Thanks mali, just got it T_T. But I've just read through the instruction ? Why do we have to use main in the command line ? Because when I tried to save it as another name, it didn't work ?

---

### Post by mali2297 on 2008-02-26
> **WILL_CHAN said:**
>  I've just download the file gcc-4.2.3.tar . And I don't know how to work with it ? Could you guys give me some instructions ! Thanks !

Is there any reason to why you want the 4.2.3 version?

Otherwise, just install the package build-essential:
```

sudo apt-get install build-essential

```
Then you will get both g++ and gcc (4.1.2).

---

### Post by mali2297 on 2008-02-26
> **WILL_CHAN said:**
> Thanks mali, just got it T_T. But I've just read through the instruction ? Why do we have to use main in the command line ? Because when I tried to save it as another name, it didn't work ?

I'm by all means not a C++ expert, but I have understood that there always should be a function **main()**.

---

### Post by eye208 on 2008-02-26
> **WILL_CHAN said:**
> Thanks a lot guys ! I tried exactly the same like you said :
 And this one is the statement that my terminal told me. How can I fix it ? Or did I miss something ?
The endl function is declared as:
```
ostream& endl(ostream& os);
```
So your call in line 6 is missing the ostream reference parameter. There are two ways to resolve this:
```
std::endl(std::cout);
```
or
```
std::cout << std::endl;
```
The latter is using the overloaded << operator declared as:
```
ostream& operator<< (ostream& (*pf)(ostream&));
```
It's important to understand what's going on here if you want to fully master C++. Operator overloading may seem complicated at first but it is an important part of the language.

---

