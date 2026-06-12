---
title: "Cdrom not working in 6.10"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Castigate on 2006-11-16
Hi, I just installed Ubuntu 6.10 and my cdrom isnt working.  I can see it in filebrowser but when I click on it I get a message saying "Unable to mount the selected volume.  mount: special device /dev/hdc does not exist".  Then I right click on it and try to mount volume and get this message "Unable to mount the selected volume.  mount: special device /dev/hdc does not exist"  Can anybody help me out?](*,)

---

### Post by Bachstelze on 2006-11-16
Please paste the output of

```
ls /dev/hd?
```

---

### Post by Castigate on 2006-11-16
Wow that was fast:-D   The output is /dev/hda  /dev/hdb  /dev/hdd
hda is the main hardrive that contains  windows xp , swap and ext3 root partitions.  hdb contains ext3 home directory.  hdd is another hardrive im using in windows.

---

### Post by Bachstelze on 2006-11-16
Now that's weird, your CD drive *should* be in there... Are you sure it's properly connected and detected by your BIOS ?

---

### Post by Castigate on 2006-11-16
Yeah Im sure it's connected.  I used it to install 6.10 plus when i boot to windows it works fine.  The only thing I wasn't sure about was maybe when I partitioned in setup I messed up.  I did manual partition and it asked to choose /media??? partition cant remeber.  I selected /home and made that hdb.  Maybe I was supposed to make a partition for cdrom?

---

### Post by Castigate on 2006-11-16
I reinstalled Ubuntu with no luck.  I also checked the disk before installing and it had no errors.  Anyone have any ideas?  Would appreciate it alot](*,)

---

### Post by Bachstelze on 2006-11-16
Well, you just need to figure out what the block device name of your CDROM drive is. How are your drives connected (all of them, IDE or SATA, on which connector, master or slave, etc.)

---

### Post by Castigate on 2006-11-16
I got it to work:-D   I had to make the cdrom slave and hdd1 master on the secondary ide connetion.  Thanks for the replies. Now I can goto sleep =D>

---

