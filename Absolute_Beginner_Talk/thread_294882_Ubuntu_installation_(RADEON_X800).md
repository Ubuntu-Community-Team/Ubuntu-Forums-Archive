---
title: "Ubuntu installation (RADEON X800)"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by rosvit on 2006-11-07
good afternoon, 
Is it possible to install edgy eft on pc with grafic card ati radeon x800xl? and if yes, how? because everytime when i begin installation, blue screen with warning that xserver cannot be started is shown... I am confused. or 6.10 cannot be installed with  ati card? ](*,)

---

### Post by taurus on 2006-11-07
Yes, you can install Edgy with ATI graphic card.  Try using the alternate CD instead of the desktop CD or LiveCD then...

---

### Post by rosvit on 2006-11-07
> **taurus said:**
> Yes, you can install Edgy with ATI graphic card.  Try using the alternate CD instead of the desktop CD or LiveCD then...

and where i can download image of alternate cd?

---

### Post by cborga1985 on 2006-11-07
for a standard pc [http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso](http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/edgy/ubuntu-6.10-alternate-i386.iso)
if you don't have a standard pc go here [http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/edgy/](http://osmirrors.cerias.purdue.edu/pub/ubuntu-releases/edgy/)

---

### Post by taurus on 2006-11-07
> **rosvit said:**
> and where i can download image of alternate cd?

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by cborga1985 on 2006-11-07
> **taurus said:**
> [http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

both of those will work

---

### Post by rosvit on 2006-11-07
thank you all, i will try to install and then i'll write here the result... :cool:

---

### Post by confused57 on 2006-11-07
Maybe this thread will help:

[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

---

### Post by rosvit on 2006-11-07
> **confused57 said:**
> Maybe this thread will help:

[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)

yes, i saw that topic and posted there a question, but still no answers yet. i don't know where i should type that command. :confused:

---

### Post by taurus on 2006-11-07
Type what command?  Do you mean the

```
sudo dpkg-reconfigure xserver-xorg
```
You type that from a terminal or a prompt...

---

### Post by rosvit on 2006-11-07
> **taurus said:**
> Type what command?  Do you mean the

```
sudo dpkg-reconfigure xserver-xorg
```
You type that from a terminal or a prompt...

```
sudo nano /etc/X11/xorg.conf
```

this is written in that topic... but i choose language, screen resolution(tried every)I got a blue screen that xwindow cannot be stared. and then i don't where i should write [I]sudo nano /etc/X11/xorg.conf
[/I]and continue by guide which is written in [that topic]("http://www.ubuntuforums.org/showthread.php?t=190133"). because there is no terminal/prompt...

---

### Post by darrenm on 2006-11-07
To open a terminal open the Applications menu, then Accessories then Terminal.

---

### Post by taurus on 2006-11-07
> **rosvit said:**
> ```
sudo nano /etc/X11/xorg.conf
```

this is written in that topic... but i choose language, screen resolution(tried every)I got a blue screen that xwindow cannot be stared. and then i don't where i should write [I]sudo nano /etc/X11/xorg.conf
[/I]and continue by guide which is written in [that topic]("http://www.ubuntuforums.org/showthread.php?t=190133"). because there is no terminal/prompt...

Okay, are you using the LiveCD or the alternate CD right now?  Or have you installed Ubuntu on your machine but are having problems with X right now?

---

### Post by rosvit on 2006-11-07
> **taurus said:**
> Okay, are you using the LiveCD or the alternate CD right now?  Or have you installed Ubuntu on your machine but are having problems with X right now?

I don't have Ubuntu installed, that's the main problem... I was using (trying to install) desktop version of edgy eft i386, now I'm downloading alternate version, but download is very very slow - 15KB/s (normal ubuntu was downloadning about 900KB/s). So it will take a few hours to download. And because of problems with X installation does not begin.

---

### Post by taurus on 2006-11-07
Make sure you pick the site closest to you, not half way around the world!  That's way, you would get a faster download speed...  Also, make sure you burn it (I assume using Windows) at a slower speed like 4x to be safe.

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)

---

### Post by paulajohnw on 2006-11-14
ANSWER HERE!!!!!

This is a very common problem and guess what I HAVE THE ANSWER!!!!!!!

I pieced this together over the last couple of hours.

1.  At the 1st screen where it gives you all the options for installing, press "F6" (Options)

2.  delete "  splash --" from the boot options

3.  Choose option #1 "Start or Install"

4.  Looks like nothing is happening for a couple of mins.  Probably depends on ur PC

5.  XServer Fails, Skip all the reports and such

6.  You should now get a terminal window.  Type the following...  
  "sudo apt-get install xorg-driver-fglrx" <enter>
  "sudo aticonfig --initial" <enter>
  "sudo aticonfig --overlay-type=Xv" <enter> (notice that is Xv not xv x is caps)

7.  startx
8.  viola

---

### Post by jon419 on 2006-11-14
> **paulajohnw said:**
> ANSWER HERE!!!!!

This is a very common problem and guess what I HAVE THE ANSWER!!!!!!!

I pieced this together over the last couple of hours.

1.  At the 1st screen where it gives you all the options for installing, press "F6" (Options)

2.  delete "  splash --" from the boot options

3.  Choose option #1 "Start or Install"

4.  Looks like nothing is happening for a couple of mins.  Probably depends on ur PC

5.  XServer Fails, Skip all the reports and such

6.  You should now get a terminal window.  Type the following...  
  "sudo apt-get install xorg-driver-fglrx" <enter>
  "sudo aticonfig --initial" <enter>
  "sudo aticonfig --overlay-type=Xv" <enter> (notice that is Xv not xv x is caps)

7.  startx
8.  viola

I remember when I was installing Ubuntu 6.06 for the first time and I had problems with my ATI card.  I had to change the drivers from "ati" to "vesa" for the install.

Now I am trying to do a fresh install of Ubuntu 6.10 and my computer locks up as soon as I pree 1 to install.  The splash screen starts to load and then the progress bar moves a tiny bit and freezes.

I am hoping this is, again, because of a faulty initial video driver.  Hopfully the above steps (disabling the splash screen) help.  I will find out after I get out of work in the morning.  Anyone experience the same thing as me??

---

### Post by sbozcan on 2006-11-25
> **jon419 said:**
> I remember when I was installing Ubuntu 6.06 for the first time and I had problems with my ATI card.  I had to change the drivers from "ati" to "vesa" for the install.

Now I am trying to do a fresh install of Ubuntu 6.10 and my computer locks up as soon as I pree 1 to install.  The splash screen starts to load and then the progress bar moves a tiny bit and freezes.

I am hoping this is, again, because of a faulty initial video driver.  Hopfully the above steps (disabling the splash screen) help.  I will find out after I get out of work in the morning.  Anyone experience the same thing as me??

I had the same problem (I've a x800gto) and paulajohnw's solution worked perfectly well. Thanks a lot dude :-D

---

### Post by galego on 2007-01-09
instead of using the fglrx driver and then running xgl just do this:

follow the above guide of paulajohnw but insert the following line instead of installing the fglrx driver

```
sudo nano /etc/X11/xorg.conf
```

find the first section that discribes your ATI card and in the driver discription change it to "radeon" instead of "ati"

then press "ctrl - x"
 say yes and then pres enter

then for beryl install just follow the how-to at the beryl wiki for ubuntu and AIGLX.

---

