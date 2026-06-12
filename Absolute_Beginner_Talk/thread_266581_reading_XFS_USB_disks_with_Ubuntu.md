---
title: "reading XFS USB disks with Ubuntu"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by Meaty Squirrel on 2006-09-27
Hi,

This is my first post, and I have never used Ubuntu (or in fact anything other than Windows before) so please be gentle with me.

I have a Buffalo Terastation. Attached to this is a 500GB IDE HDD (via a USB connection).

I have very a large amount of valuable data (family photos, videos etc.) stored on the Terastation.

I had planned to back this data up to the USB HDD and then, should the Terastation every die, I would be able to plug the USB HDD into my Windows PC and retrieve all my files.

I now discover that the Terastation will only use the full 500Gb of my USB HDD if I allow it to format the disk in XFS.

Obviously if I do this, and the terastation dies, I will not be able to access my files on the USB HDD via any of my Windows PCs.

My question is therefore, can I use Ubuntu (running from a CD) to access the files on the USB HDD disk (bearing in mind they will be stored in XFS format).

Also, if I can access them, what would I need to do to save them to another HDD in a format Windows could recognise?

Thank you all in advance for your help with this.

Meaty Squirrel

---

### Post by em3raldxiii on 2006-09-27
I found this web page that might help a little:

[http://www.ubuntuforums.org/archive/index.php/t-188194.html](http://www.ubuntuforums.org/archive/index.php/t-188194.html)

Mounting different drives to your Linux operating system is not terribly difficult, and it appears that XFS is natively supported (not like NTFS which requires that you jump through a few hoops first).

Now, no one else has answered you yet, so I am going to have a go at it, and hopefully others can correct me if I am wrong.  Here are the steps as I think they would (close anyway).

[COLOR="Blue"]1.[/COLOR]  Boot your Ubuntu computer with the USB drive connected and turned on.

[COLOR="#0000ff"]2.[/COLOR]  Once logged in and happy, type this in your console (applications > accessories > terminal)

```

sudo fdisk -l

```

This will tell you the name of all the storage devices that are connected and available to your computer.  You should get a list of stuff like this:

> 
[FONT="Courier New"]Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2497    20057121    c  W95 FAT32 (LBA)

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1275    10241406    7  HPFS/NTFS
/dev/hdb2   *        6135        9804    29479275   83  Linux
/dev/hdb3            9805        9964     1285200    f  W95 Ext'd (LBA)
/dev/hdb4            1276        6134    39029917+  83  Linux
/dev/hdb5            9805        9964     1285168+  82  Linux swap / Solaris
[/FONT]

You want to find the one that has XFS in the RIGHT hand column.  Note the name under "Device Boot" of your XFS Drive, we will use this in step 4.  I don't think you need to worry about the start/end/blocks/id for now.

[COLOR="#0000ff"]3.[/COLOR] Then we want to create a folder that will be your link to the drive (since Linux thinks "everything" is a file, including devices).  A common location is in your /media folder, but you can also choose your /home directory.  We'll use the name "mybigassdrive" so we don't get confused.

```

sudo mkdir /media/mybigassdrive

```

[COLOR="#0000ff"]4. [/COLOR] Next we'll have to edit your FSTAB file (I think of this as file system table, but I am 99% sure that's not really what it's called).  This file tells your computer which devices to mount at boot time.  Do the following in your terminal.  The first line makes a backup of your fstab (remember it's location in case you gibble something up).  The second step opens the fstab file in **gedit** text editor with "super user" powers (sudo). 

```

sudo cp /etc/fstab /etc/fstab.bak
gksu gedit /etc/fstab

```

NOTE:  If you screw something up and Linux fails to boot properly, you can [COLOR="#0000ff"]sudo cp /etc/fstab.bak /etc/fstab[/COLOR] which would return the file to it's original state.

Now you will add a line at the end of this file to refer to your XFS storage device.  Something like this:

```

/dev/hdz8    /media/mybigassdrive    xfs    defaults    0    0

```

Make sure that you've changed the **hdz8** to the correct name that we got in step 2.  The only part I am somewhat unsure of is the "defaults  0  0" part.  Those numbers may have to change, and I am hoping someone on here will know.

[COLOR="#0000ff"]5.[/COLOR]  Reboot your computer.  You MIGHT be able to get away with just a **ctrl-alt-backspace** which just restarts the X-server, but I am not 100% convinced that will work.  A full reboot (reminiscent of Windows, hey?) might be required.

[COLOR="#0000ff"]NOTE:[/COLOR]  This is very likely not the optimum way of connecting a USB drive, because USB is by nature hot-pluggable.  Unfortunately, I don't know enough about hot-plugging drives in Linux so I can't really get into it.  But this method SHOULD work as if you plan to leave the drive connected all the time.  It should be a pretty good starting point anyway.

Sorry it took so long for someone to get back to you.  It happens occasionally where something slips through the cracks.  I am just a fellow user like you, though, so you'll have to forgive me if it doesn't work perfectly on the first try ;)

Good luck, and DEFINITELY keep us updated.  If you find a different solution that works, please post it (or a link).  Cheers!

---

### Post by Meaty Squirrel on 2006-09-28
Hi,

Thank you so much for taking time to answer my question in such detail.

I really appreciate  that.

I will try what you said over the weekend and report back.

Once again, many thanks for helping me out.

Meaty Squirrel!

---

