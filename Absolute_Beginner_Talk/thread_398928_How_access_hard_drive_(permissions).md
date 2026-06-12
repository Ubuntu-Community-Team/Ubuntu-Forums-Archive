---
title: "How access hard drive (permissions)"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by vatechtigger on 2007-04-01
Hello Guys,

I am in Day 2 of Ubuntu usage. I have managed to set up a dual boot with one 200 gb IDE drive half windows/Half ubuntu.

I then added 2x 200 GB serial drives. I formated one in windows to be half NTFS for windows/half Fat32 Both of which ubuntu recognizes and can read/write to (NTFS read only)

In ubuntu then I tried to use Gparted to format the second drive to Ext3 to use as storage for linux only. The format completes, and I can see the drive in Places browser, but can not write to it (Cant create folders in file browse, says I don't have the proper permissions) Note I am logged in as user when I did the format and tried to write. So how do i get permission? :( I would think that since I formated it with my user, permission should be inherent. Thanks in advance!

Shawn

---

### Post by dstew on 2007-04-01
Your permissions are given when you mount the drive. If you want to use the drive as a regular user, you need a mount instruction in /etc/fstab that looks something like this:

/dev/hdb2 /mnt/ext3 ext3 uid=1000,gid=100 0 0

There are lots of options when it comes to granting permissions at mount time. See **man mount** for more detailed information. This site is also good:

[http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)

---

### Post by vatechtigger on 2007-04-01
thanks for pointing me in the right direction. Since I was doing it in Gparted, it was mounted automatically but I wasnt significant enough to access it. I logged in as root, changed the permissions to allow my user, then logged back in as user and all is well. Trying to aviod the terminal as much as possible until I get my bearings and can visualize exactly what I am doing. :lolflag:

---

