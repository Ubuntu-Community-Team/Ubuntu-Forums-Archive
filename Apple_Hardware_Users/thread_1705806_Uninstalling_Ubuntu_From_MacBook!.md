---
title: "Uninstalling Ubuntu From MacBook!"
date: 2011-03-12
forum: Apple Hardware Users
---

### Post by freesparks on 2011-03-12
[LEFT]Hello all,

    I have a MacBook Pro and these are the specs:

  Model Name:    MacBook Pro
  Model Identifier:    MacBookPro5,2
  Processor Name:    Intel Core 2 Duo
  Processor Speed:    3.06 GHz
  Number Of Processors:    1
  Total Number Of Cores:    2
  L2 Cache:    6 MB
  Memory:    4 GB
  Bus Speed:    1.07 GHz

I wish I could keep Ubuntu 10.10 installed on it, however because I am using this machine more and more for work and graphics that require specific mainstream software, I will have to uninstall Ubuntu because of limited disk space.  Can anyone tell me how to properly uninstall Ubuntu from my Mac? I am using this machine for a lot of work so I can't afford any down time.  If anyone can advise me on step by step procedures to take to ensure a safe uninstall, that would be greatly appreciated.

Best Regards,

freesparks

[/LEFT]

---

### Post by freesparks on 2011-04-21
Hello Everyone,

    Is there anyone that can help me with this?  I see the Linux Partitions when I launch Disk Utility while booted inside Mac OSX,  I just want to know if it is safe to delete the partitions or if there is something that I need to do on Linux side prior.  Any help on this would be greatly appreciated.  Thanks in advance!!

Best Regards,

freesparks

---

### Post by handy on 2011-04-25
You could boot with a Ubuntu LiveCD, then call GParted & delete the old Ubuntu partitions after which you could then create a new HFS+ partition.

Unfortunately GParted can't expand the existing HFS+ partition.

Another tip: When using GParted (or any other partition tool on any operating system) commit to & do each action one at a time i.e. each command such as deleting a partition, creating a partition, expanding a partition - when available - will be pending until you "Apply" it. Don't chain any of these commands. The most reliable way to do this serious business is to implement each command one at a time.

Here is something else that you may find useful, I know I did:

