---
title: "Harddrive partition  protection for Users?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Thorun on 2007-06-02
I would like to make my Ubuntu Bullet Proof from deleting important files and other stuff. 

I know how to remove the permissions from the user (and if i want to install something and stuff like that - i can login as root).
(well - found out that the root can't login from the login-screen. Which means, that i really don't know how to login as a root?)

But as user - i still have 2 harddrive partitions (the one with my WinXP and another data-backup drive) that i want to make "access denied" from the user account. 

I have read something about chmod but that seemed  ... what's it called... when something takes a long time and is difficult. 


If it can be done, what do i have to do?

---

### Post by akudewan on 2007-06-02
There are quite a few approaches one could try. If its a separate partition, then it can be mounted without write access. Or better yet, you can keep it unmounted and mount it only when you need to.

Another approach is to change the permissions and ownership of the folders and files. chown and chmod will do this.

Let me know if I should elaborate on any method.

---

### Post by Thorun on 2007-06-02
The Mount-part sounds interesting. And with this approach i could mount eg. the data-drive with a sudo-command? and unmount it after use? (or maybe a reboot could do it).

with
```
sudo fdisk -l
```
i get:

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          10       80293+  de  Dell Utility
/dev/hda2   *          11        1431    11414182+   7  HPFS/NTFS
/dev/hda3            1432        2404     7815622+  83  Linux
/dev/hda4            2405        7296    39294990    f  W95 Ext'd (LBA)
/dev/hda5            2405        2599     1566306   82  Linux swap / Solaris
/dev/hda6            2600        3619     8193118+  83  Linux
/dev/hda7            3620        7296    29535471    7  HPFS/NTFS
```


And it's the hda2 and the hda6 i need to have "access denied" to  - unless i chose to mount it temporarily. 



/Rune
Denmark.

---

### Post by akudewan on 2007-06-02
To mount these partitions manually, you can remove the entries from /etc/fstab. Do *sudo gedit /etc/fstab* and simply put a # in front of the lines with hda2 and hda6. If you reboot, the drives will not be automatically mounted.


To mount the partitions you can use the command:
```

sudo mount -t ntfs-3g /dev/hda2 /media/windows -o rw

```
and
```

sudo mount -t ext3 /dev/hda6 /media/linux -o rw

```

and to umount:
```

sudo umount /dev/hda2

```

The -o rw will tell it to mount with read and write permissions, so that you can copy files. And if you're not using ntfs-3g, then replace it with ntfs.

And replace the */media/windows* with the folder you generally use.

---

### Post by Thorun on 2007-06-02
Thank you wery much! Now it works like a charm.

some minor questions:
1. Can i somewhere check whether i'm using NTFS or NTFS-3G?
 My NTFS-partition is made from Windows System manager - but i installed on Ubuntu, the applicaiton that could mount the NTFS-drive with Synaptic. I think it's called: NTFS Configuration Tool. 

2. If i - in User Privileges - remove the mark at: Administer the system, is it then possible for the user to use the sudo-command?


And i promise that i won't post anymore questions in this thread :D

---

### Post by akudewan on 2007-06-02
You're most probably using nfts-3g since you're installed ntfs-configuration-tool. Its not a separate filesystem, but it just provides write support.

As for that "Administer the system" thing, I think it will disable sudo. Not sure, since I use KDE, not Gnome.

I'll be glad to answer any more questions :)

---

### Post by rusty4r on 2007-06-02
Yes it is possible for the user to use sudo but another user shouldn't know sudo's password

---

### Post by Skrynesaver on 2007-06-02
Actually Rusty4r each user who can sudo uses their own password to authenticate.  There isn't a single/central password to the sudo facility, however there is to the su command, this attempts to log on as root if the root user exists and demands the root password, just sayin'

---

### Post by rusty4r on 2007-06-02
> **Skrynesaver said:**
> Actually Rusty4r each user who can sudo uses their own password to authenticate.  There isn't a single/central password to the sudo facility, however there is to the su command, this attempts to log on as root if the root user exists and demands the root password, just sayin'

Thank you for correcting me, I thought su and sudo were the same just from going between Fedora and Ubuntu.

---

### Post by rusty4r on 2007-06-02
so as he asked, can you determine who can sudo and who cannot

---

### Post by Thorun on 2007-06-02
I have just testet the sudo command with a new user on my system. 
The User was setup as a desktop-user - which means access to all except "administrate the system". I typed different sudo commands to test if i could change something: 
```
sudo fdisk -l
``` didn't give me anything. It promptet for password - and i typed in the user-pass. and then nothing happened.
```
sudo gedit /etc/fstab
``` didn't give me anything either.

---

