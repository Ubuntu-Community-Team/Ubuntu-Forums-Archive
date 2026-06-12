---
title: "ATI drivers"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by blake1 on 2006-12-19
Hi,

For the last few days, I've been trying to sort out the drivers for my ATI Raedeon X300SE, but I go through all the steps (which often corrupt my xorg.conf file, so I have to use my backups ](*,) ) but at the very end, when I type in "fglrxinfo", I get this:
```

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```

How do I change that to this:
```

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON *Version*
OpenGL version string: 1.3.4893 (X4.3.0-8.10.19)

```
or something like that....

Thanks in advance!

---

### Post by renzokuken on 2006-12-19
the "mesa" issue is not uncommon and there is a way to fix it. i cant remember where the thread is but i'll go find it for you

EDIT: heres one [http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283)
heres another [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Ubuntu_6.04_.28Dapper_Drake.29](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Ubuntu_6.04_.28Dapper_Drake.29)

---

### Post by blake1 on 2006-12-19
I have just tried the first one, and now my xorg.conf has been deleted, and my backups dont work, whats happening?

---

### Post by renzokuken on 2006-12-19
wow, that is weird....

Theres obviously some other issue at hand here. 

if i was you, get into the terminal and run

```
sudo dpkg-reconfigure xserver-xorg
```

and just follow the instructions

failing that, it might be worth considering a reinstall and trying again

---

### Post by LookTJ on 2006-12-19
Try configuring xorg again

```
sudo dpkg-reconfigure xserver-xorg
```

That will make your xorg.conf file

Type that in terminal/text based screen :)

EDIT: Aw, you beat me

By the way, to get into terminal mode, hit Ctrl+Alt+F1

---

### Post by TooRight on 2006-12-19
Try this hon...

> 
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig force--initial
sudo aticonfig --overlay-type=Xv
sudo shutdown -r now


During my numerous rescues i've sometimes had to go through the process 2 or three times before it finally worked... the "force" in the that command forces the the system to redo the ati configuration, even though it already reads the xorg.conf file as referring to fglrx... at least I thinkkk that's how it works, lol

If you're wanting to install beryl then you'll have to do another kind of driver install and tinkering after this too, but this is the start :D

---

### Post by blake1 on 2006-12-19
> **TooRight said:**
> Try this hon...



During my numerous rescues i've sometimes had to go through the process 2 or three times before it finally worked... the "force" in the that command forces the the system to redo the ati configuration, even though it already reads the xorg.conf file as referring to fglrx... at least I thinkkk that's how it works, lol

If you're wanting to install beryl then you'll have to do another kind of driver install and tinkering after this too, but this is the start :D

Wow! It works!!! Thanks. Gonna try beryl now :-P

---

### Post by Redlance on 2006-12-19
> **TooRight said:**
> Try this hon...



During my numerous rescues i've sometimes had to go through the process 2 or three times before it finally worked... the "force" in the that command forces the the system to redo the ati configuration, even though it already reads the xorg.conf file as referring to fglrx... at least I thinkkk that's how it works, lol

If you're wanting to install beryl then you'll have to do another kind of driver install and tinkering after this too, but this is the start :D

simply awesome :D many thanks :)

---

### Post by finferflu on 2006-12-19
> **TooRight said:**
> Try this hon...



During my numerous rescues i've sometimes had to go through the process 2 or three times before it finally worked... the "force" in the that command forces the the system to redo the ati configuration, even though it already reads the xorg.conf file as referring to fglrx... at least I thinkkk that's how it works, lol

If you're wanting to install beryl then you'll have to do another kind of driver install and tinkering after this too, but this is the start :D

```
$ sudo apt-get install xorg-driver-fglrxsudo depmod -a
E: Command line option ‘a’ [from -a] is not known.
```

Any idea?:-k

---

### Post by LookTJ on 2006-12-19
You forgot to serperate the commands :)

```
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

---

### Post by finferflu on 2006-12-19
> **Taylor said:**
> You forgot to serperate the commands :)

```
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

You're very right! That's what happen when you just copy and paste without using your brain! ](*,) After this humiliating experience, I think I've learnt something fundamental :D

---

### Post by LookTJ on 2006-12-19
> **finferflu said:**
> ```
$ sudo apt-get install xorg-driver-fglrxsudo depmod -a
E: Command line option ‘a’ [from -a] is not known.
```

Any idea?:-k

> **finferflu said:**
> You're very right! That's what happen when you just copy and paste without using your brain! ](*,) After this humiliating experience, I think I've learnt something fundamental :D

Hey, don't worry, everyone makes mistakes. :D

---

### Post by TooRight on 2006-12-19
lmaoo, sorry, I wasn't paying attention to what I was typing, lol... edited the post now to show the line break properly :oops:

---

