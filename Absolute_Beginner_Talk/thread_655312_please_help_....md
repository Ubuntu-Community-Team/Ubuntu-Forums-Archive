---
title: "please help ..."
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by b33gl3 on 2008-01-01
i have just about read up on everything i can get my hands on ... but i just cant seem to find any info on this particular subject...  I am a newb ... I was running xp ...    but  decided to give UBUNTU a shot because i always wanted to learn Linux and Unix Os's.... 
  
                     anyways ... on Xp I was connecting online through my cell phone provider (alltel) through there WINDOWS software via usb to my MOTOROLA V3M....  Now I cant get online ....  How do i set this up in Ubuntu .... ?

  ( Everything i read tells you how to locate the phone and transfer pictures and data.. well my phone is basically my modem that hooks up via USB ....  )

---

### Post by (((X))) on 2008-01-01
Are they providig software for linux  too?
It's best you call them to help you.

---

### Post by (((X))) on 2008-01-01
Is that windows software designed to connect to the internet?:confused:

---

### Post by b33gl3 on 2008-01-01
The software is designed to connect me to the internet ... it is the dial up connection like a modem .... anyways I am going to see if my cell phone provider has any software for that .... I was wishing there was a way to convert or play an executable file ... in linux ... and get linux to recongnize my phone/modem ...   any other suggestions .... ?

---

### Post by (((X))) on 2008-01-01
There is an app that can run some windows progs called  wine, not shure if it is able to connect your mashine to internet.

---

### Post by nick_h on 2008-01-01
Does [this](http://ubuntuforums.org/showthread.php?t=629528) post help?

---

### Post by LowSky on 2008-01-01
I know of a program called Bitpim that is availible in Synaptic, which allows you to play with your phones data. The there is a program called Gnome-PPP that lets you use a dial-up modem, I think that might help. Another program called Cobex might work, Gammu might do something, gnome-phone-manager...is another choice

Just type phone into synaptic search and so much stuff comes up

---

### Post by b33gl3 on 2008-01-01
I greatly appreciate it this forum is very helpful  .... I got the programs ... but it is source code or something when i open it (.tar,.tgz )it is like a package that needs to be compiled .. how do i compile them.... do i do it through the terminal ... ?  
   Is there a website that will help me learn this ... ?     :confused:

---

### Post by nick_h on 2008-01-01
Is there a readme file in the tar.gz archive?  If you give us a link to the file then we can have a look for you.

---

### Post by DishBreak on 2008-01-01
[http://linuxbasics.org/tutorials/using/installing_applications](http://linuxbasics.org/tutorials/using/installing_applications)

google is your best friend in linux. =) of course, different tarballs are slightly different in installs, but you should be fine with this.

---

### Post by Whiffle on 2008-01-01
Try this, maybe:
[http://ubuntuforums.org/showthread.php?t=343989&highlight=razr](http://ubuntuforums.org/showthread.php?t=343989&highlight=razr)

Looks like linux support is still dicy.

---

### Post by b33gl3 on 2008-01-01
good site...  just still a little stumped on how to compile the packages because on some of the instructions on some sites tell me i need other programs that i have to compile too .... i dont know ... maybe i am just confused .. i will keep trying and wont give up till ' i learn this OS ..  (all ears and eys open to new tips ...) 
   once again thanks all ... i appreciate the time and effort to help me learn ...

---

### Post by b33gl3 on 2008-01-01
ok i got the compiling process almost figured out .... its just that i think i am doing something wrong when i go to configure the package or source... i get this same code on all my installs i try to configure:
******** first install***************************************************************
b33gl3@b33gl3-desktop:~$ cd wine-0.9.52
b33gl3@b33gl3-desktop:~/wine-0.9.52$ configure
bash: configure: command not found
b33gl3@b33gl3-desktop:~/wine-0.9.52$ makew
bash: makew: command not found
b33gl3@b33gl3-desktop:~/wine-0.9.52$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
b33gl3@b33gl3-desktop:~/wine-0.9.52$ 
*******second install**************************************************************
b33gl3@b33gl3-desktop:~/gnome-ppp-0.3.23$ cd gnome-ppp-0.3.23
b33gl3@b33gl3-desktop:~/gnome-ppp-0.3.23/gnome-ppp-0.3.23$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
b33gl3@b33gl3-desktop:~/gnome-ppp-0.3.23/gnome-ppp-0.3.23$ 

 seems like something isnt set up right or something get the samething on all my installs i try .....

---

### Post by sailor2001 on 2008-01-01
you have a sierra card most likely..[http://ubuntuforums.org/showthread.php?t=320557&highlight=sierra+875](http://ubuntuforums.org/showthread.php?t=320557&highlight=sierra+875)

---

