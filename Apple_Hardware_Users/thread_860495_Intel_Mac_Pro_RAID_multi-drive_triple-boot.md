---
title: "Intel Mac Pro RAID multi-drive triple-boot"
date: 2008-07-15
forum: Apple Hardware Users
---

### Post by domino82 on 2008-07-15
Hello all,

I'm trying to create a triple-boot on my Intel Mac Pro with the following properties:

1) I'm running a software RAID in Mac OS X (striped) with two 500GB internal HDDs.

2) I want to install Ubuntu x64 and Windows Vista x64 on another physical disk. 

In other words, I have three physical drives. Physical drives 1 and 2 form my RAID with a single OS X partition. Physical drive 3 is 69.2GB and currently blank. I want to create two equally-sized partitions on Physical drive 3, one for Windows Vista x64 and one for Ubuntu.

Any help you can provide would be invaluable. I've tried following some of the other triple-boot guides out there, but I run into trouble with rEFIt (never get the boot menu). I'm guessing it's a RAID issue.

I did have OS X and Vista x64 working with Boot Camp (somewhat), but also ran into issues when I couldn't boot to OS X by default. It would get stuck booting into Vista by default, and the only way I could get back into OS X was by using the option-menu.

Thanks

---

### Post by cyberdork33 on 2008-07-15
I guess Ubuntu doesn't show in the Option-menu either?

Have you tried reinstalling GRUB? There is a bug in the hardy installer that wipes the MBR of the hard drive you install on (in Macs).

---

### Post by domino82 on 2008-07-15
Thanks for your reply. No I guess I didn't explain-- I haven't actually gotten to the point of installing Ubuntu because I was under the impression that you needed to install rEFit first.  I've also been having a problem where I can't get boot camp to boot OSX by default. I get a gray screen even when pressing option about 2/3 of the time and occasionally get the bootcamp loader and can get into OSX. Wanting to start over from scratch.

---

### Post by cyberdork33 on 2008-07-16
You will probably have even more oddities since you are using software RAID. IDK about your current issue with bootup. It may have to do with the Software RAID as well.

---

