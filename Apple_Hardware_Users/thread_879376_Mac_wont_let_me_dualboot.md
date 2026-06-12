---
title: "Mac wont let me dualboot?"
date: 2008-08-03
forum: Apple Hardware Users
---

### Post by leo2791 on 2008-08-03
The following is a very long post, and i apologize in advance, but i am new to this operating system, and do not know what i did wrong, so it would help the most, i reasoned, if i told you folks everything

I just installed Ubuntu on my macbook, I successfully went through the ubuntu installer with a friend's help. He had me partition the 10 gigs of space i had left for Ubuntu into two parts. 9 gigs for ubuntu itself, and one gig for the swap (or whatever it's actually called). But, as I realized later, I may not have set a mount point for the mac partition of my hard drive. This may even be the cause of my biggest problem, which follows.

I futzed around in ubuntu, couldn't get wireless ( an issue, but not my biggest), then restarted my macbook to tell him that i had got it working, and even though i held down the alt/option key, i was automatically booted into linux, so i restarted again, this time managed to get into OS X, then restarted again, to try and get wireless in ubuntu ( i held  down the alt key, of course, ) but when i got to the menu that used to offer where to start the computer from (and hence, which OS to load), i was unpleasantly surprised. the only choice my computer gave me was the mac portion of my hard drive. 

I restarted my macbook several more times, all the while holding my alt key, but with no improvement

I finally gave up my tactic and logged into OS X to look at my hard drive. Disk Utilities told me that there were the three portions i had expected (mac, ubuntu, and swap) but that there was another partition, a third of a gig, and that there was an amount of free space that was, coincident or not, equal to the amount that was taken up by the Ubuntu portion of my hard drive.

I called my friend, he said it had to do with the mac boot code, and that i would probably have to rewrite parts of it, he also said that i should ask the mac-ubuntu forums for help. 

I would appreciate any help, thanks in advance.

---

### Post by kdb424 on 2008-08-03
Make it one big partition. Reinstall Ubuntu, and set the mount point to the Ubuntu partition. No swap this time. Install Grub to the Ubuntu Partition, and make sure you get rEFIt. Works every time.

---

### Post by trash on 2008-08-03
I think this used to happen to me, reset the pram let it chime at least 3 times... i think it's ctrl+alt+p+r at boot

---

### Post by leo2791 on 2008-08-04
kdb424: make the ubuntu, the swap, and the lil partition into one or those 3 and my mac?

trash: what does all that mean? sorry, im totally new here

---

### Post by trash on 2008-08-04
Hold all 4 of theose keys down at boot and hold til it chimes at least 3 time... you're basically clearing out the ram of possibly bad data, but now that i think about it i think i did this for another issue... anyway reseting the pram is in no way a bad thing to do.
while in Ubuntu try 

sudo ybin

which will rewrite the boot file... i think.

---

### Post by kdb424 on 2008-08-04
> **leo2791 said:**
> kdb424: make the ubuntu, the swap, and the lil partition into one or those 3 and my mac?

What? Ubuntu works fine on Mac's with no swap partition in most cases is what I was saying.

---

### Post by cyberdork33 on 2008-08-04
> **kdb424 said:**
> What? Ubuntu works fine on Mac's with no swap partition in most cases is what I was saying.
I wouldn't just tell people to remove their swap, especially since it is not going to fix his problem. Swap is useful for some things. Just because it _can_ work without swap doesn't mean you should.

**To the OP:**
Boot into OSX and install rEFIt.
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Reboot and you should get a nice boot screen. on the bottom row there is an icon for the partition tool. Select it and it will likely say it needs to sync the partition tables. Do it.

After that, see if you can boot into both OS X and Ubuntu, and if not, post back, as you will likely need to, reinstall GRUB.

---

### Post by leo2791 on 2008-08-04
installed rEFIt, ran partition inspector, it says this:

*** Report for internal hard disk ***

Current GPT partition table:
 No GPT partition table present!

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1                      63    213732334   af  Mac OS X HFS+
 2      213732351    214404225  83  Linux
 3      232476615    234436544  82  Linux swap / Solaris
 4      214419555    232476614  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 63:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in MBR as partition 1, type af  Mac OS X HFS+

Partition at LBA 213732351:
 Boot Code: None
 File System: ext2
 Listed in MBR as partition 2, type 83  Linux

