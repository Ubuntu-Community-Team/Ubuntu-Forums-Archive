---
title: "Error 17"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by swoskow on 2007-03-11
I have been trying to install 6.10 from the alternative disc and I am not having success.  I am getting the error 17 message at boot.  I have Ubuntu installed as follows:
Internal 200 gb HD with Root, swap, home on the internal 200 gb disc
Internal 500 gb HD, external 1 tb HD and external 500 gb set up as Raid/LVM

I followed the instructions for the alternate CD but I get error 17 on boot.  I installed from the live CD and I was able to get it to work fine but I would like to have it installed from the alternate because I am mainly going to use this as a file server on a home network for downloading and storing music and video files.  One question though is do I really need the  Alternate CD version or is the regular desktop version OK.

I have searched the forums and I have used the grub command (setup (hd0).  This did not work.

I have tried to use the Grub superdisc also did not work.  

Nothing seems to work but I know it's possible because I can get the desktop version to install and boot fine.  One item I noticed in GParted is their is no mount point listed for the partition (I know I did this in install though).  

Any help would be greatly appreciated - I feel that I am almost there.

---

### Post by matburton on 2007-03-11
Erm, I'm not sure using the alternate CD is a good idea, the desktop one will do just fine for everything you've described. The alternate CD is for very specialised use.

---

### Post by swoskow on 2007-03-11
> **matburton said:**
> Erm, I'm not sure using the alternate CD is a good idea, the desktop one will do just fine for everything you've described. The alternate CD is for very specialised use.

I read that the alternate CD does set the internal timer freq to 100 Hz vs 1 Hz for the desktop to give some extra performance.  I don't know if that makes a big difference.  

I am trying something else.  I have disconnected all the external drives and reinstalling to see if that helps.

---

### Post by dstew on 2007-03-11
There are problems with some BIOSes and grub due to the way the BIOSes number the disks. Sometimes, the disk numbers are different when you disconnect external drives, causing grub to be unable to find the root disk. The root disk is there, but the numbering changed when one drive was removed, or sometimes when the boot order is changed.

To solve these problems, you sometimes need to edit your /boot/grub/device.map file. When grub boots, it will ignore the BIOS numbering scheme and use the scheme stored in the device.map file. That way, if your BIOS numbers the disks differently under different system configurations, grub won't get confused. See this recent thread for another user's grub problem, solved by editing device.map:

[http://www.ubuntuforums.org/showthread.php?t=351974&page=2](http://www.ubuntuforums.org/showthread.php?t=351974&page=2)

---

### Post by swoskow on 2007-03-11
> **swoskow said:**
>   I am trying something else.  I have disconnected all the external drives and reinstalling to see if that helps.

That worked so there must have been some conflict with my external drives.  Now all I need to do is set up the Raid, LVM and SAMBA and I should be rolling.

---

### Post by swoskow on 2007-03-11
I spoke to soon - now I get to the ubuntu bot up screen but it hangs - the message I get says    /bin/sh: can't access tty: job control turned off (initramfs)

---

