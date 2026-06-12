---
title: "missing partitions"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2007-03-01
When I formatted my hard drive before installing ubuntu I set aside an additonal ext3 partition to store various files on, as well as a FAT32 3 GB partition to allow for easy sharing of files between the windows xp (on the primary partition).

For some reason both of the mentioned partitions are not currently accessible through ubuntu (haven't checked windows for the FAT32 par.).  The wierd thing is that a dell configuration partition (FAT16) at the beginning of the hd did show up as an icon on the desktop after install (which I removed from the fstab file).

The configuration settings in that file are how you say...a little complex, and not something that I can figure out, so does anyone have any tips on what I have to do to get access?

Thanks for the help.

---

### Post by chris.olsen on 2007-03-01
hmm well looking a little closer it seems that when I was setting up the formatting I accidentally formatted one of the drives to NTFS (the one that was supposed to be ext3) and the fat32 is still MIA.

Is there anyway to reformat this drive to ext3 from linux or should I do it through windows using partition magic?

---

### Post by STREETURCHINE on 2007-03-01
you can use gparted in linux

[http://www.google.com.au/url?q=http://gparted.sourceforge.net/livecd.php&sa=X&oi=smap&resnum=1&ct=result&cd=2&usg=__X7GtOxTTR5NC7FSv020ifZpLqx0=](http://www.google.com.au/url?q=http://gparted.sourceforge.net/livecd.php&sa=X&oi=smap&resnum=1&ct=result&cd=2&usg=__X7GtOxTTR5NC7FSv020ifZpLqx0=)

---

### Post by chris.olsen on 2007-03-02
I reformatted the incorrectly formatted partitions.  To get them to be accessible I am assuming that I have to add them to the fstab file is that correct.  If so how exactly do I get the uuid of the partitions?

Thanks  (gparted worked great)

---

### Post by Archmage on 2007-03-02
> **chris.olsen said:**
> I reformatted the incorrectly formatted partitions.  To get them to be accessible I am assuming that I have to add them to the fstab file is that correct.  If so how exactly do I get the uuid of the partitions?

```
sudo vol_id -u <partition>
```

---

### Post by chris.olsen on 2007-03-02
I thought that by adding them to the fstab file they would auto mount, but I still don't have access to them.

I figure that this might be due to the fact that they are missing a mount point (this column is blank in the gparted program), but I am not sure how to set them.

This is what I put into the fstab file

# /dev/sda5
UUID=c514c37e-9d97-46e7-b63d-6800bbf73a7f	/media/sda5	ext3	defaults,errors=remount-ro 	1	2

# /dev/sda8
UUID=45E7-D208					/media/sda8	fat32	defaults,errors=remount-ro 	1       3

---

### Post by chris.olsen on 2007-03-02
Does anyone else know the answer to this?  I figure this is probably an easy one for a somewhat experienced linux user.

Thanks

---

### Post by rccharles on 2007-03-02
> **chris.olsen said:**
> I thought that by adding them to the fstab file they would auto mount, but I still don't have access to them.

I figure that this might be due to the fact that they are missing a mount point (this column is blank in the gparted program), but I am not sure how to set them.

This is what I put into the fstab file

# /dev/sda5
UUID=c514c37e-9d97-46e7-b63d-6800bbf73a7f	/media/sda5	ext3	defaults,errors=remount-ro 	1	2

# /dev/sda8
UUID=45E7-D208					/media/sda8	fat32	defaults,errors=remount-ro 	1       3

and the option is vfat

Did you create the directory?

sudo mkdir /media/sda5
sudo mkdir /media/sda8


Some folks add some additional options to vfat.  You need the umask....:
Here is an example copied from:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
/dev/hdb1 /fat_files vfat iocharset=utf8,umask=000 0 0


&&&&&&&&

to 'run' the changes do:

sudo mount -a



Robert

---

### Post by chris.olsen on 2007-03-03
yip that was the problem and it is so close to working :)

I have write permissions to the vfat partition, but not to the ext3.  I tried to chmod 777 it but that didn't seem to work (can you tell I am a noob?)  I thought that since it has an ext3 format this wouldn't be an issue, but...

One last question.  After repartitioning the drives using gparted I didn't seem to be able to assign a name to the partitions so now I have drive icons on my desktop saying sda5 and sda8.  Is there any way to change the names?

Thanks for your help it is really appreciated.

---

### Post by rccharles on 2007-03-03
> **chris.olsen said:**
> yip that was the problem and it is so close to working :)

I have write permissions to the vfat partition, but not to the ext3.  I tried to chmod 777 it but that didn't seem to work (can you tell I am a noob?)  I thought that since it has an ext3 format this wouldn't be an issue, but...

One last question.  After repartitioning the drives using gparted I didn't seem to be able to assign a name to the partitions so now I have drive icons on my desktop saying sda5 and sda8.  Is there any way to change the names?

Thanks for your help it is really appreciated.

I recreated this situation.  

You need to change the directory attributes.
# verify that sda5 is mounted.
mount

cd /media
ls -l
sudo chmod 777 sda5
ls -l

----------

You could rename the directories in /media
sudo mv sda5 newname
# change fstab...

----------
gparted may let you change the name.  
I have seen a reference to this question.
Robert

---

### Post by chris.olsen on 2007-03-04
Thanks for the help.  I guess I was a little paranoid about renaming them in the fstab file due to previous partition issues.

Thanks again :)

---

