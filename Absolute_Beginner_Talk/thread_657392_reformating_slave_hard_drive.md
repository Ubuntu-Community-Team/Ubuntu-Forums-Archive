---
title: "reformating slave hard drive"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-03
Hi

In my computer I have two hard drives. The master has my OS system on it and I would like to use my slave as a storage drive. However, I would like to first reformat the slave drive and I would also like to set it up so that when I select pictures or music in places it will access the slave drive files. Can someone help me do this? I am still trying to familiarize myself with the Ubuntu 7.10 system so please be explicit.

Thanks

---

### Post by tech9 on 2008-01-03
sure,

use gparted to format your slave drive

open terminal and type...

```
sudo apt-get install gparted
```if it is not already installed on your system...

then browse to...

System>Administration>Partition Editor

finally...

create a folder on your slave drive and call it pictures

When saving and retrieving pictures, just browse to your slave drive /Pictures directory

---

### Post by mrphud on 2008-01-03
Ok I installed partition editor but isn't there something about mounting and unmounting secondary drives? If I unmount wont the connection be lost?

---

### Post by taurus on 2008-01-03
You need to unmount the drive first before you can format it.  And since you will be using it with Ubuntu, I recommend you format it as ext3 filesystem.  Then, you can add an entry in /etc/fstab to have it mount automatically each time you boot.  And if you want to write to it, you need to change the ownership of the mount point of your second harddrive from root to your login name.

---

### Post by bwallum on 2008-01-03
Hello

You can use gparted to reformat and partition your slave drive.

I'm assuming you have taken everything off the slave that you want to keep. The following advice wipes your slave drive.

Open a terminal and type this command

```
gksudo gparted
```

If nothing happens you need to install gparted. Go to Applications>Add/Remove and search for gparted. Make sure you have All available Applications in the show: window (top right of Add/Remove window)

When in gparted identify your slave drive and format. You will need to think about the partition file type. If you want any Windows machines to access it go for FAT32. If you want a secure Linux partition go for ext3.

Regards
Bob

---

### Post by tech9 on 2008-01-03
> **taurus said:**
> You need to unmount the drive first before you can format it.  And since you will be using it with Ubuntu, I recommend you format it as ext3 filesystem.  Then, you can add an entry in /etc/fstab to have it mount automatically each time you boot.  And if you want to write to it, you need to change the ownership of the mount point of your second harddrive from root to your login name.

yes... I forgot to mention that you need to unmount the partition before formatting it.

and no you won't loose connection... you can always mount a partition again

---

### Post by logos34 on 2008-01-03
yu also need to [create a mount point and add fstab entry]("http://www.psychocats.net/ubuntu/mountlinux") for new partition:

example:

**sudo mkdir /media/hdb1** (or sdb1)


> **tech9 said:**
> create a folder on your slave drive and call it pictures

When saving and retrieving pictures, just browse to your slave drive /Pictures directory

That or create a symbolic link in your home directory pointing to directory on slave drive partition

e.g. 

**ln -s  /media/hdb1/music+pix <link>** 

or 'Pictures'... whatever you want to call the directory

---

### Post by tech9 on 2008-01-03
> **logos34 said:**
> That or create a symbolic link in your home directory pointing to directory on slave drive partition

e.g. 

**ln -s  /media/hdb1/music+pix <link>** 

or 'Pictures'... whatever you want to call the directory

nice suggestion!

---

### Post by mrphud on 2008-01-03
OK there are a few things that are still merky. I deleted and reformatted the secondary. The funny thing is is it took only like 5 minutes. It normally took longer on windows. The second is I can't find it anymore. It does not show up in the file manager.

---

### Post by logos34 on 2008-01-03
> **mrphud said:**
> OK there are a few things that are still merky. I deleted and reformatted the secondary. The funny thing is is it took only like 5 minutes. It normally took longer on windows. The second is I can't find it anymore. It does not show up in the file manager.

Read the post by taurus and the link I gave you

---

### Post by mrphud on 2008-01-03
Ok I realize I need to switch the usr for the device but I don't know how to do that. This is still very confusing to me. Also why after I formatted my device is there about 3 gigs used up?

---

### Post by logos34 on 2008-01-03
> **mrphud said:**
> Ok I realize I need to switch the usr for the device but I don't know how to do that. This is still very confusing to me. Also why after I formatted my device is there about 3 gigs used up?

by default ~5% disk space is reserved for root user

---

### Post by bwallum on 2008-01-04
Sorry, I've been away. Did you get your slave drive sorted?

Rgds
Bob

---

### Post by bwallum on 2008-01-05
To take ownership of the hard drive follow Taurus in this thread:-

[http://ubuntuforums.org/showthread.php?t=618503]("http://ubuntuforums.org/showthread.php?t=618503")

---

