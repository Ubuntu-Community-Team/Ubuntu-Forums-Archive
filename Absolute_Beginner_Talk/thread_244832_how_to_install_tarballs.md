---
title: "how to install tarballs?"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by gerfuls on 2006-08-27
i need full directions. im a total noob!:KS

---

### Post by Metacarpal on 2006-08-27
[This how-to]("http://monkeyblog.org/ubuntu/installing/#source") should get you through it!  :) 

In fact, [this page in general]("http://monkeyblog.org/ubuntu/installing/") is good to read.

---

### Post by 3rdalbum on 2006-08-27
It depends WHAT is in your tarball.

Have you tried following the instructions in the INSTALL file which is inside the tarball? Where did things go wrong in that?

The reason I ask is because the usual ./configure, make, make install routine doesn't work when the tarball contains a binary, or it contains source that needs to be compiled with Jam, Scons or some other build system.

---

### Post by lunamystry on 2007-08-23
I am REALLY confused by this  tarball thing. I am trying to install a disk recovery program and it is in tar.bz2 and when i follow the instructions on some sites on how to install tar Ii does not work.

This is what i tried, i downloaded the file from the website, I stoed it to the desktop. I then tried to find a way to install the file and found a couple of tutorials that said i first have to extract the files then run the command ./configure
I did that and I am told there is no such directory or file. Why? The link above basically told me the same thing. Extract and run ./configure which does not work or maybe i should include somthing else in the command what? 

 how do i install Photorec? I need some folders that I was going to get aroound to backing up but accidentaly deleted. 

HELP!!!

---

### Post by Tyke91 on 2007-08-23
extract the tarball (ubuntu has a gui tool for this) and then look inside the tarball for a README or INSTALL text file... open that, and follow instructions :)

---

### Post by dwhitney67 on 2007-08-23
If you like to use the command line, issue the following command:

```
$ tar xjfv *TarBallName*.tar.bz2
```

If you have a Tarball with the "gz" or "tgz" extension, then the command is:

```
$ tar xzfv *TarBallName*.tar.gz
```

The 'v' option given to the tar command is optional, however it's nice to use so that you can tell where things are being installed.  It stands for "verbose".

For more info on tar, read the man-page.

---

### Post by mysticmatrix on 2007-08-23
Ok let me it clear point by point.

1) Tarballs(.tar.gz or sometimes .tgz) ate NOT INSTALLERS
2) What they are is simply a folder and/or files compressed. Pretty much like .rar, .zip and several other formats.
3) Now Tarballs usally, NOT ALWAYS, contain source codes of programs. Those might then be compiled to install the program.
4) If you are sure it is source code, right click on the downloaded file and click extract here.
5) Inside the extracted folder, there might be a README or INSTALL file which basically list the procedure in some technical language.

Having said all this, compiling from source is something Noobs must not try. Find out if the program has a installer in form .deb that you can double click and install.

EDIT: If you can tell us what program are you trying to install, perhaps someone might help :)

---

### Post by lunamystry on 2007-08-23
No good, i extracted the files and there was a readme text in there but it had no installation instructions. It only said that photorec works on linux and freebds and some other things but no instructions. Unless the instructions are in the doc folder which has a whole lot og files which i don't know.

Okay i downloaded some other file from the photorec site(  I think) and it had the install text. Now my problem is this:


I think I am going to write an instruction manual on how to install tarballs after this. :-)

---

### Post by r4ik on 2007-08-23
Maybe this helps,

[http://www.monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif](http://www.monkeyblog.org/ubuntu/videos/Source_install_muinescrobbler.gif)

Good luck !

---

### Post by mysticmatrix on 2007-08-23
Ok as I get it, the software is Photorec and you got it from here. [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

If that is true, I'll try to see how it works on my PC and help ypu.

---

### Post by dwhitney67 on 2007-08-23
> **mysticmatrix said:**
> 
Having said all this, compiling from source is something Noobs must not try.
Must not try??? That's ridiculous!  Sure, it's not for everyone to try, but a better statement would be "should be avoided unless necessary".

---

### Post by mysticmatrix on 2007-08-23
Ok so as it turned out to be, it was NOT A SOURCE CODE.

Guess that time to rejoice as you don't have to compile anything.
So back to point, follow this.

1)Download the Linux .tar.gz to **your desktop**
2) Right click on downloaded compressed file and choose 'Extract here'
3) Now open a terminal and **maximize it.**
4) Type(Or copy paste)

```
cd /home/<your username>/Desktop/testdisk-6.8/linux
```

Replace <your username> by the user name you use to login
5) Type 
```
sudo ./photorec_static
```

Please tell me if that still doesn't works

---

### Post by lunamystry on 2007-08-23
Third month into linux and I am loving it. I got the tar thing going, i think i can do it better now than I ever could. Actually I know I can. :)

What i came across now I am still trying to figure out. I get this message when I run

