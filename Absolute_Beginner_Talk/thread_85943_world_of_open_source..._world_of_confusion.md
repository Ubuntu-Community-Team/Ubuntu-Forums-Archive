---
title: "world of open source... world of confusion?"
date: 2005-11-03
forum: Absolute Beginner Talk
---

### Post by ecto on 2005-11-03
I have been using ubuntu for about two or three months now and quite pleased with the flexibility of linux and the n00b frienedly interface of ubuntu... I have learned many things thus far such as sudo apt-get, pwd, ls, several other commands, and so forth. However, I can't help but feel that I am missing out because i dont know how to build programs from source. Every program I see for linux only comes in source. Recently i downloaded the source for JWP and japanese word processor and have not touched it since... Can someone tell me how to build source? A general process perhaps so i can compile other programs with such a method? Any information would be good. Please help me take full advantage of this brave new world of open source.
 An ubuntu user,
 Bryan
P.S. If you have any information on how to set up a Pen and mouse tablet please visit my other [http://www.ubuntuforums.org/showthread.php?t=80721](http://www.ubuntuforums.org/showthread.php?t=80721)

---

### Post by Manny C on 2005-11-03
Don't know about pen and mouse tablet. But to build stuff from source, you need to[LIST=1]
[*] Untar the archive (say it is called foo.tar.bz2). ```
 tar jxvf foo.tar.bz2 
```
[*]Change directory to where the archive was unpacked (say foo/). Make sure you have all the dependencies and produce some make files ```
 cd foo 
``` and then ```
./configure --prefix=/usr/local 
``` You may not have all the dependencies. In this case look at the output and see what header/library packages you need. Typically need the build-essential and checkinstall packages: ```
 sudo apt-get install build-essential checkinstall
```. Checkinstall produces a .deb archive of program and installs this.
[*]Once this process is finished, issue the following commands ```
 make && sudo checkinstall 
```[/LIST]Hope this helps.

---

### Post by moffa on 2005-11-03
When you download a source package, usually there is a README file.  First I read that then in most cases you just run ./configure in that path.  It'll start to compile and all you do is sit there. The main problem I have with source packages is that there are many errors you get because of dependencies on other packages.  This generally requires me to install 5 packages to install the one I want.

Well after the ./configure, then you usually type "make install" without the quotes.  Thats generally it.

Just a tip, when running ./configure, once it stops read the last couple of lines to see if there was an error.  Otherwise, it usually compiled fine.

---

### Post by ecto on 2005-11-03
Thank you for the help...Also it would be helpful (i learned from a recent experience) it is helpful to have libl1.2-dev and libpng12-dev nasm. Howeve does this method also work if the source code is in C++ like JWP (japanese word processor) for example

---

### Post by poptones on 2005-11-03
Every package is going to have its own ependancies. Over time you will accumulate these. Because I am on dialup I archive every deb installed with synaptic so the next time I rebuild the system I have them.

./configure...

read the instructions. It will tell you it can't find a particular module, you can usually find it by searching synaptic for name and description, or by googling.

Once it finishes running configure, type make. If it crashes again, read the failure message.  It seems overwhelming at first because it looks like some foreign language, but the thing is you don't need to speak it you only need to be able to search for keywords or messages and follow the instructions.

Eventually it gets easier. Just remember that software you have to install from source is more likely to be unfinished (that's why it's not in the distribution) or its installation troublesome.

---

