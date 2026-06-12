---
title: "Install problems G3 beige desktop"
date: 2007-01-10
forum: Apple PPC Users
---

### Post by pcMoldova on 2007-01-10
Any hints for getting yaboot to work on a vintage PPC (powerMac G3 233mhz).  I have gone through the install instructions several times, and have been able to access the Open Firmware option for New World Macs, but have yet to be able to get into the Yaboot system.  When I type the boot command "boot hd:*x*, yaboot" it simply takes me back into the apple os (OS 8.5).  I have tried multiple variants, and have had little success.  I have tried switching the hd: command to ide:, and have tried every imaginable number to describe the HD and partition in the command.
Is there something that I am missing?
I did copy all of the necessary files into the HD root, and am pretty sure the disk is burned correctly, as it is recognized with the correct label by the OS.
This machine is rater slim on memory, thus I can't use the live CD, and am looking to make this work using the alternate installer.

---

### Post by didg on 2007-01-10
Is it really a new world box?

---

### Post by Brian Smith on 2007-01-10
You should instead follow these instructions:
[https://help.ubuntu.com/community/Installation/OldWorldMacs](https://help.ubuntu.com/community/Installation/OldWorldMacs)

I have successfully installed Xubuntu 6.06 on a beige G3 minitower.
I used those instructions (as well as some other links culled below) and the boot manager that you should use is BootX, not Yaboot.

other informational links concerning the g3 beige:

[http://72.14.209.104/search?q=cache:QG8D-rgRlRMJ:www.gifford.co.uk/~coredump/beigeg3.htm+g3+linux&hl=en&gl=us&ct=clnk&cd=27&client=opera](http://72.14.209.104/search?q=cache:QG8D-rgRlRMJ:www.gifford.co.uk/~coredump/beigeg3.htm+g3+linux&hl=en&gl=us&ct=clnk&cd=27&client=opera)

[http://www.applefritter.com/node/8936](http://www.applefritter.com/node/8936)

and in case it seems too complicated, encourage yourself with the fact that it's less so than this:

[http://gentoo-wiki.com/HOWTO_Install_Gentoo_on_Beige_G3_PPC](http://gentoo-wiki.com/HOWTO_Install_Gentoo_on_Beige_G3_PPC)


It took me a whole weekend, between burning and testing disks, testing the memory, adding an additional hard drive, and finally, installing BootX and Xubuntu.  Everything leading up to running the installation was much harder than everything after the CD was being run.

---

