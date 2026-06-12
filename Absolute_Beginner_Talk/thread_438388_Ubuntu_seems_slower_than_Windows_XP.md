---
title: "Ubuntu seems slower than Windows XP"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by quaaack on 2007-05-09
Hi there, I've just gotten Kubuntu installed and running, however, everything seems very slow.  For example, opening/switching a tab in firefox takes ~3 seconds while in Windows it's faster.  Also, menus and notification boxes 'draw' much slower.  Also, when I've got a window open, and I drag it around the screen, I can see trail marks that it leaves behind (they dissapear soon after).  

I was under the impression that Ubuntu was faster so I'm hoping that there's something wrong with my drivers or hardware.

I've got a Intel P4 2.2 ghz cpu
an old Nvidia GeForce4 MX 420
two 512 sticks of ram

Thanks

---

### Post by Bachstelze on 2007-05-09
```
cat /etc/X11/xorg.conf | grep Driver
```

What does that output ?

---

### Post by orb9220 on 2007-05-09
Need to install the video driver for your card or chipset.

Same thing in winXP before installing video driver winXP Slow.

---

### Post by GrueTamer on 2007-05-09
Kubuntu is also a more bloated version of Ubuntu, I myself don't like KDE because of it's resource-hungry nature compared to Gnome and XFCE and stuff.  Try turning down some of the KDE effects (it's in a setup thing, I don't remember offhand what it's called, but it's pretty easy to find), that should help with the speed after your video drivers are updated.  But, of course, if you'd rather have looks over speed, then don't do that :)

---

### Post by Bachstelze on 2007-05-09
> **GrueTamer said:**
> Kubuntu is also a more bloated version of Ubuntu, I myself don't like KDE because of it's resource-hungry nature compared to Gnome and XFCE and stuff.

You could start a war with such assertions... For your information, KDE is no more resource-hungry than Gnome !

---

### Post by daveblack on 2007-05-09
Well, Maybe you could help me. I'm using ubuntu with beryl, and opening terminal takes at least 3 seconds. Nautilus is longer to open and Opera even longer than Nautilus. Is this normal? I've installed my Nvidia driver, though it didn't seem to help much. Is there a program for linux benchmarking?

---

### Post by Duck2006 on 2007-05-09
> firefox takes ~3 seconds while in Windows it's faster

[http://ubuntuforums.org/showthread.php?t=423905&highlight=firefox](http://ubuntuforums.org/showthread.php?t=423905&highlight=firefox)

---

### Post by misfitpierce on 2007-05-09
Ubuntu is definatly faster. Something hardware related is wrong or not updated. Dont get wrong impression that KDE or Gnome is slower as well they run about same on ram its just preference of layout and compatibility. 

Try downloading latest nvidia drivers and installing and giving a fresh reboot....

---

### Post by GrueTamer on 2007-05-09
> **HymnToLife said:**
> You could start a war with such assertions... For your information, KDE is no more resource-hungry than Gnome !While KDE has been much slower for me than gnome, I respect that there are KDE users and lovers out there.  I don't want to start a war, I just carefully observed system behavior and reached that conclusion.

---

### Post by izizzle on 2007-05-09
I agree with GrueTamer. I ran Linspire (uses KDE) on the same system I am running ubuntu on and Linspire took about 5 minutes to load the SYSTEM CONFIGURATION window. In ubuntu, it took abut 5 seconds!

---

### Post by yardus on 2007-05-11
I have also the impression that Ubuntu is significantlyt slower than WinXP on my Toshiba Tecra M5 with Centrino Duo. First I noticed that when starting an identical Java application on colleagues win xp (on older piece of HW) was almost 50% faster. But I thought it could be JVM problem.
Then I downloaded GeekBenchmark and did benchmarking on WinXP in dual boot on my machine and on Ubuntu FeistyFawn with generic kernel. On Ubuntu I manually set the frequency of both cores to 2.16GHz (max) and on winxp I let the speedstep to its best - this should favour Ubuntu. However, the results are pretty depressing - 
WinXP overall score: 198
Ubuntu overall score: 84

I don't know what to think about this. I have pretty clean installation, no weird stuff, experimental modules etc. I would appreciate if anyone having dual boot of WinXP and Ubuntu could do benchmarking with geekbenchmark (so we have a common base for comparison). This slowness really hurts my performance since I need all CPU power I can get for getting my job done.

Regards

JB

---

### Post by yardus on 2007-05-11
just to clarify - on ubuntu I run the benchmark in plain console mode -no KDE or Gnome

---

### Post by Timo425 on 2007-05-11
I don't like XP mainly because it is slow. My Ubuntu is way faster.

---

