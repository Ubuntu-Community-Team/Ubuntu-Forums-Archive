---
title: "Can See NTFS drive, but can't get in"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by brainchild187 on 2006-09-02
Hey guys, I had a lot of success with my 1st question that I posted, so I'm going to try again.  I'm a very new user, and I'm trying to get Ubuntu to let me into my ntfs drive.  If I go into Places => Computer then I can see my drive, but when I double click on it, it gives me this message:  

The folder contents could not be displayed.  

You do not have the permissions necessary to view the contents of "disks-conf-hda1".

I've tried using gksudo nautilus to change the permissions on the drive, but then it gives me this error: 

The permissions could not be changed.
Couldn't change the permissions of "disks-conf-hda1" because it is on a read-only disk


can someone please help me out here?  thanks in advance.

---

### Post by brainchild187 on 2006-09-02
forgot to add.......I just want to be able to listen to my music, watch my movies....etc from that drive.  I don't want write access or anything like that.

---

### Post by bullgr on 2006-09-02
to make the ntfs drive the ability to write go there:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

it's very trusted, i use it for massive copy's, i create isos directly to ntfs drive and all this with no loss.

finaly we can say that writing in ntfs drives is now supported in ubuntu

---

### Post by brainchild187 on 2006-09-02
thanks for the reply, but I don't want to write to the drive, I just want to be able to access it so I can watch my movies and listen to my music and whatnot.   thanks anyway though

---

### Post by MaximB on 2006-09-02
and if you do "gksudo nautilus" and try to access the HD , what happens ?

---

### Post by brainchild187 on 2006-09-02
well, if I do use gksudo nautilus and goto/tmp/disks-conf-hda1 then I can get into the drive, and view/use all my files, but if I click on the "computer" button I can't see the drive anymore.  So I know the drive works, I just want it to work under my normal login so I don't have to do anything extra everytime I want to use the drive.

---

### Post by brainchild187 on 2006-09-02
any takers?

---

### Post by bollix47 on 2006-09-02
Open a terminal(under applications - accessories) and type:

cat /etc/fstab

copy and paste the output in a reply here

---

### Post by pufuwozu on 2006-09-02
> **bollix47 said:**
> Open a terminal(under applications - accessories) and type:

cat /etc/fstab

copy and paste the output in a reply here

If it doesn't have an entry for /dev/hda1 then run these commands:```
sudo mkdir /media/windows
sudo gedit /etc/fstab
```Then add this at the end:```
/dev/hda1       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0    1

```That will make it so you can only read the drive.

---

### Post by brainchild187 on 2006-09-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1 /tmp/disks-conf-hda1 ntfs nls=utf8,unmask=0222 0    0
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by brainchild187 on 2006-09-02
so it's been 9 hours since someone last posted, I figured it'd be time to get this thing finished since it doesn't seem like it would be that hard of a thing for someone who's experienced to fix.  Help me out here guys

---

### Post by DrMilo on 2006-09-02
> **brainchild187 said:**
> so it's been 9 hours since someone last posted, I figured it'd be time to get this thing finished since it doesn't seem like it would be that hard of a thing for someone who's experienced to fix.  Help me out here guys

Follow the first set of instructions here (Mounting partitions with the script:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by brainchild187 on 2006-09-03
Thanks for that page link.  I didn't however use the script.....I just used the line  ro,auto,user,fmask=0111,dmask=0000  and it fixed my problem.  Once again thanks a lot, you guys rock :D

---

