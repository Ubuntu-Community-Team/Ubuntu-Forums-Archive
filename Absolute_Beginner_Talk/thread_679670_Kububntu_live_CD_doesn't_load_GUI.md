---
title: "Kububntu live CD doesn't load GUI"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by yonni on 2008-01-27
Right, I've just decided to try linux, and after deliberation decided on Kubuntu (Gutsy Gibbon). I'm booting off the live CD (burned with [http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm) V3) on a Samsung R20 laptop 1.8GHzIntelCoreDuo CPU, 1GB RAM, ATIRadeonExpress1250m, WinVistaHomePrem, with 2 identical HD partitions (although I'm not trying to install just yet).

Upon seeing the Kubuntu start screen, I select "Start or install Kubuntu", a loading bar follows. What's odd, is that the loading bar will just stop (and the CD Drive will stop spinning) unless I provide some input every so often (hitting a key, touching the mousepad, etc) whereby it'll carry on doing what it was doing before. Following this, a load of white text starts appearing on screen about loading or whatnot (I wasn't really paying attention at this point), and eventually ends on a command prompt screen which reads (in its entirety):
```
[   364.773920] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   365.278413] PCI: Cannot allocate resource region 7 of bridge 0000:00:05.0
[   365.278460] PCI: Cannot allocate resource region 8 of bridge 0000:00:05.0
Loading, please wait...
Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the 
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ <flashing cursor>
```

From this point, the only way to shut the computer down is by holding the power button, as "sudo shutdown now" just returns more error messages :(.

Searching google for this issue, found no issue quite like this, and searching for installing linux on the Samsung R20 just gave a page saying how easy and painless the process was supposed to be :confused: 


Please help if you can, this is exceptionally annoying. And don't suggest anything that involves internet access, as  I haven't set up the wireless (due to lack of GUI) and therefore it is not connected

---

### Post by ureckifix on 2008-01-27
try this it worked for me.
boot the live CD.
Find and mount the HD .
now use the install icon.
it may take some time but should work.

Let me know

---

### Post by Trebaruna on 2008-01-27
It's an obvious one, but I guess it should be asked:
did you have Kubuntu check the CD for defects?

---

### Post by yonni on 2008-01-27
> try this it worked for me.
boot the live CD.
Find and mount the HD .
now use the install icon.
it may take some time but should work.

Let me know

To remind you, I am an absolute beginner with linux. Even so, this sounds like something you do when you've booted into KDE (I haven't got that far yet). Or if not, a complex sequence of commands that I don't know.


> It's an obvious one, but I guess it should be asked:
did you have Kubuntu check the CD for defects?

Actually no, I should really have done so shouldn't I?

am doing that now...

---

### Post by yonni on 2008-01-27
Same result after checking disc for defects

---

### Post by ureckifix on 2008-01-27
Does UBUNTU live cd run
check the site for computable hardware

---

### Post by yonni on 2008-01-27
It seems that the Samsung R20 hardware is not very Ubuntu freindly at all.

Many people have found many issues, most of them saying that it works fine with an older kernel e.t.c.


So I've given up on (k)ubuntu for the laptop, and and trying openSUSE KDE instead, as searching their support I haven't found anything significant complaining about the Samsung R20. I suppose I'll find it it works in about and hour's time when it has finished downloading.

---

