---
title: "Installing LAN Driver - Need Help"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-04-03
Hello All!

I have the following problem:

I am trying to get some LAN out of Ubuntu.

My ASUS's Text file says the following:

> 3  Prerequisites
==================
The prerequisites for compilation, loading and patch creation of the
sk98lin driver are:

- Any device using the sk98lin kernel module needs to be closed.

- The old sk98lin kernel module needs to be unloaded.
  Per default the installation script will do this automatically
  (if "user mode" installation is selected). 
  If you want to shutdown and unload the old sk98lin kernel module
  manually, run the script in "expert installation" mode.

- Your system has to be equipped with a supported network card. 
  Without a card the full driver functionality cannot be checked.

- The kernel source and kernel version have to be consistent. 
  For instance, it might be, that you run kernel version 2.4.20, but 
  the header files the kernel module will be compiled with refer to 
  kernel version 2.4.21. If you don't have the same kernel version, 
  install the sources and compile a new kernel. It's not possible to 
  mix different kernel versions!

I performed a "uname -r" & found that my kernel is:

> 2.6.12-9-386

I try with the following command to install the ASUS LAN drivers:

root@ubuntu:/usr/src/DriverInstall# sh install.sh

And get the following:

> 
Installation script for sk98lin driver.
Version 7.06 (Aug-20-2004)
(C)Copyright 2003-2004 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) user installation    3) generate patch
2) expert installation  4) exit
Choose your favorite installation method:

Here, I type: 1

Installation continues...

> 
Please read this carfully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel
module. This script will do this automatically per default.
If you want to shutdown and unload the old sk98lin kernel module
manually, run the script in the EXPERT mode.

Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) 

Here I type: y

Installation continues...

> 
Create tmp dir (/tmp/Sk98ISnjLZmNciogqALXnlaAb)                 [   OK   ]
Check user id (0)                                                              [   OK   ]
Check kernel version (2.6.12-9-386)                                     [   OK   ]
Check kernel symbol file (/proc/kallsyms)                               [   OK   ]
Check kernel type                                                               working
Check kernel type (SP)                                                      [   OK   ]
Check architecture (found)                                                 [   OK   ]
Set architecture (i386)                                                      [   OK   ]
Check compiler (/usr/bin/gcc)                                             [   OK   ]
Check mcmodel flags (32bit)                                               [   OK   ]
Check module support (/sbin/insmod)                                    [   OK   ]
Check make (/usr/bin/make)                                                [   OK   ]
Check archive file (sk98lin)                                                  [   OK   ]
Check kernel gcc version (3.4.5) (Kernel:3.4.5 != gcc:4.0.2)      [ failed ]
Check sk98lin driver availability (not loaded)                            [   OK   ]
Check kernel header files (not found)                                      [ failed ]
Kernel header not found. Please install the linux header files
development package or crate a symbolic link from the
/usr/src/KERNEL_VERSION directory to linux
     Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

Installation of sk98lin driver module failed.
Delete temp directories (done)                                              [   OK   ]

root@ubuntu:/usr/src/DriverInstall#


Whad do I do here?

Any ideas?

I am stuck with this:

> The kernel source and kernel version have to be consistent. 
  For instance, it might be, that you run kernel version 2.4.20, but 
  the header files the kernel module will be compiled with refer to 
  kernel version 2.4.21. If you don't have the same kernel version, 
  install the sources and compile a new kernel. It's not possible to 
  mix different kernel versions!

As I said before, I performed a "uname -r" & found that my kernel is:

> 2.6.12-9-386

But from Synaptic Manager, I see that:

a. My "linux-headers" are > 2.6.12-9-386

b. My "linux-kernel-headers" are > 2.6.11.2

So, my Ubuntu Kernel version & my "linux-kernel-headers" version are Different...

_Question_:
Do I need to "Downgrade" my Ubuntu's Kernel to proceed with the installation of my LAN's drivers?

And How would I do that?

My Ubuntu PC is a 64bit, but I have installed the Regular Desktop Ubuntu 5.10 (Gnome) Breezy.

Thanks.

---

### Post by Pragmatist on 2006-04-04
Based on these:
>  Check kernel gcc version (3.4.5) (Kernel:3.4.5 != gcc:4.0.2)      [ failed ]


>  Kernel header not found. Please install the linux header files
 development package or crate a symbolic link from the
 /usr/src/KERNEL_VERSION directory to linux
      Example: **ln -s /usr/src/KERNEL_VERSION /usr/src/linux**


I would try doing the two things that are suggested and then see if that works:

1.) upgrade your gcc version to 4.0.2 

2.) make the symbolic link: **ln -s /usr/src/KERNEL_VERSION /usr/src/linux**

---

### Post by dvarsam on 2006-04-04
[QUOTE=Pragmatist]Based on these:

I would try doing the two things that are suggested & then see if that works:

1. Upgrade your gcc version to 4.0.2 

2.Make the symbolic link: **ln -s /usr/src/KERNEL_VERSION /usr/src/linux**[/QUOTE]

Hello!

And thank you for your Reply!!!

1. For Uprading the "gcc" to version 4.0.2, I searched on Synaptic & found Nothing!!!

According to my Synaptic, I have the "gcc-4.0-base" which is an Installed Version "4.0.1-4ubuntu9".

So, I am missing the "0.0.1" - lol :D

What "line" do I have to Add on my "sources.list" file to be able to see the "4.0.2" & then go ahead & install it?

2. You mean specifialy type this:

> ln -s /usr/src/$(uname -r) /usr/src/linux


Sorry for being a newbie - I am 2 months in my Ubuntu & struggling to learn...
But honestly, I am trying hard on this...
And I am a good student, I visit this Forum EVERY DAY!!!
So, at least I do my homeworkl!!!

Please Help.......

Thanks.

---

### Post by Pragmatist on 2006-04-04
I'm getting a little ahead of myself.  First, let me know some more about your device:
 
  Brand = ASUS
  Model = ?
  Type of Device = router? network card?
 
 My system has gcc 4.0.2 and the only thing I did for gcc was upgrade my system.  Try this:
 
 ```
sudo apt-get update
```  
 and then
 
 ```
sudo apt-get upgrade
```  
 When everything is finished try this:
 
 ```
gcc --version
```  
 Forget about the symbolic link for now.

---

### Post by dvarsam on 2006-04-04
> **Pragmatist]I'm getting a little ahead of myself.  First, let me know some more about your device:
 
  Brand = ASUS
  Model = ?
  Type of Device = router? network card?
[/QUOTE]

Brand = ASUS
Model = P5LD2-VM (VM means with onboard VGA Graphics Adaptor)
LAN = Onboard Gigabit LAN (with Intel's Gigabit LAN controller)

Router = US Robotics - Model: 9107 

Note:
My Router is setup fine.
I am writing this to you now, behind the Router...
So, it should NOT be a Router Problem...

> 
My system has gcc 4.0.2 & the only thing I did for gcc was upgrade my system.
Try this:
 
 ```
sudo apt-get update
```  

And then:
 
 ```
sudo apt-get upgrade
```  
 When everything is finished try this:
 
 ```
gcc --version
```


ok, I think, I know now what is the problem with my "gcc" version...

After a format, I always DID a "sudo apt-get update" ONLY!

I did NOT perform a "sudo apt-get upgrade" to my Ubuntu...

On the TOP Right of my Ubuntu Screen it says:

> There are 96 updates available

The reason I did NOT "sudo apt-get upgrade" is this:
I format my Ubuntu often (a bad habit I inherited from Windows).

So, I tend to perform a "sudo apt-get update", but NOT a "sudo apt-get upgrade".

Since, whenever I get into trouble, I tend to Re-install my Ubuntu, I though:

Why should I bother do a "sudo apt-get upgrade"?

It takes me a long time & therefore I try to avoid the downloading...

I have now found a way to Backup those Packages Downloaded...
So whenever in the near future I decide to format my Ubuntu, at least, I do NOT have to download the "apt-get upgrade" packages again!
I will only have to perform JUST the Installation... (& that is a quick procedure - :D ).

I have finished performing the "sudo apt-get upgrade" & my "gcc" version, now is:

[QUOTE]gcc (GCC) 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
Copyright (C) 2005 Free Software Foundation, Inc.
This is free software said:**
> 

Looks like it is: "gcc 4.0.2" now!
 
[QUOTE]Forget about the symbolic link for now.

Ok, whatever you say dude! ;)

Thanks for all your help, man!

Without you, I would be: ](*,) 

P.S.> Sorry for the late reply, but it took forever to "sudo apt-get upgrade"...

---

### Post by Pragmatist on 2006-04-04
In looking around some more, I think I found what your really looking for:

This site says you need this package for the driver:  **e1000-6.1.16.tar.gz**
[http://www.linux-tested.com/results/asus_P5LD2-VM.html](http://www.linux-tested.com/results/asus_P5LD2-VM.html)

You can download it here:
[http://sourceforge.net/project/showfiles.php?group_id=42302](http://sourceforge.net/project/showfiles.php?group_id=42302)

---

### Post by dvarsam on 2006-04-04
[QUOTE=Pragmatist]I think I found what your really looking for:
This site says you need this package**e1000-6.1.16.tar.gz**
[http://www.linux-tested.com/results/asus_P5LD2-VM.html](http://www.linux-tested.com/results/asus_P5LD2-VM.html)
You can download it here:
[http://sourceforge.net/project/showfiles.php?group_id=42302](http://sourceforge.net/project/showfiles.php?group_id=42302)[/QUOTE]

Dear Pragmatist,

Thank you for your reply!

Let me please start with this:
You asked me to perform a "sudo apt-get upgrade"...
Of course as I told you I do NOT have Internet on that PC...
That PC will only have Internet, when I FIX the LAN, which hopefully we will do together...
So, instead of performing a "sudo apt-get upgrade", I did this:

1. Downloaded the Packages from another PC.
2. Copied them to a CD-Rom.
3. Moved them to the PC that we are trying to get its LAN work.
4. Perform a "dpkg -i xxxxxx.deb" to install the Packages.

As you understand, I had to install 96 Packages...(with 96 diff "dpkg -i" commands)...

Only later did I notice that due to Dependencies, I had ERRORS & some stuff did NOT install...

At least, ALL I can say, is that the "gcc --version" (the version you asked for), meaning version 4.0.2, seems to be installed!!!

Now, you suggested downloading either of the following drivers:

1. e1000-6.1.16.tar.gz, or
2. e1000-7.0.33.tar.gz

I also have the Driver that came with the CD.
So that makes (in total) 3 driver versions:

1. e1000-6.0.54.tar.gz
2. e1000-6.1.16.tar.gz
3. e1000-7.0.33.tar.gz

I decided to work with the latest version - above #3.

I "untarred" the file & read the ReadMe file, which says the following:

> February 3, 2006

To build a binary RPM* package of this driver, run 'rpmbuild -tb 
<filename.tar.gz>'.


The above does NOT work.
It creates an:> RPM build errors: bad exit status...

Then I read the following:

> 1. Move the base driver tar file to the directory of your choice.  For 
   example, use /home/username/e1000 or /usr/local/src/e1000.

2. Untar/unzip archive:

     tar zxf e1000-x.x.x.tar.gz

3. Change to the driver src directory:

     cd e1000-x.x.x/src/

4. Compile the driver module:

     make install

I move it to the Desktop, untar, get inside & type "make install".

This is what I get:> 
root@ubuntu:/home/elena/Desktop/e1000-7.0.33# cd src
root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# ls

Makefile         e1000_hw.c    e1000_osdep.h  kcompat.h
e1000.h          e1000_hw.h    e1000_param.c  kcompat_ethtool.c
e1000_ethtool.c  e1000_main.c  kcompat.c

root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make install

Makefile:65: *** Linux kernel source not found.  Stop.

root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src#

So, what do I do now man?

I am clueless about this...

PLEASE HELP - I have NO LAN for this machine & therefore NO Internet!!!

Thanks.

P.S.> This brings us back to the beginning man - right where I started...
        This is where I am getting stuck...

---

### Post by Pragmatist on 2006-04-04
Don't worry...yet! :)
 
 You don't want an RPM.  The simplest explanation is like this (I'm doing this because, while you probably know most of this, it is good to start with a clear idea of what is going on).
 
 1.) All software has source code
 2.) Code has to be compiled on your computer
 3.) It is very important to know certain things about your software like:
 
 (a) What other software (and versions of these software) does this depend on (dependencies)?
      
 (b) What version is this software?
      
 (c) Where to put different parts of the program (executables in one place, libraries in another, etc...etc...)
 
 Because of point #3, package managers have become very useful. Ubuntu is a Debian-based distribution.  There are hundreds of different distributions out there, but there are also groups that share some similarities.  Two big groups are Redhat-based distributions (distros) and Debian-based distros.  Redhat distros use RPM as their package manager and Debian distros use dpkg.  APT is a frontend (and synaptic is a frontend of apt!).  The real basis of apt is dpkg.
 Bottom line: If they gave you instructions on how to convert the package to dpkg format, that would be useful (but not necessary).  The main advantage of using a package manager is convenience (easier to uninstall, upgrade packages, keep track of things, etc...).
 
 The package is nothing more than the source code, a makefile, and some other information that helps with the conveniences I mentioned above.  You can package source code into a dpkg or a rpm and you can turn rpms and dpkg back into source code.
 
 whew!!  Ok, so now, you don't need the RPM. You have the source code.  So, as I mentioned, you must compile that code. I'm getting a little ahead of myself.  There are 3 steps you take to install a program from code:
 
 1.) Configure:  This gets everything ready.  There are scripts called (oddly enough ;) )  configure   What they do is look at your specific situation and make sure you have met the dependencies, and all other requirements.  This step produces a "Makefile" which is used in the next step.
 
 2.) Compile:  This is the real compiling (you did this first, but since you didn't run configure first, you had no Makefile).  You will notice that there is a Makefile in the directory contents.  The Makefile is crucial.  It has lots of important instructions like which compiler to use, and with what options to compile the software (some software can be compiled in different ways depending on a person's needs.  The Makefile is where you can customize things)  Take a look at the Makefile, just to see what it looks like.
 
 3.) Install: Now you got ready, you compiled the code, you only need to find a place for everything.  This step puts libraries, executables and other stuff in definite locations so the program knows where to look for them in the future.
 
 The way you run these three steps is usually like this (after you unpack the "tarball"--the file with the .tar.gz extension--which you did already and change into the newly created directory containing the code and the Makefile and the configure program):
 
 1.) ./configure
 
 2.) make
 
 3.) sudo make install
 
 Most of the time you need to use sudo when installing because executables/libraries are put in places you don't have write access to.
 
 So try this approach with your "tarball" and see what happens.

