---
title: "pigding compile problem"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by immelman on 2007-06-24
Hello!

I wanted to give pidgin a try and since it is not in the repositories I downloaded the source and did:

sudo ./configure
sudo makefile
sudo checkinstall

However on the last one, .deb package creation gets borked and I get this output:

```
(Reading database ... 130755 files and directories currently installed.)
Unpacking pidgin (from .../pidgin_2.0.2-1_powerpc.deb) ...
dpkg: pidgin: warning - conffile `etc/gconf' is not a plain file or symlink (= `
/etc/gconf')
dpkg: pidgin: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain f
ile or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing /home/scott/pidgin-2.0.2/pidgin_2.0.2-1_powerpc.deb (--in
stall):
 trying to overwrite `/usr/lib/gcc/powerpc-linux-gnu/4.1.2/collect2', which is a
lso in package gcc-4.1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/scott/pidgin-2.0.2/pidgin_2.0.2-1_powerpc.deb
```


Does anybody know what I should do??

cheers!

PS. Yes I'm on PowerPC so the i386.deb of pidgin is of no use to me, hence me trying to compile ;-)

---

### Post by scxtt on 2007-06-24
seems like a gcc problem - "error processing /home/scott/pidgin-2.0.2/pidgin_2.0.2-1_powerpc.deb (--install): trying to overwrite `/usr/lib/gcc/powerpc-linux-gnu/4.1.2/collect2', which is also in package gcc-4.1" - what's the output of **aptitude search gcc**?

---

### Post by immelman on 2007-06-24
The output is

```
p   colorgcc                        - Colorizer for GCC warning/error messages  
i   gcc                             - The GNU C compiler                        
p   gcc-2.95-doc                    - Documentation for the GNU compilers (gcc, 
p   gcc-3.3                         - The GNU C compiler                        
id  gcc-3.3-base                    - The GNU Compiler Collection (base package)
p   gcc-3.3-doc                     - Documentation for the GNU compilers (gcc, 
p   gcc-3.4                         - The GNU C compiler                        
p   gcc-3.4-base                    - The GNU Compiler Collection (base package)
p   gcc-3.4-doc                     - Documentation for the GNU compilers (gcc, 
p   gcc-4.0-locales                 - The GNU C compiler (native language suppor
i   gcc-4.1                         - The GNU C compiler                        
i   gcc-4.1-base                    - The GNU Compiler Collection (base package)
p   gcc-4.1-doc                     - Documentation for the GNU compilers (gcc, 
p   gcc-4.1-locales                 - The GNU C compiler (native language suppor
p   gcc-4.1-source                  - Source of the GNU Compiler Collection     
p   gcc-avr                         - The GNU C compiler (cross compiler for avr
p   gcc-doc                         - Documentation for the GNU C compilers (gcc
v   gcc-docs                        -                                           
p   gcc-h8300-hms                   - The GNU C compiler (cross compiler for h83
p   gcc-m68hc1x                     - GNU C compiler for the Motorola 68HC11/12 
p   gcc-snapshot                    - A SNAPSHOT of the GNU Compiler Collection 
p   gcc272-docs                     - Documentation for the gcc compiler (gcc272
p   gccxml                          - XML output extension to GCC               
p   lib64gcc1                       - GCC support library (64bit)               
i   libgcc1                         - GCC support library                       
p   pocketpc-gcc                    - The GNU C compiler for Pocket PC    
```

---

### Post by scxtt on 2007-06-24
now how about the output of:

sudo slocate -u
slocate collect2

---

### Post by immelman on 2007-06-24
> **scxtt said:**
> now how about the output of:

sudo slocate -u

That one gives me a big fat nothing. I don't know if it's normal :-?

> slocate collect2

For that one I get:

```
/usr/lib/gcc/powerpc-linux-gnu/4.1.2/collect2
```

Thanks for the super fast answers by the way!

---

### Post by scxtt on 2007-06-24
the 1st one is just (re)creating the "secure locate" database -- if you've never used it before, it'll make sure it's up to date - there (generally) isn't anything returned ...

i'm wondering if it's a "problem" in the configure file, just not pointing to the *exact* version of gcc installed on your box ...

how about the output of **gcc --version** (and maybe post the configure file?)

---

### Post by shifty_powers on 2007-06-24
Tbh, checkinstall, whilst handy when compiling from source, as it allows your package manager to remove it or update it later on, is known to have issues sometimes. It might just be simpler to:

```
./configure
make
sudo make install
```

I know it makes uninstalling a pain, but it was the only way i found to compile form source. Couldn't get checkinstall to play fair in this case.....

Edit: oh and just noticed form your fist post, you don't actually need, (or at least shouldn't), sudo to use ./configure and make...

---

### Post by immelman on 2007-06-24
> **scxtt said:**
> the 1st one is just (re)creating the "secure locate" database -- if you've never used it before, it'll make sure it's up to date - there (generally) isn't anything returned ...

i'm wondering if it's a "problem" in the configure file, just not pointing to the *exact* version of gcc installed on your box ...

how about the output of **gcc --version** (and maybe post the configure file?)

The output is:

```
scott@lappy:~/pidgin-2.0.2$ gcc --version
gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

[QUOTE=shifty_powers] 	Tbh, checkinstall, whilst handy when compiling from source, as it allows your package manager to remove it or update it later on, is known to have issues sometimes. It might just be simpler to:

Code:

./configure
make
sudo make install

I know it makes uninstalling a pain, but it was the only way i found to compile form source. Couldn't get checkinstall to play fair in this case.....

Edit: oh and just noticed form your fist post, you don't actually need, (or at least shouldn't), sudo to use ./configure and make...[/QUOTE]

Ok, it's good to know I don't need sudo, it's just that I was not sure and decided to go sudo all the way (I know it's potentially dangerous).  However, when running make I do need to use sudo as I have "access denied" for a certain number of stuff while it works when I use sudo.

concerning make install, I will try that and let you know!

---

### Post by shifty_powers on 2007-06-24
I find that if you use sudo to open something, it changes the permissions of that file to root only. You shouldn't need sudo to configure and make the source. I have done that without sudo many, many times ;)

Good luck with make install ;)

Like i said, just bear in mind that make install will not register the program with synaptic, so upgrading it latre may be a pain, but if it is the only way to install....

---

### Post by immelman on 2007-06-24
Make install worked a charm, I will check out how to uninstall it later. I'm missing some libraries (SSL or something) but I guess I can find this via synaptics.

Thanks for your help!
Cheers,

---

