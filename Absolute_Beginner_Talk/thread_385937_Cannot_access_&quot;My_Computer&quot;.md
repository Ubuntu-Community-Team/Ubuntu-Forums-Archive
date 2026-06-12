---
title: "Cannot access &quot;My Computer&quot;"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Brick86 on 2007-03-16
Hi, I just downloaded and installed ubuntu this morning and I like it so far. I am running as a second os (so when I start the computer it asks which I want... Ubuntu or Windows XP).  I made a partition on the install and gave ubuntu 50% of the drive. When I go into my computer in ubuntu I get this message.  I want to no how to fix it.  The message is attached.  Please notice that I am very new and will not easily understand difficult ways to solve it.  Lamens terms would be great.  Thanks!

---

### Post by taurus on 2007-03-16
Looks like you want to mount XP from Ubuntu.  Here's a guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Otherwise, open a terminal, Applications -> Accessories -> Terminal, and post the output of this command here.

```
sudo fdisk -**l**
```
(That would be lower case letter **l** as in **l**arry.)

---

### Post by Brick86 on 2007-03-16
Sorry but 1) I would follow the directions but I would get to a point in them when I was told I couldn't do something.  2) They were a little complex for me.  I tried going into the dev folder but when I got to hda "any number really" it would say cannot display location is not a folder.  Whats going on?

---

### Post by taurus on 2007-03-16
Can you post the output of this command from a terminal?  I will walk you through it.

```
sudo fdisk -l
```
Use your password, the same one that you're logged in, when it asks for one.

---

### Post by Brick86 on 2007-03-16
Thanks.  

kyle@kyle-laptop:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3910    31407043+   7  HPFS/NTFS
/dev/hda2            7271        7296      208845   88  Linux plaintext
/dev/hda3   *        3911        7129    25856617+  83  Linux
/dev/hda4            7130        7270     1132582+   5  Extended
/dev/hda5            7130        7270     1132551   82  Linux swap / Solaris

Partition table entries are not in disk order
kyle@kyle-laptop:~$

---

### Post by taurus on 2007-03-16
So, you want to mount /dev/hda1.

Open a terminal and type

```
gksudo gedit /etc/fstab
```
Scroll down to the bottom and add this line to it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
```
Save it.  Now from the same terminal, create a new mount point and mount it.

```
sudo mkdir /media/hda1
sudo mount -a
df -h  <-- You should see /dev/hda1 mounted to /media/hda1 from the output.
```

---

### Post by Brick86 on 2007-03-16
Ok, when you say to paste the code at the bottom do you mean of the terminal or the note pane that pops up?

---

### Post by taurus on 2007-03-16
The notepad with a bunch of codes already in it.  Just add this line to the end of it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
```

---

### Post by Brick86 on 2007-03-16
When I paste the code in that opens up the notepad I can paste the code you supplied into the notepad and save it but on the terminal it keeps saying... 
(gedit:8796): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by taurus on 2007-03-16
It is just a warning so don't worry about it.  Did you paste that line to /etc/fstab?  Can you post the output of this command from a terminal here?

```
cat /etc/fstab
```

---

### Post by qpwoeiruty on 2007-03-16
It's OK to continue. It's just a minor [bug](https://launchpad.net/ubuntu/+source/gksu/+bug/23917).

---

### Post by Brick86 on 2007-03-16
kyle@kyle-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=44977558-f7e5-4cd2-ad56-f8d5e70c3c0a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=15935570-31b0-4645-94a0-7c5f841fa474 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0   0
kyle@kyle-laptop:~$

---

### Post by taurus on 2007-03-16
Looks good.  Now, run these three commands from that terminal.

```
sudo mkdir /media/hda1
sudo mount -a
df -h
```
So do you see your /dev/hda1 mounted to /media/hda1 from the output of the last command?

---

