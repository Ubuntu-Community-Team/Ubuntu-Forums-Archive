---
title: "How to CD to 2nd HD"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by ICUR2Ys on 2007-05-31
I have 2 drives in my computer.  I formatted the second drive and it has the mount point /store.
My second drive /hdb1.

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1337    10739421   83  Linux
/dev/hda2            1338        4012    21486937+  83  Linux
/dev/hda3            4013        4208     1574370   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux
dace@dace-desktop:~$ cd .hdb1/store
bash: cd: .hdb1/store: No such file or directory
dace@dace-desktop:~$

---

### Post by sessine on 2007-05-31
```
cd /store
```

The filesystem dosen't care about the physical disk as long as it has been mounted.

---

### Post by ICUR2Ys on 2007-05-31
I guess the question should have been how do I mount it?

---

### Post by sessine on 2007-05-31
Typing
```
sudo mkdir /store
sudo mount /dev/hdb1 /store
```

will mount the disk (you only need the mkdir the first time).  If you want to have it auto-mount at startup you need to edit the /etc/fstab file.

Adding the line:
```
/dev/hdb1 /store ext3 defaults 0 0
```
to /etc/fstab should automount it for you (From [http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux") )

---

### Post by ICUR2Ys on 2007-05-31
OK thanks.  I learned two things.  I thought that when I made the mount point /store that it was a directory.  Second i bought A Practical Guide to Linux , etc. And couldn't find mount as a command.

So now I was able to make a subdirectory /store/backups and verified by changing to it.  I appreciate the help.   Thank you very much.

---

### Post by taurus on 2007-05-31
/store is a directory.

```
man mount
```

---

### Post by ICUR2Ys on 2007-05-31
When I first entered cd /store  I got the message that it doesn't exist.  So I entered

sudo mount /dev/hdb1 /store I again got the message that it doesn't exist.  So then I entered

sudo mkdir /store and I didn't get the error message  So I reentered


sudo mount /dev/hdb1 /store and this time it worked.  That is why I assumed that the mount point must not be a directory and didn't become one until the mkdir command was used.

Also, if the mount point /store was a directory I would assume I would get an error message.

Where am I going wrong here?

---

### Post by taurus on 2007-05-31
You tried to mount /dev/hdb1 to /store but there was no such /store directory.  That's why you needed to create it first before you could mount something to it.  Let's say you now decide to mount /dev/hdb1 to /media/hdb1.  You first need to create /media/hdb1 before you can mount to it or you will get the same error message as when you tried to mount it to /store.

---

### Post by ICUR2Ys on 2007-05-31
OK I have it now.  I appreciate the input.  Thanks.

---

### Post by HotShotDJ on 2007-05-31
Just a quick note:  I strongly urge you to mount your second hard drive in a manner consistent with the standard [Linux Filesystem Hierarchy](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html).  One way to easily do this is by creating the directory /mnt/store and mounting the drive there.

---

### Post by ICUR2Ys on 2007-06-01
OK I have done that I think.  This is the system now.

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1337    10739421   83  Linux
/dev/hda2            1338        4012    21486937+  83  Linux
/dev/hda3            4013        4208     1574370   82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux
dace@dace-desktop:~$ 

Thank you everyone for all of your help I appreciate your sharing with me.  I have learned a lot about this now.

---

