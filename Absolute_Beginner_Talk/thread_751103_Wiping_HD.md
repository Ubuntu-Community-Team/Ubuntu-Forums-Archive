---
title: "Wiping HD"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Orcaporka on 2008-04-10
My laptop has a D2D recovery system so that I can wipe my drive clean and start again. However since I have installed Ubuntu, when I press ALT+F10 at the startup (To initiate wipe) nothing happends and I go straight to grub? I need this as when I wipe my drive I still want to have windows there in a partition so is there any reason why it should not work?

Thanks.

---

### Post by neurostu on 2008-04-10
Yes.  I'm not surprised it is broken.  You laptop came with a MBR that pointed to your recovery partition. Now that grub is installed it overwrote the MBR and so grub is unaware of your recovery partition.

What you need to do is manually add the recovery partition to your grub boot loader.  This way you can boot into the recovery partition and recover (*shiver) windows.

Keep in mind that this recovery process will WIPE everything.  Ubuntu will be gone, your partitions will be gone, your files will be gone. EVERYTHING WILL BE GONE. It will be exactly like the laptop just came from the factory.  This is probably why grub isn't pointing to the partition use of the partition will remove grub and what ever it is pointing to.

You should search for something like "Grub how to restore recovery partition"

try looking at this tutorial: [http://www.klabs.be/~fpiat/linux/boot/ThinkVantage_Rescue-and-recovery/](http://www.klabs.be/~fpiat/linux/boot/ThinkVantage_Rescue-and-recovery/)

---

### Post by hurtstotalktoyou on 2008-04-10
What neurostu said is probably correct.  However, before you try wrestling with grub, please answer these two questions:

1.  What is the make/model of your laptop?
2.  Did the laptop come with any restore CDs/DVDs?  (If so, please describe them.)

Thanks!

---

### Post by Orcaporka on 2008-04-10
> **hurtstotalktoyou said:**
> What neurostu said is probably correct.  However, before you try wrestling with grub, please answer these two questions:

1.  What is the make/model of your laptop?
2.  Did the laptop come with any restore CDs/DVDs?  (If so, please describe them.)

Thanks!

I have an Acer Aspire 3610
and it came with no resotre CDs/DVDs

---

### Post by Orcaporka on 2008-04-10
Im having trouble, I have the Live CD but I think I may have damaged files on one partition as my laptop froze whilst I was changing its size.

Is there some command I can enter into the GRUB command line to restore the recovery option?

---

### Post by Orcaporka on 2008-04-10
> **Orcaporka said:**
> Im having trouble, I have the Live CD but I think I may have damaged files on one partition as my laptop froze whilst I was changing its size.

Is there some command I can enter into the GRUB command line to restore the recovery option?

Yea now when I try to load Windows on the dual boot it says "Error 13: Invalid or unsupported executable format"

---

### Post by hurtstotalktoyou on 2008-04-10
In that case, you must be very careful.  In order to restore your Windows operating system, you need to make sure your recovery partition is intact.  Installing Ubuntu typically requires screwing around with partitions, which can lead to accidental deletions.  Thus, you're not going to want to do anything until you verify your recovery partition is still working.  You're also probably going to want to back up the partition onto CDs or DVDs or something, so that in the future if you lose it, you can restore it without paying Acer a bunch of money.

To verify your recovery partition is still there, you need a partition manager.  We'll use Gparted, a great tool which is easy to use.  Boot up Ubuntu, run synaptic package manager, and mark "gparted" for installation (I think it asks you to mark something else, too, which you should do).  Then install the marked packages.

Once this is done, open up terminal, and type in "gksudo gparted".  Enter your password when prompted.  This will run gparted.

When gparted is up and running, choose your main hard disk in the device list in the upper right corner of the gparted window (it will be something like /dev/hda).  When you do this, you'll see a bunch of partitions in the main window.  They'll be labelled something like this:

/dev/hda1   ntfs
/dev/hda2   ext3
/dev/hda3   extended
  /dev/hda5   linux-swap

Now, it won't be exactly like I described, but it should be similar.  Go do all that, and then report back here what your dev/hdaX partitions are, as I have done above.

From this we should be able to figure out which is your recovery partition.  Then we can fix grub to boot into it.

IMPORTANT NOTE:  Do not change anything in gparted.  Just use it to see what your partition setup is.  (IE, look but don't touch)

---

### Post by hurtstotalktoyou on 2008-04-10
> **Orcaporka said:**
> Yea now when I try to load Windows on the dual boot it says "Error 13: Invalid or unsupported executable format"

If you fouled up your windows partition, that's fine, as long as your recovery partition is still uncorrupted.  So, cross your fingers.

---

### Post by Orcaporka on 2008-04-10
I have:
/dev/sda1 fat32
/dev/sda2 Unknown
/dev/sda3 Extended
       /dev/sda5 fat32
       /dev/sda6 linux-swap

  /dev/sda4/ ext3

---

### Post by hurtstotalktoyou on 2008-04-10
Hmm.  Okay, that's very helpful, but can you also post the size of each partition?

---

### Post by neurostu on 2008-04-10
If you stopped the partition editor while it was working you could have completely botched up your HDD.  Hopefully like they said above your recovery partition is still there.

---

### Post by Orcaporka on 2008-04-10
> **hurtstotalktoyou said:**
> Hmm.  Okay, that's very helpful, but can you also post the size of each partition?

/dev/sda1 fat32       2.98 GiB
/dev/sda2 Unknown   4.99 GiB
/dev/sda3 Extended   14.18 GiB
/dev/sda5 fat32         1.82GiB
/dev/sda6 linux-swap  211.76 MiB

/dev/sda4/ ext3    3.18GiB

I also have two lots of unallocated space 11.93 GiB and 12.16 GiB.

---

### Post by hurtstotalktoyou on 2008-04-10
Okay.  Your recovery partition is *probably* /dev/sda2.  However, it may also be /dev/sda5.  This is no problem, as we can try either one.

What you want to do next is change your grub bootloader.  Doing this is actually quite simple...

Run terminal, and type in "sudo gedit /boot/grub/menu.lst".  Enter your password when prompted.  This will open your grub boot file in text editor.  Now, look for the partition list near the bottom.  It will read something like this:

> title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=6a6ea0ce-7c6a-4ff4-b7b2-1d9bd2545222 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=6a6ea0ce-7c6a-4ff4-b7b2-1d9bd2545222 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet 

What we're going to do is add two more partitions.  Type them in as follows:

> title partition 2
root (hd0,2)
makeactive
chainloader +1

title partition 5
root (hd0,5)
makeactive
chainloader +1

Please note that the (hd0,2) and (hd0,5) must match the other partitions.  I'm assuming they're all (hd0,X).  However, if they begin with hd1, hd2, etc., then the new partitions need to be (hd1,2) and (hd1,5), or (hd2,2) and (hd2,5).  I'm sure you get the idea.

Please also note that you're adding, not replacing.  Do not delete any text in the grub file; just add more text.

Once this is done, save your grub file and reboot.  Then try your new partitions.  Hopefully, one of them will be your Acer recovery.

---

### Post by Orcaporka on 2008-04-10
> **hurtstotalktoyou said:**
> Okay.  Your recovery partition is *probably* /dev/sda2.  However, it may also be /dev/sda5.  This is no problem, as we can try either one.

What you want to do next is change your grub bootloader.  Doing this is actually quite simple...

Run terminal, and type in "sudo gedit /boot/grub/menu.lst".  Enter your password when prompted.  This will open your grub boot file in text editor.  Now, look for the partition list near the bottom.  It will read something like this:



What we're going to do is add two more partitions.  Type them in as follows:



Please note that the (hd0,2) and (hd0,5) must match the other partitions.  I'm assuming they're all (hd0,X).  However, if they begin with hd1, hd2, etc., then the new partitions need to be (hd1,2) and (hd1,5), or (hd2,2) and (hd2,5).  I'm sure you get the idea.

Please also note that you're adding, not replacing.  Do not delete any text in the grub file; just add more text.

Once this is done, save your grub file and reboot.  Then try your new partitions.  Hopefully, one of them will be your Acer recovery.


with both of them i recieve

"Error 12: Invalid device requested"

---

### Post by hurtstotalktoyou on 2008-04-10
Hmm.  Can you please copy-paste the partition list from /boot/menu/grub.lst for me?  Maybe I can figure out what might be wrong from that data.

Otherwise, don't fret.  There are lots of grub options for booting non-linux partitions.  You may just have to tinker with it until you get the right combo--not an efficient proceedure, I know, but it may be necessary.  You may also want to start another thread in the general help forum asking how to use grub map command to boot into a BIOS-triggered recovery partition.  (I personally won't be able to help much with that end of it.)

---

### Post by Orcaporka on 2008-04-10
here it is:

```

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=95978619-63a5-41e8-83a2-ce170b67257f ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=95978619-63a5-41e8-83a2-ce170b67257f ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

title partition 2
root (hd0,2)
makeactive
chainloader +1

title partition 5
root (hd0,5)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

---

### Post by hurtstotalktoyou on 2008-04-10
EDIT:  Nevermind, you've got ubuntu on hda4.

I've done all I can for you.  Someone else will have to take over.  Your recovery partition is probably on hda2 (hd0,2), but it could also be on hda5 (hd0,5) or (hd0,3).  How to get it to boot is beyond my capabilities.

Good luck!

EDIT2:

Actually, there is one last thing I can suggest: try to rule out hda5 as your recovery partition.  Since it's FAT32, Ubuntu should be able to read it just fine.  Just go into places > computer > 1.82 GB Volume, and see what's in there.

---

### Post by Orcaporka on 2008-04-10
> **hurtstotalktoyou said:**
> Okay, that's very helpful.  It appears you have installed Ubuntu on the 1.82 GB FAT32 partition.  To check this, please go to places > computer in ubuntu.  You *should* see the following, or something like it:



Now, right-click on "filesystem" and choose "preferences".  It will show you a little pie chart, but what we need to note is the following:

1.  what is the "total capacity" given?
2.  what is the "filesystem type" given?

If the total capacity is 1.82 GB, and the filesystem type is FAT32, then that means you can forget about (hd0,5), and focus on getting (hd0,2) to work, because it will mean that (hd0,2) is your recovery partition (or what's left of it).

filesystem type is ext3 and total capacity is 3.1GB

---

### Post by Orcaporka on 2008-04-10
> **hurtstotalktoyou said:**
> EDIT:  Nevermind, you've got ubuntu on hda4.

I've done all I can for you.  Someone else will have to take over.  Your recovery partition is probably on hda2 (hd0,2), but it could also be on hda5 (hd0,5) or (hd0,3).  How to get it to boot is beyond my capabilities.

Good luck!

EDIT2:

Actually, there is one last thing I can suggest: try to rule out hda5 as your recovery partition.  Since it's FAT32, Ubuntu should be able to read it just fine.  Just go into places > computer > 1.82 GB Volume, and see what's in there.


thanks for all your help!

---

### Post by Orcaporka on 2008-04-10
As the recovery is Disk to Disk the sda5 is in fact on the "D" disk, so I am thinking that that is where the restore is?

---

### Post by hurtstotalktoyou on 2008-04-10
> **Orcaporka said:**
> As the recovery is Disk to Disk the sda5 is in fact on the "D" disk, so I am thinking that that is where the restore is?

That makes sense.  Of course, one must wonder what the heck that unknown partition sda2 is.

However, 1.82 GB sda5 could be it.  The problem is, how do you boot into it?

You can make a gparted live cd (get it [here](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-11.iso?modtime=1197927842&big_mirror=0)), then delete your sda4 and sda6 partitions.  However, you must be *very* careful not to erase or delete any partition that might be your recovery partition.  Deleting those other partitions might clear the way for ALT+F10 to work.  Then again, it may do nothing but erase ubuntu.

---

### Post by Orcaporka on 2008-04-10
> **hurtstotalktoyou said:**
> That makes sense.  Of course, one must wonder what the heck that unknown partition sda2 is.

However, 1.82 GB sda5 could be it.  The problem is, how do you boot into it?

You can make a gparted live cd (get it [here](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-11.iso?modtime=1197927842&big_mirror=0)), then delete your sda4 and sda6 partitions.  However, you must be *very* careful not to erase or delete any partition that might be your recovery partition.  Deleting those other partitions might clear the way for ALT+F10 to work.  Then again, it may do nothing but erase ubuntu.

yea all I can find is using a winddows cd, which is pretty pointless with what I am trying to do.

---

### Post by Orcaporka on 2008-04-10
> **hurtstotalktoyou said:**
> That makes sense.  Of course, one must wonder what the heck that unknown partition sda2 is.

However, 1.82 GB sda5 could be it.  The problem is, how do you boot into it?

You can make a gparted live cd (get it [here](http://downloads.sourceforge.net/gparted/gparted-livecd-0.3.4-11.iso?modtime=1197927842&big_mirror=0)), then delete your sda4 and sda6 partitions.  However, you must be *very* careful not to erase or delete any partition that might be your recovery partition.  Deleting those other partitions might clear the way for ALT+F10 to work.  Then again, it may do nothing but erase ubuntu.


I have have found something called "ultimate boot cd" which might help be specifically choose where I boot from. If so That might work if not Im going to delete ext3(Ubuntu) and hope it clears the way for D2D recover.

---

