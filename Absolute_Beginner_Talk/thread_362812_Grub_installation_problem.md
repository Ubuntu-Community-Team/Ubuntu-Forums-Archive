---
title: "Grub installation problem"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by AirAshby on 2007-02-16
After Typing:
```
ad9ar@ad9ar-laptop:~/grub-1.95$ sudo ./configure

```
I get:
```
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for cmp... cmp
checking for bison... bison
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for ruby... /usr/bin/ruby
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```
Does anyone know what I need to do?

---

### Post by Stephen Howard on 2007-02-16
hmm, sounds like an incomplete installation of the compiler.

Have you installed the Build Essentials package?  sudo apt-get install build-essentials

---

### Post by Stephen Howard on 2007-02-16
oops, just checked there's no 's' on the end of build-essentials.

---

### Post by colinnwx on 2007-02-25
I think nearly every beginner linux user  who hasn't read Psychocat's guide to installing has run into the problem (i did it yesterday :rP   ) can't this be noted and put into like, a dialogue box or something? Instead of C compiler cannot create executables, maybe the error message should read C compiler not found, or build essentials not found, or something.

On a side note, as a brand new user fresh from windows, I understand that giving newbies linux commands like 

sudo apt-get install build-essential
 or 
sudo aptitude install build essential 
(what's the difference between the two anyway? I thought aptitude takes care of all loose ends or dependencies or something). 

Anyway, I understand that giving newbies these commands is more effective, but it's quite hard to figure out what's going on just from the commands. Is getting build-essential through synaptic just as effective? coz I think i'd go with that until i can actually be 100% confident with composing and executing my own terminal commands.

Maybe it's me being influenced by the book I just leafed through... Moving to Ubuntu Linux by Marcel Gagne. In the first few pages he states that linux is an OS he'd be confident giving to his mother. Maybe being great at computers runs in the family : )

---