> lunamystry@alexis:~/Desktop/testdisk-6.8$ make check
Making check in src
make[1]: Entering directory `/home/lunamystry/Desktop/testdisk-6.8/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -Wall -MD -Wpointer-arith -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wshadow -Wwrite-strings -W -Wcast-align -Waggregate-return -Wbad-function-cast -Wcast-qual -Wundef -Wredundant-decls -Wsign-compare -Wnested-externs -Winline -Wdeclaration-after-statement -MT file_jpg.o -MD -MP -MF ".deps/file_jpg.Tpo" -c -o file_jpg.o file_jpg.c; \
        then mv -f ".deps/file_jpg.Tpo" ".deps/file_jpg.Po"; else rm -f ".deps/file_jpg.Tpo"; exit 1; fi
file_jpg.c: In function &#8216;header_check_jpg&#8217;:
file_jpg.c:67: warning: unused parameter &#8216;safe_header_only&#8217;
file_jpg.c: In function &#8216;file_check_jpg&#8217;:
file_jpg.c:404: error: &#8216;my_source_mgr&#8217; undeclared (first use in this function)
file_jpg.c:404: error: (Each undeclared identifier is reported only once
file_jpg.c:404: error: for each function it appears in.)
file_jpg.c:404: error: &#8216;src&#8217; undeclared (first use in this function)
file_jpg.c:405: error: expected expression before &#8216;)&#8217; token
file_jpg.c:344: warning: unused variable &#8216;infile&#8217;
make[1]: *** [file_jpg.o] Error 1
make[1]: Leaving directory `/home/lunamystry/Desktop/testdisk-6.8/src'
make: *** [check-recursive] Error 1
lunamystry@alexis:~/Desktop/testdisk-6.8$ 

What do i need? iI don't know most of the stuff in that.

---

### Post by lunamystry on 2007-08-23
> **mysticmatrix said:**
> Ok so as it turned out to be, it was NOT A SOURCE CODE.

Guess that time to rejoice as you don't have to compile anything.
So back to point, follow this.

1)Download the Linux .tar.gz to **your desktop**
2) Right click on downloaded compressed file and choose 'Extract here'
3) Now open a terminal and **maximize it.**
4) Type(Or copy paste)

```
cd /home/<your username>/Desktop/testdisk-6.8/linux
```

Replace <your username> by the user name you use to login
5) Type 
```
sudo ./photorec_static
```

Please tell me if that still doesn't works

With the tar.gz files there are three and I am not sure which one to take. i previously downloaded the tar.bz2 files and tried to, i guess, compile. Which one do i download? does it matter?

---

### Post by r4ik on 2007-08-23
Pick a rpm and read,

[http://www.psychocats.net/ubuntu/installingsoftware#rpm](http://www.psychocats.net/ubuntu/installingsoftware#rpm)

Good luck !

---

### Post by lunamystry on 2007-08-23
It appers despite my optimisism luck is not on my side today. Two usb damaged by my PC I am guessing. The one does not show folders that were suppose to have been copied into it. the second does not open in windows anymore. I do not know why. I am now trying to install a file recoverer to try and recover the files that do not appear in the one flash in vain it would seem. When I use the .rpm file I get this error message:

lunamystry@alexis:~/Desktop$ sudo alien -i testdisk-6.8-1.i386.rpm
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
lunamystry@alexis:~/Desktop$    

What am I missing? A key? How do I get it? :-(

---

### Post by lunamystry on 2007-08-23
> **mysticmatrix said:**
> Ok so as it turned out to be, it was NOT A SOURCE CODE.

Guess that time to rejoice as you don't have to compile anything.
So back to point, follow this.

1)Download the Linux .tar.gz to **your desktop**
2) Right click on downloaded compressed file and choose 'Extract here'
3) Now open a terminal and **maximize it.**
4) Type(Or copy paste)

```
cd /home/<your username>/Desktop/testdisk-6.8/linux
```

Replace <your username> by the user name you use to login
5) Type 
```
sudo ./photorec_static
```

Please tell me if that still doesn't works

**Does not work.**

---

### Post by r4ik on 2007-08-23
Tried to install it on my Debian system and trashed it.
Dont worry it's not you i am a egghead.

---

### Post by Ink-Jet on 2007-08-23
> **mysticmatrix said:**
> Ok so as it turned out to be, it was NOT A SOURCE CODE.

Guess that time to rejoice as you don't have to compile anything.
So back to point, follow this.

1)Download the Linux .tar.gz to **your desktop**
2) Right click on downloaded compressed file and choose 'Extract here'
3) Now open a terminal and **maximize it.**
4) Type(Or copy paste)

```
cd /home/<your username>/Desktop/testdisk-6.8/linux
```

Replace <your username> by the user name you use to login
5) Type 
```
sudo ./photorec_static
```

Please tell me if that still doesn't works
You could just use /home/$USER/Desktop...

Just a tad easier.

---

### Post by dwhitney67 on 2007-08-23
> **lunamystry said:**
> It appers despite my optimisism luck is not on my side today. Two usb damaged by my PC I am guessing. The one does not show folders that were suppose to have been copied into it. the second does not open in windows anymore. I do not know why. I am now trying to install a file recoverer to try and recover the files that do not appear in the one flash in vain it would seem. When I use the .rpm file I get this error message:

