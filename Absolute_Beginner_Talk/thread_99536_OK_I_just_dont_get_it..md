---
title: "OK I just dont get it."
date: 2005-12-05
forum: Absolute Beginner Talk
---

### Post by spin1078 on 2005-12-05
I just cant understand how to install programs.  all this tarball gz stuff.  i Mean, java2 for instance.  I have a bin.  so i unpack it into a folder.  now what?  its not installed even though i installed it.  yey.  i type all these commands, unpack things, uncompress them and get files that do nothing.  what the heck?  I am very computer literate, i been doing support for 6 years professionally and many years before that on my own.  I just cant understand the linux deal.  Id love the OS if I could install stuff.  I like everything else alot more than windows

oh and my wheel mouse doesnt scroll.  I dont understand where you get/install drivers either.  Im lucy synaptic is so friggin easy or i couldnt do anything on Ubuntu but check mail and chat on AIM.

---

### Post by 23meg on 2005-12-05
See this for software installation in general: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Follow the instructions given here to install Java: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

For your mouse problem, state the brand, model and connection method of your mouse, and attach a copy of your /etc/X11/xorg.conf file.

---

### Post by spin1078 on 2005-12-05
it scrolls in terminal but not in Firefox.  its not a driver issue.  I just want a site to go to that can interactively teach me or give step by step commands and let me test them.  some kind of tutor or something.  its feels so crappy being a windows expert then an infant at this.  i feel naked lol.

---

### Post by spin1078 on 2005-12-05
heres another issue.  the ubunto wiki site says to 

sudo apt-get install fakeroot java-package java-common

i get

root@ubuntu:~/files/java2# sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
root@ubuntu:~/files/java2#


look at what im trying here.  I know its gotta be syntax.  also im not jsut trying to find out how to get it to work, why it works is important.

root@ubuntu:~# cd /home/bradd
root@ubuntu:~# ls
Desktop  files  harddrive  musicshare
root@ubuntu:~# cd files
root@ubuntu:~/files# cd java2
root@ubuntu:~/files/java2# ls
jre1.5.0_05  jre-1_5_0_05-linux-i586.bin
root@ubuntu:~/files/java2# cd jre1.5.0_05
root@ubuntu:~/files/java2/jre1.5.0_05# ls
bin  CHANGES  COPYRIGHT  javaws  lib  LICENSE  man  plugin  README  THIRDPARTYLICENSEREADME.txt  Welcome.html
root@ubuntu:~/files/java2/jre1.5.0_05# sudo apt-get install fakeroot java-package java-common
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
root@ubuntu:~/files/java2/jre1.5.0_05# cd..
bash: cd..: command not found
root@ubuntu:~/files/java2/jre1.5.0_05# ls
bin  CHANGES  COPYRIGHT  javaws  lib  LICENSE  man  plugin  README  THIRDPARTYLICENSEREADME.txt  Welcome.html
root@ubuntu:~/files/java2/jre1.5.0_05# cd ..
root@ubuntu:~/files/java2# sudo apt-get install fakeroot jre-1_5_0_05-linux-i586.bin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package jre-1_5_0_05-linux-i586.bin
root@ubuntu:~/files/java2# ls
jre1.5.0_05  jre-1_5_0_05-linux-i586.bin
root@ubuntu:~/files/java2# sudo apt-get install fakeroot jre1_5_0_05-linux-i586.bin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package jre1_5_0_05-linux-i586.bin
root@ubuntu:~/files/java2# sudo apt-get install fakeroot jre-1_5_0_05-linux-i586.bin
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package jre-1_5_0_05-linux-i586.bin
root@ubuntu:~/files/java2# sudo apt-get install fakeroot jre1.5.0_05
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package jre1.5.0_05
root@ubuntu:~/files/java2#

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=spin1078]it scrolls in terminal but not in Firefox.  its not a driver issue.  I just want a site to go to that can interactively teach me or give step by step commands and let me test them.  some kind of tutor or something.  its feels so crappy being a windows expert then an infant at this.  i feel naked lol.[/QUOTE]
In the address bar, type "about: config" then search for "mouse".  There should be some option like middlemousescrollbarposition.  Set that to true if it is not.

