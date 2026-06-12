---
title: "Learning C++ in a non-windows platform? (New to C++, new to Ubuntu)"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by Mustey on 2008-03-07
Hi!

I am trying to start one of those standard C++ books. Basically, I am on the "Hello World" level. I don't intend to reach anything spectacular for 4-5 months so some basic standard library should suffice.
In windows, I had this cool free compiler+linker. I edited a text document, ran an exe and it would compile and link an exe file which I would run and see my program.

This straight-forward and easy work is what I am looking for but **something similar in Ubuntu**. Please advice.
My purpose is to develop some basic C++ awareness (you know, arrays, structures, maybe something a little along the lines of a game).

In the long run, I promise that when I am cool with C++, I will contribute to Linux in my free time.

Please advice!

Respect. Jim.

---

### Post by ebharv on 2008-03-07
The closest thing to a Windows IDE like Dev-C++ or Visual C++ is Anjuta, but I could never get it working properly.  I still try from time-to-time. You could also try gedit w/console commands to write, then compile and link your code.  Unfortunately I never got that working to good either, Search the forums for compiling C++, most (Linux/Ubuntu) programmers use this method. At least that's what I've learned in searching trough the forums.

Anjuta is sudo apt-get install anjuta,  search for it in Synaptic, or Applications, Add/Remove Programs and search for Anjuta.

You can also try to install CodeBlocks. It's an IDE extremely similar to Dev-C++ that is said to available for Linux, but once again I could never get it working right.

---

### Post by Fixman on 2008-03-07
You may use kDevelop, but if you aren't afraid of reconfiguring things, I (greatly) reccommend using gedit with the following things:

First, open a terminal and write
```
 sudo aptitude install gedit-common gedit-dev gedit-plugins 
```

Open gedit (applications->accesories->text editor). and going to edit->preferences, on the plugins tab , tick the "external tools" tickbox.

There, close preferences window and go to tools->external tools, and create a new external tool called "Compile" saying

```
 g++ $GEDIT_CURRENT_DOCUMENT_NAME -o ${GEDIT_CURRENT_DOCUMENT_NAME%.*} 
```

Next, do a new one called "Run" saying:

```
 ./${GEDIT_CURRENT_DOCUMENT_NAME%.*} 
```

And one called "Run on Terminal" saying

```
 gnome-terminal --command="
./${GEDIT_CURRENT_DOCUMENT_NAME%.*}" --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR --hide-menubar --title="${GEDIT_CURRENT_DOCUMENT_NAME%.*}"
 
```

Set accelerators for those three (I use F3, F4 and F5), and you are done, you have the probably better and faster IDE for Linux.

If you would like to highlight test, you can create a file called "file.cpp", or go to view->highlight mode->sources->C++.

---

### Post by Snakob808 on 2008-03-07
I just finished a class on data structures in C++.  Everything is already installed on Ubuntu.  For the editor... I recommend vim... I know a lot of people like gedit and emacs, or other graphical text editors.  All distros I have tried come with g++, the C++ compiler and linker. 

In other words... if you have Ubuntu, you have everything you need already.  Just figure out what text editor you want to use, and to compile type
```
g++ filename.cpp
```

It will create an a.out file, and then type

```
./a.out
```

Hope that helps.  I hope I understood what you were asking correctly - disregard, if not.

---

### Post by excogitation on 2008-03-07
What about Eclipse?

---

### Post by Mustey on 2008-03-07
Hey, thanks.
I am on my pills now (sleep problems) so I am not receiving much.

However, as I said, I am not necessarily looking for the "Most similar to Windows" or the "Most professional". Just something that I can type in C++ code, structured like in most books (which are 99% with the idea that the to-be-programmer is using Windows and the silly blue-screen compiler).

It's important that there are no errors which are coming from the OS/Compiler SDK because that would be frustrating and would discharge plenty of my perseverance. 

Can I ask whether I am expected to write a different dialect of C++ if I am "programming" (as I said, these are my first steps) under Linux?

Also, when I create an executable... Well... Is it an executable in Linux? I don't expect it having an .exe suffix... Tell me, what's going on with that?

:popcorn:

---

### Post by Fixman on 2008-03-07
> **Mustey said:**
> Hey, thanks.
Also, when I create an executable... Well... Is it an executable in Linux? I don't expect it having an .exe suffix... Tell me, what's going on with that?

