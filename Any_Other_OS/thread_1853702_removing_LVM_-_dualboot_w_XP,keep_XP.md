---
title: "removing LVM - dualboot w/ XP,keep XP"
date: 2011-10-02
forum: Any Other OS
---

### Post by bachor on 2011-10-02
im trying to remove encrypted LVM partition I made via Alternate Kubuntu 10.

Dual boot w/ XP - need to keep XP.

Was browsing for hours and ended up helpless in here: [running LiveCD Mint 11]

```
mint@mint ~ $ sudo apt-get install lvm2 cryptsetup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cryptsetup is already the newest version.
lvm2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 225 not upgraded.
mint@mint ~ $ sudo modprobe dm-crypt
mint@mint ~ $ sudo cryptsetup luksOpen /dev/sda4 crypt1
Enter passphrase for /dev/sda4: 
mint@mint ~ $ sudo vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  No volume groups found
  No volume groups found

```I'd like to install Mint without encrypting it, and keep XP.

---

### Post by WasMeHere on 2011-10-03
Be careful and backup a cloned image of the disk at first! I like *Clonezilla* for this purpose.

During a live session, try *Gparted* (included in Ubuntu live and Mint live)! If you can see the partition, you should also be able to remove/delete it. By the way, Gparted is a good tool to do the partitioning task before you install the system. I suggest that you make your swap partition twice the ram-size.

Good luck
Olle

---

### Post by bachor on 2011-10-03
[SIZE=3]Olle,

 I erased all partitions inside LVM, don't need them.

 Gparted doesn't see it [because of LVM]. 

 fdisk won't do it either. 

 I even have tried Partition Magic on XP, which even doesn't want to start because of that LVM.

 I really don't want to Dban whole HDD and redo whole thing ](*,) [/SIZE]

---

### Post by WasMeHere on 2011-10-03
Ok, so use can view the lvm system using live mint session, but gparted doesn't see it in that same session. That's a tough one for me too. **Let's hope an lvm expert will get engaged in this thread**, but in the meantime, maybe we can look at different possibilities.

If you have a spare hard disk, maybe you could clone your. If Clonezilla can't do it I think you can do it using
```
sudo dd if=/dev/sda of=/dev/sd[COLOR="Red"]x[/COLOR] bs=4096
``` where [COLOR="Red"]x[/COLOR] is substituted to whatever suits the spare hard disk.

Test if you can boot from xp on the clone! If that is the case you can relax, and do some daring things to the original drive.

Is this correct:
- you want to keep the lvm system with xp and make the space occupied by the encrypted partition free to use for mint.
- but you cannot delete the encrypted partition.

Or would you be happy to get rid of the lvm system if you could extract xp out of it? By the way, how much time have you invested into the xp system?

---

### Post by Perfect Storm on 2011-10-03
Moved to Other OS/Distro Talk.

---

### Post by bachor on 2011-10-03
> **Olle Wiklund said:**
> Ok, so use can view the lvm system using live mint session, but gparted doesn't see it in that same session. That's a tough one for me too. **Let's hope an lvm expert will get engaged in this thread**, but in the meantime, maybe we can look at different possibilities.

If you have a spare hard disk, maybe you could clone your. If Clonezilla can't do it I think you can do it using
```
sudo dd if=/dev/sda of=/dev/sd[COLOR=Red]x[/COLOR] bs=4096
``` where [COLOR=Red]x[/COLOR] is substituted to whatever suits the spare hard disk.


Test if you can boot from xp on the clone! If that is the case you can relax, and do some daring things to the original drive.

Is this correct:
- you want to keep the lvm system with xp and make the space occupied by the encrypted partition free to use for mint.
- but you cannot delete the encrypted partition.


Or would you be happy to get rid of the lvm system if you could extract xp out of it? By the way, how much time have you invested into the xp system?


No that is not correct. I don't want to keep LVM system, but I want to keep XP intact.

