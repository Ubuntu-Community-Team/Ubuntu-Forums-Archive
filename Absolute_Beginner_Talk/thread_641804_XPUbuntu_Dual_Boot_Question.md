---
title: "XP/Ubuntu Dual Boot Question"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Frunkis on 2007-12-15
I checked through some of the previous posts with dual booting XP/Ubuntu, but I think mine is slightly well....special. I have 2 IED hard drives, a 120GB and 65GB, and the 65GB hard drive is from my old Sony computer that died. This hd still has its original XP os on it, and I am going to delete it all together, as its not used at all and I want to use this hard drive to run Ubuntu. I am new to this and just want to check get some input on this before I do anything stupid. Any suggestions would be greatly appreciated Thanks.

Asus P5BE  
Intel Duo-Core 2 6400 Conroe 2.13Ghz
Currently 1GB OCZ Gold ram, going to upgrade to 2GB shortly
Radeon X1300 Pro 256mb graphics

---

### Post by Ptero-4 on 2007-12-15
If you have ubuntu in your 120GB HD you can just format the 65GB HD and then in the /boot/grub/menu.lst (notice it's a lowercase "L" and not a "1" or uppercase "i") remove the entries referring to windoze and finally run sudo update-grub.

---

### Post by dpar on 2007-12-15
You won't have a problem.

Check this out......[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Bartender on 2007-12-15
If it was me I'd download/burn a copy of GParted LiveCD (GPLCD).  Boot from the CD, go thru the steps to get it going, look up in the right-hand corner to see the window that lets you scroll thru your drives.  In your case "sdb" ought to be the 65GB.  Make sure you pick the right one!
If you see more than one partition on the desired drive, right-click on each and delete the partitions.  
Do as the folks at GPLCD suggest - apply each step as you go.  Don't stack up three or four tasks then apply them all.  In other words, delete the partition, apply that task, and wait to see the new map with the partition gone.
When you have one big partition, right-click on it again and start creating your ext3 partition for /, a linuxswap partition for swap, and another ext3 partition for /home.
Or if that's too confusing, just format the whole thing to ext3, apply it, then get out and toss in the Ubuntu CD and let it do its thing.  That means installing to sdb, of course, not sda.
I would suggest making a /home partition unless you just don't feel comfortable doing that.  If you let Ubuntu auto-install it won't make one.
If you want to let the GRUB bootloader tweak the Windows MBR so that you get the choice when first booting up, just let Ubuntu take you thru the install process and don't worry about messing with the bootloader settings.

---

### Post by Frunkis on 2007-12-15
Thanks, I appreciate the help. I think I am ready to take a chance and do this. If anybody else has any other ideas, please let me know.

---

### Post by torgrot on 2007-12-16
If you want a failsafe method swap the drives.  Make the 65GB drive the primary master and your 120GB drive the primary slave.  The advantage is that you don't have to touch anything on your 120GB XP drive.  If everything goes to hell all you have to do is swap the drives back to their original settings 120GB primary master and 65GB primary slave and reboot.  Back to windows no problem.  And Ubuntu will set up grub to boot both from the 65GB hard drive.

torgrot

---

### Post by Bartender on 2007-12-16
torgrot -
That's an interesting idea - don't think I've ever heard anyone propose swapping drives so the Windows install is slave.
Your proposal is somewhat contingent on the OP having a BIOS that allows him to hit a key (usually F8 but I've heard of others) during boot that gives him a choice of boot devices, isn't it?
With Ubuntu installed to the master as you suggest, GRUB won't tweak the MBR on the Windows slave drive, will it?

---

### Post by torgrot on 2007-12-16
That is correct.  It never touches your Windows drive.  Grub is installed to the Ubunutu drive MBR.  I did it that way, Grub will set up a menu with all of the details set up to allow you to chose to boot either Ubuntu or Windows.  Nice and neat.  You don't need to swap things around with the bios, no key to choose which drive to boot, just select the operating system in Grub and away you go.

Here is my fdisk, I have two 160GB drives SDA is Ubuntu and SDB is Windows XP.
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2568    20627428+  83  Linux
/dev/sda2            2569       19187   133492117+  83  Linux
/dev/sda3           19188       19457     2168775   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x07066020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       16709   134215011    7  HPFS/NTFS
/dev/sdb2           16710       19457    22073310    f  W95 Ext'd (LBA)
/dev/sdb5           16710       19457    22073278+   7  HPFS/NTFS

Here is the pertinent parts of menu.lst
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=b4c0c777-d953-45c7-ab2e-ea041de9f86a ro acpi=ht pci=biosirq quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
savedefault

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1




torgrot

---

### Post by Frunkis on 2007-12-16
Let me make sure I am following you correctly so that I don't screw something up. Swap my hard drives out making the 65GB the master and the 120GB slave. Once that is done, boot the computer with the Ubuntu CD in the drive and allow it to run and install everything onto the 65GB hd. Is there anything I should be aware of as far as getting it to boot properly or anything? I am not that advanced in specific computer functions like I am with computer networking. Thanks again.

---

### Post by Frunkis on 2007-12-16
Ok so I burned everything to disk and attempted to get it to run, and it won't boot. The CD drive is set to be the first thing to boot and still loads windows. Do I need to run something else to get it to boot from disk? or do I need to change something else? Thanks.

---

### Post by torgrot on 2007-12-16
Try burning the iso at the slowest speed you can, some people claim that it makes a difference.  Can you boot off of any CD? i.e. the Windows CD.  That is the first hurdle you have to get past.  

torgrot

---

