---
title: "Help to install a program please"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by ron999 on 2006-08-18
Hi

I'm trying to install GNUDoku game on Ubuntu 6.06 Dapper Drake.
I've downloaded file
gnudoku_0.93-2_i386
from
[http://icculus.org/~jcspray/GNUDoku/](http://icculus.org/~jcspray/GNUDoku/)

But when I run the file I get reply
Error: Dependency is not satisfiable: libglibmm-2.4-1

What do I do now please?

Ron

---

### Post by waldschm on 2006-08-18
Just wanted to be check, but did you download the .deb file from the website or the source tarball? If you did download the .deb and it isn't working you are probably missing this library and should install it by going to Synaptic and searching for the file name.

---

### Post by Klaidas on 2006-08-18
First, yo should check if that program is in Ubuntu's reposities. (packages.ubuntu.com)
if it is, just do 
> sudo apt-get install program-name

If there is no program, use the one you downloaded.
As I understand, the program need a depency which is not installed (?).
Try > sudo apt-get install libglibmm-2.4-1

And try to install again :)

---

### Post by aysiu on 2006-08-18
It will be in the repositories for Edgy but not Dapper: > Package gnudoku

    * edgy (games): A program for creating and solving SuDoku puzzles [universe]
      0.93-1: amd64 i386 powerpc

---

### Post by ron999 on 2006-08-18
Hi waldschm and Klaidas

GDUduko is not listed in Syanptic.

When I try to install the dependency I get:-

sudo apt-get install libglibmm-2.4-1
Reading package lists... Done
Building dependency tree... Done
Package libglibmm-2.4-1 is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libglibmm-2.4-1c2a
E: Package libglibmm-2.4-1 has no installation candidate
ron@ron-desktop:~$


But the packages libglibmm-2.4-1c2a and libglibmm-2.4-dev are already installed.

Any more ideas please?

Ron

ps typo, package name is GNUdoku, not GDUduko

---

### Post by ron999 on 2006-08-19
Hi

Has anyone any ideas how I can install this GNUDoku program on Dapper Drake, or is it a no-no until Edgy Eft is released?

Ron

---

### Post by harisund on 2006-08-19
Welcome to the world of dependancy hell :)