[http://www.danrodney.com/mac/](http://www.danrodney.com/mac/)

[http://hints.macworld.com/article.php?story=20060619181010389](http://hints.macworld.com/article.php?story=20060619181010389)

---

### Post by freesparks on 2011-07-14
Hello Handy,

    I can't thank you enough for you reply.  I ran:

```
sudo fdisk -l
```and I got this as a result while booted in the Live CD as you suggested:

u```
buntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 121.3 GB, 121332826112 bytes
255 heads, 63 sectors/track, 14751 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00006011

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       11088    88856304   af  HFS / HFS+
/dev/sda3           11088       11088         977    0  Empty
/dev/sda4           11088       14595    28166992+  83  Linux
```Graphically, this is what I see when I launch GParted:

Partition           File System                                 Size                                        Used

/dev/sda1        fat32 --EFI                                200.00  Mib                             18.12  Mib                boot
/dev/sda2        hfs+ --Macintosh HD                84.74    Gib                             73.38  Gib                              
/dev/sda3        unknown(this is Grub)              977      Kib                                  ------                 bios Grub
/dev/sda4        ext4                                           26.86   Gib                              18.42 Gib                            
/dev/sda5        linux-swap                                 1.20     Gib                                -------            

As you can see, I have only 12 Gib left on my Mac partition, and as I have Linux on 2 other laptops, there really isn't a reason to have this on this Mac.

All I need to know is if I am deleting?

/dev/sda1------or is the EFI A Mac partition?
/dev/sda3 -----I see this is the Grub-----so I can delete this?
/dev/sda4 -----is the main Linux partition----so I can delete this?
/dev/sda5 is my ------is my swap, so I can delete this?

I also need to know in what order specifically am i deleting these partitions.  I see this is just a matter of going to the partition and right-clicking on it and selecting delete, an then what?

I just want to make sure i do this correctly so that I don't mess up my system.  Any help would be greatly appreciated.

Best Regards,

freesparks

---

### Post by srs5694 on 2011-07-14
Freesparks,

Using a Linux emergency CD or the OS X Disk Utility, go ahead and delete /dev/sda3, /dev/sda4, and /dev/sda5. *Do not* delete /dev/sda1 (your EFI System Partition) or /dev/sda2 (your OS X installation). You can either expand /dev/sda2 with Disk Utility or create a new partition in place of the Linux partitions. The latter is slightly safer; resizing partitions is always risky, although expanding them from their ends is safer than most other resizing operations.

---

### Post by freesparks on 2011-07-17
Thank you so much srs5694,

     I deleted all of the Linux partitions and now booted into OSX, but did not see the 30GB of free space that was created as a result of deleting those partitions.  I tried to format this in Linux using Gparted as Unformatted, but when I rebooted into Max OSX I tried to format the partition as an Extended Journaled to no avail.  What is the procedure to this properly in OSX, you seem to know given the fact that you mentioned disk utility.  All I want to do is to combine the 30 GB of free space with my MacPartition.  I see in Gparted that there is a hfs+ partition but it is greyed out and can not be selected.

    And, when I try and resort to resolving this in Disk Utility I get an error:
Secure Erase Free Space Failed!
A Disk With A mount point is required.

Any help would be greatly appreciated.

Best Regards,

freesparks

---

### Post by srs5694 on 2011-07-18
You shouldn't need to use the "secure erase" feature of Disk Utility; just create a partition and a filesystem. (I don't recall the exact click-by-click directions for doing this, though.)

Alternatively, you can use GParted in Ubuntu; however, you may need to install an HFS support package. I don't recall the exact name, but it's probably hfsprogs, hfsutils, or something similar.

---

### Post by life in color on 2011-07-18
Limited Disk Space? try working with a 100GB Hard Drive lol New Hard Drives are REALLY cheap you should definitely keep Ubuntu and just either get an external Hard Drive or replace your internal Hard Drive
[http://www.bestbuy.com/site/Western+Digital+-+My+Passport+Essential+SE+1TB+External+USB+3.0/2.0+Portable+Hard+Drive+-+Blue/1261484.p?id=1218244144929&skuId=1261484&cmp=RMX&ref=06&loc=01&ci_src=14110944&ci_sku=1261484]("http://www.bestbuy.com/site/Western+Digital+-+My+Passport+Essential+SE+1TB+External+USB+3.0/2.0+Portable+Hard+Drive+-+Blue/1261484.p?id=1218244144929&skuId=1261484&cmp=RMX&ref=06&loc=01&ci_src=14110944&ci_sku=1261484")[http://www.macconnection.com/IPA/Shop/Product/Detail.htm?sku=11074902&cm_mmc=Base-_-11074902-_-New-_-AN-17&ci_src=14110944&ci_sku=11074902]("http://www.macconnection.com/IPA/Shop/Product/Detail.htm?sku=11074902&cm_mmc=Base-_-11074902-_-New-_-AN-17&ci_src=14110944&ci_sku=11074902")

---

### Post by conundrumx on 2011-07-18
Stop using GParted to manipulate HFS+ partitions.

If you've deleted the linux partitions you should be able to use Disk Utility to manipulate your free space and HFS+ partition.  What do you see when you select your hard drive in Disk Utility?

---

### Post by freesparks on 2011-07-18
Hello Conundrumx,

     When I boot up with my mac and use disk Utility, I see:

disk03


Mount Point: Not Mounted
MS-Dos(FAT
Capacity 30GB

     When I try to repair the disk I get the error:

Volume Erase failed:
Volume Erase failed with the error:

POSIX reports:  The operation couldn't be completed.  Resource Busy.

     Thanks so much for the outpouring of responses, I'm learning tons.  As far as getting another hard drive, I have Ubuntu installed on 3 machines' internal drives partitioned with Windows, 1 Machine partitioned with Mac OSX, and 2 external drives that have Ubuntu installed on them that I can boot from----,,the Mac is a solid state drive, so they are expensive.  I love all things Linux and am passionate about learning it.  It's just, i'm not aloud to have separate partitions on drives where I work, and the powers that be think I'm doing something clandestine, little do they know, I've had so many instances where either my Mac or Windows machine were not operable but I was able to boot up just fine with Ubuntu.

    It never seizes to amaze me.

Best Regards,

freesparks

---

### Post by conundrumx on 2011-07-19
Select the partition in question and hit the "eject" button.  Then click on the disk itself (the drive name will be the capacity of the disk, for example "500 GB....") and select the Partition tab.  You should be able to select the 30gb partition and hit the minus symbol below to delete it.  You can then drag to resize the HFS+ partition being used by OS X.

---

### Post by jerrycal on 2011-07-21
You can also use Disk Utility from your OSX Install disk.

Boot from the disk, go through the first step of choosing your language as if you were to reinstall system (don't worry, you won't be doing that, hopefully) and then on top you'll see menu that will take you to Disk Utility. 
This guide will give you an idea: [http://kb.wisc.edu/helpdesk/page.php?id=3810](http://kb.wisc.edu/helpdesk/page.php?id=3810)

P.S. Secure Erase Free Space is for something else. It's to remove files that were "deleted" and are now in "Free Space" of the drive, so that function is to make them unrecoverable.

---

