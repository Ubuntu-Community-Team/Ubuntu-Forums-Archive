---
title: "How to reinstall Xubuntu from 32 bit to 64 bit on a MacBook"
date: 2017-05-02
forum: Apple Hardware Users
---

### Post by sbac on 2017-05-02
[COLOR=#111111][FONT=Ubuntu]I have a MacBook late 2007 with 4 Gb Ram, running _only_ Xubuntu 16.04 32 bit (single boot). I discovered that my Mac is capable of running a 64 bit version.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]How can I reinstall a 64 bit version of Xubuntu 16.04? I tried to burn a DVD-R without exit.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried to do it with a USB pen with a folder named EFI and inside this folder a BOOT folder containing the iso file of Xubuntu (64 bit) and a bootX64.efi file [COLOR=#000000][FONT=Verdana]from SevenBits Github page [/FONT][/COLOR](I used a 32 version before when I installed the 32 bit version on my Mac). I used the method described in [https://ubuntuforums.org/showthread.php?t=2266424](https://ubuntuforums.org/showthread.php?t=2266424).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The problem is that when I reinitialize the Mac now, it does not boot using the USB pen (after restarting with Alt). What can I do?[/FONT][/COLOR]

---

### Post by mörgæs on 2017-05-02
Hi, welcome to the fora.

Why do you want to switch to 64 bit?

---

### Post by sbac on 2017-05-02
Hi, it's only to get the maximum update possible with an old machine that was running before (with OSX) at 64 bit. I read also that 64 bit systems manage better RAM memory. But as I have only 4Gb RAM I just don't need to upgrade, isn't it?

---

### Post by mörgæs on 2017-05-02
If you run some very demanding applications you might see an improvement but for normal use I expect the change to be minimal. 

If you are going to install 18.04 in a year from now you could use the opportunity to switch to the 64 bit version.

---

### Post by sbac on 2017-05-02
So you think it's better to wait for Xubuntu 18.04? But I will have the same installation problem I already have now.

---

### Post by Bucky Ball on 2017-05-02
[QUOTE=sbac]But I will have the same installation problem I already have now. [/QUOTE]

Welcome. Not necessarily. You'll be a year more experienced at it by then, so it might be a breeze. ;) You don't need to do whatever you are doing with the USB. Just wipe the USB, create one FAT32 partition and use UNetbootin, Rufus or whatever else USB boot creator to do the job. The USB will boot on UEFI or legacy systems. You don't need to stuff about with that beforehand.

Having said that, I wouldn't bother with switching for now, personally.

---

### Post by sbac on 2017-05-05
Well, I tried hard and after trying to use Unetbootin and Mac-Linux-USB-loader, I found the solution to install Xubuntu 16.04 64 bit. 
The problem was that my MacBook late 2007 is a 64 bit Mac but uses a 32 bit EFI. Fortunately, I had a working DVD.
The process is described in [https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/](https://mattgadient.com/2016/07/11/linux-dvd-images-and-how-to-for-32-bit-efi-macs-late-2006-models/).

---

### Post by mörgæs on 2017-05-05
Thanks for posting the solution.
If you also mark the thread solved there is a better chance that people are going to find it.

---

### Post by sbac on 2017-05-06
Thank you, I did it now.

---

