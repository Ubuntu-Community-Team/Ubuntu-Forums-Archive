---
title: "Mounting my OS X partition"
date: 2006-12-02
forum: Apple PPC Users
---

### Post by galvatron1983 on 2006-12-02
Ive just managed to successfully install Kubuntu onto my PowerBook G4 after successfully partitioning the HD. Unfortunately my OS X partition didnt mount automatically. Id like to be able to move and share files with the OS X partition. This is my partition table from fdisk...

[IMG]http://i14.tinypic.com/2upy8ib.png[/IMG]

What terminal command would I need to mount the OSX partition, I think it should be /dev/hda3 from that table. 

Any help you could give me would be great....

---

### Post by linear on 2006-12-02
If you just want to read files, something like this should do the trick:

```
sudo mkdir /media/mac
sudo mount -t hfsplus -o "ro" /dev/hda3 /media/mac
```If you want to write as well (reportedly risky), remove **-o "ro"**, and you will likely need to adjust permissions on the OS X side.

---

### Post by pindar on 2006-12-03
If you want to *share* files between OS X and linux, you have to make sure that your UID (User ID) on both systems is identical. It's easier to adjust this on the linux side. In OS X, the first user is always assigned an ID of 501. Assuming you have the same username on both systems, run this command in Ubuntu:

```
 sudo usermod -u 501 <YOUR_USERNAME>

```

Moreover, if you want to *write* to your OS X partition, you have to disable journaling on it; newer linux kernels will not mount a journaled filesystem read/write. After this, mounting is as easy as
```
 sudo mount -t hfsplus /dev/hda3 /mnt/mac
```
(you have to create the mountpoint by simply making a directory /mnt/mac). You can also include /dev/hda3 in your /etc/fstab and have it mounted automatically, but in practice, I've always had some trouble with this after some use -- it works wonderfully for some weeks, and then suddenly, the drive doesn't mount etc.

HTH

Thomas

---

### Post by galvatron1983 on 2006-12-03
Thanks for the help guys, Im able to access my files in Kubuntu and use them perfectly. There are a couple of things I need to sort out though. I have a shortcut to the os x partition on my dekstop, but when I log into Kubuntu and open the folder its empty. This suggests to me that the os x partition dosnt mount on boot up.

What commands do I need to input into the Terminal to get the os x partition to mount on start up?

---

### Post by EuroCity on 2006-12-04
You should probably edit **/etc/fstab** to include the OS X partition:

```
nano /etc/fstab
```

and then insert a line like this one:

```
/dev/hda3   /media/macosx   hfsplus   defaults   0   0
```

which will [automatically](https://help.ubuntu.com/community/AutomaticallyMountPartitions) mount the OS X partition as read-only if it's HFS+ Journaled.

BTW, it would be cool to also have a safe Mac OS Extended Journaled *write* support enabled in future Linux versions!

---

### Post by galvatron1983 on 2006-12-04
Here is what my fstab looks like. Where should I insert that line?

[IMG]http://i16.tinypic.com/4dq3gwy.png[/IMG]

---

### Post by EuroCity on 2006-12-04
^^^ Ah, so you already have a similar entry: then, obviously, you should keep that one, instead of overwriting it.

The **/media/mac** directory already exists, of course...?

Maybe you should replace **auto** with **hfsplus**...

Anyway, if you want to write to the OS X partition, you must disable journaling from within Disk Utility whenever you reboot into Kubuntu.

---

### Post by trash on 2007-05-09
> **pindar said:**
> If you want to *share* files between OS X and linux, you have to make sure that your UID (User ID) on both systems is identical. It's easier to adjust this on the linux side. In OS X, the first user is always assigned an ID of 501. Assuming you have the same username on both systems, run this command in Ubuntu:

```
 sudo usermod -u 501 <YOUR_USERNAME>

```

Thomas

This should come with a warning... I now have no sudo rights for my user as 1000 doesn't exsist in password file.
How do i correct the damage?


EDIT: REBOOT MAKES IT BETTER:)

---

