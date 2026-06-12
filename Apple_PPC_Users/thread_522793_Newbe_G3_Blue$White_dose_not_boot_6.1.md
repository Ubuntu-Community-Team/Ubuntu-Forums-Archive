---
title: "Newbe G3 Blue$White dose not boot 6.1"
date: 2007-08-11
forum: Apple PPC Users
---

### Post by alsehendo34 on 2007-08-11
Newbee G3 Blue$White 256M memory dose not boot 6.1. 
I just get a black screen. 9.x on first partion.
Yes I have the PPC version from download and I picked it it up off Linux Central

Should this Mac run ubuntu?

Should I try ver 5?

---

### Post by pxwpxw on 2007-08-11
It should run 7.04. Please give more details of your system and what you are doing including what video cards in the B&W. When does it go black and what is the CD version  etc.

---

### Post by alsehendo34 on 2007-08-11
G3 400MHz (Machine ID 406)
I have 256M of memory
My video card is ati rage 128
My hard drive is 120 Meg IDE with 3 partions 9.2 running on first.
I downloaded the CD from ubuntu site (ubuntu-7.04-desctop-powerpc.iso)
It did not work so I got preburt one off of Linux Central

The file README.diskdefines has the below in it if this helps?
#define DISKNAME  Ubuntu 7.04 "Feisty Fawn" - Release powerpc
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  powerpc
#define ARCHpowerpc  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1

This is my wife's computer 9.2 has outlived it's usfullness!!
I have been using Linux for years on x86 but when it dose not do squat it is hard to get started.  It boots the 9.2 disk install CD fine!  

When booting / power up to ubuntu cd it actually turns the green light on the monitor on but nothing to the screen it just stays black.  
I tried reset nvram.  I cranked up the brightness / contrast to max on the monitor.

help, thanks

---

### Post by pxwpxw on 2007-08-12
You should get the 704 ppc Server install cd, that uses text install interface with several options, and will eliminate graphics problems from the install phase. Gives you a command line console installation, from which you can then easily install a full desktop in second stage. Any graphics problems can then be sorted out at the end rather than struggling at the start.

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

---

### Post by FredSambo on 2007-08-12
Also make sure your HorizonSync and VertRefresh are correct in your xorg.conf.

Let me go check on the wife's iMac (Bluberry G3 DV 400MHZ 512MB RAM)...

---

### Post by FredSambo on 2007-08-12
OK her settings are:

(in the Monitor section)
HorizSync 58-62
VertRefresh 75-117

When you get to the blank screen after boot, hit alt + f1 to get to a prompt.  You can log in and edit your /etc/X11/xorg.conf file and then hit alt + f7 to get back.

Good luck!

---

### Post by bodycoach2 on 2007-08-12
On that iMac, I suggest using the Xubuntu 6.06.1 Alternate Install CD. Make sure you burn the CD REALLY slow! I've put that version of Xubuntu on several iMacs now, and it works fine. You can upgrade from there, if you want.

---

