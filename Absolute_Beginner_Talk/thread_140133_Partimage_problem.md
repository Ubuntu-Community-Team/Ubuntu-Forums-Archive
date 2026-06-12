---
title: "Partimage problem"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-03-05
Hi
I am trying now for two weeks to make a backup copy of my [COLOR="Blue"]hda1[/COLOR] partition to a USB hard drive [COLOR="Blue"]sda1[/COLOR]. 

[COLOR="Black"][/COLOR]

I get the message:
```

can not create temp file sda1/picc83cac3.tmp Check there is space enough and you have access rights.
```

I am using the Partimage GUI from the **System Rescue CD**
I see from other threads others have had success with  Part image.
Also how do I display the priv. of sda1? When I use chmod to change priv. to 0777 I get no errors.

---

### Post by cotcot on 2006-03-05
This is the way it works by me :

I use the Kanotix live CD as this supports USB 2.0 connection.

Unmount the partition that you want to clone ("umount /hda2")

Change permissions on the partition where you want to put the clone on : 
"sudo chmod 755 /mnt/sda2" (with the partition unmounted ; this is default with the live CD I use)

Mount this partition : "mount /mnt/sda2"

Sudo partimage : make sure that you break up the clone in files of less than 4 GB when you clone to a FAT partition.

---

### Post by kent41 on 2006-03-05
OK here is what is going on.

When I get part way through the Partimage screens I see that **hda1** has 2.7 gig USED and 2.63 FREE space used out of a TOTAL of 5.33 gig.

It also shows that the USB drive **sda1** has 9 gig of free space available.

When Partimage start to transfer data from** hda1 to sda1 **it gets so far and then I get the message disk FULL. provide path or device to continue to.

THIS tells me that Partimage is trying to store the backup to **hda1** not **sda1**, am I right or wrong ?

What I am trying to do is save a backup to an external drive. Is this possible with Partimage ? or does part image only save backups to the same drive the source is on? If this is the case what value is Partimage if you get a corrupt hda1 drive? I also see no activity on the sda1 drive.

---

