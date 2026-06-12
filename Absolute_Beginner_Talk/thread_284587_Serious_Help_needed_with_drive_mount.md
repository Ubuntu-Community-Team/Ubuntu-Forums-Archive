---
title: "Serious Help needed with drive mount"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by joshgtv6 on 2006-10-25
ok, let me start by saying that I tried both the guides that are always recommended.  the one at pyschocats or whatever it's called and the one from the Ubuntu Wiki that explain how to mount a windows NTFS hardrive.  I can see the drive in both the filesystem and in disk info but I am unable to mount it. 

Some background:  I was able to mount the drive earlier today, but I had issues with the computer and Dell had me unplugging and replugging stuff.  After I got everything back to the way it was originally plugged in before Dell got their hands on it I am unable to mount my second hardrive.  

Please help.  I redid all the stuff it tells you to in both those guides and I still can't mount the drive.  I've tried rebooting and everything.

---

### Post by DaveBorealis on 2006-10-25
Hello,

Could you post the command that you're using and the error messages that you get?  Also, if you remember, what exactly were you unplugging and replugging?  (Sounds like they had you switching hard drive ribbons inside the computer box, I'm guessing.)

Best regards,
Dave

---

### Post by dbott67 on 2006-10-25
Also, can you post the output of **sudo fdisk -l**
```
dbott@dapper:~$ sudo fdisk -l
Password:

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility *[COLOR="Red"]<--- Dell Partition[/COLOR]*
/dev/sda2   *           7        2556    20482875    7  HPFS/NTFS *[COLOR="Red"]<--- XP Pro[/COLOR]*
/dev/sda3            2557        9634    56854035    f  W95 Ext'd (LBA) *[COLOR="Red"]<--- Nuked Vista[/COLOR]*
/dev/sda5            2557        5106    20482843+   7  HPFS/NTFS *[COLOR="Red"]<--- XP Media Center[/COLOR]*
/dev/sda6            5107        7656    20482843+   7  HPFS/NTFS *[COLOR="Red"]<--- Windows 2003[/COLOR]*
/dev/sda7            7657        9568    15358108+  83  Linux *[COLOR="Red"]<--- Dapper Drake[/COLOR]*
/dev/sda8            9569        9634      530113+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 14 MB, 14909440 bytes
2 heads, 32 sectors/track, 455 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         455       14531+   1  FAT12 *[COLOR="Red"]<--- SD Card[/COLOR]*
```

You can see by my output that I have a number of different partitions (all are mounted).

---

### Post by joshgtv6 on 2006-10-25
Unable to mount the selected volume.
mount: only root can mount /dev/hdb1 on /windows


below is result fdisk

Disk /dev/hda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4770    38314993+  83  Linux
/dev/hda2            4771        4863      747022+   5  Extended
/dev/hda5            4771        4863      746991   82  Linux swap / Solaris

Disk /dev/hdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36480   293025568+   7  HPFS/NTFS
jpeifley@jpeifley-desktop:~$



/dev/hdb1 is the exact location is was before they had me unplug all the ribbons and pull out the motherboard battery.  What i was trying to do was install windows on the hdb1 drive so i could set up a dual boot but we were unable to get windows to install so i said screw it and just booted up Ubunto.  Only to see that none of my cd/dvd drives were being recognized and i was now unable to mount my second hardrive that is completely empty. 

I also booted up to the live disk which is showing the hdb1 drive at being formatted to ext3, which is fine by me but without the live disk in it's showing it as being HPFS/NTFS.  Also i should add that dev/hda2 Extended Partition on Drive 1 is a new creation since the attempted installation of XP.  

So again, any help would be amazing. I know it's possible to mount this drive as I had it working this morning with no issues.

---

### Post by dbott67 on 2006-10-25
What command are you using to mount the partition?  It should be:

```
sudo mount /dev/hdb1 /windows/ -t ntfs -o nls=utf8,umask=0222
```

And you also need an empty folder on the root called 'windows' (some of the HOWTOs & WIKIs create the empty directory in **/media/windows** or **/mnt/windows**).

-Dave

---

### Post by joshgtv6 on 2006-10-25
ok, i typed that command at the terminal and got this error message:

mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

So maybe this will makes things easier.  I have no need at this point in time for a windows drive or partition.  How can I just set this second drive up with a ext3 filesystem so i can read and write to it and then of course mount it.  I'm sorry this is taking so long.

---

### Post by dbott67 on 2006-10-25
If you want to nuke the partition, click **SYSTEM > ADMINISTRATION > DISKS**.  Select you the appropriate hard drive along the left-hand side and then click the **PARTITION** tab.  Select the desired partition to format (**hdb1**, in your case).  You'll need to 'disable' the partition first (it should be already) and then click **FORMAT**.

Make note of the filesystem (NTFS vs. ext3 vs. swap vs. FAT).  This may prevent you from deleting the wrong one by accident.

See attached screenshot.

-Dave

PS - Standard warnings apply when formatting/deleting a partition.

---

### Post by joshgtv6 on 2006-10-25
> **dbott67 said:**
> If you want to nuke the partition, click SYSTEM > ADMINISTRATION > DISKS.  Select you the appropriate hard drive along the left-hand side and then click the PARTITION tab.  Select the desired partition to format (hdb1, in your case).  You'll need to 'disable' the partition first (it should be already) and then click FORMAT.