---

### Post by spin1078 on 2005-12-05
I'll try it.

btw heres what I got so far on java2

root@ubuntu:~/files/java2# chmod +x jre-1_5_0_05-linux-i586.bin
root@ubuntu:~/files/java2# sudo apt-get install fakeroot
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  fakeroot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/90.6kB of archives.
After unpacking 340kB of additional disk space will be used.

Preconfiguring packages ...
^[ORSelecting previously deselected package fakeroot.
(Reading database ... 71605 files and directories currently installed.)
Unpacking fakeroot (from .../fakeroot_1.5.1ubuntu2_i386.deb) ...

Setting up fakeroot (1.5.1ubuntu2) ...

root@ubuntu:~/files/java2# ls
jre-1_5_0_05-linux-i586.bin
root@ubuntu:~/files/java2# sudo apt-get java-package
E: Invalid operation java-package
root@ubuntu:~/files/java2# sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
root@ubuntu:~/files/java2# sudo apt-get install java-common
Reading package lists... Done
Building dependency tree... Done
java-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:~/files/java2# sudo apt-get install java-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
root@ubuntu:~/files/java2#


now I am following the directions.  I think i got the hang of it but why is the java-pakage not working.  did the web page mean the install bin file, not literally java-package?

---

### Post by Estariel on 2005-12-05
Hi!

There are generally two different ways to install packages on linux.

One way is to use the distribution's package manager. In Ubuntu's case that's apt. (apt-get install blablabla)
This will install packages from the Ubuntu CD's and any server that is listed in apt's configuration file.
Only files ending in .deb can be installed in this way. Only .deb files are packages for an apt based distribution. (Other distributions often use a different package manager which uses .rpm files).

Thus, you cannot install a tarball (.tar.gz file) using apt. Neither can apt install a .bin file.

Installing these files is the second way of installing software on your system. Everything that is not one of ubuntu's .deb files is unsupported software. Installing these files may or may not work without much hassle.

It is a lot harder than using apt, it can cause system inconsistencies and thus I discourage to install anything without using apt as long as you don't know what you are doing.

If you want to do it anyways, here is how:

A .bin file is usually an executable file. If you open a terminal, change your directory to the .bin file and issue the following command
```
chmod +x filename.bin
``` this makes linux "see" the file as an executable.
```
./filename.bin
```
the executable will be executed. "./" means execute the following file that is sitting in the directory I'm in.

A .tar.gz file usually contains a programs uncompiled source code. To run it, you must extract the code and compile it yourself. If you are missing libraries to compile it, you must track these down on your own, there is no tool to do it for you. Doing this is highly annoying.
If you want to do it anyways, here is how:
To compile the program you do the following:
Usually, there is a file in the base directory of the .tar.gz file that is named "configure". Execute it, then start the compiler:
```
./configure
make
make install

```

For your needs, I would suggest following the links that were given in other posts, in order to find the ubuntu .deb  repositories for java. Then you can apt-get install it.
This is the easiest way, it is the least error prone one, and usually, there is a .deb file for every program you possinly want to install.

Btw: you should not download the .deb files by yourself, but let apt do it for you. This is done by adding the server on which the .deb files is to your sources.list file. How this is done is also written in the documentation that already got linked in a post above.

Good luck and have fun with your new operating system

Estariel

Edit:
why don't you just use blackdown java?
```
sudo apt-get install j2re1.4
```

If you insist on using sun's java, please type the following in a terminal:
```
cat /etc/apt/sources.list
```
and paste the output in here.

Edit2: forgot making the .bin file executable. thanks CPUFreak91

---

### Post by CPUFreak91 on 2005-12-05
[QUOTE=spin1078]I just cant understand how to install programs.  all this tarball gz stuff.  i Mean, java2 for instance.  I have a bin.  so i unpack it into a folder.  now what?  its not installed even though i installed it.  yey.  i type all these commands, unpack things, uncompress them and get files that do nothing.  what the heck?  I am very computer literate, i been doing support for 6 years professionally and many years before that on my own.  I just cant understand the linux deal.  Id love the OS if I could install stuff.  I like everything else alot more than windows[/QUOTE]

Well for the bin you have to make it executable (chmod +x) or right click on the file > Properties > Permissions  and check all the executable boxes
Then execute it (click on it. Default: Double click, or use the console and cd to the directory where it's located and type: bash <filename>)

For the tar.gz stuff (I'd recommend apt-get or Synaptic for most of what you'd need with new repositories if you don't have em)
you unpack it, go to a console, 'cd' into the directory and then type configure, then make (if all goes well) then make install)

---

### Post by spin1078 on 2005-12-05
now i get this:

bradd@ubuntu:/$ cd home
bradd@ubuntu:/home$ cd bradd
bradd@ubuntu:~$ cd files
bradd@ubuntu:~/files$ cd java2
bradd@ubuntu:~/files/java2$ ls
jre-1_5_0_05-linux-i586.bin
bradd@ubuntu:~/files/java2$ chmod +x jre-1_5_0_05-linux-i586.bin
bradd@ubuntu:~/files/java2$ fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
/usr/bin/fakeroot: line 150: make-jpkg: command not found
bradd@ubuntu:~/files/java2$ sudo apt-get install java-package
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
bradd@ubuntu:~/files/java2$ jpkg
bash: jpkg: command not found
bradd@ubuntu:~/files/java2$

---

### Post by Estariel on 2005-12-05
> 
If you insist on using sun's java, please type the following in a terminal:
```
cat /etc/apt/sources.list
```
and paste the output in here.


You probably haven't switched multiverse on.
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by spin1078 on 2005-12-05
Ok, so I have CHMOD'd it and I have all the repositories on.  I even went into Synaptic and made sure the java-common and jpackage utils are installed.

I really appriciate the explaination of the "making it executable." I understand things a lot better now.  Lemme give this another shot.  Maybe I will uninstall it (another mountain to conquer) and install blackdown java.  is it better in some way?

---

### Post by spin1078 on 2005-12-05
allright so I chmod'd it.  and ./ it.  so it extracted all these files to a folder (which I have goten this far before but atleast i understand how.  I deleted the folder and started over again so this is the 2nd or 3rd time i have reached this point.)  so...NOW WHAT ? lol.

---

### Post by spin1078 on 2005-12-05
also, do I have to install it as root?  or with sudo?  because the last 4 things say permission denied.

---

### Post by Estariel on 2005-12-05
Hi!
you shouldn't execute the .bin file. If you want to install sun's java, please follow the manual; installing it by hand is hard and probably your system won't even know that you have java installed when you are done.

The problem here is that sun's java is not part of the regular ubuntu distribution since it is not open source. therefore, it is quite hard to install.

Blackdown on the other hand is open source, part of multiverse, and easy to install. It is not as good as sun's java though.
I have blackdown installed, and all my java programs run without problems. I think azureus (the popular bittorrent client) has problems with Blackdown though (I don't have azureus installed, so I don't really know)...

Back on topic, I would suggest that you just install Blackdown.
If you really really want Sun's java, we need to solve the java-package problem, since I REALLY don't want to try installing this thing by hand.

Therefore please post that sources.list file, it's not that hard ;)

---

### Post by spin1078 on 2005-12-05
ooh another question, how can I test to see if it is installed?

---

### Post by Estariel on 2005-12-06
go to a terminal and type

```
javac
``` (this calls the java compiler).

If it says "command not found" it is not installed. If it displays a help notice on how to use the java compiler, it is installed.

---

