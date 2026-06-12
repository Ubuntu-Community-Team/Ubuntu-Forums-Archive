---
title: "Attempting ext3 partition on USB HD"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-30
Hi
I just finished re-installing Ubuntu 6.06 which included reformatting and repartitioning my "Linux" drives (I'm dual nbooting with WinXP).
While I was doing this, I decided to try to change the file system (from ntfs to ext3) for one of the (three) partitions on one of my USB HDs.

This seems to go fine, although during the Ubuntu installation process a warning message appeared saying that Windows may not be happy with 2kB blocks on the USB drive partition. I ignored this and continued.

However, now when I boot into Ubuntu, I get an error message which occurs while in the "Checking all file systems" section.
The error message says (I couldn't copy and paste this so it may not be exactly verbatim):


fsck.ext3  No such file or directory while trying to open /dev/sdb6.
Superblock could not be read or does not describe a correct ext2 file system.
If device is valid and really contains the ext2 file system (not Swap or ufs or something else) then the superblock is corrupt and you might try running e2fsck with an alternate superblock  e2fsck -b8193 <device>


Then a Terminal command prompt appears. When I type Exit the boot continues normally and Ubuntu runs without problems.
As you may have guessed, /dev/sdb6 is the USB HD partition where I changed the filesystem from ntfs to ext3.
Can anybody suggest what options I have here (other than reformatting the USB HD partition to remove the ext3 file system)?
I would like to be able to copy/store stuff from Ubuntu to the USB HD

Thanks
Paul

---

### Post by mzilhao on 2006-07-30
well, if you have entries on your /etc/fstab for your USB HD, then my guess is that you didn't change the file type for your partition on fstab.
try:
```
sudo gedit /etc/fstab
```
and on the /dev/sdb6 entry change ntfs to ext3.

---

### Post by PaulFXH on 2006-07-30
Hi mzilhao
Thanks for your reply.
Actually, all of my drives/patitions are assigned the "correct" file system in fstab including /dev/sdb6

However, note that the error message seems to suggest that the ext2 (E-X-T-TWO) file system is expected here rather than ext3.
Unfortunately, I have no idea what to make of this.

Paul

---

### Post by anaconda on 2006-07-30
Have you formatted the partition in your USB hdd to be ext3?

And ext3 is actually ext2 with journaling. 

If you have formatted it then you should consider reformatting the partition, and make sure that it will be ext3...

---

### Post by catlett on 2006-07-30
I am assuming there is no data on that partition since you just formatted it, so reformat it.
Go to System<Administration<Gnome partition editor. That is gparted the partitioner for gnome. If it isn't there for some reason run
```
sudo apt-get install gparted
```Then go back to the menu.
When the window for it opens your master drive will be displayed as a bar graph.
Go to the uppper right and there is a drop down box that will give the option to display your other drives. Select the usb external drive. If you don't recognise the label, use the gb size to differentiate.
Select the partition that is having problems and right click. An option menu will appear. If the partition  is mounted you will have to unmount it first so select unmount. Then selct it again and go to "format to" and choose ext3. Make sure to hit "apply" or gparted won't run the procedure.
You shouldn't have to edit anything because you said it is listed as ext3. It seems the partition is showing ext2 instead of ext3 and it causes an error on boot when the system tries to mount it. Anyways this will make it ext3 and the error should disappear.
If not, post any error you are getting (as well as you can since you have to do it by memory)

---

### Post by PaulFXH on 2006-07-30
Thanks for the replies, guys

OK, so I used GPartEd (I had used this today already to partition the "Linux" drive before I went ahead with the install) to re-format the external USB HD as ext3.
When I tried to reboot to Ubuntu again, I got exactly the same error as before.

Then I reformatted the same external drive as ntfs and rebooted. Guess what---I got exactly the same error (referring to ext2 drives etc).

So, this time I disconnected this drive altogether and rebooted. Guess what----exactly the same error yet again.

So, it doesn't appear to be a problem on the USB HD but in the Linux boot loader or boot manager or whatever.
The message that I outlined before suggests using e2fsck (which seems to be a Linux equivalent of the WinXP chkdsk) with an alternative superblock.
Does this make sense to anybody?

Thanks
Paul

---

### Post by catlett on 2006-07-30
Post the out pu to these 2 commands. One will display your drives as the system sees them. The other will display the file that tells the system which partitions to mount and where.
```
sudo fdisk -l
```
```
cat /etc/fstab
```
Lets first see what the system sees and how it is trying to mount. Then we can see if it matches up with the actual makeup of the drive or if there is an error.

---

### Post by PaulFXH on 2006-07-30
Hi catlett
Here's the information you were looking for.
I cannot see anything strange here myself but would welcome your opinion.
I'm thinking I might just wipe the three Linux drives and reinstall before I have anything stored here.
But let's see does anything come up.

Thanks
Paul

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1           4       32098+  de  Dell Utility
/dev/hda2   *           5        3854    30925125    7  HPFS/NTFS
/dev/hda3            3855        7048    25655805    5  Extended
/dev/hda4            7049        9726    21511035    7  HPFS/NTFS
/dev/hda5            3855        4046     1542208+  82  Linux swap / Solaris
/dev/hda6   *        4047        4682     5108638+  83  Linux
/dev/hda7            4683        7048    19004863+  83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7248    58219528+   7  HPFS/NTFS
/dev/sda2            7249       30299   185157157+   f  W95 Ext'd (LBA)
/dev/sda5            7249       15068    62814118+   7  HPFS/NTFS
/dev/sda6           15069       22684    61175488+   7  HPFS/NTFS
/dev/sda7           22685       30299    61167456    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6763    54323766    7  HPFS/NTFS
/dev/sdb2            6764       20023   106510950    f  W95 Ext'd (LBA)
/dev/sdb5            6764       13437    53608873+   7  HPFS/NTFS
/dev/sdb6           13438       20023    52902013+   7  HPFS/NTFS



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hda4       /media/hda4     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda7       /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sdb1       /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sdb5       /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sdb6       /media/sdb6     ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by catlett on 2006-07-30
It appears your computer is trying to mount /dev/sdb6 as ext3
```
/dev/sdb6 /media/sdb6 [COLOR="Red"]ext3 [/COLOR]defaults 0 2
```But it is still ntfs according to fstab
```
/dev/sdb6 13438 20023 52902013+ 7 HPFS/[COLOR="Red"]NTFS[/COLOR]
```I am assuming you want it to be ext 3. Are you hitting "apply" after you make all your choices in gparted? I know it is a basic question but gparted will go through all the  procedures and not apply them until you hit apply at the top of the window.
So right now you need to either reformat /dev/sdb6 to ext3 or change your fstab to ntfs. If you go with ntfs you cannot write to it and I think that is what you wanted to do in the first place.

I use gparted live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) It is gparted but it runs off of a live cd. I have better results because the drives are not mounted and the procedures can take place right away. It might be worth downloading and burning to disc since regular gparted seems to be having trouble formatting it. Try to change it like this. Select /dev/sdb6 but choose "delete" first. Then select the unallocated space and select "new" and then format to ext3. Make sure to hit apply. Then exit and reboot. If it formatted to ext3 the the drive will match fstab and you shouldn't have any errors.

---

### Post by PaulFXH on 2006-07-30
Hi catlett
I think I may have misled you a little.
When I found that reformatting the USB HD partition to ext3 did not eliminate this booting problem, I reformatted it to ntfs which is where I left it.
This is the reason you saw this discrepancy but the error had occurred also  a number of times BEFORE I had made this change.

Anyway, I rebooted to GPartEd (I do have the LiveCD) and deleted this partition. I then reformatted it as ext3 (logical partition) and tried to reboot again, but got exactly the same error.

Some interesting observations are:
--After reformatting to ext3, this 50GB partition had 992MB used. When I reformat it to ntfs, only 63MB are used.
--Although the fdisk command shows this partition to have the ext3 file system, fstab shows it as Linux. however, it does the same for the other two Linux partitions on a different physical drive.

I believe the problem is not on the partition itself but somewhere within the Linux boot system. I'm going to have to find out what is the function of the superblocker that is referred to in the error message.
Also, I believe I made an error in trying to partition this drive as part of the Ubuntu installation when it had nothing at all to do with the installation.
Nevertheless, it is interesting that although this drive was reformatted, it did have one folder on it (Lost+Found) when I opened it immediately after the install. This indicates to me that the install process had assumed it was part of the install which it wasn't.
For this reason, I'm going to remove Ubuntu and reinstall it again without the participation of the external HD.
I can use GPartEd to reformat it AFTER I have Ubuntu booting without errors.

Paul

---

### Post by catlett on 2006-07-30
If you keep in unconnected it should change things.
For instance my Seagate 160gb USB external hard drive was not connected during install. So it doesn't have an fstab entry and the system doesn't look for it at boot.
When you "hotplug" an external, ubuntu will mount it automatically using "pmount". Pmount is how the sytem handles usb devices. This way it can be mounted without an fstab entry. The file system type is auto detected.
In my case, I have the external connected by a usb cable but powered off on startup. After I boot into my desktop I "power on" the external and an icon appears on my desktop with the drive. I can also use gparted to go into the drive and partition.
Just another note. Even though it wasn't connected during install and it mounts with pmount after I boot, I can still have it on and start up the syetem. It appears on my desktop as if I powered on after startup (meaning it isn't listed as another internal drive but as a usb device.)

