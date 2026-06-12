---
title: "[SOLVED] running console applications"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-01-17
i'm a beginner in c++, and i need to be able to run my self-written console applications.

is there any way to do this? 

i've tried wine and dosbox. neither worked for me.

thanks in advance :)

---

### Post by Tenken on 2008-01-17
You can install a program called "Build Essentials" to compile your code on your Linux machine

```
sudo apt-get install build-essential
```

Then in command line type something like

```
gcc -o output.prog input.cpp
```

Use the man pages with gcc (GNU C Compiler) for more options.

The example I gabv breaks down like this: gcc calls the complier, the -o says create an output file named "output.prog" (the name/file extension  don't matter in Linux) from the source file "input.cpp". This is assuming you're in the directory that your source code is and will create the output file there too. And to run the program type

```
./output.prog
```

---

### Post by stevescripts on 2008-01-17
> **Sinkingships7 said:**
> i'm a beginner in c++, and i need to be able to run my self-written console applications.

is there any way to do this? 

i've tried wine and dosbox. neither worked for me.

thanks in advance :)

In Linux you run your console apps from a terminal.

Click on Applications > Accessories > Terminal.

Depending on your installation, you may or may not already be set up
to build c++ apps.  If you arent set up folks here can help.

Terminal output:
```

steveo@delldesktop:~$ cd ./Desktop
steveo@delldesktop:~/Desktop$ ls *.cpp
hello.cpp
steveo@delldesktop:~/Desktop$ g++ hello.cpp -o hello
steveo@delldesktop:~/Desktop$ ./hello
hello world!

```

Typical hello world c++ program:
```

#include <iostream>

using namespace std;

int main ()
{
	cout  << "hello world!" << endl;

	return 0;
}

```

Hope this helps.  

Steve

---

### Post by Sinkingships7 on 2008-01-17
that seems to work well. 

is there any easier way, or is this it?

---

### Post by mali2297 on 2008-01-17
> **Sinkingships7 said:**
> that seems to work well. 

is there any easier way, or is this it?

I am not quite sure what you mean by easier, but there are so called IDEs (Integrated Development Environments) available. Examples are KDevelop, Anjuta, Eclipse and Geany.

---

### Post by Tenken on 2008-01-17
You could install an IDE (integrated development environment) like[ Eclipse]("http://www.eclipse.org/"), [Ajunta]("http://anjuta.sourceforge.net/downloads"), I've been using [Geany]("http://packages.ubuntu.com/gutsy/devel/geany") lately and really like it. It is lightweight, and easy to use.

---

