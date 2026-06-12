---
title: "which kernel do I need (pentium m processor)"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by christoph88 on 2008-02-05
I currently use the default kernel (x86) but ubuntu is still a lot slower than when using windows.

So which kernel is best for using with a pentium m processor (no dual processor). Or do I need to recompile it or something like that for improved performance?

Thanks in advance and sorry for the language mistakes, I'm dutch.

---

### Post by emarkd on 2008-02-05
Hmm.. I've got an older Dell laptop with a 1.6 GHz Pentium M and it runs fine with the default Gutsy kernel, just as it has with every default kernel since I first put Ubuntu on it years ago.  Are you sure that's your problem?  How about your video card?  Incorrect video drivers is the more common culprit.

---

### Post by Borbus on 2008-02-05
If there's an i686 kernel you can use that for a bit more speed, not sure if there is one for Ubuntu, though. Or you can just recompile it, yeah.

---

### Post by christoph88 on 2008-02-05
I don't know if the video drivers are my problem, the compiz fusion effects all work.

But how can I somehow test if my video drivers are the problem?

My laptop is 1.7 ghz, how long does it take to load nautilus on your computer? On my laptop it takes 5 seconds or so in comparison with windows that almost loads the explorer instantly. This is not really normal is it?

Ooh and are there any recent guides to recompiling, because on the forum I can only find old stuff or do these guides also still work? Because I don't want to mess up my system.

---

### Post by emarkd on 2008-02-05
Just to see what's going on with your processor, run

```
cat /proc/cpuinfo
```

It'll give you a bit of information about your processor, including the current speed.  If you're computer's not doing much, it'll be lower than 1700 GHz.  Test it again under load by launching an app or something and see if it jumps up to 1700 GHz.

If the 3D stuff works, you've probably got the correct drivers.

---

### Post by christoph88 on 2008-02-05
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.73GHz
stepping        : 8
cpu MHz         : 800.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up est tm2
bogomips        : 1598.01
clflush size    : 64


It doesn't matter how many things I open it still doesn't jump up. 

But just a simple question: is ubuntu is supposed to be quicker than windows or not? 
Starting up en shutting down goes quicker than xp but the loading of the programs just goes slow in comparison. Xp just seems a bit snappier. Maybe this behaviour is normal for ubuntu?

---

### Post by motion parallax on 2008-02-05
I've noticed that with program speed Ubuntu is comparable (and generally a lot quicker) than Vista.  I dual boot both Vista and Ubuntu, and Ubuntu is quicker, but not by much.  

XP is an older operating system, so the program requirements are much lower than the hardware available now.  I've run XP on a very old machine (700MHz 312MB RAM) and it was still pretty snappy.  

Five second program loads are not uncommon on my laptop (see specs below).

Question:  Have you installed a lot of software on your Ubuntu computer?  My computer was a lot quicker before I started installing programs.

---

### Post by christoph88 on 2008-02-05
I don't have that much software on my computer but thanks for the information :) 
Now I know that I just have to search for program's that are faster instead of wasting my time on other stuff. Maybe switching to a faster desktop environment.

Problem solved

---

### Post by emarkd on 2008-02-05
I'm on my laptop now and I can report that my CPU speed changes like it should when it's under load, so I think you've got a problem there.  However, I don't know how to fix it.  Sorry.

There are lots of ways to go lighter-weight.  Of course, Xubuntu is a common choice as it replaces Gnome with the lighter XFCE.  You can go even lighter than that by forgoing a Desktop Environment altogether and just running a window manager.  I've happily used Fluxbox in the past.  If the [Fluxbuntu]("http://fluxbuntu.org") project is far enough along, it may be worth a shot, but I've never tried it.  If you do, be prepared to lose some GUI functionality.  You can still do anything you can with XFCE/Gnome, you're just going to the command line more often.

By the way, opening a Nautilus window on my laptop takes 2 seconds, tops.

---

### Post by rkd on 2008-02-05
I found some advice in this thread that might help:

