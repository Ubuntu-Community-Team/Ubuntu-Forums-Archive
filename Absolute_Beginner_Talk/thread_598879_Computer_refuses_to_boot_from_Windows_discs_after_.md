---
title: "Computer refuses to boot from Windows discs after Ubuntu install."
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by City Builder on 2007-10-31
Hello,

I had a Suse server here at home and decided to install Ubuntu on it.  All went fine with the install and Ubuntu runs fine but....

I need to put a copy of Windows back on this box, so I put in *any* of my Windows CD's (98, 95, ME, XP, Vista which should all be bootable except vista) and nada.  

The computer starts up and says, Boot from CD/DVD then just sits there.  I've now swapped out 3 known good DVD drives and it's the same situation.

I put in my bootable Ubuntu disk and restart and the computer boots off of the Ubuntu CD that I made but now refuses to boot into any of the windows CD's that I have.

I don't know what is causing this, but Im about to throw the darn computer in the garbage if I can't get windows back on it.  And I really don't understand why the computer will allow me to boot off the Ubuntu bootable CD but not *any* of my Windows CD's.  It's like there is something written to the Bios that is not allowing the Windows CD's to boot up.

Can somebody tell me what is going on with this?

Thanks,

---

### Post by Frak on 2007-10-31
Check you BIOS to make sure in BOOT it has CD/DVD as first priority (usually by pressing F2, F8, or ESC at the BIOS screen)

Though, to me, it sounds as if you have a b0rked Windows disc.

---

### Post by scorp123 on 2007-10-31
> **City Builder said:**
>  I need to put a copy of Windows back on this box, so I put in *any* of my Windows CD's (98, 95, ME, XP, Vista which should all be bootable except vista) and nada.  

The computer starts up and says, Boot from CD/DVD then just sits there.  I've now swapped out 3 known good DVD drives and it's the same situation. I think you have the "Black Screen of Death" of the Windows installer program. It can't cope with the partitions you put on your harddisk. So you'd either have to completely erase every partition on your harddisk (not just format them... completely remove them so that the partition table is empty) or you'd probably need to disconnect that harddisk (I assume you want to keep your Linux partitions, right?) and put in a second harddisk on which Windows may install.

Always install Windows *before* Linux.

Credits go to Microsoft ... thanks for creating this wonderful broken and buggy installer that can't cope with any non-MS partitions. God forbid you have anything but MS OS's on your disks ... 

I had the very same problem a few weeks ago. For some tests we did I needed to install Windows XP on a machine that was previously used for Debian. Only completely removing every trace of Linux allowed me to get into the Windows setup program.

---

### Post by HereInOz on 2007-10-31
I agree with Scorp, that is the issue you face.  You need to remove the ext3 partition(s) first, and then install Windows.  You can use gparted to re-format the partition(s), or Partition Magic if you have it, and you may even get away with using a Windows 98 startup disk and run fdisk, and delete the non-dos partitions.

Again, it is one of those "thanks Bill" moments we all get to "enjoy" from time to time.

---

### Post by Frak on 2007-10-31
I would recommend clearing all partitions, installing Windows.

