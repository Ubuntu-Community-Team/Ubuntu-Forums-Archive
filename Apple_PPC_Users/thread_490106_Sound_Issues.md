---
title: "Sound Issues"
date: 2007-07-02
forum: Apple PPC Users
---

### Post by james_99 on 2007-07-02
Hi,

I have installed Feisty Fawn on my PPC Macintosh and have been having problems with getting sound to work.  It seems to work sometimes and then stop working after a few minutes, or sometimes won't work at all (not even a sound when the login window appears).  Can anyone suggest what I should do to diagnose and fix the problem?

Thanks

---

### Post by ssam on 2007-07-02
what mac is this on?

can you post the output of
```
cat /proc/cpuinfo
```

---

### Post by tcrroadie on 2007-07-02
Or better yet, run this in a terminal to give detailed information about your sound card.  Please post the output you receive from this command string.

```
sudo lshw -C multimedia
```

And also post what machine this soundcard is in.

---

### Post by james_99 on 2007-07-02
the output of ```
cat /proc/cpuinfo
``` is:
```
processor       : 0
cpu             : 7455, altivec supported
clock           : 999.999997MHz
revision        : 0.3 (pvr 8001 0303)
bogomips        : 66.56
timebase        : 33290446
platform        : PowerMac
machine         : PowerMac4,4
motherboard     : PowerMac4,4 MacRISC3 Power Macintosh
detected as     : 80 (eMac)
pmac flags      : 00000010
L2 cache        : 256K unified
pmac-generation : NewWorld

```

When I typed ```
sudo lshw -C multimedia
``` it doesn't give a final output, it prints somethings PCI, IDE, SCSI, Framebuffer while it is running and then nothing.

---

### Post by stmiller on 2007-07-02
James try doing this:

sudo nano /etc/modules

and add this to the bottom of the list:

snd-powermac

then hit Cntrl+X, Y, and enter to save. Reboot and sound should work.

Otherwise, you might have the bug that some G4 owners are having:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/87652/)

---

### Post by james_99 on 2007-07-06
The line snd-powermac was already in /etc/modules, so I think it is just the bug you referred to.
Thanks anyway for your help.

---

