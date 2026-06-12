---
title: "Installing Ubuntu &quot;Again&quot; Yaaah!"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-27
***I had everything working fine - until I booted up this morning.***  :confused:

**Yesterday**:
I could not start any OpenOffice apps. I had to install a new driver for my ATI Radeon 9200SE to get the OpenOffice apps to work. A Google search revealed that my ATI card was causing the problem. I downloaded and installed a newer driver. The OpenOffice apps worked fine. Soft boots kept everything working great.

**Today**:
A cold (hard) boot this morning prevented me from going into Ubuntu. Nothing i tried would fix the problem. So, I need to re-install Ubuntu Dapper again. :(

**Situation**:
1. I have two IDE drives. (See signature info below.)
  a. One drive has WinXP already installed on it. (160GB drive) **Set as Slave**.
  b. I now want Ubuntu installed on the other drive. (80 GB drive) **Set as Master**.

2. What is the **best** way to do the install and have GRUB work properly? **How would I set the jumpers on each drive? Which should be master and which slave? Do I have them set wrong? (See above.) I know "how" to set the jumpers. Just need to know if they are set right to install Dapper.**

3. I tried installing Ubuntu earlier today with WinXP drive set as slave and the drive where I wanted Ubuntu set as master. It messed up some files and I could not get GRUB to work when I rebooted. I want to avoid this problem on this install.

**Gratitude**:
I appreciate any advice that will make this easy. I will take hand notes for later referencing should this occur again.

Thanks for all assistance. BTW, I am not even thinking of giving up with Ubuntu. I think it is a great OS. Just need to better understand what I need to get it working right. I know one thing, this ATI Radeon 9200SE's days are numbered. 

**Speak Up!**
I would like some advice on which Nvidia video card I can buy, have everything I need for 3D and whatever else Linux needs, and still keep the price in the range of a person who is retired. Here's your chance to boot ATI. Go for it.

kh :)

---

### Post by oilchangeguy on 2007-03-27
for your jumper settings, look on the hard drive label. or go to the hard drive makers web site and search for the model to find the correct jumper settings. i dual boot also, using the same set up as you, ubuntu, master, windows, slave.

---

### Post by kittyhawk63 on 2007-03-27
> **oilchangeguy said:**
> for your jumper settings, look on the hard drive label. or go to the hard drive makers web site and search for the model to find the correct jumper settings.

I know how to set the jumpers. That is not what I am asking. I need to know which drive I set as master and which as slave when I install Dapper.

---

### Post by bulldog on 2007-03-27
Leave them as they are,windows as a slave and ubuntu as master.
If everything is as it should be,the ubuntu disk is called (hd0) and windows (hd1)
You can confirm this from the live cd by performing```
cat /boot/grub/device.map
```

You installed ubuntu before so that needs no explanation :) ,install GRUB on (hd0) which is the default and reboot after the install.
You should be able to boot ubuntu but ** not ** windows.
To boot windows you need some modification of the menu.lst```
gksudo gedit /boot/grub/menu.lst
```

Make your windows entry look like this one,but don't change you partition,just add two mapping lines and make root --> rootnoverify.
That should do it.
If you have more questions just ask.
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
map          (hd0) (hd1)
map          (hd1) (hd0)   
savedefault
makeactive
chainloader	+1
```

---

### Post by old_geekster on 2007-03-27
I have installed Edgy "13" (idiot or insanity) times in the past month.  Doing a clean install is my way of trouble-shooting.  If I can't figure out what is wrong in 5 minutes, I do a clean install.

I suggest that you install Windows before installing Linux.  This has been recommended on every site that I have researched.

I don't like the idea that "GRUB" is on the first sector of my XP drive, but it works, so who is arguing?

Q: Speak Up!
I would like some advice on which Nvidia video card I can buy, have everything I need for 3D and whatever else Linux needs, and still keep the price in the range of a person who is retired. Here's your chance to boot ATI. Go for it.

A: When I built my rig in May, 2006, I did extensive research on video cards, as well as, all other components . "XFX" was the winner in almost every category.  It is going on a year and I have absolutely no complaints.  I am using the latest nVidia driver (9755) and my card performs every bit as good in Edfy as it does in XP Pro.

You could easily get by with a 7600 or 7800 card.  Either would give you excellent performance.  In fact, I don't believe that you would gain anything by buying a 7900 for $550.

There is my $.02.

Good luck!

p.s. Notice that I did not mean-mouth ATI.  However, with that said, the negative reviews that I read about their drivers is what caused me to buy nVidia again.

---

### Post by kittyhawk63 on 2007-03-27
[quote=old_geekster;2363029]I have installed Edgy "13" (idiot or insanity) times in the past month.  Doing a clean install is my way of trouble-shooting.  If I can't figure out what is wrong in 5 minutes, I do a clean install.

You didn't say whether you would use Windows set as master or slave. How have you done it?

I have been doing it as suggested on the post before yours. However, I have read that Windows doesn't like to play second fiddle to Linux.

---

### Post by kittyhawk63 on 2007-03-27
[quote=bulldog;2362966]Leave them as they are,windows as a slave and ubuntu as master.

Bulldog, isn't this kind of a work-a-round method? If Windows is set as Master, doesn't this avoid all this terminal input? I have been doing it the way you suggest. I am just wondering if it is the "best, least troublesome" way.
kh

---

### Post by bulldog on 2007-03-27
> **kittyhawk63 said:**
> [quote=bulldog;2362966]Leave them as they are,windows as a slave and ubuntu as master.

Bulldog, isn't this kind of a work-a-round method? If Windows is set as Master, doesn't this avoid all this terminal input? I have been doing it the way you suggest. I am just wondering if it is the "best, least troublesome" way.
kh

Yes doing it this way has some advantage.
1/ You can reinstall windows without messing with grub,because it's on the other disk.
2 / In case of trouble with GRUB,you can boot windows from it's own boot loader by changing the boot order in the BIOS.


So you have a completely independent ubuntu and windows as well,the only connection is made in the GRUB menu so you can boot both from the same menu.

---

### Post by kittyhawk63 on 2007-03-27
> **bulldog said:**
> [quote=kittyhawk63;2363112]
Yes doing it this way has some advantage.
1/ You can reinstall windows without messing with grub,because it's on the other disk.
2 / In case of trouble with GRUB,you can boot windows from it's own boot loader by changing the boot order in the BIOS.
So you have a completely independent ubuntu and windows as well,the only connection is made in the GRUB menu so you can boot both from the same menu.

You make some good points. I shall continue to do it as you suggested and I've been doing. Thank you,
kh

---

