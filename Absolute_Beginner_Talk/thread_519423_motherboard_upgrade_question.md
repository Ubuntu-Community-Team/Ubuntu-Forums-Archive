---
title: "motherboard upgrade question"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by vitalejd on 2007-08-07
I may be upgrading my motherboard soon.  Will I have to reinstall Ubuntu to use it again?  And I'm really a noob at this...what will happen when I boot up the first time after I install the new motherboard?  And basically what do I NEED to do before I replace the motherboard?  Any help would be great.  thanks!!

---

### Post by sysikon on 2007-08-07
No, you do not need to reinstall Ubuntu.

Just make sure your new motherboard is ok with Ubuntu.

---

### Post by vitalejd on 2007-08-07
> **sysikon said:**
> No, you do not need to reinstall Ubuntu.

Just make sure your new motherboard is ok with Ubuntu.


How do I make sure it's ok with ubuntu?

---

### Post by Inxsible on 2007-08-07
a lot could change with changing the mobo. it all depends on what new hardware you put it. You new mobo might have a on board graphics card. it might have a different sound card, a different wireless card and so on and so forth.

At worst, you might have to install every piece of hardware related software again. Hopefully everything will be Linux compatible. :)

---

### Post by vitalejd on 2007-08-07
> **Inxsible said:**
> 

At worst, you might have to install every piece of hardware related software again. 

Is this difficult to do?

---

### Post by Inxsible on 2007-08-07
> **vitalejd said:**
> Is this difficult to do?
if your hardware does not work out of the box for Feisty, then yes it is tedious to install everything again.

---

### Post by vitalejd on 2007-08-07
> **Inxsible said:**
> if your hardware does not work out of the box for Feisty, then yes it is tedious to install everything again.

Say everything with the new mobo does work out of the box...what will ubuntu do when I try to boot it up the first time?


I am just trying to find out what to expect.  I know window$ will blow up if you try to boot in it w/ a new mobo before repairing windows.

---

### Post by Inxsible on 2007-08-07
some hardware might work, for others you might have to download additional packages. this should not be difficult. 

Of course, this is [COLOR=Red]assuming [/COLOR]that everything will work.

---

### Post by gunderwood on 2007-08-07
When you purchase new hardware check to ensure that it is supported by Ubuntu by checking [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) 

Provided that the hardware you switch over to is supported you should have very few issues. The linux kernel includes drivers for a lot of hardware so if your hardware is on the ubuntu compatability list it should just work. 

The one issue that may cause you the most grief is if you have onboard graphics instead of using the same graphics card. If you are switching graphics hardware you will have to change your X Server configuration to use a the appropriate driver for the new hardware. A simple way of doing this is to run from the command line:

```
sudo dpkg-reconfigure xserver-xorg
```

after the new hardware has been installed.

I've swapped out several pieces of hardware, including motherboards,  on linux systems over the years and there is never really a reason to have to re-install the entire OS in order to make it work. It's just a matter of compatibility and reconfiguration.

G

---

### Post by vitalejd on 2007-08-07
> **gunderwood said:**
> When you purchase new hardware check to ensure that it is supported by Ubuntu by checking [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport) 

Provided that the hardware you switch over to is supported you should have very few issues. The linux kernel includes drivers for a lot of hardware so if your hardware is on the ubuntu compatability list it should just work. 

The one issue that may cause you the most grief is if you have onboard graphics instead of using the same graphics card. If you are switching graphics hardware you will have to change your X Server configuration to use a the appropriate driver for the new hardware. A simple way of doing this is to run from the command line:

```
sudo dpkg-reconfigure xserver-xorg
```

after the new hardware has been installed.

I've swapped out several pieces of hardware, including motherboards,  on linux systems over the years and there is never really a reason to have to re-install the entire OS in order to make it work. It's just a matter of compatibility and reconfiguration.

G

Ok, thanks for your help everyone.  I plan on using the game grfx card.  I have a nvidia 7600 GS 512 MB card.  Main reason for a new motherboard is to get SLI capability along with better RAM.

Is it generally easy replacing a motherboard (the physical aspect of it)?

---

