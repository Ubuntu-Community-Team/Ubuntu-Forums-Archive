---
title: "Ubuntu Warty on original Powerbook G3 (Kanga, 3500)"
date: 2004-12-30
forum: Apple PPC Users
---

### Post by steamrunner on 2004-12-30
I'm trying to get warty running on an original Powerbook G3 (aka Powerbook 3500 aka "Kanga") using BootX to boot from OS9 to Linux. I've run through the 'old world' Mac install wiki and the BootX wiki using the noted tricks to get the installed kernel over to the OS9 (HFS) volume to allow BootX to find it etc etc.

However, on reboot to Linux (via BootX) the machine displays an (inverse?) tux and then clears to a blank screen and seems to hang. The disk is working (as it it's booting in the background), but no screen. I'm guessing this is a video driver or X config problem... but what.  

After a bit of googling for possible kernel parameter video settings for the video controller in the Kanga (a Chips & Technologies one at 800x600x16), I've got to this as boot kernel parameters...

  root=/dev/hda10 video=chipsfb,vmode:10,cmode:16 3

... (with the 3 trying to get to run level 3 i.e. sans X)... but this  doesn't work either...

Anyone any ideas? Anyone got Ubuntu (or any Linux?!?) running on a Kanga? Any idea how I can force a boot to a bare single user text console (a la the installer?). The clt-alt-F2 (or is that ctrl-option-F2?) doesn't seem to work for me...

PS/FYI:  the Kanga does not auto-detect it's Ethernet port during the install - you need to manually tell it to use the de4x5 module...

SB

---

### Post by jeltsch on 2005-07-31
I am also trying to get Ubuntu (4.1 or 5.04) running on the original PB G3 (aka Kanga aka 3500). The only problem: the screen is blank. Nothing at all, although the boot process seems to continue.

Here the story: I rebooted using the MacOS 9.1 CD, I reformatted the drive into two partitions: one 1GB and the rest (about 4GB) unallocated. Then I installed Mac 9.1 on the 1GB partition, downloaded BootX and installed it according to the instructions. Then I burned the Ubuntu PPC from the iso onto a writable CD (using a "regular" i386 Linux distribution and K3b, BTW: RW-CDs are apparently not recognized by Kanga's CD drive). Then I copied both the installation kernel and initrd from the installation CD to their respective places into the Macintosh System folder (Ubuntu_PowerPC_hoary/install/powerpc/vmlinux to Macintosh HD:System Folder:Linux Kernels and Ubuntu_PowerPC_hoary/install/powerpc/initrd.gz to Macintosh HD:System Folder:ramdisk.image.gz). Then I rebooted and selected Linux. Installation works like a charm, I couldn't believe it. The network card is detected correctly, so is apparently all other hardware. I choose the guided partitioner (select largest unused space) which created the ext3 filesystem on /dev/hda10. After the installer had finished and was about to reboot, I needed to copy the deafult kernel from the /boot to the HFS partition in order to have BootX start Linux. The fasted way I concluded was for me to switch of the machine, take out the hard disk and connect it via a USB enclosure to my i386 SuSE Linux 9.3 machine. Both the HFS partition and the ext3 partition were automatically mounted and I copied /boot/vmlinux-2.6.10-5-powerpc to my SuSE machine. Then I put the hard drive back to the Powerbook G3 and rebooted into Linux and copied the kernel via http to Macintosh HD:System Folder:Linux Kernels.

Then I executed the BootX application, but here my luck ended. What happens is that the first couple of lines of the boot messages are displayed and then the screen goes blank and never appears again. "arch:exit" is the last line that is displayed. 

 However, the machine continues booting, but since there are still some installation tasks to be done, the machine never reaches a state where I could ssh into it and fix stuff. Now I have not the faintest idea where to start as there are no error messages and nothing. Since the installer manages to address the monitor, it should be possible to get it done, but how? I have been trying to pass almost every possible combination of kernel arguments to get the video working, but to no avail (the correct kernel argument should be video=chipsfb:vmode:10,cmode:16; maybe fbdev instead of chipsfb?). My next attempt will be to install it with an external monitor connected. BTW: I had YDL 3 running on the same machine quite a while ago. But it seems there are no viable alternatives ATM to Ubuntu when it comes to PPCs.

The same procedure using Ubuntu 4.1 leads to similar (though not identical) results. The network card has to manually selected during install (de4x5 module). After the first reboot the penguin appears in the upper left corner in inverted colors and that's where the system hangs.

---