Partition at LBA 232476615:
 Boot Code: None
 File System: Unknown
 Listed in MBR as partition 3, type 82  Linux swap / Solaris

Partition at LBA 214419555:
 Boot Code: None
 File System: ext3
 Listed in MBR as partition 4, type 83  Linux



restarted my comp (not holding any buttons), got standard mac login page

---

### Post by cyberdork33 on 2008-08-04
> **leo2791 said:**
> Current GPT partition table:
 No GPT partition table present!
Well that is bad. can you boot from the Ubuntu LiveCD and run the command:
```
sudo parted /dev/sda print
```and
```
sudo fdisk -l /dev/sda
```

> **leo2791 said:**
> restarted my comp (not holding any buttons), got standard mac login page
please see the refit install instructions. you need to run the install script so that the menu will work on reboot. [http://refit.sourceforge.net/doc/c1s1_install.html](http://refit.sourceforge.net/doc/c1s1_install.html)

---

### Post by leo2791 on 2008-08-05
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  109GB  109GB   primary  hfs+              
 2      109GB   110GB  344MB   primary  ext2              
 4      110GB   119GB  9245MB  primary  ext3              
 3      119GB   120GB  1003MB  primary  linux-swap        


                                                                          
Information: Don't forget to update /etc/fstab, if necessary.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009cada

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13305   106866136   af  Unknown
/dev/sda2           13305       13347      335937+  83  Linux
/dev/sda3           14472       14593      979965   82  Linux swap / Solaris
/dev/sda4           13348       14471     9028530   83  Linux

Partition table entries are not in disk order

---

### Post by cyberdork33 on 2008-08-05
Well for some reason your GPT is gone, you only have a legacy partition table now. You do in fact have two linux partitions and a swap. The sda2 has an ext2 filesystem and is ~350MB, and sda4 is ext3 and is > 9GB. I don't know what you did to get into this situation, but I think your best option is to backup anything important in OSX and start with a fresh OS X install after completely erasing the disk first.

You can operate like it is now, but firmware updates will not go through anymore because you do not have an EFI partition. Try blessing refit (by running the enable.sh script) and hopefully rEFIt will function. If you still can't boot your Ubuntu partition from there, then you likely need to reinstall GRUB.

---

### Post by Slinky.Weasel on 2008-08-05
hello i was unable to dualboot even while holding the alt key on boot all that showed up was the mac installation so i installed rEFIt and rebooted and it still didnt work here is my partition info


*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    283263015  Mac OS X HFS+
 3      283263016    386778641  Basic Data
 4      386778642    390720048  Linux Swap

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    390721967  ee  EFI Protective

MBR contents:
 Boot Code: GRUB

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 283263016:
 Boot Code: None
 File System: ext3
 Listed in GPT as partition 3, type Basic Data

Partition at LBA 386778642:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap

---

### Post by cyberdork33 on 2008-08-05
> **Slinky.Weasel said:**
> hello i was unable to dualboot even while holding the alt key on boot all that showed up was the mac installation so i installed rEFIt and rebooted and it still didnt work here is my partition info
you have to sync the partitions too... this is is in the partition tool in the refit menu at startup.

---

### Post by Slinky.Weasel on 2008-08-05
Ok did that and selected the linux install and it said no bootable device - insert system disk to continue.  I inserted my linux disc and nothing happened for 3 minutes so I pressed some keys to see if that did anything and it didn't so i rebooted and reinstalled ubuntu and got the same problem.

---

### Post by cyberdork33 on 2008-08-05
> **Slinky.Weasel said:**
> Ok did that and selected the linux install and it said no bootable device - insert system disk to continue.  I inserted my linux disc and nothing happened for 3 minutes so I pressed some keys to see if that did anything and it didn't so i rebooted and reinstalled ubuntu and got the same problem.
the exact problem you are describing means that your partitions are not synced up.

Please do not come into an existing thread with a separate problem. This issue has been covered quite a bit in the forum, including a link in the FAQ.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by leo2791 on 2008-08-06
Okay, different problem: i boot OSX off of my backup drive, so i can partition my main drive, but Disk Utilities fails at partitioning, claiming "could not unmount disk".

I had no other apps or windows open, and i was booting off a different drive, what gives?

---

