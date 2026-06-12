---
title: "to mount or unmount?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by tenny56 on 2006-07-11
ok, very new to this, so please be patient.

i want to try and acess the part of my hard drive that has my windows file in it through the ubuntu desktop.

was told i had to unmount or something, but did not have much explanation. can some one please spend some time explaining this to me.

i am so new, i really dont understand anything, including the terminal. so please step by step instructions would be really good.

tenny

---

### Post by mogelhead on 2006-07-11
If you installed Ubuntu after you installed Windows, the windows drive should already be accessible.

Can you please post to the forum the output of this command:
```
cat /etc/fstab
```

Else, try the [mountwindows]("http://psychocats.net/ubuntu/mountwindows.php") guide.

To temporarily be able to access files on your windows hard drive you have to mount it. When you are ready you unmount it.

If you always wanto have access to your windows files when you start ubuntu, you configure your /etc/fstab file (see the guide above).

---

### Post by Zimmer on 2006-07-11
Step by step instructions 
[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)
When entering commands in a Terminal you will often need to use the Sudo command.

Sudo. In an effort to discourage users from logging in as root, the sudo command allows users to perform specific tasks as administrators without having to use the root password or logging in as root. As long as you put "sudo" in front of a command, Linux will recognize your command as a root-like command and ask you for your user password.

The commands fo r mounting and UNmounting are mount  and umount (not a typo ..umount)
Think of mounting as pointing a device to a directory location so that the file manager can read the files on it...

---

### Post by tenny56 on 2006-07-11
chris@chris-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
chris@chris-desktop:~$



does this look right to you??

---

### Post by Zimmer on 2006-07-11
> **tenny56 said:**
> chris@chris-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
chris@chris-desktop:~$



does this look right to you??

It is a display of the contents of your etc/fstab file which gives info for what drives, partitions and so on to mount at boot and the boot location.

In a Terminal type
sudo fdisk -l

and that should list the partitions on your disk and give you info on the filesystem on the partition.

---

### Post by tenny56 on 2006-07-11
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         432       18241   143058825    7  HPFS/NTFS
/dev/sda2               1         431     3461976    b  W95 FAT32
/dev/sda3           18242       30216    96189187+  83  Linux
/dev/sda4           30217       30401     1486012+   5  Extended
/dev/sda5           30217       30401     1485981   82  Linux swap / Solaris


it notes down this ^ but still not sure what i am looking at or doing,  
have tried using the pussycat how to guide.  but not sure if i am doing it right

---

### Post by mlind on 2006-07-11
Your fstab entry could look like
```

/dev/sda1       /media/C        ntfs    ro,nls=utf8,umask=0007,gid=46    0       0

```

You must be on 'plugdev' group to get read/write permissions. You can also remove gid=46 and use umask=0222 if you don't want to use plugdev as a group.

/media/C mount point must exists, so create it using
```

sudo mkdir /media/C

```

---

### Post by Zimmer on 2006-07-11
/dev/sda1 * 432 18241 143058825 7 HPFS/NTFS
/dev/sda2 1 431 3461976 b W95 FAT32

Ok, this tells me you have an NTFS partition /dev/sda1   and that you also have a FAT32 partition  /dev/sda2

What 'exactly' have you tried from the guide? I don't want to tell you something that will make things worse :)

---

### Post by tenny56 on 2006-07-11
i followed the guide as using the ntfs partion.  got down the the end where it said "now remount"  

think i need a dummies guide to...

---

### Post by Zimmer on 2006-07-11
so you have issued the command 
sudo mount -a    ?

if so, on your desktop go to places>Computer  and see if you have the partition listed there...

What does cat /etc/fstab   tell you now?

---

### Post by tenny56 on 2006-07-11
hey, hey,hey

i think i have done it.  it was trying to get my head around not having a c: thing.

thank you for your time and patience

tenny

---

### Post by Zimmer on 2006-07-11
That's ok. It is always best to do as much reading/research on something before you start bashing away at the terminal ;) Past reading informed me that Writing to NTFS partitions from Linux was a bit dodgy , to say the least.That is why you are always advised to create a FAT32 partition as a gate way to swapping files between your Windows install and your Linux partition.

---

### Post by tenny56 on 2006-07-11
yeah,  have been reading, and reading.  putting into motion is tricking, after using windows for years, it is a case of trying to relearn what you almost remember from DOS

thank you for your help once again.

---