I don't have a spare disk [this is a Laptop btw.]. 

And I use XP only for my photography, it's not good on anything else :D

I do have an external HDD, if that would help.

Thanks for trying.

---

### Post by WasMeHere on 2011-10-03
Short answer now. (I'll be back later)

Do you really need xp for photography? I think there are many good tools in ubuntu. *I use digikam, gimp, feh and imagemagic*k. I think you can find a lot of information and inspiration browsing this forum.

---

### Post by bachor on 2011-10-03
> **Olle Wiklund said:**
> Short answer now. (I'll be back later)

Do you really need xp for photography? I think there are many good tools in ubuntu. *I use digikam, gimp, feh and imagemagic*k. I think you can find a lot of information and inspiration browsing this forum.

I use Nikon's NX2 and ViewNX2 and I'm kinda used to. What is it you use for RAW in sRGB? I've used Gimp in emergencies before,took me a while to figure things out.

I love NX2 thou.

---

### Post by WasMeHere on 2011-10-03
Just wanted to check that: I agree that you install dual boot with winxp. So let us get some information to decide which would be the best way to get what you want:

Assuming xp inside the lvm:
- How much work would it be to save your private files (documents and media files (pictures, music, videos)) and reinstall xp? (chance to succeed 100%)
- How much work would it be to clone xp and move it out of the lvm? (chance to succeed ???)

Unless you get qualified help from an lvm expert, we can only guess the chance to succeed, maybe 50% or less.
--
Using dd would create a big file, probably bigger than 4GB, which is the limit in a common filesystem of external HDDs, FAT32. If that is the filesystem of your external HDD, you would have to reformat it to NTFS or some linux filesystem for example ext3. But if you keep backup data there, it's a bad idea.
--
What about saving the private files and reinstalling the operating system?

---

### Post by bachor on 2011-10-03
> **Olle Wiklund said:**
> Just wanted to check that: I agree that you install dual boot with winxp. So let us get some information to decide which would be the best way to get what you want:

Assuming xp inside the lvm:
- How much work would it be to save your private files (documents and media files (pictures, music, videos)) and reinstall xp? (chance to succeed 100%)
- How much work would it be to clone xp and move it out of the lvm? (chance to succeed ???)

Unless you get qualified help from an lvm expert, we can only guess the chance to succeed, maybe 50% or less.
--
Using dd would create a big file, probably bigger than 4GB, which is the limit in a common filesystem of external HDDs, FAT32. If that is the filesystem of your external HDD, you would have to reformat it to NTFS or some linux filesystem for example ext3. But if you keep backup data there, it's a bad idea.
--
What about saving the private files and reinstalling the operating system?

XP is not in LVM. In LVM is only Kubuntu with Swap and /home [which I erased already].

I just want to get rid of that LVM drive or partition or system or whatever it's called so I can install un-encrypted Mint without touching on XP system [which I don't want to waste any of my time [-( ].

:D

---

### Post by bachor on 2011-10-03
I just thought it would be faster just to get rid of that whole LVM stuff. Like fdisk or something. Guess not. 

Every howto I found on LVM explains all in excelent details, but how to get rid of it none #-o

---

### Post by jmcvey on 2011-10-03
Bachor..

Saw this and have an idea or two. It's been a while since I messed with LVM. Sounds like you just want to get rid of the partition that LVM is using. If that's the case, and you can boot via a "live" linux disc, then running fdisk should work. If you run fdisk and have it display all the partitions it sees on the disc you should have one with a partition type of "8e". I believe that's the ID for LVM. From fdisk you should then be able to see which partition that one is and tell it to delete that partition. That will remove the LVM partition and whatever was inside it from your disc.

Jer

---

### Post by WasMeHere on 2011-10-04
Well, that sounds nice. Then I think you can make an image of your disk to your external disk, and then try to get rid of everything except your xp partition. Don-t go ahead now! I'll come back later with details how to make the image.

---

### Post by WasMeHere on 2011-10-04
Hello again *bachor*,

*1. Backup before doing potentially dangerous work on your hard disk.*

Since the xp partition is outside of the lvm I suggest that you make an image of it using Clonezilla (a free live CD or USB system). Do not make an image of the whole disk, because that would
- waste space on your external disk
- make it more difficult to restore  xp, if you would need that after you install ubuntu.

*2. I'm glad [I]jmcvey* posted. So try what he suggests: fdisk[/I]

If I understand his text, you could boot with almost any live linux disk, they should all have fdisk, and you need no lvm software.

Read the manual of fdisk ```
man fdisk
``` List your partitions and disks with ```
sudo fdisk -lu
``` and identify which partition to delete. Then make sure that **no** partition of the harddisk is mounted! Start the interactive mode with

```
sudo fdisk /dev/sd[COLOR="Red"]a[/COLOR]
...
command (m for help): c
command (m for help): u
command (m for help): m
command (m for help): p     (show partition table)
command (m for help): [COLOR="Red"]d[/COLOR]     (and perform the critial operation, delete the partition containing LVM)
command (m for help): q     (quit if you are not sure)
command (m for help): w     (write if you are confident)
``` The red letter [COLOR="Red"]a[/COLOR] should represent the disk that you are going modify (typically sd[COLOR="Red"]a[/COLOR] for the first sata disk)

Good luck and let us know the result :-)
Olle

---

### Post by bachor on 2011-10-04
> **jmcvey said:**
> Bachor..

Saw this and have an idea or two. It's been a while since I messed with LVM. Sounds like you just want to get rid of the partition that LVM is using. If that's the case, and you can boot via a "live" linux disc, then running fdisk should work. If you run fdisk and have it display all the partitions it sees on the disc you should have one with a partition type of "8e". I believe that's the ID for LVM. From fdisk you should then be able to see which partition that one is and tell it to delete that partition. That will remove the LVM partition and whatever was inside it from your disc.

Jer

 Yes, I just want to get rid of LVM. Which fdisk command should I use? Bellow is fdisk -lu

> **Olle Wiklund said:**
> Hello again *bachor*,

*1. Backup before doing potentially dangerous work on your hard disk.*

Since the xp partition is outside of the lvm I suggest that you make an image of it using Clonezilla (a free live CD or USB system). Do not make an image of the whole disk, because that would
- waste space on your external disk
- make it more difficult to restore  xp, if you would need that after you install ubuntu.

*2. I'm glad [I]jmcvey* posted. So try what he suggests: fdisk[/I]

If I understand his text, you could boot with almost any live linux disk, they should all have fdisk, and you need no lvm software.

Read the manual of fdisk ```
man fdisk
``` List your partitions and disks with ```
sudo fdisk -lu
``` and identify which partition to delete. Then make sure that **no** partition of the harddisk is mounted! Start the interactive mode with

```
sudo fdisk /dev/sd[COLOR=Red]a[/COLOR]
...
command (m for help): c
command (m for help): u
command (m for help): m
command (m for help): p     (show partition table)
command (m for help): [COLOR=Red]d[/COLOR]     (and perform the critial operation, delete the partition containing LVM)
command (m for help): q     (quit if you are not sure)
command (m for help): w     (write if you are confident)
``` The red letter [COLOR=Red]a[/COLOR] should represent the disk that you are going modify (typically sd[COLOR=Red]a[/COLOR] for the first sata disk)

Good luck and let us know the result :-)
Olle

```
mint@mint ~ $ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd18ed18e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    29382884    14691411    7  HPFS/NTFS
/dev/sda2        29384704   175879619    73247458    b  W95 FAT32
/dev/sda3   *   175867904   176259071      195584   83  Linux
/dev/sda4       176259072   234440703    29090816   83  Linux

Disk /dev/sdb: 8061 MB, 8061451776 bytes
248 heads, 62 sectors/track, 1023 cylinders, total 15745023 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061c62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              62    15545135     7772537   83  Linux
/dev/sdb2        15545136    15729647       92256   83  Linux
Partition 2 has different physical/logical endings:
     phys=(1023, 247, 62) logical=(1022, 247, 62)

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c88d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   154263551    77130752    b  W95 FAT32
/dev/sdd2       154263552   234440703    40088576    5  Extended
/dev/sdd5       154265600   234440703    40087552   83  Linux

```SDA3 is Grub I believe
SDA4 is Kubuntu

SDB is Mint LIVE i'm on now

SDD is extrenal HDD where I made FAT32 and EXT4

I made Clonezilla USB LIVE on other USB device.

Have to make backUp before I start cloning,and before I follow this great [step-by-step]("http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image") from Clonezilla.

Which partition should I save it to? EXT4? Does it matter? will be back tomorrow.

Thank you all for helping.

Btw, which fdisk command should I use to get rod if that LVM?  fdisk sda4 didn't work

---

### Post by WasMeHere on 2011-10-05
Clonezilla makes 2GB chunks of the image, so it's OK to save it on FAT, but it might be faster to use ext4. 

Make sure that no partition of the harddisk is mounted! Do 'fdisk' , not 'fpartition'. Start the **interactive mode** with

**sudo fdisk /dev/sda**
...
command (m for help): c
command (m for help): u
command (m for help): m
command (m for help): p     (show partition table)
command (m for help): d     (and perform the critial operation, delete the partition containing LVM)
command (m for help): q     (quit if you are not sure)
command (m for help): w     (write if you are confident)

After pressing **d** you can expect to be prompted to select the partition. Does it feel scary?

---

### Post by bachor on 2011-10-05
Thanx Olle for helping,I choosed 4th partition LVM and first time P option didn't show it,next time it is still there. That is some hard-to-remove-it stuff I'll tell you, I think it is great for security reason for sure. But not when real "owner" needs to remove it :) 

