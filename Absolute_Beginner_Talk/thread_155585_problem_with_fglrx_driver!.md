---
title: "problem with fglrx driver!"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by SamSlater on 2006-04-05
Having installed Ubuntu and having to use the 'vesa' drivers just to get into the desktop I'm now unable to again after installing the fglrx driver.

I have a amd64 system with the ati radeon x800 gfx card and followed the advise on [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

I used these commands:

> Ubuntu provided drivers

Install the kernel drivers. These drivers should be installed by default, but it's better to make sure they are installed. You need the package linux-$arch, where you replace $arch by the CPU architecture for the machine. This is 386 for Intel Pentium, 686 for Celeron, Pentium Pro, Pentium II, Pentium III, and Pentium 4 without Hyper-Threading. 686-smp for Pentium 4 with Hyper-Threading, or k7 or k7-smp for AMD athlon. On 64-bit systems, this may be amd64-generic, amd64-k8, amd64-k8-smp, or amd64-xeon.

sudo apt-get install linux-686 (amd64-generic for me)

sudo apt-get install xorg-driver-fglrx

echo fglrx | sudo tee -a /etc/modules

sudo dpkg-reconfigure xserver-xorg

Restart your computer

I'm choosing the fglrx driver during the reconfigure but get this error:

> Fatal server error:
Module load failure

Please consult the The X.Org Foundation support at [http://wiki.X.Org](http://wiki.X.Org) for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

X10 fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.

I did everything exactly as it says so whats wrong?

Thanks in advance....

SamSlater

---

### Post by dasdas on 2006-04-14
I have the same problem...

---

### Post by pertheusual on 2006-06-02
I realize it was a couple months ago, but did either of you have any luck? I have the same problem with my 9800 Pro.

Thanks

---

