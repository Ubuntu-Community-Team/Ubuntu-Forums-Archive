---
title: "WinXP and Ubuntu on 2 different bootable harddrives."
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by lemik on 2007-06-11
Hello all.

I tried to install Ubuntu 6.10
I'm a newbie in Linux, so didn't want to remove Windows(XP) from my computer.
I have one hard drive with WinXP inside of the computer and other, pullout one for Ubuntu.
I turned off the power in the inside disk, installed Ubuntu on the pullout disk, and connected the power to the inside disk back.
So I have two disks bootable. I turned the BIOS so when the pullout disk is in, it starts, when it's out starts the disk that always inside.
After some days that I worked with Ubuntu ( never mounted the inside disk ), WinXP installation crashed, so I need to reformat the inside disk and reinstall WinXP. The problem was that the partition table crashed, and even on other computer with WinXP I didn't see anything on the inside disk.

My question: may be Ubuntu erased something on the hard drive with WinXP? What does it do with other hard drive that just connected to the motherboard and is not mounted to OS Linux? Or I have to mount other hard drives when I start Ubuntu?

Thank you in advance.

---

### Post by ikonia on 2007-06-11
Ubuntu doesn't touch XP.

You don't need to take disks out or put them in - just leave both in and install XP to one disk and ubuntu to the other. 

Then put the grub bootlaoder on either the XP disk MBR and boot off that, or put Grub on the second disk MBR and use your bios to select your boot disk.

---

### Post by lemik on 2007-06-11
Thank you for reply. I tried to use the same bootloader (GRUB) for both OS, but when I needed to start CheckDisk on WinXP, it only scheduled and didn't work after restart. I guess, GRUB is to blame. But if you say, that Ubuntu does do anything with another hard drive - OK, so the problem is in another place.

---

