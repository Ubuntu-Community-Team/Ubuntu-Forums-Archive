---
title: "Re: How do I install PSF plugin for XMMS?"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by elaich on 2007-02-21
I'm having a similar problem trying to compile and install the Sexy PSF plugin for XMMS.

Here is what the readme says:

"This is sexypsf, based off of pcsx and peops.

To compile, go to the xmms directory, and type "make", if you're 
running on an x86(IA32) system.
If you want to compile for a generic LSB-first(ARM, IA32, AMD64, etc.), do 
"make CPU=LSBFIRST".  For a generic MSB-first(PowerPC) platform,
do "make CPU=MSBFIRST".

You can then do "make install" to install it to ~/.xmms/Plugins"

I have followed the instruction in this thread and in the readme. I get:

sudo: make: command not found.

The contents of the XMMS directory are makefile, and xmms.c

This is confusing.

---

### Post by taurus on 2007-02-21
You need to install the build-essential package first before you can run make.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Luk0r on 2007-02-21
Did you try doing
```
sudo apt-get install build-essential
```?

Ah, beaten to it. :)

---

### Post by aysiu on 2007-02-21
> **elaich said:**
> I'm having a similar problem trying to compile and install the Sexy PSF plugin for XMMS. Even though the problem is similar, it isn't the same problem and deserves its own support thread, so I've moved your post into a new thread.

> 
sudo: make: command not found. Ubuntu, for no good reason, doesn't include *make* with a default installation. You have to install compile tools before you compile from source: ```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by po0f on 2007-02-21
elaich,

```
[font="courier new"]$ sudo apt-get install build-essential[/font]
```

[EDIT]

Geez, where were you guys 30 seconds ago?  :p

---

### Post by Maestro23 on 2007-02-21
> **elaich said:**
> I'm having a similar problem trying to compile and install the Sexy PSF plugin for XMMS.

Here is what the readme says:

"This is sexypsf, based off of pcsx and peops.

To compile, go to the xmms directory, and type "make", if you're 
running on an x86(IA32) system.
If you want to compile for a generic LSB-first(ARM, IA32, AMD64, etc.), do 
"make CPU=LSBFIRST".  For a generic MSB-first(PowerPC) platform,
do "make CPU=MSBFIRST".

You can then do "make install" to install it to ~/.xmms/Plugins"

I have followed the instruction in this thread and in the readme. I get:

sudo: make: command not found.

The contents of the XMMS directory are makefile, and xmms.c

This is confusing.

If you are installing from source, you need "build-essential" installed first.

Open a terminal:

> sudo aptitude update && sudo aptitude install build-essential checkinstall

*Then follow the instructions in the README.

Some links to read/bookmark:

Command Line Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Installing in Ubuntu:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Good luck.

EDIT:  Never can have to much help I see..:)

---

### Post by elaich on 2007-02-22
Does anybody want to see the load of errors I got back after doing the download and install so that make will work?