[http://ubuntuforums.org/showthread.php?t=505325](http://ubuntuforums.org/showthread.php?t=505325)

It says:

Open gconf-editor, go to /apps/gnome-power-manager/cpufreq 
and check the box consider_nice.

This for 7.10 Gutsy.

---

### Post by stchman on 2008-02-05
> **christoph88 said:**
> I currently use the default kernel (x86) but ubuntu is still a lot slower than when using windows.

So which kernel is best for using with a pentium m processor (no dual processor). Or do I need to recompile it or something like that for improved performance?

Thanks in advance and sorry for the language mistakes, I'm dutch.

I have a Celeron M on my laptop (Pentium M offshoot) and it runs Feisty FAR better than it ran Vista.

---

### Post by dcstar on 2008-02-05
> **christoph88 said:**
> I currently use the default kernel (x86) but ubuntu is still a lot slower than when using windows.

So which kernel is best for using with a pentium m processor (no dual processor). Or do I need to recompile it or something like that for improved performance?

Thanks in advance and sorry for the language mistakes, I'm dutch.

The "-default" kernel is for Pentium class processors, the "-i386" one is the old one.

Check other threads on "slow" performance, and do a forum search for "disable ipv6".

---

### Post by Shazaam on 2008-02-05
Two more factors to consider- installed memory amount (and since it's a laptop "shared memory") and hard drive speed. Hard drive speed is the big bottleneck in modern systems.

---

### Post by jordanmthomas on 2008-02-05
> **christoph88 said:**
> 
Starting up en shutting down goes quicker than xp but the loading of the programs just goes slow in comparison. Xp just seems a bit snappier. Maybe this behaviour is normal for ubuntu?

I'll probably get attacked for this :)   but for me at least, Ubuntu has been getting slower and slower with each release.  A fresh Windows XP installation is faster than a fresh Ubuntu installation on my computer.

---

### Post by emarkd on 2008-02-05
> **jordanmthomas said:**
> I'll probably get attacked for this :)   but for me at least, Ubuntu has been getting slower and slower with each release.  A fresh Windows XP installation is faster than a fresh Ubuntu installation on my computer.

I'm not sure about the XP bit, but Ubuntu has slowed some.  I think most of that is caused by their choices in default enabled software.  For instance, trackerd is a system hog and useless to the way that I use my computers.  Sure, disabling it is easy if you know that it's causing issues, but new users don't know that.  There are other examples; I just reached for that one.

---

### Post by jordanmthomas on 2008-02-05
> **emarkd said:**
> I'm not sure about the XP bit, but Ubuntu has slowed some.  I think most of that is caused by their choices in default enabled software.  For instance, trackerd is a system hog and useless to the way that I use my computers.  Sure, disabling it is easy if you know that it's causing issues, but new users don't know that.  There are other examples; I just reached for that one.

Yep, this is exactly the kind of thing I'm talking about.  It's one of the many reasons I don't use Ubuntu (though I suppose I could just build up from the server version).

---

### Post by emarkd on 2008-02-05
Or take out what you don't want.  This is the approach I take, since I find it quicker to mold Ubuntu to work like I want it to  than other distros.  None of them seem to be just right on a fresh install, at least to me.

---

### Post by jordanmthomas on 2008-02-05
> **emarkd said:**
> Or take out what you don't want.  This is the approach I take, since I find it quicker to mold Ubuntu to work like I want it to  than other distros.  None of them seem to be just right on a fresh install, at least to me.

Very true, they all need a little TLC at first.  Like I said, it's not the only reason I don't use it (I love ABS and AUR from arch, which Ubuntu has no *real *equivalent to) but I guess this isn't really the place to discuss it.

My apologies to the OP

---

### Post by emarkd on 2008-02-05
Agreed.  I guess we kinda hijacked this thread.  Sorry.

---

### Post by christoph88 on 2008-02-06
> **rkd said:**
> I found some advice in this thread that might help:

[http://ubuntuforums.org/showthread.php?t=505325](http://ubuntuforums.org/showthread.php?t=505325)

It says:

Open gconf-editor, go to /apps/gnome-power-manager/cpufreq 
and check the box consider_nice.

This for 7.10 Gutsy.

This fixed the problem :D

and thanks everybody for the support had no idea linux community was so helpful :)

---