Anyway, I used the source and a package called checkinstall to create a i386 binary. Tell me if it works at [http://harisund.com::8680/~misc](http://harisund.com::8680/~misc)

Install it using the standard dpkg --install method. If it doesn't work, let me know. If it does, please let me know as well :)

A couple of suggestions. Don't generally expect to be able to download a .deb package from the web and successfully install it. Perhaps in Debian, but definitely not in Ubuntu. 

Second, when possible, search in the repositories. I know, in this case the package wasn't in the repositories, and sometimes you might need a version newer than what is in the repos. But still. 

Third, just like in Windows where you download and double click on a .exe file, in Linux you download a .tar.gz file and compile it. In most cases, the author would have provided a uninstall option for the package. But preferrably, in the final stage use checkinstall and create a .deb package so that not only can you distribute it (as in use on other machines with the same architecture) but you can also uninstall it neatly.

---

### Post by ron999 on 2006-08-19
Thanks harisund

I've installed the deb and it's put a shortcut in my games menu - but it won't run.
Can you tell me where the program will have been installed and is there a command that I can use at the terminal instead of the shortcut?

---

### Post by harisund on 2006-08-19
To what did you put a shortcut in the Games menu? 

The executable name is GNUdoku. Hit capital G in your terminal, and hit tab, the bash shell will automatically complete the command, and most likely the only command that begins with an upper case G in your machine will be GNUdoku game. 

Once you get the binary name right, create a shortcut in your Games menu for the file /usr/bin/GNUdoku. I think the entire path /usr/bin is required.

Alternative you can hit Alt+F2 to open up a run dialog box, and enter GNUdoku to play the game.

---

### Post by ron999 on 2006-08-19
Hi harisund
I didn't set up the shortcut, it just appeared, or maybe it's from an aborted install that I tried before.
I've looked in the etc/bin folder and can't see anything that looks like our program. When I use the terminal I get:-
GNUDoku
GNUDoku: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open sh ared object file: No such file or directory
ron@ron-desktop:~$

Any suggestions?
Ron

ps I've just tried alt F2 method and nothing happened

---

### Post by harisund on 2006-08-19
First, try installing the following packages, and check if it works again: 
sudo apt-get --yes install libgtkmm-2.4-dev

If it doesn't, hmm... ok never mind. Apparently a .deb I created for you doesn't necessarily work in your machine. Sorry to have wasted your time. 

Do the following. 

1. Download the .tar.gz file from the website. 
2. make sure the libgtkmm-2.4-dev library is installed (you should have installed it from previously). 
3. Untar the package. Go into the folder, run make and then run sudo make install. You will be good to go. 

When done, do make uninstall and the package will no longer exist in your system

---

### Post by ron999 on 2006-08-19
Hi harisund
It's working!

I followed your instructions, more or less-
Unticked shortcut from games menu using alacarte
Completely removed GNUDoku using synaptic
Installed library using:- sudo apt-get --yes install libgtkmm-2.4-dev
Then installed program using sudo dpkg -i /home/ron/Desktop/gnudoku-0.93_0.93-1_i386.deb

Now it's installed it ok, with a shortcut in games menu.
I can start it using the shortcut, or GDUDoku at the terminal or with alt f2.

It looks like the 2.4 dev library wasn't already installed, I thought it was.

So your deb file works ok, I'll save it on a floppydisk.

Just one more thing, I've looked in usr/bin folders and I can't find the program (yet), is there an easy way to locate a program?

Best wishes
Ron

---

### Post by harisund on 2006-08-19
Yes, the easiest way to find out where the executable file is, is to execute 'whereis GNUdoku' on the commandline. 

On a side not, if you want to find out all the files that a package installed, do 'dpkg --listfiles package_names'. In this case I think you would do 'dpkg --listfiles GNUdoku', if not, search for the exact package name using 'dpkg --list | grep GNUdoku' and then use that package name for listfiles. 

Also, check my signature for the post on dealing with packages.

---

### Post by ron999 on 2006-08-19
Hi harisund
Whereis and list | grep don't recognize GNUDoku, but it's not a problem, I can search again at a later date. Perhaps it's saved as some other name.
I've bookmarked the Package Management post to digest later too.
There are two other Sudoku programs that I've tried, KSudoku 0.3 and GNOME Sudoku 0.5.0, but I think this GNUDoku is going to be the best.

Thanks for all your help
Ron

---

### Post by harisund on 2006-08-19
What is the output of ```
dpkg --list | grep oku
```

---

### Post by ron999 on 2006-08-19
Hi harisund
The output shows all three sudoku games, so it's in there somewhere!
Here:-
dpkg --list | grep oku
ron@ron-desktop:~$ dpkg --list | grep oku
ii  contact-lookup-applet                  0.14-0ubuntu1    contact lookup applet for GNOME
ii  finger                                 0.17-9    user information lookup program
ii  gnome-sudoku                           0.5.0-1    A puzzle game for the popular Japanese sudok
ii  gnudoku-0.93                           0.93-1    GNUDoku game?
ii  ksudoku                                0.3-4    sudoku puzzle generator/solver
ron@ron-desktop:~$

---

### Post by harisund on 2006-08-19
Ok, so gnudoku-0.93 is the name of the package. 

Now execute 'dpkg --listfiles gnudoku-0.93'

I don't know how to create packages. Naturally, the file name is kind of funny. But otherwise, you should be good to go

---

### Post by ron999 on 2006-08-19
Hi harisund

Found it!

ron@ron-desktop:~$ dpkg --listfiles gnudoku-0.93
/.
/usr
/usr/local
/usr/local/bin
/usr/local/bin/GNUDoku
/usr/local/share
/usr/local/share/applications
/usr/local/share/applications/GNUDoku.desktop
/usr/local/share/pixmaps
/usr/local/share/pixmaps/GNUDoku.png
/usr/share
/usr/share/doc
/usr/share/doc/GNUDoku-0.93
/usr/share/doc/GNUDoku-0.93/COPYING
/usr/share/doc/GNUDoku-0.93/Changelog
/usr/share/doc/GNUDoku-0.93/README
/usr/share/doc/GNUDoku-0.93/TODO
ron@ron-desktop:~$

It's there in /usr/local/bin It's GNUDoku 70.8KB executable.
Sorted!
Thanks again

---

### Post by harisund on 2006-08-19
Yep! You are now good to go.

---

