---
title: "Dev c++ has owned me."
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-04-11
Okay... (I've tried to post this a few times but failed due to  crashed and accidentally closing the browser)

After discovering that Darkbasic professional didn't work under wine, I decided to re-learn c++ again, for the umpteenth time, but this time,  I'm running Linux. (Ubuntu 6.06 LTS dapper). I lost  the CD that came with my book, "Game Programming all in one" , but I know that it had the Dev C++ compiler and the Allegro Libraries on it.

So, I downloaded the linux version of Dev C++

(here is the exact file I downloaded: 
[http://sourceforge.net/project/downloading.php?groupname=dev-cpp&filename=dev-src_Jul_30_23h03.tar.gz&use_mirror=puzzle](http://sourceforge.net/project/downloading.php?groupname=dev-cpp&filename=dev-src_Jul_30_23h03.tar.gz&use_mirror=puzzle) )

After running the install script, it all failed and went mad and complained. I read the readme and installed all of the necessary  repositories, but it failed and I don't know why.

This is exactly what happened:

```

david@david-desktop:~$ cd /home/david/devc++/c++/setup
david@david-desktop:~/devc++/c++/setup$ ls
INSTALL  #install.sh#  install.sh  install.~sh  install.sh~  README  README~
david@david-desktop:~/devc++/c++/setup$ sudo sh install.sh
Password:
** Dev-C++ installation script **

You must be root to install. Do you want to continue ?
 (Y/n) ? y
tar: binary.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
Where do you want to install Dev-C++ ? [/home/david/dev-c++] :
mv: cannot stat `TODO': No such file or directory
mv: cannot stat `BUGS': No such file or directory
mv: cannot stat `bin/devcpp': No such file or directory
mv: cannot stat `bin/libqtintf.so*': No such file or directory

* This script will now guess your gcc and make paths
* Press enter if the path is correct for each program

make is located in : [/usr/bin/make] :
gcc is located in : [/usr/bin/gcc] :
g++ is located in : [/usr/bin/g++] :
gdb (or your favourite debugger) is located in : [/usr/bin/gdb] :
xterm, aterm or Eterm is located in : [/usr/bin/xterm] :

* Configuration file is now been written in /home/david/.devcpp/config


* Installation terminated, you may now run /home/david/dev-c++/devcpp

david@david-desktop:~/devc++/c++/setup$

```

/home/david/dev-c++/ is empty.

So, basically, can anybody make any sense of any of this? 

Are there any healthy alternatives, like a nice happy binary installer somewhere?  Or another way to get dev c++ onto my computer? (or maybe even a different c++ compiler, so long as it can use allegro library.)

I dunno what to do. I really need dev c++ so I can install the Allegro Library and then get down to some game programming, but it's just being IRKSOME!

This noob here needs help.

 And another thing, EVEN if I do get dev c++ to run, I have no idea how I'm going to install Allegro so that it works and everything.

---

### Post by flewis7777 on 2007-04-11
According to the install text file DevC++ wants the QT library installed first.
It also says to make sure you have all the basic development files installed - Ubuntu does not install those by default - so from the CD you need to install "Build Essential" (if you haven't already).

Good Luck

---

### Post by LaurelLynn on 2007-04-11
Dear Neon_Knight,

Allegro 4.1 can be loaded in Synaptic.  From Settings->Repositories  make sure the the ¨Community Maintained (Universe)¨ repositories are enabled.

Hit the Reload button then Search.  Enter ¨allegro¨, it should find demos, documentations, and all the library files.

From what I´ve just read on the net, Dev c++ is not necessary for using allegro. Lots of people seem to be using g++ just fine.  (in fact the messages you posted showed the script trying to use g++ to compile Dev c++).  You will also probably need Mingw when you want to produce a Windows executable.

---

### Post by Neon_Knight on 2007-04-11
flewis: Yeah, I have QT installed, but I'll try that with the development files...

Laurel: Aha. I did not know that.  I know I have g++ installed,but how do I run it? Does g++ have a reasonable GUI? I was under the impression it was a pretty low-level application, that wouldn't necessarily have a GUI of any sort... 

But then I don't actually know anything.


*******EDIT*******

I already have 'build essential' installed.

---

### Post by LaurelLynn on 2007-04-11
Dear Neon_Knight,

g++ has serveral!

The big one is Eclipse from IBM, very Visual Studioesc in proportions.  Most people think of it as for Java, but it has plug-ins for many languages.  The Welcome screen has an icon on it that looks like a chalkboard. It leads to some excellent tutorials.

Anjuta is an IDE specifically for C++.

Another tool I love is Glade for building GUIs.

I personally directed the writing of a neworked real-time radar anaysis sytem that used to be attached to military radars. 

We used nothing but a gedit like editor, and a command line compiler. So don´t feel you need an integrated environment unless you like them.

---

### Post by Neon_Knight on 2007-04-11
Yes, well I feel alot more comfortable using an integrated environment, I don't particularly like messing with text editors and compilers and not knowing where things are going wrong and loading the wrong file and blah blah blah de blah. (I had horrible experiences learning HTML that way, with notepad and Internet Explorer)

Automatix just so happens to have Anjuta, as I only just installed it from another thread talking about VMplayer. So I'll install that and go moo.

Oh, just one last thing, I have installed the Allegro repositories, does that mean that anjuta will automatically be able to load all of the Allegro functions, or is there more I have to do?

---

### Post by LaurelLynn on 2007-04-11
Anjunta and Allegro will be separate downloads.  I doubt that either depends on the other.

Good Luck, and Enjoy!

---

### Post by Neon_Knight on 2007-04-12
so, how can I then get Allegro to work with Anjuta? I've compiled it and everything, with "Configure", "make" , and "make install", does that mean now I can use the Allegro finctions? Or what else is there? Do I have to add it specifically in Anjuta?

---

### Post by LaurelLynn on 2007-04-12
Dear Neon_Knight,

Take a look at this forum, someone new is basically asking the same questions you have:

[http://www.allegro.cc/forums/thread/589877/647120#target](http://www.allegro.cc/forums/thread/589877/647120#target)

Note that it starts:

[INDENT]I am using Ubuntu and used synaptic to install ALL allegro packages.[/INDENT]

They don´t come with Ubuntu, so they need to be installed first, as I described above.
The text shows an example of compiling the program from the command line, and explains how to link in the Allegro libraries.

As to using it with Anjuta.  I have to confess that I have only installed that IDE to try it out, and removed it a few days latter, not that it wasn´t good, it just wasn´t better for me than what I was already using.  As to Allegro, I have not used it before, I only know what I´m reading on the web, and that implies it should works like any other library.

I myself use gedit and the command line for short and simple stuff (because it is often faster). And Eclipse for bigger projects. Partly because I work in Java a lot. Mostly because it´s backed by IBM, so skill in using it translates into more job opportunities. It works with a lot of languages, and has many useful 3rd party plugins. It can be a bit slow though and uses a lot of memory.  For graphical programming I use Glade or OpenGL.

For more info on Anjuta and Allegro, I would recommend looking at the project websites, they have manuals, freqently asked questions lists, and forums specifically for people using them (and hence smarter than me :( ):

[http://anjuta.sourceforge.net/](http://anjuta.sourceforge.net/)
[http://alleg.sourceforge.net/](http://alleg.sourceforge.net/)

This site also seems to be a useful source of Allegro information:

[http://www.allegro.cc/about](http://www.allegro.cc/about)

If you have any more problems using g++, or installing the libraries, I will be happy to help if I can :D

---