---

### Post by PaulFXH on 2006-07-30
Hi catlett
OK, I reformatted the USB HD partition to ntfs using GPartEd.
Then I re-installed Ubuntu (6.06) including re-formatting all three Linux drives.
So, now the problem is gone and I can boot without any errors which I think confirms that the problem was related to me having formatted the USB HD to ext3 DURING THE INSTALLATION.

Incidentally, my two external HDs were both powered on and connected throughout the installation and the boot without causing any problems.
It's interesting what you mention about your "USB devices" showing up on your desktop.  Mine only appear there sporadically and I really don't understand why this is the case.

My intention now is to format the same external partition to ext3 with GPartEd and see if I can write to it from Ubuntu.
Thanks for all of your comments and suggestions.
Paul

---

### Post by moshuptrail on 2006-07-30
PaulFXD -
I had exactly the same experience when I used GParted to create an extended partition and then created 3 logical partitions.  I created one for Linux (ext3), one for swap, and one for /home (ext3) and then installed Vector Linux.  I had the exact same error on the last partition and assumed it was something I had done.  I tried formatting it and re-installing linux with no luck.  Eventually I just reformatted it to ext2.
Maybe there's a bug in GParted.  I was using a GParted LiveCD, but not the latest version.  (The latest LiveCD version seems to have some trouble scanning devices sometimes)

---

