---
title: "iMac G5 PPC Lucid 10.04 - Crash on Startup"
date: 2010-05-31
forum: Apple Hardware Users
---

### Post by shanmakor on 2010-05-31
I have an iMac 20" G5 running Ubuntu 9.10 without a problem.  I upgraded to 10.04 and cannot boot.

The problem seems with be with Xorg.conf addressing the graphics card, but I am not sure.  The system boots, shows various lines of code as it loads, and then displays either alternating black and white lines or an array of multicolor pixels.  It looks like Ubuntu is trying to place my display into the wrong resolution.  Sometimes, the mouse will appear center screen at normal resolution.  I can move the mouse for a second and then it freezes.

I have unsuccessfully tried to boot with a variety of commands including:

Linux video=ofonly nosplash
Linux video=radeon:1680x1050
Linux video=radeon
Linux simple

I have installed from a CD and from an update download - both times the same issue occurs.

I'm out of ideas and none of the similar threads have not proven helpful.  Any ideas how to get 10.04 booting?  Thanks in advance!

---

### Post by linuxopjemac on 2010-05-31
how does your xorg.conf file (which worked in Karmic) look like?

can you post it here?

---

### Post by shanmakor on 2010-05-31
> **linuxopjemac said:**
> how does your xorg.conf file (which worked in Karmic) look like?

can you post it here?

Just got 10.04 up and running.  There is something wrong with the Alternate version of PPC 10.04.  Neither the update or clean install worked properly.  I downloaded the Desktop version and it's working fine so far.  

For all you other iMac owners getting errors, screen noise, and other problems on startup, stay away from the Alternate install!

---

### Post by Library Eye on 2010-05-31
I installed yesterday off desktop disc actually & am having similar problems actually on my iMc G5 20:  It booted fine (despite FATAL windfarm error during startup), ran ok (though fans ran unnecessarily compared to under Leopard). I installed updates when prompted & rebooted and it ran (same error upon start, but ran ok). Then after I shudown and started ,  it's a pixel mess. can't glimpse a hint of anything visual- lines everywhere that even persisted upon booting into OS X and I thought maybe it had really damaged my screen (was ok after a while under OS X) Sound was obviously working though.

---

### Post by sha.goyjo on 2010-05-31
I've been fooling around with shifting the radeon driver out of kernelspace and back into userland. Can you try booting with

```

radeon.modeset=0

```

It's what I use to get DRI working on my ibook g4. I'd also recommend taking linuxopjemac's advice and taking a good square look at your xorg.conf. I always check over at the arch linux wiki, as they (arch users) tend to use very little automation (and thus have very verbose xorg.conf's).

Good luck and happy hunting.

---

### Post by linuxopjemac on 2010-06-01
Sha.goyjo is right about Radeon. It doesn't work well together with kernel modeset. You can disable KMS by his line of code.

---

### Post by canadiandude007 on 2010-08-15
I've had the same issues ... worked fine after installed 10.4 and then with the update ... video problems galore!

I could basically see the Ubuntu 10.4 words being displayed, then looked like a supernova went off and shades of white and black spread out over my screen.  Nothing.

I tried Linux video=radeon.modeset=0 

but that didn't help.

Any other thoughts?

I guess will try to boot off the CD and then look for my Xorg.conf file.

---

### Post by linuxopjemac on 2010-08-15
I have an Xorg.conf file for an iMac G5/1.8 17 inch. You can try that. If you have a different iMac, we might need to adjust the file:

[http://mac.linux.be/content/g5-imac-18-ghz-17-inch-xorgconf](http://mac.linux.be/content/g5-imac-18-ghz-17-inch-xorgconf)

to get the file:
```
wget http://mac.linux.be/files/xorg/g5_2.txt
```

If your Mac is different, please give me the link in everymac.com

---

