---
title: "Vista &amp; Ubuntu dual boot help required"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by maxim1 on 2007-04-06
Hello to eery one one these forums 

I need  advice and help, I am trying to install Ubuntu on a laptop which has pre installled vista.

I read the forums and all the support documentation as I am completelly new to linux. I decided that all I need to was pop the down loaded CD of Ubuntu into the drive and follow the on screen directions.

All went as planned Ubuntu loaded fine, I wanted to test that the dual boot would work ok, this is were the problems started.

Vista was in the options to boot but I kept getting a grub error 15 at this stage I started to panic and reboot and got the same thing. I decided to roll back and load my vista recovery disk as this is a brand new machine so nothing will be lost. After the rebuild to my surprise the grub loader started up and gave me error code 22.

After some research I managed to fix the boot thingign and get vista loading 

I have a 160gb drive which is partioned into two, I choose the 3rd option in Ubuntu install which was I think to install to the 2nd partion. Is this correct should i have chosen a different option.

Is there a simple step by step installion procedure some were ?

---

### Post by Doug11 on 2007-04-06
> **maxim1 said:**
> Hello to eery one one these forums 

I need  advice and help, I am trying to install Ubuntu on a laptop which has pre installled vista.

I read the forums and all the support documentation as I am completelly new to linux. I decided that all I need to was pop the down loaded CD of Ubuntu into the drive and follow the on screen directions.

All went as planned Ubuntu loaded fine, I wanted to test that the dual boot would work ok, this is were the problems started.

Vista was in the options to boot but I kept getting a grub error 15 at this stage I started to panic and reboot and got the same thing. I decided to roll back and load my vista recovery disk as this is a brand new machine so nothing will be lost. After the rebuild to my surprise the grub loader started up and gave me error code 22.

After some research I managed to fix the boot thingign and get vista loading 

I have a 160gb drive which is partioned into two, I choose the 3rd option in Ubuntu install which was I think to install to the 2nd partion. Is this correct should i have chosen a different option.

Is there a simple step by step installion procedure some were ?

So what exactly is happening now? Does it just load straight to windows?

---

### Post by maxim1 on 2007-04-06
Yes it boots stright into vista

---

### Post by Doug11 on 2007-04-06
you need to reinstall grub,,use the first part of this easy howto

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Virgo53 on 2007-04-06
If you can load Vista and get online you might want to download the GParted-Live CD

from [http://gparted.sf.net](http://gparted.sf.net) (I just downloaded version 0.3.4-5.iso to resize my Ubuntu 

partition)

Then you can create a ext3 partition for Ubuntu along with a Linux-swap partition from your Vista

partition for Ubuntu. After you install to your new partition,. Grub should list both operating systems 

at bootup. Good luck!

---

### Post by TheMono on 2007-04-06
Try this:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

Except, instead of the first stage, the installing of Vista, use the Gparted live CD (see above) to shrink the Vista partition.

---

### Post by maxim1 on 2007-04-09
Thanks a lot guys, got it sorted. All i need to do is tidy up the GRUB boot file. I seem to have several options of vista and Ubuntu.

---

