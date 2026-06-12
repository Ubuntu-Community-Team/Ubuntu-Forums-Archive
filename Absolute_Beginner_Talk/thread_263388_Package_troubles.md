---
title: "Package troubles"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by someonedumb on 2006-09-23
I'm trying to learn about compiling things from source in Ubuntu. I cannot connect to the internet from Ubuntu so I cannot use the "apt-get install build-essential" command.

How can I get the packages I need from Windows? I went to the ubuntu repository and found the a file called "build-essential_11.3_i386.deb" but it ended up being just a 6.81kb file which appeared to be only a list of other packages, although I was not able to read that list (it wouldn't unpack because of dependancies).

Should I forget about trying to get ahold of the normal Ubuntu packages and just start looking for GCC from other places?

---

### Post by aysiu on 2006-09-23
The *build-essential* package is on the CD.

Enter these commands in the terminal: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by someonedumb on 2006-09-23
Well I feel silly now :P 

Thanks alot for the reply :)

---

### Post by aysiu on 2006-09-23
Don't feel silly. The developers thought it was worth putting on the CD but not worth installing, for some strange reason.

---

### Post by someonedumb on 2006-09-23
GARG!!!!!

Now that I know I can install the package using the CD I cannot... A few days ago I tried to install a modem driver but the install failed, so I marked it for removal. The removal script returned an error, so it cannot be removed.

Now whenever I try to use the package manager to install anything it tries to remove the old driver first, and fails, and quits with an error message that I cannot remove the driver package.

---

### Post by Arevos on 2006-09-23
Try typing into a terminal:
```
sudo apt-get remove <name of problem package>
```
Sometimes this returns instructions how to solve the problem, or will give people on the forums extra information with which they can offer a solution, if you post the output here.

---

### Post by someonedumb on 2006-09-23
someone@someone-desktop:~$ sudo apt-get remove ltmodem-2.6.8-2-386
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  ltmodem-2.6.8-2-386
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1348kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 69970 files and directories currently installed.)
Removing ltmodem-2.6.8-2-386 ...
find: warning: you have specified the -mindepth option after a non-option argument -name, but options are not positional (-mindepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

find: warning: you have specified the -maxdepth option after a non-option argument -name, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.


Could not identify your distribution's way of automatically loading modules,
Exiting.

dpkg: error processing ltmodem-2.6.8-2-386 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 ltmodem-2.6.8-2-386
E: Sub-process /usr/bin/dpkg returned an error code (1)
someone@someone-desktop:~$

---

### Post by someonedumb on 2006-09-23
I can see all the files installed by this broken package if I look at the file info tab in the GUI... is it safe to go in and just delete all the files on that list? Or would that just cause more funny business?

---

### Post by someonedumb on 2006-09-23
It turned out that the GUI did not list the files because the package was broken, so I did a 'locate ltmodem' and deleted all the files from the problem package that were listed and it actually worked :D Package manager is working properly and I have my 'build-essentials' now.

Now I have to figure out why simple C code doesn't compile in GCC the same way it does with microsoft compilers >:[

For example, this code gives the error "for loop initial declaration used outside C99 mode"

> #include <stdio.h>
#include <stdlib.h>

int main(){

	for(int i = 2; i<10; i++){
		int x = 1;
	}
	double d = 12.4;
	printf("Hello World!");
	return 0;

}

This program compiles and runs properly if I comment out the for loop. I have *never* seen a proper for loop declaration cause an error in a Microsoft compiler.

---

### Post by sktx on 2006-09-23
> **someonedumb said:**
> Now I have to figure out why simple C code doesn't compile in GCC the same way it does with microsoft compilers >:[

For example, this code gives the error "for loop initial declaration used outside C99 mode"

As your knowledge of GNU/Linux expands, especially at the  beginning, you'll find that a lot of things are radically different from what you're used to. But, sometimes, there are only subtle differences and small changes between the new environment and your old familiar way of doing things, and this can be exponentially more frustrating and difficult to understand;  sometimes, something that was part of your skillset on your previous OS of choice seems to have grown a few kinks as you try to use it under Linux.  Don't get frustrated, although Ubuntu doesn't have as steep of a learning curve as other posix-type OSes, or of a lot of other distributions of GNU/Linux, it still requires a lot of reading, searching, and asking, if you really *want* to dig into it and learn how to run it efficiently.  In my opinion, all of the legwork pays off. 


As an example, I went and pulled a couple links for you. The first is a forum with someone who had the same problem as you did, albeit in a longer program. The second is an archived post from the gcc-patches mailing list.  I got both links by googling "[C99 mode]("http://www.google.com/search?q=C99+mode")."

"*The problem is that you can't declare a variable in a for() under C.*"
  from: [http://www.daniweb.com/techtalkforums/thread1260.html](http://www.daniweb.com/techtalkforums/thread1260.html)

"*Though C99 inline is very different from the GCC extension and the semantics will need reimplementing for C99 mode following the standard (the note in c99status.html that "C99 inline implies static" is not precisely accurate, and simply doesn't cover the full incompatibilities), it seems worthwhile to at least allow the "inline" keyword in C99 mode now, which this patch does.*"
from: [http://gcc.gnu.org/ml/gcc-patches/2000-07/msg00679.html](http://gcc.gnu.org/ml/gcc-patches/2000-07/msg00679.html)

---

