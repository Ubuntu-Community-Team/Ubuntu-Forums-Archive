---
title: "Partition Question"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by HappyEisentrout on 2007-11-30
I had XP installed on my hard drive but wanted to switch to ubuntu.  I installed Ubuntu and now i cna't access my other partition and i have a lot of pictures on it that i would like to get.  anyone know what i cna do?

---

### Post by Partyboi2 on 2007-11-30
you will need to reinstall grub so that you can boot into windows again
have a look at this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mikewhatever on 2007-11-30
> **Partyboi2 said:**
> you will need to reinstall grub so that you can boot into windows again
have a look at this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Grub should have nothing to do with accessing partitions.

HappyEisentrout, do you get any error messages when trying to access that partition? Can you post the outputs of the following commands:
> sudo fdisk -l
sudo cat /etc/fstab

---

### Post by HappyEisentrout on 2007-11-30
sudo fdisk -l
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf942c0b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        5430        7296    14996677+  83  Linux
/dev/sda2            5383        5429      377527+  82  Linux swap / Solaris

Partition table entries are not in disk order

sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5fb3aa60-3c39-49ff-ada6-19a51fb5d2b0 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=3fe63c96-1e99-4a57-b491-097a241c93b2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by Sef on 2007-11-30
check out [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").   It will reinstall GRUB.

---

### Post by mikewhatever on 2007-11-30
So, what other partitions are you talking about? You seem to only have one hdd, /dev/sda, and two partitions on it, sda1 and sda2, and both are perfectly accessible. Do you have another drive or more partitions on the first one?

---

### Post by niteshifter on 2007-11-30
Er ... ahh.... folks:

Look closely at his fdisk report: there's a whole section of disk missing there, that is, where are cylinders 1 - 5382? 

Methinks that's what was his XP installation. I also don't think SGD will fix this, the partition table on the disk needs editing. Such can be done, manually with Ubuntu tools, but it's not for the faint of heart / inexperienced.

I think the best course of action is for HappyEisentrout to dig up his XP CD and use it to repair his MBR, that should restore XP. **Then backup what he needs to CD and-or USB key drive (in Windows).** Then attempt another install of Ubuntu.

---

### Post by HappyEisentrout on 2007-11-30
is there an easier way to access that partition just to get my pictures off?  or will i have to dig up an xp disk to fix it and then install ubuntu again?  and how would i go about doing that?

---

### Post by niteshifter on 2007-12-01
I wish I could help you in detail on recovering Windows, but it's been years since I've had to do that - all I can recall is that the Windows version of fdisk can be invoked as FDISK /MBR. Google "windows mbr repair" and see what that gets you.

Now as to why I've not done this in years: 'Tis far easier to restore from an image backup than to re-install Windows. I learned this with Win NT4. It applies to any modern OS.

---

### Post by bumanie on 2007-12-01
If you have a windows disk, the best thing to try is to boot into the windows disk and go to recovery console (this is for xp). Once in recovery console you can type fixmbr. This is meant to reinstall the windows mbr - I have never had it work for myself to be honest, but I believe that is the M$ suggested procedure.

---

### Post by fortiaAli on 2007-12-01
I think there may be two ways of fixing this. I have used both methods, However my recollection of is a little rusty so please proceed with caution or wait for another post to either confirm or flame.

Method 1- If you have your original Xp disk, reboot your computer with the XP CD installed in the drive. If the Windows installer doesn't automatically detect that you have a broken Windows MBR and/or broken Windows files and begin to correct these automatically you will be led to several blue screens. I think you have to select the  "agree", "f8" and "install" options on these windows (do a web search to confirm this) .  DO NOT choose the "repair" option.   Windows should now re-install the broken/missing/corrupted files and restore the MBR . At some point you will be prompted to enter the WinXP product code/key number.  When finished and upon a reboot you should now be able to access your Windows partition and files (but not Linux).  Then reload your Ubuntu CD, re-partition your hard drive and re-install Ubuntu.

Method 2) After Ubuntu I like PuppyLinux.  Download a copy and burn to Cd.  Reboot your computer with the PuppyLinux in your CDTray.  Puppy runs entirely in ram and allows the rest of your computer to be easily accessed. Remove the Puppy disk, pop in a Blank CD/DVD locate the files you wish to keep and copy them to Cd/DVD..  By the way, i always use Gparted on my PuppyLinux Cd to create a blank ext3 partition on my hard drive before installing another OS onto it.  I don't know why i do this but it works for me.

Method 1 has the advantage of being able to reboot into windows at any time.  Method 2 is quicker but you will not be able to use Windows until you fix the MBR.

Good luck.

---

### Post by meierfra on 2007-12-01
If you are lucky your windows partition is still intact and only your partition table is corrupted. In this case testdisk might be able to fix the problem: [Hermanzone info on testdisk]("http://http://www.users.bigpond.net.au/hermanzone/p21.html")

---

