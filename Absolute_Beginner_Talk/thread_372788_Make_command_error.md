---
title: "Make command error"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by mielie007 on 2007-02-28
I'm having a problem getting "make" to compile and install drivers that i have downloaded for my iburst desktop modem. It gives me the following error message and then stops.

root@Dapper-Drakie:/etc/tmp/ibdriver-1.3.1-linux-2.6# make
make -C /lib/modules/2.6.17-10-server/build SUBDIRS=/etc/tmp/ibdriver-1.3.1-linux-2.6 modules
make[1]: Entering directory `/lib/modules/2.6.17-10-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-server/build'
make: *** [default] Error 2
root@Dapper-Drakie:/etc/tmp/ibdriver-1.3.1-linux-2.6#


Please help. what do i do to fix the problem?

---

### Post by energiya on 2007-03-01
Did you ./configure first? Or that is not needed for this install? What does the README or INSTALL file say about installing?

Also check if you have installed build-essential. If not
> 
sudo aptitude install build-essential


---

### Post by bracc0 on 2007-03-01
Hi, energiya,
I need to install build-essential 11.3
I downloaded the appropriate (I hope!) package release for my ubuntu 6.10 and I got a .tar.gz file

How I get this package installed?
I can't run any apt-get install at the moment because my company firewall blocks it.

Thanks in advance
Claudio

---

### Post by energiya on 2007-03-01
You should check *.deb packages. These are the debian style packages (Ubuntu is based on Debian). Download from [here]("http://packages.debian.org/unstable/devel/build-essential"). Choose the one to fit your hardware.

to install just
```

sudo dpkg -i build-essential_11.3_WHATEVER.deb

```

---

### Post by bracc0 on 2007-03-01
I have downloaded and untared the debian package. This is what I got:

claudio@claudiubuntu:~/pippo/build-essential-11.3$ ls -la
total 252
drwxr-xr-x 3 claudio claudio  4096 2007-03-01 13:53 .
drwxr-xr-x 3 claudio claudio  4096 2007-03-01 13:51 ..
-rw-r--r-- 1 claudio claudio 28166 2005-07-07 20:27 aclocal.m4
-rw-r--r-- 1 claudio claudio   116 2003-09-26 03:13 AUTHORS
-rwxr-xr-x 1 claudio claudio 83538 2005-07-07 20:28 configure
-rw-r--r-- 1 claudio claudio   673 2005-07-07 20:27 configure.ac
drwxr-xr-x 2 claudio claudio  4096 2006-07-10 01:43 debian
-rw-r--r-- 1 claudio claudio   332 2006-07-10 01:31 essential-packages-list-alpha
-rw-r--r-- 1 claudio claudio   332 2006-07-10 01:32 essential-packages-list-amd64
-rw-r--r-- 1 claudio claudio   330 2006-07-10 01:32 essential-packages-list-arm
-rw-r--r-- 1 claudio claudio   331 2006-07-10 01:32 essential-packages-list-hppa
-rw-r--r-- 1 claudio claudio   329 2006-07-10 01:32 essential-packages-list-hurd-i386
-rw-r--r-- 1 claudio claudio   331 2006-07-10 01:33 essential-packages-list-i386
-rw-r--r-- 1 claudio claudio   331 2006-07-10 01:33 essential-packages-list-ia64
-rw-r--r-- 1 claudio claudio   331 2006-07-10 01:33 essential-packages-list-m68k
-rw-r--r-- 1 claudio claudio   331 2006-07-10 01:34 essential-packages-list-mips
-rw-r--r-- 1 claudio claudio   333 2006-07-10 01:34 essential-packages-list-mipsel
-rw-r--r-- 1 claudio claudio   334 2006-07-10 01:34 essential-packages-list-powerpc
-rw-r--r-- 1 claudio claudio   331 2006-07-10 01:34 essential-packages-list-s390
-rw-r--r-- 1 claudio claudio   152 2005-07-05 17:26 essential-packages-list-sh
-rw-r--r-- 1 claudio claudio   332 2006-07-10 01:35 essential-packages-list-sparc
-rwxr-xr-x 1 claudio claudio  9231 2005-07-07 20:28 install-sh
-rw-r--r-- 1 claudio claudio  3533 2006-07-10 01:20 list
-rwxr-xr-x 1 claudio claudio  3127 2003-09-26 03:13 list2depends
-rwxr-xr-x 1 claudio claudio   827 2006-07-10 01:31 make-esslist.sh
-rw-r--r-- 1 claudio claudio   538 2005-07-07 20:27 Makefile.am
-rw-r--r-- 1 claudio claudio 13495 2005-07-07 20:28 Makefile.in
-rwxr-xr-x 1 claudio claudio 10587 2005-07-07 20:28 missing

As you can see, there are no .deb packages.
I tried to install the i386 file anyway with this command:

sudo dpkg -i essential-packages-list-i386

but I got an error that states more or less that the file is not in a debian archive format.
I tried to cp the file as  essential-packages-list-i386.deb but this dirty trick failed.
Any suggestion?

Thanks in advance
Claudio

---

### Post by energiya on 2007-03-01
Wait a second. I really don't understand what you did there. You unpacked build-essential ? Download the .deb package by clicking [here]("http://http.us.debian.org/debian/pool/main/b/build-essential/build-essential_11.3_i386.deb"), if you didn't allready do so, and just open a terminal window, change directory to where you downloaded and write this
```

