---
title: "GRUBB and multiboot with Windows 2000"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by Howard Kaikow on 2007-05-11
I am planning on installing 7.04 in an ext3 on a USB drive, then setting up multiboot via the NT loader in boot.ini.

I do not want GRUBB modifying the MBR on any drive, except, if necessary, for the ext3 partition.
I would then copy te stage1 file to a FAT32 partition, and then, in Windows, to the C drive and set up boot.ini.

However, somebody mentioned that GRUBB has a mind of its own and would modify the MBR of the C drive anyway.

How can this be prevented?

---

### Post by eltorodeoro on 2007-05-11
I'm not sure about USB drives, but generally, GRUB only modifies the MBR of the HDD that Linux is being installed on.  Regardless, GRUB is equally capable (if not moreso) of handling your booting needs as NTLDR is.  So if your MBR for HDA is overwritten, you shouldn't worry.

---

### Post by Howard Kaikow on 2007-05-11
> **eltorodeoro said:**
> I'm not sure about USB drives, but generally, GRUB only modifies the MBR of the HDD that Linux is being installed on.  Regardless, GRUB is equally capable (if not moreso) of handling your booting needs as NTLDR is.  So if your MBR for HDA is overwritten, you shouldn't worry.

I've seen statements that the NT loader wants to be in control, so I'd rather play itsafe and use NT Loader.

What about the following:

1. Do a full True Image backup just before the Linux install.
2. Install Linux.
3. Copy the GRUB stage1 file to the FAT32 partition or floppy.
4. Restore drive C MBR from backup.
5. Copy stage1 file to C, and modify boot.ini to include Linux.

---

### Post by dstew on 2007-05-11
Actually, it is not that simple. The grub stage1 file is only a boot-loader skeleton, not the real boot loader that is installed when you create your system. Grub modifies the stage1 file to point it to the rest of the grub boot system (stage1.5 or stage2) when it installs it.

What you really have to do is install grub into the partition that contains your linux installation. At the end of the installation process, you will have the option to do this. It might be a separate menu, such as "Advanced". Or, you can not install grub at all, and do it as a separate step using a supergrub disk. The key thing is to install grub into the **partition**, not into the MBR of your USB drive.

After grub is installed, you should make sure that linux will boot, using an external disk like supergrub. If linux boots OK, in order to get Windows to boot it, you will need to create an image file of the first sector of the linux partition, that contains the grub boot loader (the modified stage1 file). You need to store this image in the boot directory of windows, and point the windows booter to it.

The full gory details are seen in this [How-To]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html").

---

### Post by Howard Kaikow on 2007-05-11
> **dstew said:**
> Actually, it is not that simple. The grub stage1 file is only a boot-loader skeleton, not the real boot loader that is installed when you create your system. Grub modifies the stage1 file to point it to the rest of the grub boot system (stage1.5 or stage2) when it installs it.

What you really have to do is install grub into the partition that contains your linux installation. At the end of the installation process, you will have the option to do this. It might be a separate menu, such as "Advanced". Or, you can not install grub at all, and do it as a separate step using a supergrub disk. The key thing is to install grub into the **partition**, not into the MBR of your USB drive.

After grub is installed, you should make sure that linux will boot, using an external disk like supergrub. If linux boots OK, in order to get Windows to boot it, you will need to create an image file of the first sector of the linux partition, that contains the grub boot loader (the modified stage1 file). You need to store this image in the boot directory of windows, and point the windows booter to it.

The full gory details are seen in this [How-To]("http://www.geocities.com/epark/linux/grub-w2k-HOWTO.html").

That was what I was going to do.
My point of confusion was how/where to install GRUB.

I doubt that I can boot directly off of a USB drive on my ancient hardware.
I'll try booting via boot.ini.

One goal is to get a feel for Linux, then decide whether I want to build my own Linux hardware, or but a linux system, with Ubuntu from Dell.

I've not yet looked into how to dual boot Linux with Vista and what is the impact if Vista is installed after/before Linux. But, this should be a separate thread.

---

