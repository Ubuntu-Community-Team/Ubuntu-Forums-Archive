---
title: "Black screen instead of desktop when booting to Ubuntu quantal on rMBP"
date: 2012-10-17
forum: Apple Hardware Users
---

### Post by catus on 2012-10-17
I'm writing this post from Mac OS X. After an update about 2 hours ago, my Ubuntu boots into a black, blank screen, when desktop is expected to display. I can see the logs like starting something, checking battery state before the screen turns black when quiet is off.
I got the same black screen when I tried to run Xorg failsafe mode.

Laptop details:
Memory: 8GB
Intel® Core™ i7-3615QM CPU @ 2.30GHz × 8
Graphics: GeForce GT 650M/PCIe/SSE2 + Intel HD 4000
256GB SSD

Current system:
Ubuntu 12.10 (x64, with proposed update) with Linux 3.5.0-? (should be the newest version in xorg-edgers PPA), nomodeset, gfxmode line removed
Installed nvidia-current.
Booting from EFI
xorg-edgers PPA used.


The upgrade includes nvidia-current, and I suspect the latest NVIDIA driver is causing problems, but I'm not sure.

I tried to startx after login in a terminal, but it only outputs 2 lines and then it seems to be struck there.
I can confirm the system is fine expect display, for the laptop shuts down when I press the power button twice.

I also booted into recovery mode. Yes I get root shell, but when I try to turn on networking from the recovery menu, there is no more output after fsck message. It resumes to normal boot after I pressed ^C. And I don't know how to rmount / as read-write.

Maybe I could get the Xorg log file in the root shell, but how can I put it here? I mean, I don't even have access to the internet in recovery mode.

I can provide more information if needed. Please tell me if I forget about something.

---

### Post by cipherboy_loc on 2012-10-17
Are you running with a wired connection? If you are, you should be able to manually bring up wired Ethernet through the terminal. If that works, you should be able to install the package pastebinit, which after installing you should be able to point it at the Xorg logs in /var/log, and write down the URL to post here. Did you recently install a new kernel? It seems that installing new kernels has started a trend of nvidia not working (probably not configured correctly), which leads to a few systems without graphical interfaces. Can you try booting using an older kernel version?

Thanks,
Cipherboy

---

### Post by catus on 2012-10-17
> **cipherboy_loc said:**
> Are you running with a wired connection? If you are, you should be able to manually bring up wired Ethernet through the terminal. If that works, you should be able to install the package pastebinit, which after installing you should be able to point it at the Xorg logs in /var/log, and write down the URL to post here. Did you recently install a new kernel? It seems that installing new kernels has started a trend of nvidia not working (probably not configured correctly), which leads to a few systems without graphical interfaces. Can you try booting using an older kernel version?

Thanks,
Cipherboy

Thanks for your reply! I installed a new kernel in the past few days, but it worked fine until the  nvidia driver update today. I'll try an older kernel now.

I'm trying to internet access via the wired connection, but I simply don't know how. I tried `service networking start`, but it doesn't help. Maybe should I first re-mount the file system as read-write? Please tell me how to do it by terminal.

---

### Post by catus on 2012-10-17
I just downgraded nvidia-current to 304.51, and the problem was solved.
Now I can confirm 310.14 is causing problems. It is not working with older kernels either.

Thanks again!

---

### Post by peterpan891 on 2013-01-22
I can confirm this problem. I have a MBP retina and Ubuntu 12.10 and tried various nvidia drivers (aincluding download from nvidia-webpage) and the only one working is 304.51 that gets installed via ubuntu-current-updates.
Moreover it only works with a single kernel which is 3.6.0-030600rc6-generic

All other drivers or other kernels give a black screen instead of the greeter. Also failsafeX yields such a black screen. Moreover Crtl-Alt-F1 console is not accessible.
Very scary!

At some point, I'd like to update my kernel!

---

