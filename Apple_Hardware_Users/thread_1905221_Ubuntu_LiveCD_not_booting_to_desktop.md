---
title: "Ubuntu LiveCD not booting to desktop"
date: 2012-01-06
forum: Apple Hardware Users
---

### Post by razaz03 on 2012-01-06
I'm trying to boot into a macbookpro (4,1) using the liveCD to install gdisk and solve my multi-boot MBR issues.

I can't "try ubuntu before installing" with the liveCD as it takes me to   a black screen on my mac, nomodeset seems to load the drivers but it's   welcoming me to Ubuntu 11.10 via command line - it won't boot into a   graphical environment and I'm not sure why.

The final line displayed is Welcome to Ubuntu 11.10 (Linux 3.0.0-12-generic x86_64) with a 
ubuntu@ubuntu:~$ cursor, and the liveCD boots into a GUI fine in another PC.


Specs are a 4th gen MacBookPro, googling shows it a 2.6GHz core 2 Duo   with 4 GB DDR2 SDRAM memory and a GeForce 8600M GT 512MB graphics card.

Please help me to boot into desktop from the liveCD!

---

### Post by 2F4U on 2012-01-06
Do you have log files is /var/log? If yes, look into /var/log/Xorg.0.log and see if you can find any errors.

---

### Post by razaz03 on 2012-01-06
> **2F4U said:**
> Do you have log files is /var/log? If yes, look into /var/log/Xorg.0.log and see if you can find any errors.


Well there are around 250 lines: manually searching and looking for red flags I've listed below what could be relevant:

```
...
load module 'nvidia'
failed to load module 'nvidia'
unloading module nvidia
...
load module 'nouveau'
....
load module 'nv'
failed to load module 'nv'
unloading module 'nv'
...
Nouveau driver for chipset families:
...
**Geforce 8                (G8x)**
....
....
(EE) Screen(s) found, but none have a usable configuration
Fatal server error: No screens found
Please consult the bla bla
...
DdxSigGiveUp: Closing Log
```As I'm stuck with this problem for a while now, I'd really appreciate some prompt advice.

Thanks,

---

### Post by razaz03 on 2012-01-06
Bump.

Please people!

---

### Post by 2F4U on 2012-01-07
Read carefully through this article, which deals with blank screens. There are several things you can try to fix the problem or get additional diagnostic information

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

### Post by razaz03 on 2012-01-08
> **2F4U said:**
> Read carefully through this article, which deals with blank screens. There are several things you can try to fix the problem or get additional diagnostic information

[https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)


```
**Workaround A:  Non-graphical Boot**

 You can disable the graphical bootscreen via: 
set gfxpayload=text 
```By itself does not help at all; in fact it creates a little more instability but (in conjunction with nomodeset) brings me back to the same command-line interface.

```
**Workaround B:  Disable Plymouth**

 If  Plymouth crashes during boot, X *should* still boot up, just that  you'll be left looking at a black screen a lot longer than you'd like.   However, if plymouth dies at just the right time it can leave the system  stuck on a blank vt, and can't recover.  This is because with plymouth  in initrd, it's a bit racy. 
To  check this, in the grub menu edit the kernel line and remove 'splash'  from the end of the line, and boot.  If that solves the issue, you can  remove it from your /boot/grub/menu.lst as a workaround. 
```Removing splash and not replacing it with nomodeset leaves a black screen, hence removing quiet splash and replacing with nomodeset is more successful to get to command-line.

```
**Workaround C:  Disable the VESA framebuffer from grub**

 The  linux kernel uses the framebuffer for doing graphics prior to X  starting up.  For systems that support Kernel Mode Setting (KMS), this  includes using the higher resolutions of the video card.  The kernel  uses a framebuffer driver for this, such as -vesafb.  However this can  misbehave sometimes (e.g. hardware-specific bugs). 
You can disable vesafb in grub by passing it a nonsensical parameter.  E.g.: 
vesafb.nonsense=1 
```Does not seem to affect anything: On it's own the boot process will hang at a black screen/off monitor. In conjunction with nomodeset and/or **Workaround A**, it simply takes me back to the same command-line interface as above.

**```
Analysis Techniques
```**```


...


```

 [SIZE=2]Adding [/SIZE]drm.debug=0x4 and plymouth:debug as boot option parameters leaves the screen hanging whereby the end text seems to state a significant: 



"fb: conflicting fb hw usage nouveaufb vs EFI VGA - removing generic driver
scsi3 : ahci"


before hanging. Note that before this information is listed there was a message stating:


plymouth:debug command not recognised, press any key to continue.



Doing the above but removing "set gfxpayload=keep" as instructed resulted in exactly the same output as above, hanging after the error stated.

No luck with any of the workarounds, the rest of the help page which is relevant (Problem: General Blackscreen issue) contains info on how to gather log files.

I should note that I had xubuntu installed before I formatted and reinstalled ubuntu on the same space as it was very erratic (touchpad issues that ubuntu didn't have), but the GUI *did* load and it continues to be fine with windows/osx lion so it is not a hardware issue.

---

### Post by razaz03 on 2012-01-08
As I've no data on my linux/windows partitions as of yet, would anyone know if Ubuntu 10.04 reinstall would be more stable? 

I would still encounter the partition problems and would need to enter a GUI environment to attempt to fix it, but if I am able to enter to desktop I would be getting somewhere.

---

### Post by razaz03 on 2012-01-08
Guess I'll try a dual-boot 10.04 install then, windows and linux.

Although this comes as a massive inconvenience to me, losing my osx lion, especially as there's a chance it may not even work.

I am a little disappointed but I'll try the installs in a bit if nobody can offer me their advice.

---

