---
title: "Can not install Ubuntu 6.10"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by to4i on 2006-11-01
I have a problem with the desktop iso cd. I'm going for a clean install.
So, I can not boot from the live cd, It starts to loading but can not enter the desktop, just hangs aorund 97% or something and not diong anything. May be it's because of the X server... I have an ati GPU.

---

### Post by raqball on 2006-11-01
Simple answers are :

Did you md5 check the download and did you burn at 4x or lower?

---

### Post by to4i on 2006-11-01
I used the same CD and installed on VMware 5.5 with no problem at all.
So that should be ok.

---

### Post by taurus on 2006-11-01
Maybe there is a problem with your graphic card using the LiveCD!  Why don't you try using the alternate CD then?

---

### Post by to4i on 2006-11-01
My card is Ati X700. 
But if I use alternate CD, do I have to install by comand-line(not good) or just text mode?

---

### Post by raqball on 2006-11-01
It's just text mode, you will be fine :)

---

### Post by to4i on 2006-11-01
Ok, I hope I will :)
Thanks for the fast answers, and your help, awesome...
If I get stick agian, I'll write back.

---

### Post by Hasen_A on 2006-11-01
> **taurus said:**
> Maybe there is a problem with your graphic card using the LiveCD!  Why don't you try using the alternate CD then?

What alternative CD are you referring to? How am I able to start the installation without the Live CD process and directly use text mode?

---

### Post by taurus on 2006-11-01
> **Hasen_A said:**
> What alternative CD are you referring to? How am I able to start the installation without the Live CD process and directly use text mode?

Please look at this link regarding the alternate CD, a page down...

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by Aranel on 2006-11-01
> **Hasen_A said:**
> What alternative CD are you referring to? How am I able to start the installation without the Live CD process and directly use text mode?

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

Once you've selected a location, go to "Other Installation Options." There, you'll find an "Alternate Install CD" or some such - just look for the word "alternate."

Edit: taurus beat me to it. :p

---

### Post by to4i on 2006-11-03
OK, I installed Ubuntu 6.10 in text mode, everything went fine, but at the end when I try to start it, it could not load the desktop, the progress bar went like 97% and just hang...
I do not know what to type to change something in the X server or...

---

### Post by rionoco on 2006-11-04
ATI graphic cards are very bad for Linux.nvidia are the best for the job.
i have too a X700...i tryed to install the headers with the number of kernel version of the graphic card but nothing happen..

i found a temporaty solution for that kind of issue with the ATI graphic card, run the live cd in save graphic mode and install it from there.
:p

---

### Post by cohman on 2006-11-05
I ha just the same problem as to4i. My GPU is ATI X800XL. I got Ubuntu installed with the alternate cd but i don't get xserver to work. I have tried to reconfigure xserver and it just won't work. What shall i try next. ](*,)

---

### Post by EdInHouston on 2006-11-05
I'm trying to use the standard 386 Live DVD with the ATI visiontec card which I believe is a X700.  The kernel will load but Xorg wont run.  I can't switch to VESA because I can't get the terminal to work.  Puppy works in VESA mode but XORG doesn't work with this card as well.  If I could get the terminal to work it would be great.  I'm about to go back to my shared graphics memory and sell the card on Ebay.

---

### Post by Edgar on 2006-11-07
I've got an Acer Aspire 1694 Wlmi (piece of crap) and I managed to install Ubuntu 6.10 on it, but then I booted into the system and the problems started. Ubuntu system startup sound and a black screen. I tried going into text mode (Ctrl + Alt + F1) to modify the xorg.conf file, but when I do the screen goes all funny, and it's everything but usable! Any sugestions?

---

### Post by Paul133 on 2006-11-07
Is there a reason you're installing 6.1 and not 6.06? I know many people have had problems with 6.1.

---

### Post by Edgar on 2006-11-08
The only reason I'm installing 6.10 is because it's the latest version. That is what people tend to do, if it's new it can only be better, which is obviously not true. I had a look around the forum and it does seem loads of people are indeed having trouble with 6.10. If you have any good sugestions or advice it would be appreciated :D

---

