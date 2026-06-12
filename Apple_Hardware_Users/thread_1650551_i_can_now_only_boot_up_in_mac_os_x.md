---
title: "i can now only boot up in mac os x"
date: 2010-12-21
forum: Apple Hardware Users
---

### Post by stoopkitty on 2010-12-21
about a 9 months ago, my iMac's OS died, and since I had used ubuntu and linux a little bit before, i decided that rather than reinstalling Mac OS X (10.6 Snow Leopard), I would install ubuntu. so I wiped the whole thing out and installed ubuntu (10.04 lucid). recently, i decided that i wanted to start learning about how to make ios apps. since the only way to do this is in Mac OS, i installed mac from my install disk back onto the computer today, splitting my ubuntu partition in half so i would have a place to install it. this pretty much worked, it took a little work, but i eventually got it.

so now, i am writing this in mac os x and i am unable to boot into ubuntu, or even access my ubuntu partition from mac (when i click mount in disk utility, it just thinks about it for a second, and then gives up). when i boot up my computer, it does not give me any options of what OS i would like to boot into, the apple logo just shows up on the screen and it boots into mac os. i think this might have been because when i installed the mac os, it put in its own bootloader (or at least i think that is what it is called) that always boots into mac. Is there anyway to reinstall ubuntu's bootloader or a different one so that i can choose which operating system i want to boot into at startup? or is there something i am missing like some key that i have to hold down at startup to decide? thanks

fyi, i have 4 partitions on my hard disk:
disk0s1, a 1MB partition which i assume is ubuntu's bootloader that it installed when i originally installed it 9 months ago
DISK0S2, a 200GB partition that i gave to ubuntu's filesystem when i split it earlier today
Macintosh HD, ~293GB containing my Mac filesystem
Linux Swap, 6.13GB, i'm not sure what this is but it was added when i originally installed ubuntu
~200MB of free space that gparted automatically put in there when i partitioned today

Thanks!! sorry for the long post

---

### Post by yugnip on 2010-12-21
You can press 'option' at boot to get to grub, then choose your kernel. Alternatively, and the better option, you can install [Refit]("http://refit.sourceforge.net/"). Just follow the instructions on the site.

Still, I don't think you'll be able to boot Ubuntu because Grub is not installed on the Ubuntu partition, but alongside mac's EFI bootloader. This presents a problem of which there is no easy fix. 

Grab Refit and follow the instructions for install. Then pop in the Ubuntu cd and reboot. At boot, choose the Ubuntu cd, not the linux partition. Choose install. Choose advanced and you'll see gparted. Choose the Ubuntu partition. Make certain to check the dropdown for where to install Grub-- very important. Install grub @ / of the Linux partition. Proceed with the install. Eject the disc and reboot.

One caveat here, and this is where the 'no easy fix' comes in: You now have in the Refit menu 3 items, Mac, LinuxHD, Linux on partition. The LinuxHD is where you first installed Grub and will not boot. Not sure of an easy way to get rid of it. However, booting from mac, and booting from Linux partition will work fine.

Hope this helps

---

### Post by stoopkitty on 2010-12-21
Hi, sorry i got some of that, but i don't understand some of it.

so i installed Refit, it comes up when i boot and i booted to the live cd, then i clicked install, and when the installer asked me how i wanted to partition the drive i said advanced, and then it brought me to a window showing me all of my partitions (which i guess could be gparted, although it didn't look a lot like it).

so from there, what do i do? you say to check the dropdown for where to install grub? i don't quite know what that means. also, which partition should i do this on? my sda2(where ubuntu is now)? i want to make sure that i keep all of the data on that partition. i have pictures, music and documents that i put in my linux filesystem that i want to keep. you said to install grub at / of that linux partition which i assume would wipe out everything. also, i don't see anything about grub or installing grub anywhere in the installer, isn't it just for installing ubuntu?

sorry for being so naive, i don't know much about this.

---

### Post by yugnip on 2010-12-21
> **stoopkitty said:**
> you say to check the dropdown for where to install grub? i don't quite know what that means. also, which partition should i do this on? my sda2(where ubuntu is now)? i want to make sure that i keep all of the data on that partition. i have pictures, music and documents that i put in my linux filesystem that i want to keep. you said to install grub at / of that linux partition which i assume would wipe out everything. also, i don't see anything about grub or installing grub anywhere in the installer, isn't it just for installing ubuntu?

Sorry, I assumed incorrectly this was a fresh installation, with no data to lose. Stop the install. You'll need to backup your data first.

---

### Post by stoopkitty on 2010-12-22
ok, thanks for clarifying. once i backup, how do i reinstall ubuntu with grub?

---

### Post by yugnip on 2010-12-22
Install on your Ubuntu partition as you said, making sure to install Grub at the root of that partition. The dropdown menu at the bottom of the installer partition window shows where Grub is to be installed.

For example, if EFI is @ Sda, Mac @ Sda2, and Ubuntu @ sda3, Swap @ sda4, then install Grub @ sda3 with mount point /

---