lunamystry@alexis:~/Desktop$ sudo alien -i testdisk-6.8-1.i386.rpm
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
warning: testdisk-6.8-1.i386.rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
lunamystry@alexis:~/Desktop$    

What am I missing? A key? How do I get it? :-(

It's just a handful of warnings, not errors.  What are you installing, an application?  If so, see if it is present on your system.  Use the command line to run:

$ which app-name


P.S.  Your other post about the compilation errors tells me that either the tarball you obtained is missing source code, or your system is missing a dependent header file (probably from another package).

---

### Post by mysticmatrix on 2007-08-24
> **lunamystry said:**
> With the tar.gz files there are three and I am not sure which one to take. i previously downloaded the tar.bz2 files and tried to, i guess, compile. Which one do i download? does it matter?


Well I am telling these instructions for the third link from top which reads

[IMG]http://www.cgsecurity.org/os/linux.png[/IMG] Linux, tar.bz2. [http://www.cgsecurity.org/testdisk-6.8.linuxstatic.tar.bz2](http://www.cgsecurity.org/testdisk-6.8.linuxstatic.tar.bz2)

---

### Post by lunamystry on 2007-08-24
> **dwhitney67 said:**
> It's just a handful of warnings, not errors.  What are you installing, an application?  If so, see if it is present on your system.  Use the command line to run:

$ which app-name


P.S.  Your other post about the compilation errors tells me that either the tarball you obtained is missing source code, or your system is missing a dependent header file (probably from another package).

The application I am trying to install is in the:   /usr/sbin/photorec  directory. How do i run it? it does not appear in new applications. Is it installed? I am too frustrated to google an explanation of the directories right now. I stayed up all night trying to install the thing and I am no better off then when i began.

---

### Post by Bout to Snap on 2007-08-24
> **lunamystry said:**
> No good, i extracted the files and there was a readme text in there but it had no installation instructions. It only said that photorec works on linux and freebds and some other things but no instructions. Unless the instructions are in the doc folder which has a whole lot og files which i don't know.

Okay i downloaded some other file from the photorec site(  I think) and it had the install text. Now my problem is this:


I think I am going to write an instruction manual on how to install tarballs after this. :-)

i was browsing(figured i;d try to help) ima noob myself ...anyway i noticed a RPM download of the software, If i were you i would download that and click the help link on your desktop and use the information provided there.

example:

click help icon (blue with ? mark)

then click on adding removing software

then click on installing a single package

If you read on down it will show you how to convert a RPM file into a Deb file

deb file is what you need will make installation auto (Less headache)

---

### Post by lunamystry on 2007-08-24
I downloaded the .rpm and i installed it. IF it is installed it does not show on the new applications menu and when I try katapult and alt+F2 to run it also does nothing. I also wrote the url /usr/sbin/photorec and it asked if i was sure i wanted to run the program i clicked yes then nothing.

---

### Post by Bout to Snap on 2007-08-24
> **lunamystry said:**
> I downloaded the .rpm and i installed it. IF it is installed it does not show on the new applications menu and when I try katapult and alt+F2 to run it also does nothing. I also wrote the url /usr/sbin/photorec and it asked if i was sure i wanted to run the program i clicked yes then nothing.

Nice to know that you got it installed unfortunatley like i said im new to ubuntu also i would have no idea what command in terminal to type to get it running however you might be able to try this.

Right click on Applications.

then click on Edit Menus

In the menu section click the appropriate one(would tell you specifically but have no idea where the program would be

after finding the program select it by check marking the box afterwards it should be added to the menu

---

### Post by mysticmatrix on 2007-08-24
> **lunamystry said:**
> I downloaded the .rpm and i installed it. IF it is installed it does not show on the new applications menu and when I try katapult and alt+F2 to run it also does nothing. I also wrote the url /usr/sbin/photorec and it asked if i was sure i wanted to run the program i clicked yes then nothing.

Well first of all, this is a command line application and hence I don't think it will run anywhere but terminal. 
As I don't think you got my instructions previously, I have created a video of the procedure. Please view the video at [http://www.esnips.com/doc/f4e9b296-9675-4c75-90f7-1a28d44a1f49/out](http://www.esnips.com/doc/f4e9b296-9675-4c75-90f7-1a28d44a1f49/out) 

If you still face problems, tell me what errors are you getting?

---

### Post by lunamystry on 2007-08-24
Thank you!!:o

---

### Post by mysticmatrix on 2007-08-24
Just in case anyone is having problem for not being able to view video file, you may find other formats(Xvid,avi) at 
[http://www.esnips.com/web/VideosforUbuntu](http://www.esnips.com/web/VideosforUbuntu)

---

### Post by lunamystry on 2007-08-25
I can't play the video for some reason. I don't have compiz because I remember It does not allow me to watch videos. This used to happen when I had compiz it  only shows a blue screen as shown on the picture. 

More on tarballs, why does the ./configure thing work for boot screens and icons that I downloaded from KDE-look? They don't have read me files or install instruction in them. what command do I use for them, because for the one I used ./inst and it worked, but I cant use it again for some reason. Is it that different people use different ways to save the tarballs?

---