sudo dpkg - i NAME_OF_THE_FILE.deb

```

Sorry if I missunderstood.

---

### Post by bracc0 on 2007-03-01
> **energiya said:**
> Wait a second. I really don't understand what you did there. You unpacked build-essential ? Download the .deb package by clicking [here]("http://http.us.debian.org/debian/pool/main/b/build-essential/build-essential_11.3_i386.deb"), if you didn't allready do so, and just open a terminal window, change directory to where you downloaded and write this
```

sudo dpkg - i NAME_OF_THE_FILE.deb

```

Sorry if I missunderstood.

Oh, I see what happened. Your first suggested link leads to the debian page for build-essential, and I kept downloading the .tar.gz :-)

Your second suggestion links directly to the .deb file. It works, but I need two more packages (depens by).

Thank you very much!
Claudio

---

### Post by bracc0 on 2007-03-01
Still no luck.
The build-essential package downloaded from the link you provided asks for more packages "debian style" that Synaptics shows as installed with "ubuntu style": gcc, g++, libc6-dev, and more.

Claudio

---

### Post by jvc26 on 2007-03-01
EDIT:: Apologies re-read and now understand why you can't apt-get install.
Il

---

### Post by rjfioravanti on 2007-03-01
so have you been downloading packages onto another computer and then transferring them to your internetless ubuntu machine? what packages do you need to install build-essential and what is stopping you from getting them

---

### Post by bracc0 on 2007-03-02
Finally I got build-essential installed!
The solution was astonishingly easy: package and all dependancies was onto the live CD.

Bye
Claudio

---

### Post by energiya on 2007-03-02
> **bracc0 said:**
> Finally I got build-essential installed!
The solution was astonishingly easy: package and all dependancies was onto the live CD.

Bye
Claudio

Sorry, forgot about that!

---

### Post by mielie007 on 2007-03-02
i'm still keep getting the same error as before 

and i am using build-essential 11.3

please can somebody look at this error out put and tell me why i cant get it to run make and make install](*,) 

root@Dapper-Drakie:/etc/tmp/ibdriver-1.3.2-linux-2.6# make
make -C /lib/modules/2.6.17-10-server/build SUBDIRS=/etc/tmp/ibdriver-1.3.2-linux-2.6 modules
make[1]: Entering directory `/lib/modules/2.6.17-10-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-server/build'
make: *** [default] Error 2
root@Dapper-Drakie:/etc/tmp/ibdriver-1.3.2-linux-2.6#

---

### Post by bracc0 on 2007-03-02
Hve you tried to run ```
./configure
``` before running ```
make
```? Let us know

---

### Post by Big_Rog on 2007-03-02
for reasons i can't explain, ./configure doesn't exist on my system.  I'm using xubuntu 6.10 (which is GREAT!! by the way)  and as far as i can tell, I have the right packages (gcc, build-essential, and the like) because make attempts to work, but any variant of configure (configure, .configure, ./configure) all return that the script does not exist...  Which package should I be looking for to make sure I have that script?

---

### Post by rjfioravanti on 2007-03-03
I am pretty sure a file called configure is supposed to be provided whenever you download from source. what source package did you download?

---

### Post by Big_Rog on 2007-03-03
sorry, this was in regard to a different app, but googling for ./configure only showed a few threads.  The app (nostromo n52 drivers) apparently used to use a configure file, but now does not.  I managed to get imwheel to configure, but like you said, it had a configure script with it.  Thanks anway =)

---

### Post by Maestro23 on 2007-03-03
> **Big_Rog said:**
> sorry, this was in regard to a different app, but googling for ./configure only showed a few threads.  The app (nostromo n52 drivers) apparently used to use a configure file, but now does not.  I managed to get imwheel to configure, but like you said, it had a configure script with it.  Thanks anway =)

Where did you d/l the file from?  Got a link?

---

### Post by mielie007 on 2007-03-04
>  bracc0  
	  	
Re: Make command error
Hve you tried to run
Code:

./configure

before running
Code:

make

? Let us know
Reply With Quote

i have also tried the ./configure command but no luck. there is also no configure file that i got out of the tag file that i downloaded. the file i downloaded was a driver for a iburst desktop modem. her is the link  [http://sourceforge.net/projects/ibdriver](http://sourceforge.net/projects/ibdriver)

i'll be glad for any help

---

### Post by bracc0 on 2007-03-05
I've d/l the same file.

Uncompress it and un-tar it. Then go into the directory you got. have a look into the README file.
It says to run 

./make

Should this command fail, you probably need some aditional packages. Grab the output of the command and post here.

Hope it helps
Claudio

---

### Post by mielie007 on 2007-03-05
I tried ./make

here is the out put for the command

root@Dapper-Drakie:/etc/tmp/ibdriver-1.3.2-linux-2.6.17# ./make
-bash: ./make: No such file or directory
root@Dapper-Drakie:/etc/tmp/ibdriver-1.3.2-linux-2.6.17#

---

### Post by rjfioravanti on 2007-03-05
just type 

make

its a command =)

---