---

### Post by dvarsam on 2006-04-04
[QUOTE=Pragmatist]Don't worry...yet! :)

You have the code. 
You must compile the code.
There are 3 steps you take to install a program from code:
 
1.) ./configure
2.) make
3.) sudo make install

Most of the time you need to use sudo when installing because executables/libraries are put in places you don't have write access to.
So try this approach with your "tarball" and see what happens.[/QUOTE]

Dear Pragmatism,

                       the problem is that I have NO file named "configure" to run...

I have the following files:

> 1. src (folder)
2. e1000.7
3. e1000.spec
4. ldistrib.txt
5. LICENSE
6. README
7. SUMS

Please visit:[http://i69.photobucket.com/albums/i58/dvarsam/Screenshot1.png](http://i69.photobucket.com/albums/i58/dvarsam/Screenshot1.png)

According to the "ReadMe" file, I am supposed to go inside the "src" folder & run the commands...
So, the src (folder) contains the following:

> 01. e1000.h
02. e1000_ethtool.c
03. e1000_hw.c
04. e1000_hw.h
05. e1000_main.c
06. e1000_osdep.h
07. e1000_param.c
08. kcompat.c
09. kcompat.h
10. kcompat_ethtool.c
11. Makefile

Please visit: [http://i69.photobucket.com/albums/i58/dvarsam/Screenshot2.png](http://i69.photobucket.com/albums/i58/dvarsam/Screenshot2.png)

So, if there is NO file named "configure", that means that I can avoid this step?

After what I tried in my previous message, I decided to try this out:

> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make

Makefile:65: *** Linux kernel source not found.  Stop.

I then try:

> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# Makeinstall

-bash: Makeinstall: command not found

I then try:

> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make Makeinstall

Makefile:65: *** Linux kernel source not found.  Stop.

What the heck do I have to type to make this work?

I am clueless...

Thanks man, I appreciate!!!

---

### Post by dvarsam on 2006-04-04
Dear Pragmatist,

I also noticed this:
> NONE of My the above files in the Driver folder have EXECUTE Permissions

So I did a:[/code]chmod +x -R *[/code]

to fix this.

I hope I helped a bit...

But my problems still remain...?

---

### Post by dvarsam on 2006-04-04
Dear Pragmatist,

Before you read this, I have also created 2 more posts, so you might want to read them Too!
They are right above this post...

Listen to this:

As I told you, when I tried to type:
> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make install

Makefile:65: *** Linux kernel source not found. Stop.

I thought: what could the  "#65" refer to?
Then I thought that maybe it refers to line 65 of the file named "Makefile"...

BANG!!!

That is it!!!

Look at what Lines 64 & 65 of the file named "Makefile" say:

> ifeq (,$(KSRC))
  $(error Linux kernel source not found)

I can see that the:
> Linux kernel source not found

...is what is printed on my screen as an ERROR, when I type the "make install" command...

_The question is_:
What is the "$(KSRC)" that the IF statement is looking for?

If we find what it is, maybe we can find what is missing & install it!!!

Any clues?

P.S.> I feel I am so close to the solution now... if only I knew?](*,)

---

### Post by Pragmatist on 2006-04-04
Please show us the Makefile

---

### Post by Pragmatist on 2006-04-04
Nevermind about the Makefile. I've downloaded the package and I have the Makefile. (although attaching it here might be useful for others that see this thread)

I think your original idea was correct.  Go into synaptic and do a search with this as your keyword: [B]linux-source-2.6.9

[/B]Once you find it, install it.  Then try the **make install** again.

---

### Post by dvarsam on 2006-04-05
[QUOTE=Pragmatist]
Nevermind about the Makefile.
I've downloaded the package and I have the Makefile.
(although attaching it here might be useful for others that see this thread)

I think your original idea was correct. 
Go into synaptic and do a search with this as your keyword: **linux-source-2.6.9**
Once you find it, install it.
Then try the **make install** again.[/QUOTE]

Are you sure what I need is: > linux-source-2.6.9

And NOT: > linux-source-2.6.12.9

I am asking this because:

A. I performed a Search in the Synaptic Package Manager, for:

   1. linux-source
   2. linux-source-2.6.9
   3. linux-source-2.6.12.9

   And found NOTHING!!!

   Maybe I have to add a line in my "sources.list" file...

   Any idea, what the line should be?

B. I then performed some "yahoo-ing" Search for "linux-source-2.6.9" & found this:

   > Linux: 2.6.9 Released
   Posted by Jeremy on Tuesday, October 19, 2004 - 04:17
   Linux creator Linus Torvalds released the official 2.6.9 kernel today,...

   It seems that the version you are suggesting is Too old...
   It takes us back, 2,5 years ago...

Are you sure we are looking for: "2.6.9" and NOT "2.6.12.9"?

But, still - even if you are correct - I can't FIND any of them...

---

### Post by dvarsam on 2006-04-05
OK, I found the following:

> linux-source-2.6.12

But NOT:

> linux-source-2.6.9

Sorry, but for some reason, Some of the Repos were down!

So, I had to fix my Sources.list & perform a "Refresh" or "apt-get update".

Now I am downloading the file "linux-source-2.6.12" & will inform shortly about how it went...

Thanks man, I appreciate!!!

---

### Post by dvarsam on 2006-04-05
As I said before:

I downloaded the "linux-source-2.6.12_2.6.12-10.30_all.deb" file, Installed it & got the same St*pid message:

> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make install

Makefile:65: *** Linux kernel source not found. Stop.

It seems that Nothing has changed!!!

Any more ideas?

P.S.> The only difference with what you suggested is the version:
        You suggested version 2.6.9, which I could NOT find & I installed the version 2.6.12. Is that what is wrong?

---

### Post by dvarsam on 2006-04-05
Dear Pragmatism,

I have done some progress on this...

Let me get you up to date...
(you can read some of my previous posts too - if you like...)


I have installed the following packages:

> 1. build-essential
2. cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
3. gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb
4. gcc-3.4_3.4.4-6ubuntu8.1_i386.deb
5. linux-source-2.6.12_2.6.12-10.30_all.deb
6. linux-headers-2.6.12-10_2.6.12-10.30_i386.deb
7. linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb
8. linux-headers-386_2.6.12.16.1_i386.deb
9. linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb

Now by typing "make", I get the following:

root@ubuntu:/home/elena/Desktop# cd e1000*
root@ubuntu:/home/elena/Desktop/e1000-7.0.33# cd src
root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make

> 
make: Warning: File `Makefile' has modification time 2.3e+06 s in the future
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/elena/Desktop/e1000-7.0.33/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: Warning: File `/home/elena/Desktop/e1000-7.0.33/src/Makefile' has modification time 2.3e+06 s in the future
CC [M] /home/elena/Desktop/e1000-7.0.33/src/e1000_main.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c: In function 'e1000_set_mac':
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:2086: warning: pointer targets in passing argument 1 of 'is_valid_ether_addr' differ in signedness
CC [M] /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /home/elena/Desktop/e1000-7.0.33/src/kcompat.h:37,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_osdep.h:43,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.h:36,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.c:33:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
CC [M] /home/elena/Desktop/e1000-7.0.33/src/e1000_param.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:29:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c: At top level:
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:78: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:88: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:101: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:113: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:130: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:143: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:155: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:164: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:173: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:182: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:191: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:200: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c: In function 'e1000_check_options':
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:339: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:369: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:445: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:467: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:489: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:511: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:543: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
CC [M] /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.c:31:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
from /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.c:31:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
CC [M] /home/elena/Desktop/e1000-7.0.33/src/kcompat.o
In file included from include/linux/if_ether.h:107,
from include/linux/netdevice.h:29,
from /home/elena/Desktop/e1000-7.0.33/src/kcompat.h:37,
from /home/elena/Desktop/e1000-7.0.33/src/kcompat.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
LD [M] /home/elena/Desktop/e1000-7.0.33/src/e1000.o
make[2]: warning: Clock skew detected. Your build may be incomplete.
Building modules, stage 2.
MODPOST
CC /home/elena/Desktop/e1000-7.0.33/src/e1000.mod.o
LD [M] /home/elena/Desktop/e1000-7.0.33/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: warning: Clock skew detected. Your build may be incomplete.

Do you have any idea what can I do to FIX this error message?

Whad does:
> make: warning: Clock skew detected. Your build may be incomplete.

really mean?

Is there another Package I need to install?

Thanks.

---

### Post by Pragmatist on 2006-04-05
Your absolutely right, I meant 2.6.12  Sorry, that was a bad mistake on my part.

I'm not sure if it was good to install the headers or not. Meanwhile, I would leave whatever you installed and try and fix the Make errors one-by-one and see what we can figure out.

The clock skew error should have nothing to do with anything else we've done.  Apparently it is due to a system clock error.  I looked on [www.google.com/linux](www.google.com/linux) and typed in: Clock skew detected    This is the results page:

[http://www.google.com/linux?hl=en&lr=&q=Clock+skew+detected&btnG=Search](http://www.google.com/linux?hl=en&lr=&q=Clock+skew+detected&btnG=Search)

These suggestions look interesting:
[http://www.linuxsa.org.au/pipermail/linuxsa/1999-January/004534.html](http://www.linuxsa.org.au/pipermail/linuxsa/1999-January/004534.html)
[http://www.linuxquestions.org/questions/showthread.php?t=40364](http://www.linuxquestions.org/questions/showthread.php?t=40364)

But I would read some more sites from google and try some ideas out.  Then run Make again and post the next error here :)  (this is how Make works sometimes.  With Linux, installing software is sometimes like giving birth! :)

---

### Post by dvarsam on 2006-04-05
[QUOTE=Pragmatist]
I'm not sure if it was good to install the headers or not. Meanwhile, I would leave whatever you installed and try and fix the Make errors one-by-one and see what we can figure out.
[/QUOTE]

Dear Pragmatist:

In then meantime I have decided to Re-Format my Ubuntu & have a Clean Install...

So, please tell me anything you would like me to install, cause everything is now clean & ready & awaiting your instructions...

Shoot me with anything you want me to install...

System is clean & waiting your orders...man!

Thanks!

---

### Post by Pragmatist on 2006-04-05
What packages did you choose to install from the installer?

Just so you know, I'm not sure that starting over will change the situation with your system clock.

---

### Post by dvarsam on 2006-04-05
[QUOTE=Pragmatist]What packages did you choose to install from the installer?

Just so you know, I'm not sure that starting over will change the situation with your system clock.[/QUOTE]

I had installed the following packages:

Quote:
1. build-essential
2. cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
3. gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb
4. gcc-3.4_3.4.4-6ubuntu8.1_i386.deb
5. linux-source-2.6.12_2.6.12-10.30_all.deb
6. linux-headers-2.6.12-10_2.6.12-10.30_i386.deb
7. linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb
8. linux-headers-386_2.6.12.16.1_i386.deb
9. linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb

All those from ".deb" files with "dpkg -i" command...

Bud I had also performed a "dpkg -i" install on all "apt-get" upgrade packages...

Because of dependencies, that created errors though...

Now, that I have a clean install, I can see for example:

gcc-4.0 through Synaptic (instead of the gcc-3.4 before)
cpp-4.0 through Synaptic (instead of the cpp-3.4 before)

What do you think?

---

### Post by Pragmatist on 2006-04-05
Read this:

[https://wiki.ubuntu.com/CompilingSoftware?action=show&redirect=ConfigureMakeMakeInstall](https://wiki.ubuntu.com/CompilingSoftware?action=show&redirect=ConfigureMakeMakeInstall)

---

### Post by dvarsam on 2006-04-05
[QUOTE=Pragmatist]Read this:

[https://wiki.ubuntu.com/CompilingSoftware?action=show&redirect=ConfigureMakeMakeInstall](https://wiki.ubuntu.com/CompilingSoftware?action=show&redirect=ConfigureMakeMakeInstall)[/QUOTE]

As you understand, I do NOT have Internet on that maching, so using "apt-get" is out of the question...

A working LAN will provide my way, out to the outside world...

I am currently writing to you from a different PC...

Should I go with Synaptic's gcc-4.0

Do you want me to install the header files or not?

From the list I provide above - starting from 1-9, what do you want me to install?
Do you want me to prefer newer package-versions compared to old, or just stick with the old ones?

Thanks.

---

### Post by Pragmatist on 2006-04-05
I think that by reinstalling you might not have changed much.  You still need to compile the driver!  You'll still probably have problems compiling the driver!  This is the nature of compiling from source.

So really, you just need to get that e1000 tarball and unpack it and follow the instructions and come back when you hit a wall! :)

---

### Post by dvarsam on 2006-04-05
[QUOTE=Pragmatist]I think that by reinstalling you might not have changed much.  You still need to compile the driver!  You'll still probably have problems compiling the driver!  This is the nature of compiling from source.

So really, you just need to get that e1000 tarball and unpack it and follow the instructions and come back when you hit a wall! :)[/QUOTE]

Ok, then I will try to prefer newer package versions instead of older ones, cause you never know, older ones could have flaws...

I will get back soon...

---

### Post by Pragmatist on 2006-04-05
>  Originally Posted by: **dvarsam**
_I had installed the following packages_:
 
 Quote:
 1. build-essential
 2. cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
 3. gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb
 4. gcc-3.4_3.4.4-6ubuntu8.1_i386.deb
 5. linux-source-2.6.12_2.6.12-10.30_all.deb
 6. linux-headers-2.6.12-10_2.6.12-10.30_i386.deb
 7. linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb
 8. linux-headers-386_2.6.12.16.1_i386.deb
 9. linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb

Did you install these or not?  If you have NOT installed them, then I would  start by just installing these: 

1. build-essential
2. linux-source-2.6.12_2.6.12-10.30_all.deb

>  Originally Posted by: **dvarsam **
As you understand, I do NOT have Internet on that maching, so using "apt-get" is out of the question...

Actually, you could use apt-get.  You set up your /etc/apt/sources.list file to use your CD:

Backup your /etc/apt/sources.list file
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.BAK
```

Add this line to your /etc/apt/sources.list file:
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

Then comment out (put a # at the beginning of the line) every line but the one you just added.

Save the file and now try using apt-get

---

### Post by Pragmatist on 2006-04-05
make sure you run **sudo apt-get update** after you edit your /etc/apt/sources.list file.

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist,

I tried to run "make" without these installed:

> 6. linux-headers-2.6.12-10_2.6.12-10.30_i386.deb
7. linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb
8. linux-headers-386_2.6.12.16.1_i386.deb

And I get the following error (sound familiar?):

> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make

Makefile:65: *** Linux kernel source not found. Stop.

So it seems to me that the above 3 packages are _Required_.

You suggested to avoid these...

You want me to install them & try again?

Thanks.

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist,

I decided to go ahead & installed the above 3 files (I will mention them again - just to keep things simple):
> 6. linux-headers-2.6.12-10_2.6.12-10.30_i386.deb
7. linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb
8. linux-headers-386_2.6.12.16.1_i386.deb

And _ONLY_ then was I able to run the "make" command...

So, I got the following output:

root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make

> make: Warning: File `Makefile' has modification time 2.2e+06 s in the future
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/elena/Desktop/e1000-7.0.33/src modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: Warning: File `/home/elena/Desktop/e1000-7.0.33/src/Makefile' has modification time 2.2e+06 s in the future
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_main.o
In file included from include/asm/system.h:5,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/kernel.h:10:20: error: stdarg.h: No such file or directory
In file included from include/asm/system.h:5,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:17,
                 from include/linux/thread_info.h:21,
                 from include/linux/spinlock.h:12,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/kernel.h:94: error: syntax error before 'va_list'
include/linux/kernel.h:95: warning: function declaration isn't a prototype
include/linux/kernel.h:98: error: syntax error before 'va_list'
include/linux/kernel.h:99: warning: function declaration isn't a prototype
include/linux/kernel.h:102: error: syntax error before 'va_list'
include/linux/kernel.h:103: warning: function declaration isn't a prototype
include/linux/kernel.h:107: error: syntax error before 'va_list'
include/linux/kernel.h:108: warning: function declaration isn't a prototype
include/linux/kernel.h:119: error: syntax error before 'va_list'
include/linux/kernel.h:120: warning: function declaration isn't a prototype
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c: In function 'e1000_set_mac':
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:2086: warning: pointer targets in passing argument 1 of 'is_valid_ether_addr' differ in signedness
make[2]: *** [/home/elena/Desktop/e1000-7.0.33/src/e1000_main.o] Error 1
make[1]: *** [_module_/home/elena/Desktop/e1000-7.0.33/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2

This above stupid thing, seems to be asking again for "gcc-3.4" - which a downgrade from what I have (e.g. "gcc-4.0")...

Look at the beginning lines:

> /usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[1]: gcc-3.4: Command not found

So I think I have to go now & install that "gcc-3.4" (downgrade)...:( 

What do you think?

Thanks.

P.S.> I know it is a downgrade..., but what else can I do?

---

### Post by Pragmatist on 2006-04-05
I'm still not sure you should use those header files.  Let me see something:

```
ls -l /usr/src
```
```
ls -l /lib/modules
```

---

### Post by Pragmatist on 2006-04-05
Ok, here is what I would do if I really wanted to know EXACTLY what the problem is:
First go into the directory where the Makefile is and then do this:
1. Backup a copy of the Makefile (cp Makefile BACKUP_Makefile)
2. Edit the Makefile  (gedit Makefile)
3. Add echo lines to find out what exactly is happening as the Makefile goes through.

For example:
> 
###########################################################################
# Environment tests

# Kernel Search Path
# All the places we look for kernel source
KSP :=  /lib/modules/$(BUILD_KERNEL)/source \
        /lib/modules/$(BUILD_KERNEL)/build \
        /usr/src/linux-$(BUILD_KERNEL) \
        /usr/src/linux-$($(BUILD_KERNEL) | sed 's/-.*//') \
        /usr/src/kernel-headers-$(BUILD_KERNEL) \
        /usr/src/kernel-source-$(BUILD_KERNEL) \
        /usr/src/linux-$($(BUILD_KERNEL) | sed 's/\([0-9]*\.[0-9]*\)\..*/\1/') \
        /usr/src/linux

# prune the list down to only values that exist
# and have an include/linux sub-directory
test_dir = $(shell [ -e $(dir)/include/linux ] && echo $(dir))
KSP := $(foreach dir, $(KSP), $(test_dir))


Now you add some echo lines to print out the content of variables to yourself to see the real progress of the Makefile:

In the above example, the Makefile is trying to create a variable called KSP and it should hold the Kernel Search Path for your system.  Lets see what it is using by putting these lines in:

echo The value of KSP is: $KSP

Put them wherever you'd like to know the progress.  I would put them in every possible place in the above code to see the assignment of that variable So the code becomes:
> 
 ###########################################################################
 # Environment tests
 
 # Kernel Search Path
 # All the places we look for kernel source

**echo The value of BUILD_KERNEL is: $BUILD_KERNEL**

 KSP :=  /lib/modules/$(BUILD_KERNEL)/source \
         /lib/modules/$(BUILD_KERNEL)/build \
         /usr/src/linux-$(BUILD_KERNEL) \
         /usr/src/linux-$($(BUILD_KERNEL) | sed 's/-.*//') \
         /usr/src/kernel-headers-$(BUILD_KERNEL) \
         /usr/src/kernel-source-$(BUILD_KERNEL) \
         /usr/src/linux-$($(BUILD_KERNEL) | sed 's/\([0-9]*\.[0-9]*\)\..*/\1/') \
         /usr/src/linux
 **echo The value of KSP is: $KSP**
 # prune the list down to only values that exist
 # and have an include/linux sub-directory
 test_dir = $(shell [ -e $(dir)/include/linux ] && echo $(dir))
 KSP := $(foreach dir, $(KSP), $(test_dir))
**echo The value of KSP is: $KSP**
 

Notice I also printed out the value of the BUILD_KERNEL variable _before_ it is used to create the KSP variable.

---

### Post by Pragmatist on 2006-04-05
Two more improvements in this 'trace' method:

1.) make the text more descriptive:  Instead of "The value of...is..." do something like "echo Before KSP BUILD_KERNEL is: $BUILD_KERNEL" This way your printout describes **where** the variables are (sometimes your checking variable assignment at different points in the code)

2.) Output the echo lines to a file for easy reading.  For this just add **>> filename** at the end of each line. So this:

"echo Before KSP BUILD_KERNEL is: $BUILD_KERNEL"

Becomes this:
"echo Before KSP BUILD_KERNEL is: $BUILD_KERNEL >> filename"

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist,

Sorry for the late reply, but I found something that hopefully you will _REALLY_ like & I think that IF you compare to the page 2 of this Thread, it might help you understand more... & identify the problem...

So here it is...
(Sorry it took me long to reply - and I have _NOT_ yet read your repplies - but since I had a Clean System I had to experiment on SOME other PC to find what would the correct order be, to install those ".deb" files correctly... & without dependency Errors... - I wanted to keep the PC as clean as possible...)

As I told you, I can NOT "apt-get"...

So I had to downgrade from "gcc-4.0" to "gcc-3.4" to compile...

So I did...!

I run the file named "orderofinstall.sh" which contains the following commands:
(this is what took me sooo long...)

> #!/bin/bash

## Order of Installation:

# We will have to install the package "gcc-3.4-base" first, becase
# the package "cpp-3.4" requires it.
dpkg -i gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb


# Note: "cpp-3.4" Requires the package "gcc-3.4-base".
# So, it MUST be installed after that!
dpkg -i cpp-3.4_3.4.4-6ubuntu8.1_i386.deb

dpkg -i gcc-3.4_3.4.4-6ubuntu8.1_i386.deb

dpkg -i linux-source-2.6.12_2.6.12-10.30_all.deb


Now, what is _VERY-VERY_ _Interesting_ is THIS Output:

> root@ubuntu:/home/elena/Desktop# sh orderofinstall.sh
tar: ./md5sums: time stamp 2006-03-06 21:56:06 is 4918087 s in the future
tar: ./control: time stamp 2006-03-06 21:56:05 is 4918086 s in the future
tar: .: time stamp 2006-03-06 21:56:06 is 4918087 s in the future
Selecting previously deselected package gcc-3.4-base.
(Reading database ... 72545 files and directories currently installed.)
Unpacking gcc-3.4-base (from gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb) ...
Setting up gcc-3.4-base (3.4.4-6ubuntu8.1) ...
tar: ./md5sums: time stamp 2006-03-06 21:56:09 is 4918085 s in the future
tar: ./control: time stamp 2006-03-06 21:56:09 is 4918085 s in the future
tar: .: time stamp 2006-03-06 21:56:09 is 4918085 s in the future
Selecting previously deselected package cpp-3.4.
(Reading database ... 72552 files and directories currently installed.)
Unpacking cpp-3.4 (from cpp-3.4_3.4.4-6ubuntu8.1_i386.deb) ...
Setting up cpp-3.4 (3.4.4-6ubuntu8.1) ...
tar: ./md5sums: time stamp 2006-03-06 21:57:28 is 4918163 s in the future
tar: ./control: time stamp 2006-03-06 21:57:27 is 4918162 s in the future
tar: .: time stamp 2006-03-06 21:57:28 is 4918163 s in the future
Selecting previously deselected package gcc-3.4.
(Reading database ... 72559 files and directories currently installed.)
Unpacking gcc-3.4 (from gcc-3.4_3.4.4-6ubuntu8.1_i386.deb) ...
Setting up gcc-3.4 (3.4.4-6ubuntu8.1) ...
tar: ./postinst: time stamp 2006-03-11 19:35:21 is 5341636 s in the future
tar: ./control: time stamp 2006-03-11 19:37:12 is 5341747 s in the future
tar: .: time stamp 2006-03-11 19:37:12 is 5341747 s in the future
Selecting previously deselected package linux-source-2.6.12.
(Reading database ... 72615 files and directories currently installed.)
Unpacking linux-source-2.6.12 (from linux-source-2.6.12_2.6.12-10.30_all.deb) ...
Setting up linux-source-2.6.12 (2.6.12-10.30) ...


Notice what it says at some points again&again:

> tar: .: time stamp 2006-03-11 19:37:12 is 5341747 s in the future

Something about a date set in the future...

If you can compate this outcome with what I got on "Page 2" of this thread (which I am retyping now), might help you solve this...

_Page 2 Outcome_:

>  make: warning: Clock skew detected. Your build may be incomplete.

So, the "date set in the future" & the "clock skew detected" must mean something...

Any ideas?

But it seems that THIS is the problem!!!

Thanks.

P.S.> I feel that we are really getting somewhere here...!!!:D

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist:

I am giving you what your requested:

1. The output of "ls -l /usr/src" command, is:

> root@ubuntu:/home/elena/Desktop# ls -l /usr/src

total 39460
drwxr-xr-x  18 root root     4096 Jan  8 22:58 linux-headers-2.6.12-9
drwxr-xr-x   4 root root     4096 Jan  8 22:58 linux-headers-2.6.12-9-386
-rw-r--r--   1 root root 40351275 Mar 11  2006 linux-source-2.6.12.tar.bz2

2. The output of "ls -l /lib/modules" command is:

> root@ubuntu:/home/elena/Desktop# ls -l /lib/modules

total 4
drwxr-xr-x  6 root root 4096 Jan  8 22:58 2.6.12-9-386
root@ubuntu:/home/elena/Desktop#

Do they help any?

P.S.> Sorry, but I do NOT have any clue what we are doing here...

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist:

I am giving you what your requested:

1. The output of "ls -l /usr/src" command, is:

> root@ubuntu:/home/elena/Desktop# ls -l /usr/src

total 39460
drwxr-xr-x  18 root root     4096 Jan  8 22:58 linux-headers-2.6.12-9
drwxr-xr-x   4 root root     4096 Jan  8 22:58 linux-headers-2.6.12-9-386
-rw-r--r--   1 root root 40351275 Mar 11  2006 linux-source-2.6.12.tar.bz2

2. The output of "ls -l /lib/modules" command is:

> root@ubuntu:/home/elena/Desktop# ls -l /lib/modules

total 4
drwxr-xr-x  6 root root 4096 Jan  8 22:58 2.6.12-9-386
root@ubuntu:/home/elena/Desktop#

Do they help any?

P.S.> Sorry, but I do NOT have any clue what we are doing here...

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist:

I am giving you what your requested:

1. The output of "ls -l /usr/src" command, is:

> root@ubuntu:/home/elena/Desktop# ls -l /usr/src

total 39460
drwxr-xr-x  18 root root     4096 Jan  8 22:58 linux-headers-2.6.12-9
drwxr-xr-x   4 root root     4096 Jan  8 22:58 linux-headers-2.6.12-9-386
-rw-r--r--   1 root root 40351275 Mar 11  2006 linux-source-2.6.12.tar.bz2

2. The output of "ls -l /lib/modules" command is:

> root@ubuntu:/home/elena/Desktop# ls -l /lib/modules

total 4
drwxr-xr-x  6 root root 4096 Jan  8 22:58 2.6.12-9-386
root@ubuntu:/home/elena/Desktop#

Do they help any?

P.S.> Sorry, but I do NOT have any clue what we are doing here...

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist:

I am giving you what your requested:

1. The output of "ls -l /usr/src" command, is:

> root@ubuntu:/home/elena/Desktop# ls -l /usr/src

total 39460
drwxr-xr-x  18 root root     4096 Jan  8 22:58 linux-headers-2.6.12-9
drwxr-xr-x   4 root root     4096 Jan  8 22:58 linux-headers-2.6.12-9-386
-rw-r--r--   1 root root 40351275 Mar 11  2006 linux-source-2.6.12.tar.bz2

2. The output of "ls -l /lib/modules" command is:

> root@ubuntu:/home/elena/Desktop# ls -l /lib/modules

total 4
drwxr-xr-x  6 root root 4096 Jan  8 22:58 2.6.12-9-386
root@ubuntu:/home/elena/Desktop#

Do they help any?

P.S.> Sorry, but I do NOT have any clue what we are doing here...

---

### Post by Pragmatist on 2006-04-05
This: [B]linux-source-2.6.12.tar.bz2
[/B]Is of no use to you at all.  You must decompress this by:

```
tar xvjf linux-source-2.6.12.tar.bz2
``` I'm not sure why you submitted FOUR!!!! copies of your last post.

I agree that the clock skew is a problem, and I posted a couple of websites that discuss this.  Have you read them yet?

Overall, I think you have very definite ideas about how to fix your problem.  Maybe they will work.

If you still have problems, let me know exactly what questions you have and I'll do my best to help you solve your problem your way.

If you want my help from beginning to end, however, you need to try my suggestions and give me the results. It is like the old expression, "too many cooks spoil the broth!". I don't mind you following your own advice and then asking questions as long as your **consistent with your ideas**. It doesn't make sense to start testing one idea and then quit and start another idea. If your SURE the first idea was wrong then it is OK. Otherwise, what will happen is that you'll try somethings, then change your mind, try some other things, change your mind, start over (!) by reinstalling, change your mind, etc...etc...

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist,

Sorry for this late Reply, but for the Past 2,5 hours I was NOT able to pass through NOT a single post...

The post that you saw there being posted 4 times, I had it written out & was pressing the "Submit Reply" button, but NOTHING went through...

I would get this circle around my mouse icon moving around & around (this wait icon...), but my post seemed to NOT go through...

So I would stop My Mozilla Brower & perform a Refresh & then click on the "submit reply" button again & again...

I must have done this 4 times (at least) I guess...(thank god it ONLY came in as 4 times...)

And things were moving VERY-VERY slow...(I mean the pages loading)...
Some times the Mozilla would "expire" during the loading of the page...

I finally decided to "Save" my Text in a "Text Editor" & send it to you as soon as I get myself accessing the Forum again (& the problem being fixed)...

I thought it was the Router... I reset it & got nothing... it was working fine!!!

I then thought it was My PC problem... so shutdown & Restart... but it was also working fine!!!

I then thought maybe my ISP was down for some time... but it was ok!!!
(when browsing other Internet pages I was browsing fine!).

However, whenever I was typing in my Mozilla Firefox the Internet address of "www.ubuntuforums.org", I would NOT get through...

I reset Mozilla Firefox's Cookies & Cache... but nothing...

Now, I hope this post will go through...

I do NOT know why this happened...

It has happened to me another 2 times in the past 2 months...

And I do NOT know if it has to do with Ubuntu's Forum Servers, or anything...
...I sometimes wonder if there is a big traffic & that traffic reaches the Servers max limits & some people do NOT get through...
I do NOT really know, only can do rough guesses...

Did you experience anything similar during those past 2,5 hours?
Have you ever experienced something like this - in the past?

Please forgive me, but it was NOT my fault...

Thanks.

---

### Post by dvarsam on 2006-04-05
> The output of "ls -l /usr/src" command, is:

root@ubuntu:/home/elena/Desktop# ls -l /usr/src

total 39460
drwxr-xr-x 18 root root 4096 Jan 8 22:58 linux-headers-2.6.12-9
drwxr-xr-x 4 root root 4096 Jan 8 22:58 linux-headers-2.6.12-9-386
-rw-r--r-- 1 root root 40351275 Mar 11 2006 linux-source-2.6.12.tar.bz2

Regarding the output of ""ls -l /usr/src" command, and the last line up here:
> linux-source-2.6.12.tar.bz2

...I do not know what its doing there...

All I did was perform a "dpkg -i" command to the ".deb" file I gave in line #5:
> 5. linux-source-2.6.12_2.6.12-10.30_all.deb

How that package turned from a ".deb" to a ".tar.gz" & moved in the directory "/usr/src" I have NO clue & I have NOT performed such a command...

I honestly do NOT know how to trasform a ".deb" package to ".tar.gz" - maybe the System did it & needed it there for some reason...

By the way, even on my other PC, for some reason I have the SAME ".tar.gz" package lying on that SAME path...
Why? I do NOT know...

> 
This: "linux-source-2.6.12.tar.bz2" is of no use to you at all.

You must decompress this by:

```
tar xvjf linux-source-2.6.12.tar.bz2
```


Do I need it for some reason?
If it is of NO use, why should I bother decompressing it?

Sorry, but I do NOT know what to do with it...
I only installed the ".deb" file named like this...

Please advise me what you want me to do with it...

> 
I agree that the clock skew is a problem & I posted a couple of websites that discuss this.
Have you read them yet?


Sorry I did NOT know about this problem...

What I also noticed on my Ubuntu during Boot was that I had a "failed" signal on the "Clock Syncronization" - but I do not know what exactly it is & do NOT know how to fix it...
... I could NOT even read the whole line because it was moving up so fast...
I tried to press the "Pause" button - maybe to freeze the page - but I guess it does NOT freeze at that boot stage...

I have only taken a quick look on those Sites you suggested...
I will read those Sites more carefully & try to use the code they suggest...

> 
Overall, I think you have very definite ideas about how to fix your problem.  Maybe they will work.


I hope I can do something, we will see...

> 
If you still have problems, let me know exactly what questions you have and I'll do my best to help you solve your problem your way.

If you want my help from beginning to end, however, you need to try my suggestions and give me the results.
It is like the old expression, "too many cooks spoil the broth!".
I don't mind you following your own advice and then asking questions as long as your **consistent with your ideas**.


Ok I will try them out & see how it goes...

Anyway, I will keep you posted at ALL times - so please do NOT abandon me, cause you are the only person I have got...

> 
It doesn't make sense to start testing one idea and then quit and start another idea. If your SURE the first idea was wrong then it is OK.
Otherwise, what will happen is that you'll try somethings, then change your mind, try some other things, change your mind, start over (!) by reinstalling, change your mind, etc...etc...

I will visit those sites you suggested & try out their code...

If it does NOT work, I will then try those "echo" commands to see what the Intel's "Makefile" does, but HONESTLY I am NOT so good at mastering those "script" commands...

However, I know that this is my only way out to solving this...

Thank you & please visit this thread to see where I am standing every now & then...

P.S.> There are 4 more people having this SAME problem...
        (one of them has the SAME Mobo like me...)
        If you want me I can give you the Thread #'s to see it for yourself...

---

### Post by Pragmatist on 2006-04-05
Please give output of:

```
lsmod
```

---

### Post by dvarsam on 2006-04-05
[QUOTE=Pragmatist]Please give output of:

```
lsmod
```[/QUOTE]

Dear Pragmatist, I thought you would have left the Forum by now...

Glad to hear from you:

My "lsmod" is the following:

root@ubuntu:~# lsmod

> Module                  Size  Used by
vfat                   12288  0
fat                    46492  1 vfat
nls_cp437               5888  0
isofs                  32824  0
udf                    75524  0
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
i915                   17920  1
drm                    58004  2 i915
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
hw_random               5268  0
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
snd_hda_intel          15872  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  3 ehci_hcd,uhci_hcd
sd_mod                 17424  3
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_generic             1664  0
ata_piix                9476  4
libata                 47876  1 ata_piix
scsi_mod              124872  2 sd_mod,libata
piix                    9476  1
ide_core              125268  3 ide_cd,ide_generic,piix
unix                   24624  590
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

Any ideas?

---

### Post by dvarsam on 2006-04-05
Dear Pragmatist, I visited the first link you suggested:

[http://www.linuxsa.org.au/pipermail/linuxsa/1999-August/008869.html](http://www.linuxsa.org.au/pipermail/linuxsa/1999-August/008869.html)

Tried the commands suggested in there:

> 
make clean
# Put timestamps on all files equal to current time

find . -exec touch {} \;
# Rebuild all output files

make

This is what I get:

> elena@ubuntu:~/Desktop/e1000-7.0.33/src$ make clean

rm -rf e1000.ko e1000.o e1000.mod.c e1000.mod.o e1000_main.o e1000_hw.o e1000_param.o e1000_ethtool.o kcompat.o e1000.7.gz .*cmd .tmp_versions

Then:

> elena@ubuntu:~/Desktop/e1000-7.0.33/src$ find . -exec touch {} \;

elena@ubuntu:~/Desktop/e1000-7.0.33/src$

Then:

> elena@ubuntu:~/Desktop/e1000-7.0.33/src$ make

make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/elena/Desktop/e1000-7.0.33/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_main.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/skbuff.h: In function ‘skb_add_data’:
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/net/sock.h: In function ‘skb_copy_to_page’:
include/net/sock.h:992: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c: In function ‘e1000_set_mac’:
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:2086: warning: pointer targets in passing argument 1 of ‘is_valid_ether_addr’ differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_osdep.h:43,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.h:36,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.c:33:
include/linux/skbuff.h: In function ‘skb_add_data’:
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_param.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:29:
include/linux/skbuff.h: In function ‘skb_add_data’:
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:29:
include/net/sock.h: In function ‘skb_copy_to_page’:
include/net/sock.h:992: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c: At top level:
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:78: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:88: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:101: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:113: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:130: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:143: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:155: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:164: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:173: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:182: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:191: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:200: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c: In function ‘e1000_check_options’:
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:339: warning: pointer targets in passing argument 1 of ‘e1000_validate_option’ differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:369: warning: pointer targets in passing argument 1 of ‘e1000_validate_option’ differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:445: warning: pointer targets in passing argument 1 of ‘e1000_validate_option’ differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:467: warning: pointer targets in passing argument 1 of ‘e1000_validate_option’ differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:489: warning: pointer targets in passing argument 1 of ‘e1000_validate_option’ differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:511: warning: pointer targets in passing argument 1 of ‘e1000_validate_option’ differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:543: warning: pointer targets in passing argument 1 of ‘e1000_validate_option’ differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.c:31:
include/linux/skbuff.h: In function ‘skb_add_data’:
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.c:31:
include/net/sock.h: In function ‘skb_copy_to_page’:
include/net/sock.h:992: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/kcompat.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.c:29:
include/linux/skbuff.h: In function ‘skb_add_data’:
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of ‘csum_and_copy_from_user’ differ in signedness
  LD [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000.o
  Building modules, stage 2.
  MODPOST
  CC      /home/elena/Desktop/e1000-7.0.33/src/e1000.mod.o
  LD [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'

I do NOT see any errors, just warnings:

> 
warning: pointer targets in passing argument 1 of ‘is_valid_ether_addr’ differ in signedness

warning: pointer targets in initialization differ in signedness

warning: pointer targets in passing argument 1 of ‘e1000_validate_option’ differ in signedness

Maybe more... sorry I can NOT see clear NO more, my eyes man, my eyes...
I see the screen blurred man, it is too many hours...
In the end, I' ll be seing birds... and I'll be in heaven...

I do NOT think this is getting anywhere man...

I know there are NO errors, but if I perform a "make install", I get that st*pid error again:

> make: warning: Clock skew detected. Your build may be incomplete.

I can't think right now, I need some sleep...

Maybe be can do a bit tomorrow, but I don't see it coming...

See you man...

Thanks.

P.S. 1> The Clock is getting "skewed" & I am getting "screw*d"...

P.S. 2> I also tried the 2nd Site you suggested...
          The only difference is in the "find" command they are suggesting me to use...
However, the outcome is the same "...Clock skew...".
If you want me, I will post the outcome Tomorrow...

---

### Post by Pragmatist on 2006-04-05
Just think...when your finished you'll have internet access on Ubuntu!!!  :)

The reason I asked you to do **lsmod **is because I found the e1000 driver already on Ubuntu!  So maybe all you need to do is load this driver!!!

Mine is located here:
[B]/lib/modules/2.6.12-10-386/kernel/drivers/net/e1000/e1000.ko

[/B]If you find it, type this:
```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/e1000/e1000.ko
``` 

Note: You can actually type `uname -r` as part of the path, just *make sure that you use the **`** which is located near the 1 key and usually on the same key as the ~  This is NOT a double quote (") or single quote(')*

Another way to look for the e1000 files is to first update your locate database:
```
sudo updatedb
``` 
And now use locate:
```
locate e1000.ko
``` 
Note: the extension .ko  are both letters (it is an o  not a zero 0)

If you find it and run the insmod command in this post, then you should try to see if your "LAN" works!!

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

Thank you for your reply!

> Just think...when your finished you'll have internet access on Ubuntu!!!


And for your nice comments... helps my esteem up & running...

> I asked you to do **lsmod **is because I found the e1000 driver already on Ubuntu!
So maybe all you need to do is load this driver!!!

Maybe it gets in there by default...

> Mine is located here:

/lib/modules/2.6.12-10-386/kernel/drivers/net/e1000/e1000.ko

So does Mine!!!

> If you find it, type this:
```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/e1000/e1000.ko
```

Note: You can actually type `uname -r` as part of the path, just *make sure that you use the **`** which is located near the 1 key and usually on the same key as the ~  This is NOT a double quote (") or single quote(')*


I performed an "insmod e1000.ko" as root, and this is what I got:

> root@ubuntu:/lib/modules/2.6.12-9-386/kernel/drivers/net/e1000# insmod e1000.ko

insmod: error inserting 'e1000.ko': -1 File exists

> Note: the extension .ko are both letters (it is an o not a zero 0)

I tried that & thanks for clarifying... but ... Nothing...

> If you find it & run the insmod command in this post, then you should try to see if your "LAN" works!!

I wish it would... if I didn't get that ERROR man...

Maybe Intel does this for a purpose...
You see, on my other Mobo, an Intel D865PEARL, its LAN gets recognized with no fuss...
I understand that ASUS uses the SAME LAN controller - Intel's...
And Intel is supposed to provide for a Driver...
Maybe Intel does this intentionally (to kill competition...)...
In their Mobo's they make the LAN auto-detected...
But when they give drivers to other Mobo companies that buy their chips, they make it NON-auto-detected, so that I end up hitting my head against the wall... return the ASUS Mobo & buy an Intel instead...
That is probably their game strategy... (remind you of any other company trying to kill competition...?). An Ubuntu OS competitor?...

Any other ideas?

Thanks.

---

### Post by Pragmatist on 2006-04-06
I definitely do NOT think this is some Intel consipiracy to make life hard for you!! :)

this error message means that the module is already installed!:
 insmod: error inserting 'e1000.ko': -1 File exists

How do I know?  Well, I did some tests!

1.) switched to the /var/lib/`uname -r`/kernel/drivers/net/e1000  directory
2.) I ran **lsmod |grep e1000 **and got nothing (it is NOT loaded)
3.) I ran **sudo insmod e1000.ko **I got NO error
4.) I ran **lsmod |grep e1000 **and got a response of e1000 (it IS loaded)
5.) I ran **lsmod |grep e1000 **A SECOND TIME, WHILE e1000 IS STILL LOADED!
I got this error:
insmod: error inserting 'e1000.ko': -1 File exists

So try this:
```
lsmod | grep e1000
```

If you get the answer: e1000  then this means that you have the driver loaded.

Try your device and see if it works!

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

Thank you for your reply!!!

> I definitely do NOT think this is some Intel consipiracy to make life hard for you!

I hope too!!!

> 
The following error message means that the module is already installed!:
insmod: error inserting 'e1000.ko': -1 File exists

I hope too!

> 
So try this:
```
lsmod | grep e1000
```

If you get the answer: e1000  then this means that you have the driver loaded.

Try your device and see if it works![/QUOTE]

I performed as you said:

> root@ubuntu:/# lsmod |grep e1000

e1000                 111928  0

OK, it exists!!!

Then I did this:

> root@ubuntu:/# ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:15:F2:03:6F:6D
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xd800 Memory:cffe0000-d0000000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5338483 (5.0 MiB)  TX bytes:5338483 (5.0 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

When running the above command in the past (e.g.  "ifconfig -a)", I used to get:

> lo   ...blah ...blah...
sit0   ...blah ...blah...

For some strange reason, NOW, I can see the > eth0   ...blah ...blah... too!!!

And I can NOT understand how did we make it appear...?

Was it the Drivers?

Was it the "lsmod |grep e1000" command?

What in the "heck" was it?

And how come my Ubuntu does NOT see this, on a Normal install?

IF I assume that Ubuntu uses some default "e1000" drivers, how come did it NOT work from the beginning?

Now:

From the Menu, I selected "System\Administration\Networking" & saw the "Ethernet Connection" device...(in the past, it was NOT there!!!)

I selected it, clicked on "Properties" button, clicked on "Enable this connection" checkbox....

Under "Configuration:", i selected "DHCP"...

Clicked on the "OK" button...

Then I clicked on the button named "Activate"...

Clicked on the "OK" button...

Launched Mozilla Firefox Web Browser....

Typed in "www.yahoo.com"...

And BANG!!!

YES!!!!

YES!!!

I CAN SEE!!!

MY UBUNTU IS NOT BLIND ANY MORE!!!!!!!
(thank God I didn't either...lol :D )

_Questions_:
1. I also want to do a Restart, perform a Clean Ubuntu install & type "lsmod |grep e1000" & see IF this is ALL it was needed... you think that was all?

2. What were the "key" steps we typed to make this work?
    I seem to be missing how we got this fixed...
    Did you really understand how we did this?

Thanks man!!!

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

I am trying to simulate how we got it fixed:

1. I formated the PC & make a clean installation.

2. Launch a Terminal Window, log-in as "root" & perform a:
> insmod /lib/modules/`uname -r`/kernel/drivers/net/e1000/e1000.ko

insmod: error inserting 'e1000.ko': -1 File exists

3. Then run "lsmod | grep e1000" to get:
>  root@ubuntu:/# lsmod | grep e1000

e1000   89780   0

So, here I verify that the driver "e1000" exists!!!

4. Then I do the following:>  root@ubuntu:/# ifconfig -a

lo ...blah ...blah...
sit0 ...blah ...blah...

I do NOT get the:> eth0 ...blah ...blah...

What am I doing wrong?

Am I supposed to run "make" to install the drivers?

I thought the Driver install was un-successfull...

Were the Drivers really installed?

What am I doing wrong?

Thanks.

---

### Post by Pragmatist on 2006-04-06
Yes, I understood how we did this. I've done this sort of thing many times.  The mistake I made was to begin with your assumptions (i.e. that there was a tarball that needed to be compiled).  It is always important, when troubleshooting, to be METHODICAL!  So you go step-by-step.  If this was my computer, I would have thought like this:
 
 1.) Why is my LAN not working?
 2.) Well, it is a device and devices need drivers.
 3.) Ok, do I have the driver on my computer already?
 4.) If yes, then use insmod to insert the driver module in the kernel.
 5.) If no, then can I get the driver from the repositories (via synaptic)
 6.) If no, then can I find a Debian package (.deb) somewhere?
 7.) If no, then can I find a tarball somewhere?
 8.) If no, I'm screwed!
 9.) If yes, then I need to download the tarball, **decompress** it, **configure** my system, **compile** it, and **install** it.
 
 My mistake was I started with number 9!!  Instead of number 3!  As I said, the reason was I assumed that you knew what you were doing :p:p
 
 Ok, that explains what happened in this thread.  Now to answer some more of your questions.
 
 1.) It is completely NORMAL for the computer NOT to recognize some hardware.  To understand what happened here, you need to understand how the KERNEL works.  The kernel is just a program--a complicated program. When you compile a kernel (download the tarball...same concept), there are LOTS of options and features.  If you understand your system completely, you can include the features you want and not include those that you do not want.  This gives the cleanest, most lightweight, kernel possible.  However, when you just install a distribution, it is like buying a suit in a clothing store.  They can't make it perfect to fit you because then it won't fit somebody else.  They make it so it can fit a large number of people--but not everybody and every situation.  One way they handle this situation is by including OPTIONS.  Every feature of your kernel has one of three different possibilities:
 1.) It is included (also called YES and given just the letter 'y')
 2.) It is NOT included
 3.) It is included as a MODULE (shown as 'm')
 
 Many drivers are included as a module.  The reason is because there are SO MANY types of hardware out there that it makes the most sense to only include the most popular and the rest are included as MODULES.  As you see, it is not hard to insert the module (just one command).
 
 You have a very bad habit of reinstalling your system.  This is not only a waste of time, it also prevents you from learning many different things.  The only times you should reinstall your system are:
 
 1.) You are upgrading to a new version (like to Dapper from Breezy) and you prefer to install it rather than do a distribution-upgrade through apt.
 
 2.) Your TOTALLY SCREWED.  By this I mean that you have tried almost everything and realized that it is easiest to just reinstall.
 
 The situations where you are reinstalling don't fit either of these categories.  You are reinstalling because you think that it will lead to a cleaner system.  It won't.  The only thing that leads to a clean system is keeping paper records of everything that you do.  This way you can uninstall or reverse what you've done.  A computer is meant to be used and when you use it you will get it dirty.  **The important thing is to know how to clean it**, not just throw it away and start over.
 
 As to whether I knew what I was doing, the answer is: YES!  If you want to be convinced, read my thread "How To Help Yourself"  Read section [B]11. Hardware Information:
[/B]>  Originally Posted by: **Pragmatist** in "How to Help Yourself"
 [http://www.ubuntuforums.org/showthread.php?t=142716](http://www.ubuntuforums.org/showthread.php?t=142716)
 * (d) **lsmod** and **modprobe** lsmod lists the modules that are currently loaded on your system. A driver typically takes the form of a module. A module is a way to add something to the kernel (the Linux OS). When a kernel is compiled it has the most relevant options included. Options that aren't used often, or are specific to less common hardware, are included in the kernel as modules that must be loaded. modprobe adds or removes modules depending on circumstances. Often you will be adding a driver module, but sometimes you also have to remove conflicting modules.*

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

Thank you for your reply!!!

Please read the message I posted, right before your post.

I tried to Simulate exactly as you instructed & it could NOT work...

I do NOT know why....?

Thanks.

---

### Post by Pragmatist on 2006-04-06
>  I tried to Simulate exactly as you instructed & it could NOT work...

I did NOT instruct you to reinstall Ubuntu!!!

---

### Post by dvarsam on 2006-04-06
[QUOTE=Pragmatist]I did NOT instruct you to reinstall Ubuntu!!![/QUOTE]

I am Sorry...!!!

The "instructed" word, I typed down/used, had to do with what this Thread is about...!:D 

...To be able to install the drivers successfully I have to find how this is done...

I mean a "method" found, to _actually_ put it to work...

And this is what I want to give to the other 4 people with the SAME problem...(one of them has the SAME Mobo as I do... - the others have not stated what their Mobos are - maybe same, maybe NOT...)

A straightforward method, with NO un-needed or un-neccessary steps in between...

IF I Simulate what we did here, on this Forum Thread's _5 Pages_, I might make it work, but at the same time, I would have performed many un-necessary/un-wanted steps...

I need to "screen-out" the un-nessesary steps...

AND I am NO "master" at this...

_YOU_ are my "master"!!!

Thanks...

P.S.> Sorry, I hope I have NOT dissapointed you...

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

My time is is 20:00 p.m. & I have to go to the Supermarket...

Here they close at 21:00 p.m.

I will be back at 21:30 p.m. my time - (1,5 hours from now)

I hope I see you then...

Thanks - you have been of great help!!!!

P.S.> I promised my girl I would escort her - if I do NOT she will file for Divorce...or let me starve for a week...:D

---

### Post by Pragmatist on 2006-04-06
For those people who are trying to solve a similar problem, most of this thread is not useful.

We found the solution.  All you have to do is make sure that the e1000 driver is loaded (AND that it loads every time you boot).

You loaded the e1000 driver and you got internet access!!  So the problem is solved.  We know the problem isn't with the driver.  The driver is available, all that is necessary is to run the insmod command to get it loaded.

If the driver is loaded and your internet isn't working, this has nothing to do with the driver.  This is a different problem and a different thread! (your title is: Installing LAN Driver - Need Help).

---

### Post by Pragmatist on 2006-04-06
Ok, let me be clearer.  Since you know that the driver (e1000) is available on your system, here are your steps to determine the problem:

1.) Is the driver loaded:  ```
lsmod |grep e1000
```(a) If no, then load it: 
```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/e1000/e1000.ko
```(b) If it is loaded I would try this:

unload it:
```
sudo rmmod /lib/modules/`uname -r`/kernel/drivers/net/e1000/e1000.ko
```
then reload it:
```
sudo insmod /lib/modules/`uname -r`/kernel/drivers/net/e1000/e1000.ko
```

If all of that doesn't work, then I don't think the problem is with the driver.

IMPORTANT:  This assumes you DO NOT LEAVE THE SYSTEM (reboot, shutdown, logout)  Once you've got it working, I'll show you how to make it permanent so that it always works, even when you restart the system.

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

I performed an "lsmod |grep e1000" & listen to what I got:

> root@ubuntu:/# lsmod | grep e1000

root@ubuntu:/#

I am NOT getting the: > e1000   89780   0

NOT only that, but _now_, I can ONLY get up to:

> cd /lib/modules/`uname -r`/kernel/drivers/net/

The folder named "e1000" does NOT exist!!!

I am getting crazy HERE!!!

After I re-installed Ubuntu (as I said to you, on my previous message), I mentioned that the folder "e1000" was _there_!!!

And the "lsmod ..." & everything seemed fine... 

Now, it is NOT like that & I have NOT changed anything... have NOT installed NOT a single package...!!!

_I am thinking of the following_:

When I install Ubuntu, my Hard Drive does NOT really re-format!!!

Maybe, during the re-install, SOME of the files are touched/changed & the rest instead of being "deleted" they remain as is...

I know, it sounds like "crazy", but I can NOT figure out how they seemed to "exist" before & now they do NOT!!!

I have NOT touched anything!!!...#@$^&*(%

I think I may have to re-install something - maybe the drivers...?

Thanks.

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

                     I noticed this:

On a clean Ubuntu v5.10 install, to be able to "compile" a package, you need to install the following:

_List 1_:
> 1. build-essential
2. gcc-4.0
3. linux-headers-386
4. linux-source-2.6.12

Now, in the past, I have mentioned 9 packages:

_List 2_:
> 1. build-essential
2. cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
3. gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb
4. gcc-3.4_3.4.4-6ubuntu8.1_i386.deb
5. linux-source-2.6.12_2.6.12-10.30_all.deb
6. linux-headers-2.6.12-10_2.6.12-10.30_i386.deb
7. linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb
8. linux-headers-386_2.6.12.16.1_i386.deb
9. linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb

But, on an Ubuntu v5.10 _clean_ install:

a. If you install the above #1 (from "List 1"), it is as if you install: #1 & #9 (from "List 2").

b. If you install the above #2 (from "List 1"), it is installed as is (& is equivalent to #4 from "List 2")
You do NOT need to install the #2 & #3 (from "List 2"), because they are already pre-installed in Ubuntu v5.10.

c. If you install the above #3 (from "List 1"),  it is as if you install: #6-#8 (from "List 2").

d. If you install the above #4 (from "List 1"), it is the same as #5 (from "List 2").

So, as a conclusion, on an Ubuntu v5.10 clean install, _only_ the above 4 packages (from "List 1") need to be installed to "compile" a program from source!

_Question_:
Do you want me to install those 4 packages?

Thanks.

P.S.> You probably wonder why am I supplying this list...
        I am supplying for ALL the people reading this thread...

---

### Post by Pragmatist on 2006-04-06
I think you need to seperate two things:

1.) Getting something to work.
2.) Understanding WHY it works.

I think it is more important that we focus on 1. Don't worry about the other people reading this thread. You can always summarize everything AFTER you have got your system working.

I can assure you that most people that will read this thread want to be able to get their LAN working and UNDERSTANDING is not the TOP priority. :) It may sound silly to do it that way, but this is life. NOBODY understands everything about Linux or computers or virtually any subject.

If you want more help from me, you need to do the following:

1.) Stop reinstalling your system.
2.) Don't install anything
3.) Don't compile anything.
4.) Don't try to guess why all of this is happening to you
5.) Don't make complicated theories about your system or situation.
6.) Don't change your system AT ALL until you've thought it through and we've discussed it here.

What you should do is:

1.) Use [www.google.com/linux]("http://www.google.com/linux")  and READ about your problem.
2.) Go step-by-step and be methodical. Methodical means that you only DO something when it is part of a PLAN. You only change plans when you have concrete proof that it is not a good plan.

So, what is your plan?

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

I am ALL yours!!!

AND ALL ears...

ALL my system is on your hands awaiting for your instructions...

> So, what is your plan?

I guess my plan is what you say:

> What you should do is:

1.) Use [www.google.com/linux](www.google.com/linux) and READ about your problem.
2.) Go step-by-step and be methodical. Methodical means that you only DO something when it is part of a PLAN. You only change plans when you have concrete proof that it is not a good plan.

If you suggest me to do  what they say in there, this is what I will do...

You are my _Master_!

Thanks.

---

### Post by Pragmatist on 2006-04-06
What is the output of this command:

```
 sudo lshw -C network
```

---

### Post by Pragmatist on 2006-04-06
> Originally Posted by: **dvarsam **here:[http://www.ubuntuforums.org/showthread.php?t=102083&highlight=e1000](http://www.ubuntuforums.org/showthread.php?t=102083&highlight=e1000)
Hello !!!
 How come your Untel 1000 Network does NOT work?
 What Motherboards do you have guys?
 Cause I have an INTEL PERL with 865 chipset & works fine!

I'm confused:-k

---

### Post by dvarsam on 2006-04-06
> What you should do is:

1.) Use [www.google.com/linux]("http://www.google.com/linux")  and READ about your problem.
2.) Go step-by-step and be methodical. Methodical means that you only DO something when it is part of a PLAN. You only change plans when you have concrete proof that it is not a good plan.

Dear Pragmatist,
                      the site you suggested [www.google.com/linux](www.google.com/linux)

Is just a google search page, it is NOT a specific step-by-step article or procedure...

I could perform a search like "how to setup a LAN", or variations of that, or even "installing e1000 driver" but other that I have NO clue...

I do NOT know if you intended to direct me to a specific page & you mistyped the page's address with the google's search page instead... 

Other than that, if you have nothing specific to suggest, I can only think of what we have done here - thoughout this thread - & try to repeat it to see what I can make of...

Thanks for ALL your help & I appreciate you being with me.

Dimitris.

P.S.> If you do NOT reply with something specific, then I will just try to "compile" the driver as we have done in this thread & see what I get myself into...
Who knows, maybe I will be lucky at some point & manage to setup my LAN again...

---

### Post by Pragmatist on 2006-04-06
What happens if you follow the instructions in this thread (they are in post #16):

[http://www.ubuntuforums.org/showthread.php?p=741687]("http://www.ubuntuforums.org/showthread.php?p=741687")

Follow them exactly.  If you are at all unsure about anything, ask me and I'll try and help.

---

### Post by dvarsam on 2006-04-06
[QUOTE=Pragmatist]What is the output of this command:

```
 sudo lshw -C network
```[/QUOTE]

I just saw your response:

What you asked is the following:

> root@ubuntu:/home/elena/Desktop# lshw -C network

  *-network UNCLAIMED
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: iomemory:cffe0000-cfffffff ioport:d800-d81f irq:5

What do I do now?

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

                       the Thread you suggested is VERY-VERY insteresting!!!
[http://www.ubuntuforums.org/showthread.php?p=741687](http://www.ubuntuforums.org/showthread.php?p=741687)

Basically it says the following:

> _Do not install using gcc-4.0 you will get errors_!


These are the links to the files:

gcc-3.4-base
cpp-3.4
gcc-3.4

Remember the ERROR we got when we used the "gcc-4.0"...

It would NOT compile unless we compiled with "gcc-3.4"...

That is why I had to Downgrade!!!

So, it seems like a good thread!!!

The guy in there, suggests installing the following:

1. linux-headers-2.6.12-10-386
2. binutils
3. build-essential
4. cpp-3.4_3.4.4-6ubuntu8_i386.deb
5. gcc-3.4_3.4.4-6ubuntu8_i386.deb
6. gcc-3.4-base_3.4.4-6ubuntu8_i386.deb

His #1 is equivalent (from our "List 2") to #6 &  #7
He does NOT install (from our "List 2") the # 8

His #3, by default installs his #2 too! (he just does NOT know that!).
So we have that too! This is equivalent (from our "List 2") to #1 & #9

His #4-$6 are equivalent (from our "List 2") to #2-#4

_Conclusion_:
Basically he does NOT install (from our "List 2") # 5 & 8

_ONLY_ we do!!!

I am NOT sure about #8 but I think #5 is _needed_.

You want me to try to do it like he did, without my #5 & #8 & with downgrading to "gcc-3.4?

As I said before, the downgrading (as he also suggests) we had to do it too!!!

We couldn't get our package to "make" without it...

What do you think?

P.S.> At the same time, after the "make install" he suggests doing a "modprobe e1000" - which we had not performed...

---

### Post by dvarsam on 2006-04-06
> Follow them exactly. If you are at all unsure about anything, ask me and I'll try and help.

Sorry, I missed that...

As you said, I will follow the directions as suggested in there & post back!

Thanks.

---

### Post by Pragmatist on 2006-04-06
> he suggests doing a "modprobe e1000" - which we had not performed... 
insmod and modprobe are the same thing.  Also, read my post #49 in this thread.

I suggested the link: [www.google.com/linux](www.google.com/linux)  to you so that YOU would search and READ what others have done.  The most important principle in computers is "Don't Repeat Yourself".  If somebody has solved your problem already, then use their solution.  It is an important skill to search on google.  So, YES, type in different keywords such as e1000 ubuntu asus  whatever...use your common sense.

I am just trying to GUIDE you in solving your problem.  It is ultimately YOUR responsibility for whatever happens--good or bad.  Let's remember that this is your computer, your LAN, your problem.  If you succeed, take the credit.  If you fail, take the blame.

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist:

With the following packages NOT installed:

> 5. linux-source-2.6.12_2.6.12-10.30_all.deb
8. linux-headers-386_2.6.12.16.1_i386.deb

This is what I get when I run "make":

> root@ubuntu:/home/elena/Desktop/e1000-7.0.33/src# make
make: Warning: File `Makefile' has modification time 2.1e+06 s in the future
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/elena/Desktop/e1000-7.0.33/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
make[2]: Warning: File `/home/elena/Desktop/e1000-7.0.33/src/Makefile' has modification time 2.1e+06 s in the future
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_main.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:29:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c: In function 'e1000_set_mac':
/home/elena/Desktop/e1000-7.0.33/src/e1000_main.c:2086: warning: pointer targets in passing argument 1 of 'is_valid_ether_addr' differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_osdep.h:43,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.h:36,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_hw.c:33:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_param.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:29:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c: At top level:
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:78: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:88: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:101: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:113: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:130: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:143: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:155: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:164: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:173: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:182: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:191: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:200: warning: pointer targets in initialization differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c: In function 'e1000_check_options':
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:339: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:369: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:445: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:467: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:489: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:511: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
/home/elena/Desktop/e1000-7.0.33/src/e1000_param.c:543: warning: pointer targets in passing argument 1 of 'e1000_validate_option' differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:46,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.c:31:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
In file included from include/linux/ip.h:84,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000.h:61,
                 from /home/elena/Desktop/e1000-7.0.33/src/e1000_ethtool.c:31:
include/net/sock.h: In function 'skb_copy_to_page':
include/net/sock.h:992: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  CC [M]  /home/elena/Desktop/e1000-7.0.33/src/kcompat.o
In file included from include/linux/if_ether.h:107,
                 from include/linux/netdevice.h:29,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.h:37,
                 from /home/elena/Desktop/e1000-7.0.33/src/kcompat.c:29:
include/linux/skbuff.h: In function 'skb_add_data':
include/linux/skbuff.h:1067: warning: pointer targets in passing argument 1 of 'csum_and_copy_from_user' differ in signedness
  LD [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000.o
make[2]: warning:  Clock skew detected.  Your build may be incomplete.
  Building modules, stage 2.
  MODPOST
  CC      /home/elena/Desktop/e1000-7.0.33/src/e1000.mod.o
  LD [M]  /home/elena/Desktop/e1000-7.0.33/src/e1000.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: warning:  Clock skew detected.  Your build may be incomplete.

Now I want to compare this with what we have got before when those 2 packages above were installed, to see if there is any difference in the "make" results...

If you go back to our "Page 2", you will find that those results are the SAME with what we have here!
Which is:

> make: warning: Clock skew detected. Your build may be incomplete.

Now I would like to test if the "e1000" folder exists.
To test this, I need to do this:

> cd /lib/modules/`uname -r`/kernel/drivers/net/e1000/

-bash: cd: e1000: No such file or directory

For some reason it seemed logical to me that the "e1000" folder would NOT exist, because I _only_ tried to "make" the driver but did NOT go ahead & install it...

To install the Driver (if I am not wrong), I would have to use the command "make install" instead...

I guess that is what the guy is doing in the site you suggested...

So, I decided to now run "make install", and then visit:

> cd /lib/modules/`uname -r`/kernel/drivers/net/e1000/

-bash: cd: e1000: No such file or directory

I was supposed to find the "e1000" folder, but I did NOT...

So, now I have to go back & see what steps we performed to make this work...

I will keep you posted...

---

### Post by dvarsam on 2006-04-06
Dear Pragmatist,

I tried to use the command "lsmod | grep e1000", to see if the driver exists:

> root@ubuntu:/# lsmod |grep e1000

root@ubuntu:/#

Nothing is found...

I then decided to install the package "linux-source-2.6.12_2.6.12-10.30_all.deb" as you suggested to me in "Page 2" of this thread...

Tried to run "make" again, to get:

> make: warning: Clock skew detected. Your build may be incomplete.

Then, I run "make install" to get the SAME result...

Then, tried this:

> cd /lib/modules/`uname -r`/kernel/drivers/net/e1000/

-bash: cd: e1000: No such file or directory

I tried lots of things...in the end I really do NOT know in what order...

But somewhere in the End I decided to "Restart" Ubuntu...

And the command "lsmod |grep e1000" showed me that "e1000" exists...

And the command "locate e1000.ko" is locating it...

And the command "ifconfig -a" shows my "eth0"...

But I need to find ALL the right steps right from the start...

Than means "Re-formatting" my Ubuntu!!!

Again, I will keep you posted, with my Results...

Hang on & I will have the Best Solution...

Thanks for everything man!

---

### Post by Pragmatist on 2006-04-06
>  Originally Posted by: **dvarsam**
But I need to find ALL the right steps right from the start...
 Than means "Re-formatting" my Ubuntu!!!
 Again, I will keep you posted, with my Results...
 Hang on & I will have the Best Solution...
 Thanks for everything man!

Glad you appreciated my help dvarsam.  Good luck!! :)

---

### Post by dvarsam on 2006-04-07
> **Pragmatist]Glad you appreciated my help dvarsam.  Good luck!! :)[/QUOTE]

Dear Pragmatist,

Thank you for being with me ALL the time!!!

Without you I would be nowhere....

I managed to find what is the "Minimum" Commands Needed to make my ASUS Mobo - Model P5LD2-VM to activate its LAN!

So, here is the HowTo!

You will be surprized to how "easy" it was...

Please, do not misunderstand me here...

It is _NOT_ your fault that it was so easy...

On the contrary: WITHOUT _YOU_ I'd BE HIDING SCARED BEHIND THE BUSHES!!!:D 

I would NOT really know what to do...

Again, I have to _admit_ that without you I would have had _NO_ chances man...

It would have been impossible to find a solution...

It took me _exactly_ 6 days to find this solution, working 16/6...lol :D (meaning 16 hours a day, 6 days of a week)...

And do NOT think that the remaining 8 hours... was sleep time...

I have turned into a "zombie" to make this work...

I was forced to do this, because _IF_ I could NOT make it work, but at the same time, had spent too many days working on this, it would have been "too late" to return it for a replacement to the PC shop I got it from...
(e.g. I can NOT return it after a "month", saying: "sorry, but I couldn't make it work - I need a replacement..." - they would NOT accept this! - Would you?)

A non-easy way, means learning more...

Hopefully, if I ever have to set up another Motherboard or LAN, it will be easier having passed through all this...!

Besides, I love my Ubuntu & want to learn how to use it!!!

And I have been trying hard on this...

Look (if you want) at my "desperate" posts:

1. Article#: 102083
2. Article#: 153441
3. Article#: 154076
4. Article#: 154532 (this post)
5. Article#: 155497

Here is the other people who had the SAME problem like me...

1. User: "jbellny" - Article#: 102083
2. User: "j2fraser" - Article#: 102083
3. User: "p47" - Article#: 102083
4. User: "smelly feet" - Article#: 153441 (This guy has the SAME Motherboard like Me!!!)

_Note_:
Users #1-#3 have NOT stated what Motherboard they have, maybe they have the same, maybe not...
But the messages they were getting, were the same like mine...

>  root@ubuntu:/home/elena/Desktop# lshw -C Network

*-network UNCLAIMED
...blah... ...blah...
...blah... ...blah...


But at least, I can now suggest to them to come & visit this thread & try out _IF_ a similar solution to this would solve their problems...

I know that on some occasions, Ubuntu is harder than working on a Windows machine...

But that is the sacrifice involved:
You get it for Free, but you need to "work" to make "all" things work...
If you are lucky, everything will be setup & running right from the start..., without any fuss involved from you...

Visiting this Forum _every_ day, has boosted my knowledge _exponentially_...

I have:

1. Learned how to setup sound, LAN, even wrong Graphics Resolution...

2. Learned about how to Setup a LAMP (this was another "pain" story for me...:D )
3. Learned how to open a Router's port to accept Internet connections for the Internet & passed over to my Web Server...

4. Learned how to find my IP.

5. Learned how to be able to post a picture inside a thread (e.g. inside a post in this Forum).

6. Learned how to perform anonymous Surfing that works on my Ubuntu...

7. Learned the advantages of IMAP E-mail accounts versus POP3...

8. etc. etc. ...

Now that I have 2 PC's (1 for me & 1 for my girl), I will hopefully manage to learn the following:

1. Setup the LAN to work/communicate between 2 Ubuntu PC's.

2. Setup the LAN to work/communicate between an Ubuntu & a Windows machine...

3. Learn how I can turn DHCP to Static (working more on my Router).

4. Learn & create a Web Page on an Ubuntu machine, using PHP & My SQL.

5. There is so much more...


This whole "world" of knowledge has opened to me...

And ALL that, thanks to you guys in THIS Forum...!!!

Without you, the Ubuntu OS would be nowhere...

Wherever I turned to the guys on the PC shop for help, they were like "I am sorry, but I know nothing about _how_ to setup any Linux"...

My answer to them is this:
Well, _I_ _DO !!!_8) 

And hopefully anyone who is willing in this Forum, will also_ do_!!!

Now: isn't this an advantage or what?

We know, but they do NOT!!! ...he...he... said:**
> Building Kasablanca...
Oh... dear...:-D

---

### Post by Pragmatist on 2006-04-07
> Originally Posted by: [B]dvarsam
[/B]I guess, now I will have to put my "HowTo" on a next post...

Yes, you should definitely make your HowTo.  If you don't post it in this thread, make sure to post a link to it here.

The way to pay back all the help you get is to give help to others.

Again, I'm glad I was able to help.  It is always a pleasure to assist in the education of a newbie! :)  After all, everybody begins as a beginner.

---

### Post by dvarsam on 2006-04-07
_HowTo_:
Install LAN Driver on _ASUS P5LD2-VM_ Motherboard

_Notes_:
1. Reading this "HowTo" or this full Thread could probably help you how to setup "your" Motherboard's LAN - no matter what the brand, model or maker of the Motherboard!
2. If you can perform on a Terminal window (from Menu select "Applications\Accessories\Terminal"), an "ifconfig -a" command & you can get the following:

> eth0   ...blah... ...blah...
lo   ...blah... ...blah...
sit0   ...blah... blah...


Seeing that the "eth0" part is already in there, means that your Network card is recognized by your Ubuntu!
IF this is _your_ case, do NOT bother to go on & install drivers for your Network card - you do NOT need them...

I could NOT see the "eth0" device & that is why I had to go on & install drivers for it...
Typing commands you learned throughout this thread (many thanks to user "Pragmatist" - my "mentor" for all the nice things he has teached me), should NOT help - they did NOT help me...
However, reading ALL this thread, should help you understand how things work, so if you want to learn more, "dive" in it...
Besides, I have learned many things, thanks to my mentor!!!

So you want to perform the "Minimum" possible Commands Needed to make your ASUS Mobo - Model P5LD2-VM to have its LAN activated!

So, here is the HowTo:

_For Ubuntu v5.10 Breezy_:

_Note_:
I assume that you have performed an Ubuntu clean/fresh Install.
But it should NOT really matter, as long as you follow the instructions below...

_Step 1_:
You need to install the following Packages:

    a. Using "Synaptic Package Manager", install:

        1. build-essential
        2. gcc-4.0
        3. linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
        4. cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
        5. gcc-3.4_3.4.4-6ubuntu8.1_i386.deb

        _Notes_:
        1. I think #2 gets auto-installed by #1, you might want to verify this...
        2. Above #4 & #5 means _downgrading_ your "gcc-4.0" but this is 
           a  requirement if you want to compile the Intel's "e1000" LAN driver.
           I also thing that if you install #5, #4 gets auto-installed, you might 
           want to verify this also...

    OR: Alternatively:

    b. Going independent & installing the packages one-by-one:

        01. dpkg -i binutils_2.16.1-2ubuntu6_i386.deb
        02. dpkg -i make_3.80-9_i386.deb
        03. dpkg -i dpkg-dev_1.13.10ubuntu4_all.deb
        04. dpkg -i gcc-4.0_4.0.1-4ubuntu9_i386.deb
        05. dpkg -i linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb
        06. dpkg -i gcc_4%3a4.0.1-3_i386.deb
        07. dpkg -i libc6_2.3.5-1ubuntu12.5.10.1_i386.deb
        08. dpkg -i libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb
        09-11: dpkg -i g++-4.0_4.0.1-4ubuntu9_i386.deb g++_4%3a4.0.1-3_i386.deb libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb
        12: dpkg -i build-essential_11.1_i386.deb
        13. dpkg -i linux-headers-2.6.12-9_2.6.12-9.23_i386.deb
        14. dpkg -i linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb
        15. dpkg -i gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb
        16. dpkg -i cpp-3.4_3.4.4-6ubuntu8.1_i386.deb
        17. dpkg -i gcc-3.4_3.4.4-6ubuntu8.1_i386.deb

        _Notes_:
        1. The above _order_ of installation _matters,_ so do NOT in any way 
            change the order - or you will end up having some packages NOT 
            installed & you will NOT be able to compile the "e1000" drivers. 
        2. The above Steps #9-#11 are co-dependent! This means that I can 
            NOT choose an order of install - the MUST _all_ be installed 
            simultaneously (as one, or: all together). You could also do this for all 
            the above packages but someone would NOT be able to read 
            something like the following or easily spot the package names that 
            are in fact installed, clearly: 
            
            dpkg -i binutils_2.16.1-2ubuntu6_i386.deb make_3.80-9_i386.deb dpkg-dev_1.13.10ubuntu4_all.deb gcc-4.0_4.0.1-4ubuntu9_i386.deb linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb gcc_4%3a4.0.1-3_i386.deb libc6_2.3.5-1ubuntu12.5.10.1_i386.deb libc6-dev_2.3.5-1ubuntu12.5.10.1_i386.deb g++-4.0_4.0.1-4ubuntu9_i386.deb g++_4%3a4.0.1-3_i386.deb libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb build-essential_11.1_i386.deb linux-headers-2.6.12-9_2.6.12-9.23_i386.deb linux-headers-2.6.12-9-386_2.6.12-9.23_i386.deb gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb cpp-3.4_3.4.4-6ubuntu8.1_i386.deb gcc-3.4_3.4.4-6ubuntu8.1_i386.deb

        3. You could as easily create a nice "Script" file (if you know how to do 
            this) & see all of the above run auto-matically (or auto-magically), 
            without any fuss from your side... It is very easy, but I am not going 
            to go through this here, cause it is going to take too long...
            (besides, 6 days for this was way too much for me too! - not to think 
             about my "mentor" spending time with me...!) 


_Step 2_:
You need to download the latest Intel "e1000" drivers.

The best site for this is the following:
[http://sourceforge.net/project/showfiles.php?group_id=42302](http://sourceforge.net/project/showfiles.php?group_id=42302)
(Many thanks to user "Pragmatist" for providing the above thread - as he were my "mentor" & Ubuntu "spiritual" guide throughout all this!!!) 

_Note_:
In this "HowTo", I have downloaded & used the latest drivers - which now are "e1000-7.0.33.tar.gz".
Download the latest drivers you can find, hopefully they should work too!!!


_Step 3_:
Unzip the driver you downloaded.
I usually find it easier to "unzip" with the following way:

1. Right-click on your "e1000-7.0.33.tar.gz" file & select "Open with Archive Manager".

2. From the Standard Toolbar" click on the button named "Extract"

3. Under the "Extract in folder:" option, select "Desktop".

4. Click on the button named "Extract"

5. Close the "Archive Manager's" open window.

On your "Desktop" you should now see a folder named "e1000-7.0.33".

_Note_:
Others prefer using the "tar" command.
Perform as you prefer - I prefer using a GUI compared to a Terminal environment.


_Step 4_:
We are now going to compile the downloaded "e1000-7.0.33" driver.

To do this, do the following:

1. Launch a Terminal window (from the Menu, select "Applications\Accesories\Terminal")

2. Type "sudo -i" & then type your user password to have "root" priviledges.

3. Type "cd /home/dimitris/Desktop/e1000-7.0.33/src", replacing "dimitris" with your username (the one you type during boot).

4. Type "make install" to Compile & Install your "e1000" driver.

    _Note_:
    When you have finished compiling the "e1000" driver, you will notice that there are ERRORS created..., like:
    >  make: warning: Clock skew detected. Your build may be incomplete.
    Simply ignore this ERROR if you get it...
    IF you get an error like:
    > Makefile:65: *** Linux kernel source not found. Stop.
    that means, that you are missing some of the packages I told you to 
    install!!! Go back to "Step 1a" or "Step 1b", find what packages you did 
    NOT install & go ahead & install them!!! Only then, come back here & 
    attempt again to "make install" (or compile) your drivers...

5. This is the MOST IMPORTANT PART:
    On your "Terminal" window, type > shutdown -r now

    You must Shutdown & Restart your Ubuntu PC!
    No matter what other command suggested in this thread, IF you do NOT do 
    this, NOTHING will work...
    You can play around with any command you wish, before shutting down & 
    restarting..., but it did NOT work for me & I advise you NOT to, cause you 
    will be waisting your time...

   _ Note_:
   I do NOT know why this was _SO_ important, but I guess it is a 
   required step, if you want to make this work...

6. Now that you have Restarted your Ubuntu PC, launch a "Terminal" window (from the Menu, select "Applications\Accesories\Terminal") & type:

> dimitris@ubuntu:~$ifconfig -a

eth0   ...blah... ...blah...
lo   ...blah... ...blah...
sit0   ...blah... blah...


If you can see the "eth0" line, then your LAN is detected & you are ready to "Roll" - your drivers are installed & your card is ready to work!!!

You just need to play around with the LAN Card's configuration settings.

IF not, try again, or ask for some help in this Forum!!!

Lots of guys should be willing to help, including me!!! ;) 

Have Fun!!!

P.S.> Again many thanks to all of you who helped & most of all: user "Pragmatist"!

---

### Post by rgibbs421 on 2007-02-25
Hello my name is Robert and I am having problems getting edgy to see my network adapter.
I have spent several hours a week for about 6 weeks loading a dialup modem driver in the past only to find out that the only code I could find was 14.4 restricted so I stopped using ubuntu until now. I have gotten high speed Internet and wanted to get back into Linux on a connection that I can finally do something with it. I have read all the forums that look like it has the information that I need to fix my problem and at the start of this thread looked the closest. I am posting this just after one day of working on this new problem so maybe I can get it fixed fast enough that I do not drop using the OS totally.

My hardware
Marvell Yukon Ethernet Controller 
In windows it loads as a generic
Generic Marvell Yukon Chipset based Ethernet
PCI slot5

My computer
Brand = Acer
Model = Aspire AST180-ES340M
Type of Device = I go through a linksys router but I think the first device I need help with is the Marvell NIC


I have downloaded the
marvell-88e8050_linux_v8.16.2.3
Zip and tried to run the install 
On the third window where it runs through the below stuff

Create tmp dir (/tmp/Sk98ISnjLZmNciogqALXnlaAb) [ OK ]
Check user id (0) [ OK ]
Check kernel version (2.6.12-9-386) [ OK ]
Check kernel symbol file (/proc/kallsyms) [ OK ]
Check kernel type working
Check kernel type (SP) [ OK ]
Check architecture (found) [ OK ]
Set architecture (i386) [ OK ]
Check compiler (/usr/bin/gcc) [ OK ]
Check mcmodel flags (32bit) [ OK ]
Check module support (/sbin/insmod) [ OK ]
Check make (/usr/bin/make) [ OK ]
Check archive file (sk98lin) [ OK ]
Check kernel gcc version (3.4.5) (Kernel:3.4.5 != gcc:4.0.2) [ failed ]
Check sk98lin driver availability (not loaded) [ OK ]


I GET SNAGGED

Check kernel header files (not found) [ failed ]
Kernel header not found. Please install the linux header files
development package or crate a symbolic link from the
/usr/src/KERNEL_VERSION directory to linux
Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux

I have made the link I think by typing
ln -s /usr/src/ linux-source-2.6.10 /usr/src/linux
I ran the program again and got the same response
I then typed
ln -s /usr/src/ linux-source-2.6.10generic /usr/src/linux
and it said the link was already there.

Okay I’m lost what do I do now

---

### Post by gertmul on 2007-08-30
rgibbs421, this might be a little late, but for the record, you need to remove the first link you created by doing "rm /usr/src/linux" before trying to create the 2nd link with "ln -s /usr/src/linux-source-2.6.10generic /usr/src/linux"

---

### Post by urinnersmile on 2008-01-09
I am having a problem installing my LAN. I am using the following motherboard:

Make: ASUS
Model: P5N-E SLi (Nvidia 650i chipset)

It has a LAN (RJ-45) port supported by Marvell 88E1116 Gigabit LAN controller.

Can anyone please help? 

I cannot shift completely to Ubuntu simply because I cannot connect to the internet. I am using a ADSL modem (Huawei 1003A) through ethernet.

---

