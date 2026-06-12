---
title: "can Linux and Mac OS dual boot on one hard drive?"
date: 2006-09-17
forum: Apple PPC Users
---

### Post by baosheng on 2006-09-17
hi, I have used Linux on x86 for 3 years but I haven't tried Linux on Mac.
I have a very newbie question. Can I install Mac OS and Linux on different partitions and use a boot loader to select which system I wanna enter? 

Oh, maybe on Mac there is no boot loader like x86?

---

### Post by blue_chili on 2006-09-17
You didn't do much research did you :P 

I came up with the following post:
[http://www.ubuntuforums.org/showthread.php?t=7558](http://www.ubuntuforums.org/showthread.php?t=7558)

Also (outside of these forums:)
[http://www.philroche.net/archives/osx-and-ubuntu-dual-boot/](http://www.philroche.net/archives/osx-and-ubuntu-dual-boot/)
[http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html](http://www.askdavetaylor.com/how_do_i_dual_boot_ubuntu_linux_mac_os_x.html)

I also vaguely remember doing this on my ibook a while back, though its a powerpc so not sure whether its different if you are using an intel mac.

Hope that helps.

---

### Post by stmiller on 2006-09-17
Yes you can dual boot. We have yaboot, the bootloader. New intel machines use grub. Read about yaboot. The ubuntu ppc install discs configure and install yaboot in the boot partition space.

---

### Post by kulath on 2006-09-17
Can you share a separate home partition between Linux and Mac OS X?

I haven't been able to find any specific advice about how to do this - philroche just mentions it in an aside, and I don't understand why he gets permissions in a mess if he gets the user ID to be the same on both systems.

---

### Post by baosheng on 2006-09-19
well, I am making an experiment. 
I put another hard drive on to my PowerMac G4. And I seprated two partitions by the program in Mac OS 9 installation CD. One is for Mac OS 9 and another is for Ubuntu. Then I booted it with Ubuntu mac live CD and formatted the partition I prepared for Ubuntu into ext3. I haven't prepared the swap coz this is just a test.

---

### Post by linear on 2006-09-20
> **baosheng said:**
> Then I booted it with Ubuntu mac live CD and formatted the partition I prepared for Ubuntu into ext3. I haven't prepared the swap coz this is just a test.

You would have an easier time if you just leave the Ubuntu partition unformatted, as free space. The installer will re-partition it and set up the swap.

---

