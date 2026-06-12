---
title: "Need help getting Lexmark x75 to work"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by 4iko on 2007-12-18
It detects and installs the printer but I can not get it to print...
 I cannot load the page to download the Z600 driver,I tried with Z32 it feeds the paper but it still doesn't print
 downloaded the lxx74-cups-0.8.4.2 to desktop and extracted there but installation wasn't successful 4 some reason
 Your help will be greatly appreciated!Thanks!

---

### Post by spiderbatdad on 2007-12-18
installation was not succesful? was there an error message? What type of package was it ( ie, what were the last letters in the name, .deb, for example)?
How did you try to install it?

---

### Post by 4iko on 2007-12-18
thats the error Im getting:
 tar -xvzf lxx74-cups-0.8.4.2tar.gz
tar: lxx74-cups-0.8.4.2tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by spiderbatdad on 2007-12-18
looks like you are not in the directory of the tar file. for example, if it is on your desktop, when you open the terminal you must ```
cd Desktop
``` notice capital D.
once in the directory of the file you can untar it, then cd into the newly created folder and:```
./configure
make
sudo make install
```

also...consider clicking on the folder and looking for a readme file prior to installing. There may be special installation instructions, like using ./autogen instead of ./configure

---

### Post by spiderbatdad on 2007-12-18
also you can use the Tab Key to auto complete lines for you...makes it a lot easier when enter package names and avoids typos. just begin typing cd De   in the terminal, then hit the Tab Key. As long as you dont have several directories with names beginning with De, auto complete will finish the word Desktop. Same thing with package names, once you are in the correct working directory

---

### Post by chips24 on 2007-12-18
ummmm, the lexmark series dont work on linux. sorry

---

### Post by spiderbatdad on 2007-12-18
> **chips24 said:**
> ummmm, the lexmark series dont work on linux. sorry

really...there are drivers listed in the print configuration tool. And he has a tar.gz package. Why would these exist if the printer doesn't work with linux?

---

### Post by 4iko on 2007-12-18
> **spiderbatdad said:**
>  once in the directory of the file you can untar it, then cd into the newly created folder 
  can U pls translate to a newbie language.How do I untar and how do I cd into the newly created folder?
 Thanx

---

### Post by spiderbatdad on 2007-12-18
> **spiderbatdad said:**
> looks like you are not in the directory of the tar file. for example, if it is on your desktop, when you open the terminal you must ```
cd Desktop
``` notice capital D.
once in the directory of the file you can untar it, then cd into the newly created folder and:```
./configure
make
sudo make install
```

also...consider clicking on the folder and looking for a readme file prior to installing. There may be special installation instructions, like using ./autogen instead of ./configure

post #4 is this still unclear? and untar is the command you copied in post #2 tar -xvzf filename

you might want to try the driver in the printer config tool @ System-->Administration-->Printers

---

