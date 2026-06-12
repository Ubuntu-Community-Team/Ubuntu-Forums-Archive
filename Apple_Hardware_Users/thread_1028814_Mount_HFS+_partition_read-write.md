---
title: "Mount HFS+ partition read-write"
date: 2009-01-02
forum: Apple Hardware Users
---

### Post by DanielCarrera on 2009-01-02
I have successfully setup dual boot with Ubuntu (Intrepid) and Mac OS X. I have an HFS+ partition which I want to use as the "home" partition for both OS X and Ubuntu. So it would be a shared home partition.

This partition is formatted as HFS+ **without journaling** so Ubuntu should be able to mount it read-write. But for some reason, it is mounting it read-only.

Am I sure that journaling is off? Yes, very sure. On OS X I run **diskutil** and it says that journaling is disabled. More tellingly, if I boot using the **Ubuntu LiveCD** I can instantly mount the partition **read-write**!

So Ubuntu is perfectly capable of mounting this partition read-write, but for some reason the Ubuntu installed on my disk doesn't want to. I have tried mounting the partition through the GUI and through the command line, and I get the same result. The command I'm using is:

> mount -t hfsplus -o rw /dev/sda3 /home2

This command gives no error. The partition is mounted successfully, but if you try to write a file it says that you can't because the partition is mounted read-only.

If I replace "hfsplus" by just "hfs" I get an error, so that's not it.

What things have I changed in Ubuntu since I installed it? Not much. I installed a couple of hours ago. Let's see...

* I installed the 208 updates.
* I change the user id of my regular user account to match the one from my user account at Mac OS X. The idea is that I'll need this if I am to share the home partition between the two OS's.

I think that's pretty much it.

Does anyone have any ideas?

---

### Post by mkvnmtr on 2009-01-02
The command you use looks like what I use to mount my external hard drive but I don't use rw. I set permissions in the storage device manager as rwx. Read write and execute. I believe  the storage manager was a program I downloaded from Synaptic.I really don't seam to have it right because I have to mount it each time but I can read write and transfer files from my Ubuntu to the harddrive and then to mac and of course back. With Hfsplus I can read write and use everything on both systems. To change ownership to you try the command [sudo chown -R me:me Music]. Me is my log in name. You will use yours. Music is the file. Your will use the partition you wish to have ownership of. Then you can change the permisions..

---

### Post by pxwpxw on 2009-01-02
**DanielCarrera**

The problem is that you are mounting on /home2, which is  owned by root.

If you mount on a sub-directory of your ubuntu $HOME directory
(or ~), it works (but you will have to mount as root).
Here I mounted om ~/aaa.
```

pxw@wdc:~$ sudo mount -t hfsplus -o rw /dev/sdb7 aaa
pxw@wdc:~$ mount | grep sdb7
/dev/sdb7 on /home/pxw/aaa type hfsplus (rw)
pxw@wdc:~$ mkdir aaa/pxwfolder
pxw@wdc:~$ touch aaa/foo3
pxw@wdc:~$ ls -l /home/pxw/aaa/
total 0
-rw-rw-rw- 1 root root 0 2009-01-03 12:35 foo
-rw-r--r-- 1 pxw  pxw  0 2009-01-03 12:35 foo2
-rw-r--r-- 1 pxw  pxw  0 2009-01-03 12:41 foo3
drwxrwxrwx 1 root root 3 2009-01-03 12:29 New Folder
drwxr-xr-x 1 pxw  pxw  2 2009-01-03 12:50 pxwfolder

```

---

### Post by DanielCarrera on 2009-01-03
Strangely, it seems to work now. And as far as I can tell I'm not doing anything different. As far as I can tell, all that's happened is that I rebooted.

pxwpxw's suggestion seemed odd, I had never heard of a partition being mounted read-only because the mount directory was owned by root. But I decided to test anyways, in case it is some odd peculiarity of HFS+. So I rebooted and did the following:

1) Mounted the partition from the GUI, so it goes to /media/Home and to my surprise it was mounted read-write.

2) So I remounted the partition from the terminal onto a directory owned by the regular user, and again, it worked. The partition was mounted read-write.

3) So I decided to test again with /home2 and to my astonishment, it worked! The partition was once again mounted read-write.

I have no idea why it didn't work before, but I'm glad it works now.

---

### Post by pxwpxw on 2009-01-03
I think that ownership and permissions were also a factor.

---

### Post by DanielCarrera on 2009-01-03
> **pxwpxw said:**
> I think that ownership and permissions were also a factor.

Possible but not likely. I always tested writing as root and I took a close look at the permissions. But no matter, it works now and I really appreciate the help you guys offered. Thanks.

---

### Post by cyberdork33 on 2009-01-05
you can also try repairing the filesystem as it will sometimes mount read only if there is a problem.

---