:popcorn:

All files in Linux are simple text streams, that means that the only thing that differentiates a text file with an executable its their permissions. So, an executable file could have any extention (more commons are .out or .o) or none at all.

You can't run natively a windows .exe in Linux, however, some programs, like wine, let you (not perfectly) do that.

---

### Post by Snakob808 on 2008-03-07
All you need is to create a text file and end it with .cpp.  I use vim (a terminal text editor).  

So, in the terminal you would type...

```
vim nameofyourfile.cpp
```

The .cpp is identifying the program as C++ code.  

The executable is created after you have typed your code, saved the file, and compiled with 
```
g++ nameofyourfile.cpp
```

g++ will create (assuming there are no compilation errors) an a.out file, which is the equivalent of a Windows .exe file.

---

### Post by Hospadar on 2008-03-07
I'd suggest either:
Use a text editor and terminal to start with (g++)
Use Kdevelop
Use the CDT plugin for eclipse

Anjuta isn't terrible, but I think Kdevelop and CDT are much more full-featured and robust.  Really though, if you are just getting started, I think using a text editor like gedit (or kate, which I prefer) and the command line is the best way to get aquainted with linux C++ development, even if it is a little nasty-looking at the start.

---

### Post by Mustey on 2008-03-11
So I created the program, called it code.cpp and went to: Applications>Accessories>Terminal
typed g++ code.cpp and it said, here's a copy-paste:
The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: g++: command not found
tod@tod-desktop:~$ apt-get install g++
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Anyone here willing to throw in a helping hand?

---

### Post by vikasmk on 2008-03-11
try this
 ```
sudo apt-get install g++
```

---

### Post by vikasmk on 2008-03-11
You dont have g++ installed
 so try this
 ```
sudo apt-get install g++
```
 it'll ask for your password and then installation will be complete
 then do this
```
 g++ filename.cpp

``` 
 and thats it

---

### Post by Cerny on 2008-03-11
Yah i would recommend, if you want an interface like in windows, Dev-C++ as was mentioned earlier. I usually use gedit or nano from the command line to run most of my program.

---

### Post by StOoZ on 2008-03-11
I use the latest version of 'Netbeans' , it is a great IDE.

---

### Post by t0p on 2008-03-11
Let me add my vote for using gedit (or the text editor of your choice) and g++ in terminal.  IDEs are all well and good, but they add nothing worthwhile to the programming experience.

---

### Post by StOoZ on 2008-03-11
> **t0p said:**
> Let me add my vote for using gedit (or the text editor of your choice) and g++ in terminal.  IDEs are all well and good, but they add nothing worthwhile to the programming experience.

ha?
auto-complete?
list of functions in headers when calling a proper class?

only 2 out of many useful things...
also, a debugger....

---

### Post by chris200x9 on 2008-03-11
geany :) but remember first sudo apt-get install build essential(s) I don't remember which exactly.

---

### Post by Mustey on 2008-03-12
So I typed it in, put my password and it displayed:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
Suggested packages:
  g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc manpages-dev
  libstdc++6-4.1-doc
The following NEW packages will be installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev
0 upgraded, 5 newly installed, 0 to remove and 29 not upgraded.
Need to get 3150kB/7150kB of archives.
After unpacking 30.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)'
in the drive '/cdrom/' and press enter

