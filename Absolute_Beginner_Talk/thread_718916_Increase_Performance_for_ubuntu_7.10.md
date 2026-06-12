---
title: "Increase Performance for ubuntu 7.10"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by bluescreenofdeath on 2008-03-08
I would like to know where some web sites are that explain (step by step) how to improve performance and customizing ubuntu 7.10?

 Like how xp has [http://www.tweakxp.com/](http://www.tweakxp.com/).

---

### Post by kwacka on 2008-03-08
OK I'll bite.   ;)

For eye-candy see [http://www.gnome-look.org/](http://www.gnome-look.org/)   or   [http://art.gnome.org/](http://art.gnome.org/)  or [http://gnome-themes.org/](http://gnome-themes.org/)

Click on System --> Preferences --> Advanced Window Effects (make sure you've got Compiz insatlled).

What aspects of performance do you want to improve?

BTW, I can't find an Ubuntu equivalent of [http://www.annoyances.org](http://www.annoyances.org)

---

### Post by bluescreenofdeath on 2008-03-08
> **kwacka said:**
> OK I'll bite.   ;)

For eye-candy see [http://www.gnome-look.org/](http://www.gnome-look.org/)   or   [http://art.gnome.org/](http://art.gnome.org/)  or [http://gnome-themes.org/](http://gnome-themes.org/)

Click on System --> Preferences --> Advanced Window Effects (make sure you've got Compiz insatlled).

What aspects of performance do you want to improve?

BTW, I can't find an Ubuntu equivalent of [http://www.annoyances.org](http://www.annoyances.org)


I would like it to load faster, open programs faster. Get rid of services that are not needed.

I would like to know pretty much everything about making it go faster. 

Just overall it seems slower then windows xp.

---

### Post by Giradman on 2008-03-08
Might want to provide some information on your system (e.g. brand/model computer, CPU, and RAM)?  I'm running Ubuntu 7.10 on an older IBM laptop which came w/ 256 MB RAM - had to use the 'alternate' CD for installation (not doing dual booting w/ XP) - upgrading to 512 MB improve the speed noticeably.  :)

---

### Post by Tatty on 2008-03-08
There have been several threads on this on the forums.  I cant find any right now but try searching and seeing what pops up.

Is there anything in particular that seems to be causing you problems? perhaps we could offer specific help in the absense of any guide...

---

### Post by bluescreenofdeath on 2008-03-08
My motherboard is GA-8ig1000 pro-g

Intel p4 3ghz 

2gb 3200ddr ram


 I'm running it with xp on the same drive.

 112gb drive I split it in half.

 It seems slow when loading the desktop and staring programs.

---

### Post by Tatty on 2008-03-08
try installing bootchart:

```
sudo apt-get install bootchart
```

Reboot your machine, when it loads it will analise how long it is taking to complete each part of the boot...  it will save a bootchart at /var/log/bootchart

Please post this so we can see if there are any specific problems during boot.

---

### Post by bluescreenofdeath on 2008-03-08
> **Tatty said:**
> try installing bootchart:

```
sudo apt-get install bootchart
```

Reboot your machine, when it loads it will analise how long it is taking to complete each part of the boot...  it will save a bootchart at /var/log/bootchart

Please post this so we can see if there are any specific problems during boot.

Here it is.

---

### Post by Nythain on 2008-03-08
k. mandla wrote an AMAZING guide/tut/webpage that covers just about every aspect of tweaking ubuntu imaginable... i just download and read it a couple hours ago, and now i cant remember teh url... aha, i found it
[http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/](http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/)
you have to download the guide as it is rather large, remember, i said it covers EVERYTHING (not quite, but close enough)

read through that, follow the advice, play around, and soon your system will be flyin

Thanks K. Mandla for writing such an amazing guide :)

---

### Post by radioaktivstorm on 2008-03-08
A possible (and my favorite)  solution to this issue: install Xfce. it is a lot lighter than GNOME and may be just what you were looking for.  :)

```
sudo aptitude update && sudo aptitude install xubuntu-desktop
``` should do it.

If youre interested, it looks and feels a lot like gnome on a superficial level. but there are some differences, and it requires fewer resources.

good luck!
~radioaktivstorm

---

### Post by oldos2er on 2008-03-08
Have you been to [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100) ?

 Also [http://linux.wordpress.com/2007/04/25/ubuntu-performance-guides/](http://linux.wordpress.com/2007/04/25/ubuntu-performance-guides/)

---

### Post by jken146 on 2008-03-08
An educative way of getting a slick-running linux distro is to install everything yourself from scratch.  Arch is exactly that, but you can get a similar effect for a lot less hassle with a Ubuntu minimal install -- [www.psychocats.net/ubuntu/minimal](www.psychocats.net/ubuntu/minimal)
This way you'll only install what you need and nothing extra will get in the way.

GNOME is really bloated, so use a lighter WM -- icewm is very simple to set up.

---

### Post by K.Mandla on 2008-03-09
> **Nythain said:**
> Thanks K. Mandla for writing such an amazing guide :)
My pleasure. I'm glad people get something from it. Cheers!

---

### Post by Tatty on 2008-03-09
> **bluescreenofdeath said:**
> Here it is.

My word your comp boots in 25 seconds?  Thats good!  Is it after the login that it slows down slightly?

That has been a fairly common complaint with Gutsy... It is a little sluggish logging in.  But hopefully that should be fixed in Hardy.

---

