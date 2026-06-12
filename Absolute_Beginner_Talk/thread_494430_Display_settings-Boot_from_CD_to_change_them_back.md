---
title: "Display settings-Boot from CD to change them back?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by ddk13 on 2007-07-06
I recently installed 7.04 feisty on my second hard drive, keeping windows XP on the first.  I have used Ubuntu before and love it.  I did come across a problem.  Somehow i changed my display settings and now unable to boot Ubuntu.  I need help changing my Xorg.conf file (i think that's what i need to do).  I can't connect to the X-server.  I was wondering how to boot from Live CD to correct my screwup it that is possible.  Any help is appreciated.

Thanks, 
Dave K

---

### Post by Raineer on 2007-07-06
You don't need to, you can do all the fixing you need to from what you're calling the "unable to boot" Ubuntu.

When it crashes, press Ctrl-Alt-F2 and log in. Now type the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
and choose an appropriate driver.  It will help to know which graphics card you have.

---

### Post by overdrank on 2007-07-06
> **ddk13 said:**
> I recently installed 7.04 feisty on my second hard drive, keeping windows XP on the first.  I have used Ubuntu before and love it.  I did come across a problem.  Somehow i changed my display settings and now unable to boot Ubuntu.  I need help changing my Xorg.conf file (i think that's what i need to do).  I can't connect to the X-server.  I was wondering how to boot from Live CD to correct my screwup it that is possible.  Any help is appreciated.

Thanks, 
Dave K

Hi and welcome, if you would use the alt,ctrl.F1 keys at the same time when you see the grub loading it will bring you to the terminal
then enter your screen name and password and then enter
```
sudo dkpg-reconfigure -phigh xserver-xorg
```
Hopefully (after you answer a few simple question) you will be able to boot to a desktop.
Good luck!:popcorn:

---

### Post by ddk13 on 2007-07-07
I  have come to the point where I need to select a driver.  I have an Intel Celeron 2.5GHz in my emachines T2542.  Which driver do I select?  Again, thank you for your help as I am still learning my way around!!

Dave K

---

### Post by ddk13 on 2007-07-07
And of course I forgot to ask what settings I should use.  I think I was at 1024 x 768.  Thanks again!!

Dave K

---

### Post by KuroRai on 2007-07-08
you only gave us the processor name ddk13 :P we need the graphic card name... if its nvidia, try nvidia, then nv, then vesa... iAm not sure about which it (thye) are for ATI because iDon't use them! hope this helps!

---

### Post by ddk13 on 2007-07-08
The processor is Intel Extreme Graphics AGP.  Thanks!!

---

### Post by lninjo on 2008-01-30
thanks for the information

---