### Post by dstew on 2007-05-11
You are right, you probably cannot boot an external USB drive directly if you have old hardware. I assume you have installed a linux system on your USB hard drive, but did not install grub. However, you should still be able to boot Linux from the opening menu of the Ubuntu Live CD, just to be sure it works.

If your linux system boots, you can install grub from the Live CD. Quit and reboot from the live CD, and go to the Live CD desktop instead of your linux on the hard disk. Open a terminal window, and enter **grub**. This should get you the grub prompt:```
grub>
```At the grub prompt, enter```
grub>find /boot/grub/stage1
```The output of this command will give you the partition name that will become grub's root. If you have one hard disk and one USB disk, it will probably be (hd1,0). Use whatever result you get in the next grub commands, then quit and reboot:```
grub>root (hd1,0)
grub>setup (hd1,0)
grub>quit
```This will install the boot loader into the first sector of your linux installation. Now, you can follow the guide, make an image of the grub boot loader, and use the Windows bootloader.

---

### Post by Howard Kaikow on 2007-05-12
> **dstew said:**
> You are right, you probably cannot boot an external USB drive directly if you have old hardware. I assume you have installed a linux system on your USB hard drive, but did not install grub. However, you should still be able to boot Linux from the opening menu of the Ubuntu Live CD, just to be sure it works.

If your linux system boots, you can install grub from the Live CD. Quit and reboot from the live CD, and go to the Live CD desktop instead of your linux on the hard disk. Open a terminal window, and enter **grub**. This should get you the grub prompt:```
grub>
```At the grub prompt, enter```
grub>find /boot/grub/stage1
```The output of this command will give you the partition name that will become grub's root. If you have one hard disk and one USB disk, it will probably be (hd1,0). Use whatever result you get in the next grub commands, then quit and reboot:```
grub>root (hd1,0)
grub>setup (hd1,0)
grub>quit
```This will install the boot loader into the first sector of your linux installation. Now, you can follow the guide, make an image of the grub boot loader, and use the Windows bootloader.

Thanx.

I have to install Linux on a USB drive on this PC, unless I pull a tape drive and add a 4th hard drive.
I've got about 19GB free on the hard drives, but that's spread over 10 logical drives, no practical way to repartition the critters.

I used Partition Magic to set up an ext3 partition on my largest USB drive, and a Linux Swap partition on my 2nd largest USB drive. This exposed the bug described in MSFT KB article 836662. I have 4 Windows 2000 on the PC, 2 of which were affected by the bug, one permanently, or so it seems, the other was repairable, or so it seems.

I have not yet installed Linux.
I have read two books and a bunch of articles.
Only thing left to do is gcather my internet, network and PPP settings, and get a few questions answered, before I summon the courage to do the install.

For example: "What is the advantage of using GNOME PPP instead of the Networking section of System | Administration in Ubuntu? "

I will be doing a full Acronis True Image backup just before the install.

My goal is to get enough experience with Linux so I could build a PC using a Live CD as the test software.
Then, I could add the retail/OEM Vista, as well as Linux. and, likely, make Linux te default OS.  I want no part of the pre-installed crap that is included on Windows PCs.

I used to use Unix 9 years ago (BSD) and in my last few years at DEC (Ultrix), so I expect that once I get past the installation, I'll remember stuff quickly.

Linux books have been disappointing.

---

### Post by Howard Kaikow on 2007-05-15
Well, I summoned the courage to install 7.04, but I'm not sure that I handled GRUB properly.
I am installing on a USB drive and will be using NT Loade rfor multibootig.

1. During the install, run from LiveCD, GRUB was installed without offering me an opportunoty to NOT put in the MBR.

2. Instead of installing on hd0, I instalkled on /dev/sda5, and then used dd to copy the boot sector.

3. I then rebooted to Windows, put the boot sector on the C drive, and modified boot.ini accordingly.

4. When I tried to boot into Linux, I got a "GRUB Geom Error".
Does that mean I have to repartition things so Linux is installed in a partition beginning prior to cylinder 1024?

Is there a way around this?

---

