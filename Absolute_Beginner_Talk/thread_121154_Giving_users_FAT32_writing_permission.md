---
title: "Giving users FAT32 writing permission?"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by Heretic Monkey on 2006-01-24
Alright, finally got Ubuntu almost working the way i want to to (with a CRAP-load of help from most of the people at these forums), but there's still one thing that eludes me.....

How do i give a normal user permission to write files to another FAT32 partition?  I can put files there through the root account, but i want to be able to write from my user account GUI.  I've tried accessing the Xserver through my Root account, then right clicking on the partition to enable the permissions, but whenever i check the "Write" box for the names, it automatically UN-checks them and makes a beeping sound.

It seems simple enough, but the check-box won't stay...... checked.......  Is there a trick i'm missing with this, or should i become proficient in managing/copying/moving/deleting/creating files through  the root command line?

---

### Post by Turin Turambar on 2006-01-24
type:

sudo gedit /etc/fstab

Look where your VFAT drive is (e.g. hda4). Replace "defaults" with "rw,users,gid=users,umask=000"

---

### Post by aysiu on 2006-01-24
Or see the fourth link of my signature.

---

### Post by Heretic Monkey on 2006-01-24
Great, thanx for the help Turin

---