See attached screenshot.

-Dave

PS - Standard warnings apply when formatting/deleting a partition.

i've tried this before.  When i format it to EXT3, it says that it did in fact format it to EXT3.  Then when i exit the disk utility and go back into it the drive is back to NTFS.  What the hell is going on?

---

### Post by joshgtv6 on 2006-10-25
i've got to bump this because I really need to be able to access this drive. Someone has to be able to help me.

This is the error I recieve when trying to mount the drive. 

mount: only root can mount /dev/hdb1 on /windows

---

### Post by DaveBorealis on 2006-10-25
> **joshgtv6 said:**
> 
This is the error I recieve when trying to mount the drive. 

mount: only root can mount /dev/hdb1 on /windows

You might have two problems happening simultaneously, one being your CD/DVD ribbon not properly plugged into the motherboard, and the other being mounting the ext3 drive.  Because you said that it was reformatted to ext3, I'm assuming that you simply tried:
```
sudo mount -t ext3  /dev/hdb1 /windows/
```

---

### Post by joshgtv6 on 2006-10-25
> **DaveBorealis said:**
> You might have two problems happening simultaneously, one being your CD/DVD ribbon not properly plugged into the motherboard, and the other being mounting the ext3 drive.  Because you said that it was reformatted to ext3, I'm assuming that you simply tried:
```
sudo mount -t ext3  /dev/hdb1 /windows/
```

i'm actually having a strange problem.  The CD/DVD's drives are fixed. That was simple enough.  But i'm having a serious problem with this second drive.  As i've posted in this thread, i couldn't mount it using the guides provided.  So i figured i would just format it to EXT3 and then try mounting it.  When i do that, it says that indeed it is EXT3.  Ok, great.  Then i exit the disk utility and go back into it and the drive is back to being NTFS. Wierd huh?  

So....I had a wacky idea that I would simply boot the live CD and do it from there.  So when i went to format that drive under the live cd it said that is was EXT3.  

Live CD: says /dev/hdb1 is EXT3
Booting into Ubuntu without the live cd says /dev/hdb1 is NTFS

?????? that makes no sense, so what the heck is it?  it can't be both.  

So i get the bright idea of installing Ubuntu on this wierd drive that claims to be both file systems.  I successfuly install, and boot up withouth the live cd, select the proper install for the second drive that is giving me trouble and everything boots up fine.  So now this Drive HAS to be ext3 for Ubuntu to be running on it.  One would think at least.  Now i restart and boot up into the original Ubuntu install and check in the disk utility to see that in fact the second hardrive is now EXT3, nope, disk utility is still saying it's NTFS which we know is impossible.  

Anyone care to take a stab at what the heck is going on here?

---

### Post by dbott67 on 2006-10-26
I'm stumped... it's very weird that it's reporting NTFS when in fact Linux is installed.

I was reading the man pages for fdisk and it does report that fdisk is buggy.  Try runnning run cfdisk & see what it reports:

```
sudo cfdisk
```

If it still reports NTFS, perhaps you can try using cfdisk to delete the partition & make it 'free space' and then create a new partition.

---

### Post by joshgtv6 on 2006-10-26
thanks, i ended up getting it figured out last night.  I just used a partioner to wipe all the partitions on it, and then made it ext3.  Now all is well.  thanks for you continued help.  By chance, do you know how I can get the drive to show up in here?

[IMG]http://h1.ripway.com/jpeifley/screen.png[/IMG]

i have the drive mounting to /media which is where people are saying to mount it to have it show up on the desktop, but i want it to show up actually as a drive like it used to in the location shown in the screenshot.  thanks.

---

### Post by dbott67 on 2006-10-26
I don't think it has to be mounted to **/media**, as I have an external NAS device mounted to **/home/dbott/music** that shows up on the Desktop as well as in the 'Computer' folder (see screen shot).

There is a setting in gconf-editor that allows the mounted volumes to display on the desktop:
```
sudo gconf-editor
```
Browse to **APPS > NAUTILUS > DESKTOP > VOLUMES_VISABLE** (check)

However, even without doing that, the mounted volumes appear when I open 'Computer'.

Have you tried using the 'Disk Mounter' applet (right-click Toolbar & select **ADD TO PANEL > DISK MOUNTER**).

-Dave

---

### Post by joshgtv6 on 2006-10-26
> **dbott67 said:**
> I don't think it has to be mounted to **/media**, as I have an external NAS device mounted to **/home/dbott/music** that shows up on the Desktop as well as in the 'Computer' folder (see screen shot).

There is a setting in gconf-editor that allows the mounted volumes to display on the desktop:
```
sudo gconf-editor
```
Browse to **APPS > NAUTILUS > DESKTOP > VOLUMES_VISABLE** (check)

However, even without doing that, the mounted volumes appear when I open 'Computer'.

Have you tried using the 'Disk Mounter' applet (right-click Toolbar & select **ADD TO PANEL > DISK MOUNTER**).

-Dave

huh, i'm starting to wonder if my install of Ubuntu is corrupted.  As i don't have Nautilus even listed under apps, and when I try to add something to the panel it doesn't actually add it.  You can visually see that it makes a space for it but nothing appears and as soon as you close the add to panel box the empty space disappears.  Interesting, i'll have to see what's going on here.  Thanks again though.

---

