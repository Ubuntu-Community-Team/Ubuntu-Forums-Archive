---
title: "[SOLVED] Need to reinstall Windows after Ubuntu--Will this work&amp;quot;=?"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by ebeckhusen on 2007-11-11
Situation:  I installed Ubuntu, but now I find there are a couple of things I can't do in Ubuntu.  So I would like to reinstall windows.  I only have an OEM disk for Windows.  I do not want to have to reinstall Ubuntu if it can be avoided.

So, if I do the following will it work?

1. Use GParted to create a Fat32 partition
2. Use the OEM disk to install Windows on the Fat partition (will it even let me do this, or will it take over the whole drive?)
3. Fix Grub so that it recognizes both OSes.

If you see anything problematic with this, or have a better solution, please let me know.

Thanks:)

---

### Post by magicman5421 on 2007-11-11
Which version of windows are you using? Vista or xp? because i know that vista doesn't make it too hard to install it on a partition.

---

### Post by bigken on 2007-11-11
what is it that you cant do in Ubuntu but can in Windows ? the reason for asking someone might have an alternative instead of installing windows plus you could install and use vmware and run windows

---

### Post by ebeckhusen on 2007-11-11
> **magicman5421 said:**
> Which version of windows are you using? Vista or xp? because i know that vista doesn't make it too hard to install it on a partition.

The OEM disk has XP.  It's the "Recovery Disk" that came with my computer.

---

### Post by bigken on 2007-11-11
usually recovery discs wipe the whole drive

---

### Post by ebeckhusen on 2007-11-11
> **bigken said:**
> what is it that you cant do in Ubuntu but can in Windows ? the reason for asking someone might have an alternative instead of installing windows plus you could install and use vmware and run windows

I need to run Rhapsody To Go, a program for the HomeScan program (I think it's call the HomeScan Transmitter), and a program I use to strip DRM from the Rhapsody files to I can use them on my XM portable player.

Does VMWare need you to have access to your Windows disks?  Because the disk I have is a Recovery Disk that came with my computer, not just a Windows disk, so I don't think there's any way to just access the Windows files.

---

### Post by bigken on 2007-11-11
ye vmware is no good you need a windows install disc a recovery disc   
will wipe the whole drive have tried wine to run your windows aplications

---

### Post by bigken on 2007-11-11
[http://digitalmusictogo.blogspot.com/2006/12/rhapsody-for-linux.html](http://digitalmusictogo.blogspot.com/2006/12/rhapsody-for-linux.html)

found this using google

---

### Post by ebeckhusen on 2007-11-11
> **bigken said:**
> [http://digitalmusictogo.blogspot.com/2006/12/rhapsody-for-linux.html](http://digitalmusictogo.blogspot.com/2006/12/rhapsody-for-linux.html)

found this using google

Thanks, but I looked at that already, and it doesn't allow downloading.  I use Rhapsody To Go to download music to my XM portable player.

---

### Post by ebeckhusen on 2007-11-11
> **bigken said:**
> ye vmware is no good you need a windows install disc a recovery disc   
will wipe the whole drive have tried wine to run your windows aplications

Okay, thanks.  Looks like I will have to wipe everything, install Windows, then reinstall Ubuntu.
Was really hoping that I wouldn't have to, because it took me forever to get some stuff working the way I want in Ubuntu, and I have no idea how I did it!

---

### Post by bigken on 2007-11-11
have you tried running rapsody in wine ?

---

### Post by magicman5421 on 2007-11-11
Or, if you are willing to fork over some cash, you could consider buying crossover. Commercial version of wine, great support.

---

### Post by meierfra on 2007-11-11
My  recovery disk lets me install windows Xp to any partition I want to.

---

### Post by ebeckhusen on 2007-11-11
> **bigken said:**
> have you tried running rapsody in wine ?

Yeah, tried that, but it didn't work.  And from what I read, it won't work.

---

### Post by ebeckhusen on 2007-11-11
> **magicman5421 said:**
> Or, if you are willing to fork over some cash, you could consider buying crossover. Commercial version of wine, great support.

Yeah, looked at that, but can't afford to do it right now.  Will keep in mind for the future, though.

---

### Post by inversekinetix on 2007-11-11
Cant you back up your whole ubuntu installation then copy it to another location and use wingrub to load it?

---

### Post by ebeckhusen on 2007-11-11
Thanks to you all.  I did end up just reinstalling Windows and then reinstalling Ubuntu.  Not everything is back to the way I want it, but it's getting there:).  And Ubuntu is definitely easier to install than Windows (I still haven't gone through the hassle of downloading all the updates and getting my hardware set up):tongue:

---