me@me-desktop:~$ cd sexypsf/xmms
me@me-desktop:~/sexypsf/xmms$ make
make: gtk-config: Command not found
gcc  -Wall -O2 -finline-functions -ffast-math -fomit-frame-pointer -mcpu=i686 -f no-exceptions -I. -I.. -I/usr/include/g++ -DPSS_STYLE=1 -DSPSFVERSION="\"0.4.6\" "  -c -o ../PsxBios.o ../PsxBios.c
`-mcpu=' is deprecated. Use `-mtune=' or '-march=' instead.
In file included from ../PsxBios.c:25:
../PsxCommon.h:38:18: error: zlib.h: No such file or directory
../PsxBios.c: In function ‘bios_atoi’:
../PsxBios.c:272: warning: null argument where non-null required (argument 1)
../PsxBios.c: In function ‘bios_atol’:
../PsxBios.c:277: warning: null argument where non-null required (argument 1)
../PsxBios.c: In function ‘bios_strcmp’:
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 2)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 2)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 2)
../PsxBios.c:356: warning: null argument where non-null required (argument 1)
../PsxBios.c:356: warning: null argument where non-null required (argument 2)
../PsxBios.c: In function ‘bios_strpbrk’:
../PsxBios.c:479: warning: null argument where non-null required (argument 2)
../PsxBios.c:479: warning: null argument where non-null required (argument 2)
../PsxBios.c:479: warning: null argument where non-null required (argument 2)
../PsxBios.c: In function ‘bios_strspn’:
../PsxBios.c:487: warning: null argument where non-null required (argument 1)
../PsxBios.c:487: warning: null argument where non-null required (argument 2)
../PsxBios.c:487: warning: null argument where non-null required (argument 1)
../PsxBios.c:487: warning: null argument where non-null required (argument 2)
../PsxBios.c:487: warning: null argument where non-null required (argument 1)
../PsxBios.c:487: warning: null argument where non-null required (argument 2)
../PsxBios.c: In function ‘bios_strcspn’:
../PsxBios.c:488: warning: null argument where non-null required (argument 1)
../PsxBios.c:488: warning: null argument where non-null required (argument 2)
../PsxBios.c:488: warning: null argument where non-null required (argument 1)
../PsxBios.c:488: warning: null argument where non-null required (argument 1)
../PsxBios.c:488: warning: null argument where non-null required (argument 1)
../PsxBios.c:488: warning: null argument where non-null required (argument 2)
../PsxBios.c:488: warning: null argument where non-null required (argument 1)
../PsxBios.c:488: warning: null argument where non-null required (argument 2)
../PsxBios.c: In function ‘bios_strstr’:
../PsxBios.c:504: warning: null argument where non-null required (argument 2)
../PsxBios.c:504: warning: null argument where non-null required (argument 2)
../PsxBios.c: In function ‘bios_bcmp’:
../PsxBios.c:549: warning: null argument where non-null required (argument 1)
../PsxBios.c:549: warning: null argument where non-null required (argument 2)
../PsxBios.c:549: warning: null argument where non-null required (argument 1)
../PsxBios.c:549: warning: null argument where non-null required (argument 2)
../PsxBios.c: In function ‘bios_memcmp’:
../PsxBios.c:589: warning: null argument where non-null required (argument 1)
../PsxBios.c:589: warning: null argument where non-null required (argument 2)
../PsxBios.c:589: warning: null argument where non-null required (argument 1)
../PsxBios.c:589: warning: null argument where non-null required (argument 2)
../PsxBios.c: In function ‘bios_memchr’:
../PsxBios.c:594: warning: null argument where non-null required (argument 1)
../PsxBios.c: In function ‘psxBiosInit’:
../PsxBios.c:1248: warning: pointer targets in passing argument 1 of ‘strcpy’ di ffer in signedness
make: *** [../PsxBios.o] Error 1

Does this plugin have to be specifically configured for Debian? In Puppy, someone made a .pup of it, and I had it installed in no time. I have other issues with Puppy, but playing these PSF files is something that is high on my list. Thanks for the help so far.

---

### Post by po0f on 2007-02-22
elaich,

This should solve your immediate problems.

```
[font="Courier New"]$ sudo apt-get install libgtk1.2-dev zlib1g-dev[/font]
```

If something else comes up, post back.

---

### Post by elaich on 2007-02-28
Didn't work. I get even more error messages now. :(

---

### Post by elaich on 2007-03-04
Just for the record, I never was able to compile this plugin. Even the guy who is hosting it couldn't figure out why. I even tried downloading it as an RPM, and using alien to make it into a .deb. No dice. But, there's a simple solution for those who want to play .psf files in XMMS. It's Highly Experimental.

[http://www.brownjava.org/software/he-xmms/](http://www.brownjava.org/software/he-xmms/)

No install required. You simply drop a file into .xmms/Plugins. Works great.

---