### Post by finferflu on 2006-12-19
Yep!
Anyway, it didn't work. X session didn't start, and I had to revert to the previous xorg configuration... That's my second attempt, I've tried with method one on the Ubuntu Wiki, with this one, but I still have to check out method 2, even though I'm not that optimistic...

---

### Post by LookTJ on 2006-12-19
> **finferflu said:**
> Yep!
Anyway, it didn't work. X session didn't start, and I had to revert to the previous xorg configuration... That's my second attempt, I've tried with method one on the Ubuntu Wiki, with this one, but I still have to check out method 2, even though I'm not that optimistic...

None of the methods worked for me.

I have a Radeon Mobility 9000.(My INSPIRON 600m came with it).

I wonder why ATI doesn't support Linux as much as nVidia does.

---

### Post by finferflu on 2006-12-19
> **Taylor said:**
> None of the methods worked for me.

I have a Radeon Mobility 9000.(My INSPIRON 600m came with it).

I wonder why ATI doesn't support Linux as much as nVidia does.

There you go, I've got the same graphic card! So I guess there's even less hope for me now...

---

### Post by LookTJ on 2006-12-19
> **finferflu said:**
> There you go, I've got the same graphic card! So I guess there's even less hope for me now...

But I still use ubuntu and ditched M$.

---

### Post by Ben Sprinkle on 2006-12-19
Did this last night with Debian.
```

sudo apt-get install xserver-xorg
sudo apt-get install xorg

```
After that, issue this command:
```

sudo dpkg-reconfigure xserver-xorg

```
When you get to the configure screen with the drivers, scroll to the top and choose 'ATI'.

---

### Post by LookTJ on 2006-12-19
> **Goat Spirit said:**
> Did this last night with Debian.
```

sudo apt-get install xserver-xorg
sudo apt-get install xorg

```
After that, issue this command:
```

sudo dpkg-reconfigure xserver-xorg

```
When you get to the configure screen with the drivers, scroll to the top and choose 'ATI'.

Lol, I tried everything, my card just doesn't get supported.

---

### Post by Ben Sprinkle on 2006-12-19
Search in the debian repository, search your driver. If you need the repositories I can give you. :)
They are probably there. ;)

---

### Post by finferflu on 2006-12-19
> **Goat Spirit said:**
> Search in the debian repository, search your driver. If you need the repositories I can give you. :)
They are probably there. ;)

How do you search my driver in the repository? The Debian website always confuses me...

---

### Post by LookTJ on 2006-12-19
> **Goat Spirit said:**
> Search in the debian repository, search your driver. If you need the repositories I can give you. :)
They are probably there. ;)

Where can I find this driver supported for Linux

ATI Mobility Radeon 9000

---

### Post by Ben Sprinkle on 2006-12-19
[http://packages.debian.org/unstable/x11/fglrx-driver](http://packages.debian.org/unstable/x11/fglrx-driver)
```

This version of the ATI driver officially supports: 

 * Radeon X300, X550, X600, X700, X800, X850, X1300, X1600, X1800, X1900
 * Radeon 8500, 9000, 9100, 9200, 9500, 9550, 9600, 9700, 9800

```
I sent it to you too Taylor. :)

---

### Post by LookTJ on 2006-12-19
Ok I removed xorg-driver-fglrx

then tried dpkg -i the fglrx deb package and got this output

```
taylor@dapper:~/Desktop$ sudo dpkg -i fglrx-driver_8.28.8-4_i386.deb
(Reading database ... 103841 files and directories currently installed.)
Preparing to replace fglrx-driver 8.28.8-4 (using fglrx-driver_8.28.8-4_i386.deb) ...
Unpacking replacement fglrx-driver ...
dpkg: dependency problems prevent configuration of fglrx-driver:
 fglrx-driver depends on libc6 (>= 2.3.6-6); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
 fglrx-driver depends on libgcc1 (>= 1:4.1.1-12); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 fglrx-driver depends on xserver-xorg (>= 1:7.1.0); however:
  Version of xserver-xorg on system is 7.0.0-0ubuntu45.
dpkg: error processing fglrx-driver (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-driver
taylor@dapper:~/Desktop$

```

---

### Post by Ben Sprinkle on 2006-12-19
You don't have the right dependancies, like I said, manually download them from that page. ;)

---

### Post by Patrick-Ruff on 2006-12-19
I don't get the point of this .  . . it seems that if you guys had simple followed directions in the wiki you wouldn't need a 3 page thread . . . oh well. this is absolute biginners . . . I suggest you /all/ read the terminal tuturial, and a whole bunch of other stuff about linux and try to solve problems your self before you go off posting threads all over the place.  it's a more effecient learning tactic and it will surely help you in the future. with my self, I messed up ubuntu 6 times, and now I know sooo much more about it by fixing it.

---

