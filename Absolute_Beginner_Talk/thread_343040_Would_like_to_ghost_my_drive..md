---
title: "Would like to ghost my drive."
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by peejaygee on 2007-01-20
Dear All, 

new to ubuntu, new to linux, like to mess around.....but for ease I would like to ghost a recent (working) install, so if I muck it up, I can just re-install from the image..

I've found g4l, but that only seem to allow ghosting to a ftp (unless I'm looking at the wrong options) I would like to ghost to a cd/dvd, that makes a bootable cd/dvd of the whole harddisk.

Is there anything out there for me, I've searched in the add/remove, and the synaptic package manager, and I'm either putting in the wrong text to search, or there is nothing in there?

Hope someone can help me...

Regards
Paul.

---

### Post by billingsworld on 2007-01-21
Hi,

I did the same thing in windows.  Partimage was recommended:

[http://partimage.org](http://partimage.org)

I haven't used it yet, but, you can image to your home directory if that's where you want to store your backup image file.

---

### Post by aysiu on 2007-01-21
This may help:
[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

### Post by Frank Golden on 2007-01-21
```

```Partimage is my choice. You get it with the Linux System Rescue CD.

Get it here.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

and see these tutorials about using it.
The first one I wrote the second was written by another member with better writing skills
than I using my original material. I use partimage a lot for just the thing you want. If you store the backup on another partition on your drive backups and restores will be quick.
In my case about 6 minutes either way (backup/restore)

[http://www.ubuntuforums.org/showthread.php?t=226402](http://www.ubuntuforums.org/showthread.php?t=226402)

[http://www.ubuntuforums.org/showthread.php?t=287522](http://www.ubuntuforums.org/showthread.php?t=287522)

Once you use partimage a few times it will become second nature  to you.

PS this is not a program you install in Ubuntu but an image you download and burn to a CD to create
a live CD like the CD you installed Ubuntu with. A bootable tool disc.
Partimage is just one of many tools on the CD.

When the CD finishes booting and you have mounted the destination partiton you invoke partimage
by typing ```
partimage 
```at the prompt.
All this info is explained in the above tutorials.

---

### Post by keithpeter on 2007-01-21
> **Frank Golden said:**
> ```

```Partimage is my choice. You get it with the Linux System Rescue CD.

Frank and all

Downloading the ISO as I type.

Suppose I want to install a new larger hard drive. Can I use the live CD to back up my present main partition to an external USB drive, pop the new hard drive in, boot off the live CD again to partition the new hard drive (swap and main partition) and restore the backup from the external USB drive to the main partition? Are there tools on the CD that can create Ext3 and Swap partitions and possibly format the new drive?

I have a somewhat customised Xubuntu and would rather try that than re-install from scratch. The computer is a low profile desktop and there isn't room for two hard drives.

Cheers

---

### Post by Frank Golden on 2007-01-26
> **keithpeter said:**
> Frank and all

Downloading the ISO as I type.

Suppose I want to install a new larger hard drive. Can I use the live CD to back up my present main partition to an external USB drive, pop the new hard drive in, boot off the live CD again to partition the new hard drive (swap and main partition) and restore the backup from the external USB drive to the main partition? Are there tools on the CD that can create Ext3 and Swap partitions and possibly format the new drive?

I have a somewhat customised Xubuntu and would rather try that than re-install from scratch. The computer is a low profile desktop and there isn't room for two hard drives.

Cheers
Gparted is the partitioning tool on the CD.
What I would do is create a Fat32 or ext3 partition on your present drive and image
the install you want to save to it. Partimage is very quick when saved to a partition on the same drive. A matter of minutes vs. over an hour to an external drive.
Then just copy the image to the external drive temporarilly.
Popin your new drive and use gparted on the Sysresccd to partition like you want.
Make sure the ext3 partition is exactly the same size as the original partition or a little larger to be sure. Even though partimage only images the used space on a drive it notes the original size of the partition including free space. If for instance you image a 15GB
partition with a 3 GB Ubuntu install the resulting uncompressed image will be 3GB. If you try to restore to a partition that is not exactly 15GB or slightly bigger the restore will fail.

Create another partition for your image file also. You will copy you image from the external drive to here later.

Your new and old drives should have the same partition structure also.
For instance if your old drive has a ext3 partition labeled sda1 with a swap sda2 and a storage partition sda3 then your new one should have the same structure.
The reason for this is the image you made will have this info in the form of entries in the /etc/stab and /boot/grub/menu.lst files. You can edit these files later but it is better to 
have them right at the beginning.

Now you can either install a base Xubuntu install using the CD (recomended).
This installs grub and makes the partition bootable. You then copy your image
to the storage partition and then use partimage to restore your customized Xubuntu
over the base install. It will overwrite it. If you kept the original partition assignments
you old grub will have no trouble booting.

The other method is to skip the base install and restore your image directly to a empty
ext3 partition. You will need to restore grub stage 1 to the MBR manually this way though.

Remember patimage works much faster if the place you create/restore from is on the same drive. Of course it can't be the partition you are trying to image.

---

### Post by keithpeter on 2007-01-28
> **Frank Golden said:**
> Remember patimage works much faster if the place you create/restore from is on the same drive. Of course it can't be the partition you are trying to image.

Hi Frank

Thanks for this post, and I will have a bash when the new disc arrives. If i mess it up, all I loose is a few hours customising as all my data is backed up.

Cheers

---

### Post by linuxjerk on 2007-04-02
I don't think there is a good disk copying program. Someone needs to find one.

---

### Post by aysiu on 2007-04-02
> **linuxjerk said:**
> I don't think there is a good disk copying program. Someone needs to find one.
PartImage is a good one.

More details here:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by linuxjerk on 2007-04-02
All those still require the disk be unmounted to copy. Try G4U I got it to work on my system.
You can either do floppies or cd.
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

---

### Post by vatechtigger on 2007-04-02
> **linuxjerk said:**
> You can either do floppies or cd.
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

Do you know where I can get 20,000 Floppies :lolflag:

---

### Post by vjones777 on 2008-01-06
Just to update this thread, theres a 'new kid' on the block - clonezilla.  It supports more filesystems than partimage (for example, partimage's support for NTFS is [listed]("http://www.partimage.org/Supported-Filesystems") as experimental) and it is reported as being under active development - I've heard that partimage isn't so active now.

One point to note is that Ghost4inux (G4L) makes a bit for bit copy of the hard drive, so it doesnt care what the filesystem is.  That has the disadvantage that every bit has to be copied, whether or not that part of the drive has any useful data or not - so the backup is larger and takes more time.  It also means theres restrictions on the size of the hard drive the image has to be restored to.  

Partimage and clonezilla use knowledge of the filesystem to skip unused portions (& I think they will also usefully skip memory swap files).  As I mentioned, Clonezilla supports more filesystems and, for those it doesn't, it reverts to using 'dd' to do a bit-for-bit copy - so you get G4L behaviour.

I found a useful tutorial on G4L [here]("http://www.howtoforge.com/back_up_restore_harddrives_partitions_with_ghost4linux")

[Clonezillas homepage]("http://clonezilla.sourceforge.net/")
Disclaimer - I havn't personally used clonezilla yet.

There's a couple of useful live CDs combining clonezilla with other system tools:
[LIST]
[*][GParted-CloneZilla Live CD]("http://clonezilla.sourceforge.net/gparted-clonezilla/") - This project by LarryT combines the [gparted]("http://gparted.sourceforge.net/") hard disk partitioning tool with CloneZilla.
[*] [Clonezilla-SysRescCD]("http://members.hellug.gr/sng/clonezilla-sysresccd/index.html") - This is another excellent combination of tools made by Spiros Georgaras. This liveCD combines the system repair and data recovery collection of tools of the [SysRescCD]("http://www.sysresccd.org/Main_Page") with CloneZilla.
[/LIST]
I can vouch for systemrescueCD - although its interface is very DOS like (clunky), it is functional and reliable.
BTW, some of the above was lifted from [CloneZilla instead of Partimage]("http://www.g-loaded.eu/2007/09/15/clonezilla-instead-of-partimage/")

---

