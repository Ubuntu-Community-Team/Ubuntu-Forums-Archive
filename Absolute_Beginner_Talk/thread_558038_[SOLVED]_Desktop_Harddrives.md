---
title: "[SOLVED] Desktop Harddrives"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2007-09-23
So I have these three harddrives on my desktop that won't go away.  I used to have six, until I followed the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=531366](http://ubuntuforums.org/showthread.php?t=531366).  That removed the mounted drives, but now I have three that read: "59GB FAT32(LBA) Volume (sdb1)" (that's the windows half of my external drive, where Linux is installed), "195GB NTFS Volume (sda3)" (that's the main Vista drive, internal) and "10GB NTFS Volume (sda2)" (which is Dell's rescue partition of the main drive).

The three drives that disappeared were the mounted counterparts of the three drives mentioned above: "Lacie" (the proper name of "[sdb1]"), "OS" (the name of "[sda3]") and "Recovery" (again, the proper name of "[sda2]"). 

Now, I think the reason these drives are displayed is that when I right-click on any of them and bring up "Properties" the location displayed for them is "/home/michael/Desktop" (my name is michael, and, as such, so is my login name).  Why is this?  Can it be changed?

-Mike

---

### Post by logos34 on 2007-09-23
Post your fdisk and fstab:

**sudo fdisk -l** (lowercase L)

**cat /etc/fstab**

---

### Post by mikeserv on 2007-09-23
sudo fdisk -l:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       25628   195312500    7  HPFS/NTFS

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7390    59360143+   c  W95 FAT32 (LBA)
/dev/sdb2   *        7391        9896    20129445   83  Linux
/dev/sdb3            9897       10011      923737+   5  Extended
/dev/sdb5            9897       10011      923706   82  Linux swap / Solaris

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=eb2c5d78-45c0-45d1-9e5f-bba285eb8ef1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=0e5680ac-f586-43e9-a811-ff9f88b2144b none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0


Oh, and thanks for trying to help me.

---

### Post by logos34 on 2007-09-23
They should mount in /media, not /home/user dir.

There's no need to mount the recovery partition.

Edit fstab to include vista and sdb1:

**gksudo gedit /etc/fstab**

add these lines:
> 
/dev/sda3 /media/vista ntfs defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sdb1 /media/fat32 vfat defaults,umask=0000 0 0

then make the mount points:
[B]
sudo mkdir /media/vista
sudo mkdir /media/fat32[/B]
[B]
sudo mount -a[/B]

---

### Post by mikeserv on 2007-09-23
Uhhh...   No change, really...

After the edit:

sudo mount -a
mount: /dev/sda3 already mounted or /media/vista busy
mount: according to mtab, /dev/sda3 is mounted on /media/sda3

I'm thinking that those drives were already mounted (I can see them under "/media" as "sda3," "sda2" and "sdb1").  And when I check "volumes-visible" in gconf-editor I see them as "LACIE," "OS" and "RECOVERY" (by the way, I agree with you about mounting/unmounting "RECOVERY," but when I right-click the drive and select "Unmount Volume" I get the error "Cannot Unmount Volume" details "Cannot open /media/.hal-mtab").  But for some reason the other three, the three that won't go away ARE the same drives!  SDB1 = LACIE, SDA3 = OS and SDA2 = RECOVERY.

Why would they display twice?  And why would only half of them go away?  And why can't I unmount RECOVERY?

Again, thanks for helping.

-Mike

(P.S.  In case you can't tell, I only installed Linux a few days ago.  On Friday I wouldn't have known what you mean by "sudo fdisk -l (lowercase L); cat /etc/fstab")

---

### Post by mikeserv on 2007-09-23
I'm not sure if this is relevant, but it strikes me as odd that when I right-click on one of the three drives that won't go away and select "Properties" I see that their "MIME type"s all read "application/x-desktop."  But when I right-click on one of the three that does go away and select "Properties" it doesn't even have a MIME-type.  It just says "Volume:  RECOVERY".  Something else I noticed is that in the properties menu the three that will go away have 6 tabs: "Basic, Emblems, Permissions, Notes, Drive, and Volume"; while the three that won't go away only list the first four of those.

-Mike

---

### Post by mikeserv on 2007-09-23
Woah...  Update:

I guess I should have rebooted after following your advice in the first place, because I just did and the two drives that you told me change in that fstab file are gone!  Well, at least they're off the desktop and relegated to their respective /media locations.  But the Dell RECOVERY drive is still there.  Is there a way to edit that file to tell it specifically NOT to mount the drive?

-Mike

---

### Post by logos34 on 2007-09-23
'lacie', 'OS' and recovery are the volume labels of those partitions.  If you've disabled 'volumes visible' or whatever in gconf then I'm not sure what you're asking.  They're apparently already mounting in /media. (although I don;t know why sda3 in particular is automounting without fstab entry--EDIT: or rather *was* before you changed it.)

to unmount recovery try:

**sudo umount /media/sda2**

---

### Post by bodhi.zazen on 2007-09-23
LOL

I do not think it matters any longer where you mount the partition/drive.

Open the Gnome Configuration editoer : Applications->System Tools->Configuration Editor
		Go to apps->nautilus->desktop->volumes_visible flag

---

### Post by logos34 on 2007-09-23
Ok, so at this point your ntfs and fat32 are mounting fine according to the edited fstab, without additional volume labels showing up on desktop, right?  But the dell recovery is still mounting as 'Recovery'?  If so, I'm not sure why or how to tell it not to mount.. the umount thing won'r prevent it from mounting again at boot...maybe bodhi.zazen knows.

---

### Post by mikeserv on 2007-09-23
Ok, I've fixed it.  The problem didn't lie in the "volume-visible" dealie, the problem is this:

I'm not just using Ubuntu, I'm using an Ubuntu-derivative distribution called LinuxMint.  LinuxMint comes with a control panel called "MintDisk" (in Menu > System > Administration).  It automounts drives with selections like "Mount FAT32 and FAT32 LBA partitions" and "Mount NTFS partitions".  

It also has a selection for "Show links for mounted partitions" (which is checked by default) and the default links location is "<<HOME>>/Desktop/" which is why I was showing the drives whether I turned off "volumes-visible" or not.  And when I had it on, Gnome was showing me my mounted drives AND mintDisk was showing me links to those same drives.  In effect, it was nothing but annoyingly redundant.

And since I provided for my drives in the fstab (thanks logos!) it wasn't showing those two (at the bottom of the panel it has this to say: "Note: mintDisk does not mount partitions that are present in /etc/fstab").  But it was still automounting the third (unwanted) partition.

The bottomline is this: If you setup your mounted drives correctly in the fstab file, mintDisk is better turned off.

-Mike

---

### Post by logos34 on 2007-09-23
aha, so you're running LinuxMint, and mintdisk was the culprit!  I was actually playing around with Linuxmint up until recently and was impressed with the built-in ntfs support (ntfs-3g) and disk management (mintdisk).  Didn't get all that familiar with it, though, so I probably wouldn't have connected it up in my mind anyway.  But it appears it's capable of causing a bit of confusion with disk mounting!  

Well, glad everything is working more or less like it should be.  Enjoy ubuntu!

---