### Post by spiderbatdad on 2007-12-18
oh sorry...to cd into the new folder simply, while the terminal is open (assuming you're doing everything on your desktop ```
cd begin typing folder name and hit tab key
``` then enter. once this is all done you can trash all this stuff from your desktop

---

### Post by 4iko on 2007-12-18
That's clear.I did this and that's what happened:
 kokich@kokich-desktop:~$ cd Desktop/
kokich@kokich-desktop:~/Desktop$ tar -xvzf lxx74-cups-0.8.4.2.tar.gz
lxx74-cups-0.8.4.2/
lxx74-cups-0.8.4.2/lpoptions
lxx74-cups-0.8.4.2/lxx74.convs
lxx74-cups-0.8.4.2/lxx74.drv
lxx74-cups-0.8.4.2/lxx74.install
lxx74-cups-0.8.4.2/lxx74.types
lxx74-cups-0.8.4.2/Makefile
lxx74-cups-0.8.4.2/version
lxx74-cups-0.8.4.2/rastertolxx74
lxx74-cups-0.8.4.2/rastertolxx74.c
lxx74-cups-0.8.4.2/self-portrait.out.gz
lxx74-cups-0.8.4.2/testprint.ps
lxx74-cups-0.8.4.2/lxx74.ppd.gz
kokich@kokich-desktop:~/Desktop$ 
 but what do U mean by cd into the newly created folder
 What do I type next?
sorry 4 the dumb questions but I just installed Ubuntu less than a week ago 4 first time in my life...

---

### Post by spiderbatdad on 2007-12-18
you should see a new folder on the desktop of the same name as the package```
cd name of new folder
```

then:```
./configure
make
sudo make install
```

these are not dumb questions. and not long ago I was right where you are now in terms of understanding how to handle packages. if you've closed the terminal, you'll need to```
cd Desktop/lxx (tab key)
```

---

### Post by 4iko on 2007-12-18
OK.I'm following your instructions and I'm getting nowhere
 kokich@kokich-desktop:~$ cd Desktop/
kokich@kokich-desktop:~/Desktop$ tar -xvzf lxx74-cups-0.8.4.2.tar.gz
lxx74-cups-0.8.4.2/
lxx74-cups-0.8.4.2/lpoptions
lxx74-cups-0.8.4.2/lxx74.convs
lxx74-cups-0.8.4.2/lxx74.drv
lxx74-cups-0.8.4.2/lxx74.install
lxx74-cups-0.8.4.2/lxx74.types
lxx74-cups-0.8.4.2/Makefile
lxx74-cups-0.8.4.2/version
lxx74-cups-0.8.4.2/rastertolxx74
lxx74-cups-0.8.4.2/rastertolxx74.c
lxx74-cups-0.8.4.2/self-portrait.out.gz
lxx74-cups-0.8.4.2/testprint.ps
lxx74-cups-0.8.4.2/lxx74.ppd.gz
kokich@kokich-desktop:~/Desktop$ cd lxx74-cups-0.8.4.2/
kokich@kokich-desktop:~/Desktop/lxx74-cups-0.8.4.2$ ./configure
bash: ./configure: No such file or directory
kokich@kokich-desktop:~/Desktop/lxx74-cups-0.8.4.2$

---

### Post by spiderbatdad on 2007-12-18
./configure  is a separate command as is make and sudo make install, but first you must be in the correct working directory...open the terminal and type:```
cd Desktop/lxx (then hit the tab key to complete the line
``` then hit enter
then type```
./configure
``` then hit enter
then ```
make
```then enter
then```
sudo make install
```

---

### Post by spiderbatdad on 2007-12-18
ahh there is no ./configure file...try to ```
make
sudo make install
``` those are separate commands. also try clicking on the folder and looking for a readme file with instructions for this package. Tar packages can be a pain if you are not used to them. They have quirks and differences. A .deb is always best choice for Ubuntu as it self installs by clicking on it. Have you tried using the driver x73 in the printer configuration tool?

---

### Post by cp1969 on 2007-12-18
[http://ubuntuforums.org/showthread.php?t=340735&highlight=lexmark](http://ubuntuforums.org/showthread.php?t=340735&highlight=lexmark)

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X75](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-X75)

You might find some help there.

Also, here is some info on doing a CUPS installation from the OpenPrinting site:

[http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation](http://www.linux-foundation.org/en/OpenPrinting/Database/CUPSDocumentation)

---

### Post by 4iko on 2007-12-19
BINGO!After few days of struggle trying to get my printer to work I finally figured it out.
 Who said Lexmark don't work on Linux?
 OMG!I can't believe it works!!!
I was so desperate and disappointed I even thought about giving uncle Bill $100 & helping him in his attempt to reclaim the first spot as the richest man in the world.Sorry uncle Bill,not this time...
 I was so desperate I even thought about suicide...just kiddin'...thanks for all of your help guys!U saved my life!
  Here's what worked for me,hopefully it will help other newbies too:
 
 kokich@kokich-desktop:~$ sudo apt-get install libcupsimage2-dev libcupsys2-dev libtiff4-dev libtiffxx0c2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcupsys2-dev is already the newest version.
The following extra packages will be installed:
  libjpeg62-dev libpng12-dev
The following NEW packages will be installed:
  libcupsimage2-dev libjpeg62-dev libpng12-dev libtiff4-dev libtiffxx0c2
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 978kB of archives.
After unpacking 3228kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libpng12-dev 1.2.15~beta5-2ubuntu0.1 [172kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libtiffxx0c2 3.8.2-7ubuntu2 [5036B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libjpeg62-dev 6b-14 [188kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main libtiff4-dev 3.8.2-7ubuntu2 [555kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main libcupsimage2-dev 1.3.2-1ubuntu7.1 [58.6kB]
Fetched 978kB in 6s (142kB/s)                                                  
Selecting previously deselected package libpng12-dev.
(Reading database ... 102711 files and directories currently installed.)
Unpacking libpng12-dev (from .../libpng12-dev_1.2.15~beta5-2ubuntu0.1_i386.deb) ...
Selecting previously deselected package libtiffxx0c2.
Unpacking libtiffxx0c2 (from .../libtiffxx0c2_3.8.2-7ubuntu2_i386.deb) ...
Selecting previously deselected package libjpeg62-dev.
Unpacking libjpeg62-dev (from .../libjpeg62-dev_6b-14_i386.deb) ...
Selecting previously deselected package libtiff4-dev.
Unpacking libtiff4-dev (from .../libtiff4-dev_3.8.2-7ubuntu2_i386.deb) ...
Selecting previously deselected package libcupsimage2-dev.
Unpacking libcupsimage2-dev (from .../libcupsimage2-dev_1.3.2-1ubuntu7.1_i386.deb) ...
Setting up libpng12-dev (1.2.15~beta5-2ubuntu0.1) ...
Setting up libtiffxx0c2 (3.8.2-7ubuntu2) ...

Setting up libjpeg62-dev (6b-14) ...
Setting up libtiff4-dev (3.8.2-7ubuntu2) ...

Setting up libcupsimage2-dev (1.3.2-1ubuntu7.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kokich@kokich-desktop:~$ cd Desktop/lxx74-cups-0.8.4.2
kokich@kokich-desktop:~/Desktop/lxx74-cups-0.8.4.2$ make
gcc -g -c rastertolxx74.c
gcc -o rastertolxx74 rastertolxx74.o -lz -lcupsimage -lcups
kokich@kokich-desktop:~/Desktop/lxx74-cups-0.8.4.2$ sudo make install
bash lxx74.install
Installation done.

 OMG!I'm so happy!U cannot imagine how happy I am!

---

### Post by 4iko on 2007-12-19
Well...it prints OK now but there's a very weird printing problem.It splits every page in two...printing the left half on the right and the right side on the left???
 All settings seem fine ..maybe it's the resolution which is set to 600 DPI but when I click on it there is no any other option...the only thing I can change in "Printing options" is the media size - from letter to A4..I cannot change .Color Mode (set to Color)  & Resolution (set at 600 dpi) at all.
 Is that where the problem is...?  Any ideas?
 Thanks!

---

### Post by stchman on 2007-12-19
> **4iko said:**
> It detects and installs the printer but I can not get it to print...
 I cannot load the page to download the Z600 driver,I tried with Z32 it feeds the paper but it still doesn't print
 downloaded the lxx74-cups-0.8.4.2 to desktop and extracted there but installation wasn't successful 4 some reason
 Your help will be greatly appreciated!Thanks!

The Lexmark Z600 series of printers are paperweights according to openprinting.org.  The Lexmark Z32 works partially under Linux according to the same site.  This is typical for Lexmark to not support Linux.  That is why I do not buy Lexmark printers.

---