Get:1 [http://bg.archive.ubuntu.com](http://bg.archive.ubuntu.com) gutsy-updates/main linux-libc-dev 2.6.22-14.52 [653kB]
Get:2 [http://bg.archive.ubuntu.com](http://bg.archive.ubuntu.com) gutsy-updates/main libc6-dev 2.6.1-1ubuntu10 [2497kB]
99% [Working]                                                     

It just stays there!
(I put the disk I used to install Ubuntu on this machine.)

What do I do?

---

### Post by Mustey on 2008-03-13
Hey, I installed something else - it didn't work, of course, but what I did notice is that it installed some packages with the g++ name in them. I think I got this thing working now.
Anyone willing to supply a working "hello world" program?
I have one but it doesn't compile without nagging from the... well.. here's a screen:
tod@tod-desktop:~$ g++ Desktop/code.cpp
In file included from /usr/include/c++/4.1.3/backward/iostream.h:31,
                 from Desktop/code.cpp:1:
/usr/include/c++/4.1.3/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.

I'll get to it (learning c++ in a moment), I will watch the Maccabi game and hit the sack.

All I am asking is that someone gives me a program that he knows that works in that g++ thingy.
I am sorry if it sounds like I am asking you to teach me c++ or do something instead of me.

---

### Post by Andross707 on 2008-03-13
I'm in the same boat... Dev-C++ on windows is my basic ideal so far. All I have to do is open it, start a new project, type in the program instructions, then press F9 and the program compiles and runs. There was a post earlier about some plugins that you can use for Gedit that I might try once I get home, but how Dev-C++ works as written above is what I'd like in Linux.

---

### Post by stevescripts on 2008-03-13
A simple helloworld in C++:

```

#include <iostream>

using namespace std;

int main(int argc, char * argv[])
{
	cout << "Hello World!" << endl;
	
	return 0;
}

```

To build and run (from a terminal):
```

steveo@linux:~/Desktop> g++ helloworld.cpp -o myhello
steveo@linux:~/Desktop> ./myhello
Hello World!

```

In my humble opinion - better to start learning without an ide ...

Hope you find this helpful

Steve

---

### Post by ByteJuggler on 2008-03-13
> **stevescripts said:**
> 
In my humble opinion - better to start learning without an ide ...


+1

---

### Post by Mustey on 2008-03-14
That's why I said I don't want an IDE...
Now I am going to try that code. THANKS!
(BTW, very funny avatar, stevescripts)

---

### Post by Mustey on 2008-03-14
OK, it went smooth (there were no messages after the g++ command).
This is what I typed:
tod@tod-desktop:~$ g++ Desktop/code.cpp -o jim
(If I type it without Desktop/, it cannot find the code.cpp)
However:
1. I cannot find the .out file, as far as I can guess, it should be called "jim.out", right?
2. What is that -o parameter?
3. Is there a way to make the compile-link routine more click-based, that is, make an icon that upon enclickment (:))  will open the terminal, type "g++ Desktop/code.cpp -o jim" instead of me and would pop up the "program". I would like as less steps as possible between tries as I always forget something (either save the source, compile the code) and then I don't understand my bugs so well.

BTW, "jim" seems to open correctly with the ./jim command :)
The code is working right (although it can be optimized ;))

---

### Post by Mustey on 2008-03-14
NEWS: Found Jim.

---

### Post by cwmoser on 2008-03-14
No one mentioned MonoDevelop.
I could never get Ajunta to work but MonoDevelop works just fine.
Still not as good as Visual Studio -- yet.

Carl

---

### Post by Cadmus on 2008-03-14
I'm putting a +1 on using text editors and the terminal too, at least to start with.

Starting out immediately on an IDE can lead to cargo-cult programming, where you don't necessarily understand what it is you're doing.

---

### Post by Rui Pais on 2008-03-14
[Code::Blocks ]("http://www.codeblocks.org/")it's a very nice/simple IDE and good for cross-platform too.
[How-to install on Ubuntu.]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu")

> **Mustey said:**
> OK, it went smooth (there were no messages after the g++ command).
This is what I typed:
tod@tod-desktop:~$ g++ Desktop/code.cpp -o jim
(If I type it without Desktop/, it cannot find the code.cpp)
However:
1. I cannot find the .out file, as far as I can guess, it should be called "jim.out", right?
2. What is that -o parameter?
3. Is there a way to make the compile-link routine more click-based, that is, make an icon that upon enclickment (:))  will open the terminal, type "g++ Desktop/code.cpp -o jim" instead of me and would pop up the "program". I would like as less steps as possible between tries as I always forget something (either save the source, compile the code) and then I don't understand my bugs so well.


1. 2. the -o it's a flag to indicate the name you want to give to executable (-o jim makes an exec named jim. To have a jim.out you need to put -o jim.out. Default, no -o flag, will produce a plain a.out)

3.You can create a launcher, it depends on th DE you use, but should have something like: "g++ $f;./a.out".. or something of the kind. 

I don't see any special gain/lost in do it with/without IDE. 
You want to learn to code or how to pass instructions to the compiler? :lol:
(you can tune that too on any decent IDE, and save lots of time navigate on code on large projects, and cut on typos with coloring syntax and auto-completion, easy debug, etc...)

---