```
mint@mint ~ $ sudo fdisk /dev/sda

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): d
Partition number (1-4): 4

Command (m for help): p

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd18ed18e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1829    14691411    7  HPFS/NTFS
/dev/sda2            1830       10948    73247458    b  W95 FAT32
/dev/sda3   *       10948       10972      195584   83  Linux

Command (m for help): q

mint@mint ~ $ sudo fdisk /dev/sda

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd18ed18e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1829    14691411    7  HPFS/NTFS
/dev/sda2            1830       10948    73247458    b  W95 FAT32
/dev/sda3   *       10948       10972      195584   83  Linux
/dev/sda4           10972       14594    29090816   83  Linux

``` even Disk Utility doesn't see it changed,GParted still "unallocated".

I think if i DBAN it and reinstall XP quickly w/ no updates [just for NX2] it would be faster ](*,)  :biggrin:

---

### Post by WasMeHere on 2011-10-05
I think you are close now :-) But you have to type [COLOR="RoyalBlue"]w[/COLOR], because fdisk does not do anything with the partition table before exit. You exited with q which means quit without writing. So dare to use

```
[COLOR="RoyalBlue"]w[/COLOR]     write table to disk and exit
```

---

### Post by bachor on 2011-10-06
:lolflag:   no comment here,maybe => RTFM!  right? :-)

 Thank You Olle! It worked, of course :-) Let see if I can install Mint on it. 

 Thank You for your time,

 Pavel

---

### Post by WasMeHere on 2011-10-06
You are welcome, it's a pleasure to help people who really try :-)
Olle

---

### Post by bachor on 2011-10-06
Thanks again Olle,  I'm bit surprised nobody try to help me before this thread got moved in here. Especially it was so easy. Maybe that's why :)

I was surprised how easier it was to install Mint. I've tried without preparing partition and it even found XP. wow

 Have a great day and  ):P

 Learning every day :P

SOLVED

---

