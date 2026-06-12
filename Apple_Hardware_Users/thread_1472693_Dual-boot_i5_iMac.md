---
title: "Dual-boot i5 iMac"
date: 2010-05-04
forum: Apple Hardware Users
---

### Post by tmette on 2010-05-04
I did a search of the forums and noticed that others are having trouble installing Ubuntu from the CD because it doesn't display anything.  Most of the replies have referred the posters to this site:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660)

However, I'm not sure what to do at all.  On that site, someone posted the workaround of installing the alternate i386 install.  Then "added "radeon.modeset=0 nomodeset" to the boot options", but I have no idea what this means or how to do it.

Can anyone provide me with extremely simple instructions on how to get Ubuntu to install on a separate partition on my HDD?  I'm pretty tech-savy, but I just don't know anything about Linux or it's distrobutions.  Right now I have Ubuntu running in a Virtual machine, but I would like to dual-boot it as well.

Thanks!

---

### Post by tmette on 2010-05-04
Has anyone resolved the issue of the blank screen on the new iMacs?  I have searched the forums and tried everything like entering the "radeon.modeset=0 nomodeset" during the live CD, but still no luck.

Has anyone SUCCESSFULLY installed Ubuntu 10.04 64bit on a newer iMac with the ATI cards?  If so I would LOVE to hear how you did it so I can get mine working properly.  :)

---

### Post by ne0genius on 2010-05-04
I successfully installed on my 2008 MacPro 3,1 with ATI HD 2600. I used the instructions from the [->bugtracker<-]("https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/542660") 

> gizmo:
I had the same problem on my iMac 27" but found a workaround for me:
* installed Ubuntu 10.04 (32 bit) with the text based installer (alternate-i386 CD)
* select the recovery mode and added "radeon.modeset=0 nomodeset" to the boot options (the line with linux ...)
* the recovery mode detected problems with the graphics and allowed me to use failsafe graphics for one session
* install the proprietary driver from ATI
* normal reboot: success.

i didn't really check if everything works, i think i still need some time to get all the hardware working, but at least i managed to log in and write this post :p

good luck

basically download the alternate install CD and install like you normally would, single boot, dual boot whatever your method is and when you go to boot for the first time in grub, point to the recovery version of the kernel, should be second boot option, hit 'e' and enter 'radeon.modeset=0 nomodeset' at the end of the line starting with linux (note: the linux line spanned two lines so the end was one line below)

boot up w/ (ctrl+x)

when offered boot options select failsafe mode and wait for a couple minutes after getting to the desktop for Ubuntu to offer you the restricted drivers. install them reboot. done ;)

---

### Post by kpholmes on 2010-05-04
im looking to install 10.04 to my 27inch imac as well. ive read your suppose to do a text install just until you can get the cli and get the drivers to support the gpu.

when i do my install ill come back and let u know how it went. also anything you come accross that might be helpful just throw it into this forum for other users who might be in the same boat.

---

### Post by tmette on 2010-05-05
Thank you for responding, I will try this out tonight after work.  One quick question, what do you mean by the "boot up w/ (ctrl+x)" part?  Am I supposed to type that in and then hit Ctrl+x?

---

### Post by wmittz on 2010-05-05
Do to circumstances I used another method. I installed Karmic first, (previously installed but wiped clean) did the updates, and then did the distro update online. A couple of things come to mind, you need to have an ether net connection, to at least get the wireless driver installed, if you use wireless. And don't forget about rEFIt the boot loader that should go in first.  I didn't have luck with the Lucid disk so I doubled back. Load the disk into the machine, turn the machine off, as you power on the machine hold the C key down until it boots to the disk. Another trick I learned while reading here was that you can always hold the alt/option key down, where the computer lists the disk as windows, both work. Have fun.

Warren

---

### Post by tmette on 2010-05-05
Ok, I got the drivers installed and everything on my iMac, so far there are a few problems.


My sound isn't working right now either, but I plan on searching through some posts for the solution to that problem.  I believe I saw a few posts on that earlier when roaming the forums.


Thanks for the help!!

**EDIT:**  Doing updates fixed the wireless and graphic problem.  Only problems now are no sound and the color depth.

---