If you really want Linux back, its best to install AFTER you install Windows. (Windows doesn't play well with other foreign partitions)

Forgot about the BlSOD. It's a rare occurance now since Vista fixes this issue (mostly)

---

### Post by City Builder on 2007-10-31
I should have mentioned that I did unplug the only hard drive in the computer but the results were the same.

Im now sure the windows discs are fine, they boot up on my other PC just fine.  I'll see about wiping out the hard drives partitions just in case the windows discs are balking at not having any hard drive being available at all but that seems a bit off to me since the PC only has to boot to the CD, it doesn't have to write anything to a HDD yet until I get going on the installation.

Will the Ubuntu CD allow me to wipe out the partitions on the existing Ubunt installed HDD?

---

### Post by City Builder on 2007-10-31
Okay, problem solved.
 
I downloaded Ultimate Boot Program and created a boot CD with it, then went into disk management and wiped out the partitions and upon rebooting with the Windows XP CD in the drive it's now on it's way to installing.

So whom ever said it was likely the Linux partition causing the issue seems to be correct.

I will be putting Ubuntu back on this particular PC after XP is loaded up however as it seems to be a nice distro IMO.

Thanks for the suggestions, without the ones about the partitions I probably would have just retired the computer to the garage and sold it in a garage sale or something such as that.

My appreciation to you.

---

### Post by oilchangeguy on 2007-10-31
> **scorp123 said:**
> I think you have the "Black Screen of Death" of the Windows installer program. It can't cope with the partitions you put on your harddisk. So you'd either have to completely erase every partition on your harddisk (not just format them... completely remove them so that the partition table is empty) or you'd probably need to disconnect that harddisk (I assume you want to keep your Linux partitions, right?) and put in a second harddisk on which Windows may install.

Always install Windows *before* Linux.

Credits go to Microsoft ... thanks for creating this wonderful broken and buggy installer that can't cope with any non-MS partitions. God forbid you have anything but MS OS's on your disks ... 

I had the very same problem a few weeks ago. For some tests we did I needed to install Windows XP on a machine that was previously used for Debian. Only completely removing every trace of Linux allowed me to get into the Windows setup program.

this is wrong. booting from a cd, is just that. booting and running the computer from a cd. at the proper time in the install process windows will prompt you to set up partitions. what happens when you run fdisk from a 98 boot floppy on a hd formated ntfs, and not fat, or fat 32? you'll get a message something along the lines of the hard drive may have some problem, virus, etc. the problem is not the fact that the hd is formated ext3, and not ntfs. it's something else.

---

### Post by tigerjk1410 on 2007-10-31
i'm having a similar problem and i have no idea how to fix it as it is my first experience with ubuntu. i booted from the ubuntu cd to check it out and then i decided to install it on one of my hard drives but after it completed the install and rebooted i couldn't access that drive anymore. i can't see the drive in winxp either and i would really like to use it.

is there any way to recover the drive so that winxp recognizes it? the drive shows up in BIOS but not anywhere in windows.

thanks!

---

### Post by City Builder on 2007-10-31
See my post number 7 in this thread.  That was the way that I recovered the drive.

---

### Post by scorp123 on 2007-11-01
> **oilchangeguy said:**
>  this is wrong.  Google for "black screen windows setup linux" and see for yourself. This is a known problem of the Windows installer program which will refuse to work in some cases if there are Non-Microsoft partitions present on the harddrive.

> **oilchangeguy said:**
>  booting from a cd, is just that. *booting* ain't the issue ... It will boot, yes. But getting into the SETUP.EXE is the issue: It will hang and instead of the blue setup screens of the Windows installer you will get a "black screen of death". Again: Google around. There are many examples of this.

> **oilchangeguy said:**
>  the problem is not the fact that the hd is formated ext3, and not ntfs. it's something else.   You know the difference between *formatting* hard drive partitions and *partitioning* a harddisk, yes? See above. :)

---

### Post by louieb on 2007-11-01
> **tigerjk1410 said:**
> i'm having a similar problem ... decided to install it on one of my hard drives but after it completed the install ...couldn't access that drive anymore. i can't see the drive in winxp either and i would really like to use it...is there any way to recover the drive so that winxp recognizes it? the drive shows up in BIOS but not anywhere in windows.
Your problem is really quite different from the one in this thread. Go ahead and start a new thread.  Give it a title like *Can't see Ubuntu from windows. *
Is the PC able to dual boot Ubuntu and window now? 
Do you know how to list the partition table using Ubuntu?
Do you want to keep Ubuntu and dual boot or just reclaim the drive for windows to use?

---

### Post by tigerjk1410 on 2007-11-08
> **louieb said:**
> Your problem is really quite different from the one in this thread. Go ahead and start a new thread.  Give it a title like *Can't see Ubuntu from windows. *
Is the PC able to dual boot Ubuntu and window now? 
Do you know how to list the partition table using Ubuntu?
Do you want to keep Ubuntu and dual boot or just reclaim the drive for windows to use?

i am looking to reclaim the drive for windows use.

---

### Post by buccaneere on 2007-11-09
> **City Builder said:**
> See my post number 7 in this thread.  That was the way that I recovered the drive.


Recovered the drive? Data too? Or just **access**, so you could do a windows re-install???

---

### Post by mridkash on 2007-11-09
There is a driver for windows that lets you see and read/write an ext3 partition. Its called ext2fs something, search for it. I have it on my laptop and works solid! It creates a Drive in 'my computer'.

---

