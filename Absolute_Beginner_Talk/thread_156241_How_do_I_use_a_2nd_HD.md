---
title: "How do I use a 2nd HD?"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-04-06
Hey all,

Bios detects and sees my 2nd HD but I can't seem to navigate to it through Ubuntu.  I know in Win-dohs it would have a drive letter...  Where is it in Ubuntu?

gs

---

### Post by aysiu on 2006-04-06
You need to mount it.
Has the hard drive been formatted in any way?

---

### Post by taurus on 2006-04-06
Well, you need to mount it first before you can access it!  I will assume the second harddrive is the slave in which case is known as /dev/hdb1 in Linux and it is Windows XP which uses NTFS as a filesystem...  Open a terminal, Applications -> Accessories -> Terminal, and type
```

sudo mkdir /media/windows

```
Now, you need to edit your /etc/fstab so it will mount automatically upon boot.  Again, from the same terminal, do
```

sudo cp /etc/fstab /etc/fstab.bak <-- make a backup copy in case you screw up the original...
sudo gedit /etc/fstab

```
Then, add this line to the end of the the file and save it...
```

/dev/hdb1  /media/windows  ntfs  udf,defaults,umask=0222  0  0

```
Now, run these two commands from the same terminal and see if your second harddrive is on the list...
```

sudo mount -a
df -h

```

---

### Post by guysmiley on 2006-04-06
Thanks Tauro!

Can I be a stickler and ask what the umask numbers represent?

gs

---

### Post by taurus on 2006-04-06
0 means all permissions while 2 means only read.  Since it's a NTFS filesystem, reading from it is the safest because if you write to it, you will soon file out you won't be able to boot XP anymore.  So, if you want to share a partition (read and write) between Ubuntu (or Linux) and XP, better make it as fat32 (or vfat in Linux).  Then, you can mount it as "umask=0000" and everybody can read or write to it.

---

### Post by guysmiley on 2006-04-06
Thanks again Taurus!

As soon as I'm done making a backup of my system I'll give this a shot.  Thanks again!

gs

---

### Post by taurus on 2006-04-06
You're welcome and good luck.

---

