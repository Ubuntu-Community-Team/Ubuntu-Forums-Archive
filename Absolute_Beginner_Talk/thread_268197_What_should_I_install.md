---
title: "What should I install?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by Zargoon on 2006-09-29
I'm two days new to kubutu and I'm pretty impressed.  It's twice as fast and stable as SuSE was.  However, the packages that I need to install seem to vary a little from SuSE.  When ever I try compile things I get some stuff about not being able to find C and C++ compilers.  I tried to install various C++ packages but I haven't made any headway.  Also, when I try to install the NVIDIA graphics driver it says it can't find the kernel-sources package even though I knwo I installed it.

Thanks,
Zargoon

---

### Post by nthdegree on 2006-09-29
Open a terminal:
sudo apt-get install build-essential


Problem solved.

---

### Post by morphodone on 2006-09-29
To compile - you can install the package 'build-essential'.

You can also install the nvidia drivers with synaptic.
No need to use the drivers from nvidia website.  If you
wish to, all you need are the kernel-headers I believe.

---

### Post by skymt on 2006-09-29
The kernel-sources package actually installs a .tar.bz archive of the sources. You'll need to unpack it to actually get to the sources.

But, you don't need to. Just follow [this howto](https://help.ubuntu.com/community/BinaryDriverHowto) to get the drivers up and running.

---

### Post by Zargoon on 2006-09-30
OK I followed the howto and I think I did something wrong.  Now my X server won't start.  I tried to boot it up in failsafe and removed any changes I made to my xorg.conf but It didn't do anything.  In fact, when I boot up in the normal mode it gets to the kubuntu splash screen and then just hangs there.  I tried booting into the amd-generic-kernel thingy but it did the exact same thing.  What sould I do?

---

### Post by morphodone on 2006-09-30
When you boot and xserver fails it should send you to a login prompt
at the command line interface.

Login there and fix your xorg.conf file as so...

```
sudo nano /etc/X11/xorg.conf
```

Look for this section...

```
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

```

Change 'nvidia' to 'vesa'.

At this point you can try to restart xserver.

```
sudo /etc/init.d/gdm restart
```

When you get your graphical interace back we
can work on getting nvidia drivers to work.

---

### Post by Zargoon on 2006-09-30
I tried it but It didn't work:( .  Any other ideas?

---

### Post by Zargoon on 2006-09-30
Any ideas?

---

### Post by easyease on 2006-09-30
the easiest way of installing a lot of very worthwhile apps is by installing automatix from here 
[http://www.getautomatix.com/](http://www.getautomatix.com/)
it covers a lot of proprietory software like google earth and nvidea drivers.
 :-D
just be careful to select the option not to change your source list when you have finished.

---

### Post by morphodone on 2006-09-30
How is it failing?  There is usually a screen that tells you what
error has occured if you tried to start gdm.

---

### Post by easyease on 2006-09-30
oh and as for the x server problem,you could try to reconfigure xserver by....
 sudo dpkg-reconfigure xserver-xorg
and clicking through the options and using the "VESA" driver for a while.

---

### Post by Zargoon on 2006-09-30
It just says it can't find /etc/init.d/gdm restart.

---

### Post by skymt on 2006-09-30
> **Zargoon said:**
> It just says it can't find /etc/init.d/gdm restart.

It can't find /etc/init.d/gdm? That's what's known as a Bad Thing. Try this command:```
dpkg-query -s gdm
```If that tells you that gdm isn't installed:```
sudo aptitude install gdm
```If gdm *is* installed:```
sudo aptitude reinstall gdm
```

---

### Post by Zargoon on 2006-09-30
Thanks for the help but I just gave up becuase I needed my system back and reinstalled.  I had my /home partition so I was fine.

---

### Post by morphodone on 2006-10-01
> **Zargoon said:**
> Thanks for the help but I just gave up becuase I needed my system back and reinstalled.  I had my /home partition so I was fine.

Yep, sometimes that's the fastest way...

---

