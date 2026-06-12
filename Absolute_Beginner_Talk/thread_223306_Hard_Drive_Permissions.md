---
title: "Hard Drive Permissions"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by justicerulesok on 2006-07-26
I have two hard drives in my machine.  I installed ubuntu on the one in the list that was highlighted as I assumed it was deult setting but I cant mount or do anything with the bigger one as I only have read permissions.

I found some instructions to open / edit fstab but am not really sure what to do.  I've never posted code before so if it look funny/wrong sorry

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
 
```

this is my fstab file  I have no idea if hda1 or hda5 is my unmountable disk.  please help.  thank you,

Justice.

---

### Post by Dinerty on 2006-07-26
Here is a good guide which allows you to set persmissions to hard drives, I used it and it is ok :)

[http://psychocats.net/ubuntu/mountlinux.html](http://psychocats.net/ubuntu/mountlinux.html)

---

### Post by justicerulesok on 2006-07-26
thank you,

I've followed it & got the drive ready for use but my permissions still wont let me rename it or allow others to write to it.

---

### Post by sebz2005 on 2006-07-26
Open a terminal
Run as root:
sudo -s
<Password>

And open the file browser:
nautilus

Go to the folder, right mouse click on it and go to the permitions tab and check all the boxes.

---

### Post by justicerulesok on 2006-07-26
Every time I click i get 'sorry the permissions could not be changed'
??

Next suggestion please ;-)

---

### Post by OU812 on 2006-07-27
Please change

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

to

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

john

---

### Post by aysiu on 2006-07-27
If they're Windows partitions...
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If they're Linux partitions, see post #2.

---

### Post by justicerulesok on 2006-07-27
> **OU812 said:**
> Please change

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

to

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

john


I did this & then found my spare hdd turned into a cdrom in 'places' 'computer' so I changed it back again & now both the new cdrom & the HDD have vanished from my system !!!!!

HHEEELLLPPP MMMMEEEEE please.

Justice.

---

### Post by justicerulesok on 2006-07-27
Right my fstab is now ...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1        /storage       ext2    defaults        0       0

```

sda1 is my drive which yesterday I could see but not mount, then mounted but could not edit the permissions on.  Today I can't see it in 'places' 'computer' at all.

when I changed the one letter in dev/hdb to hdc as suggested the icon for the hdd sda1 turned into an icon for a cdrom drive.

When I changed the c back to a b the new cdrom icon vanished but no hdd reapeared. :cry: 

What have I done?

Justice.

---

### Post by aysiu on 2006-07-27
It's not that bad actually.

Just do this: ```
sudo chown -R justice:justice /storage
``` Then go to Places > Computer > Filesystem > Storage

Bookmark it. It will now appear in Places.

---

