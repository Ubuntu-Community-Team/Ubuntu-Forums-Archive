---
title: "[SOLVED] New HardDrive, How do I mount?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-22
I installed a 400gb HD and formated it with ext3, here are the results of "sudo fdisk -l":```
:~$ sudo fdisk -l
[sudo] password for chris:

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a423a42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5492    44114458+   7  HPFS/NTFS
/dev/sda2   *        5493       17717    98197312+  83  Linux
/dev/sda3           17718       18241     4209030    5  Extended
/dev/sda5           17718       18241     4208998+  82  Linux swap / Solaris

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2cdcc81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   83  Linux
```
Now how can I mount this (sdb1) as an extra "storage" drive so I can start filling it up with junk :) ?

---

### Post by kaginken on 2008-02-22
have you tried the 'mount' command?  

if you need some helpless with the mount command, try the man page

'man mount'

---

### Post by Rocket2DMn on 2008-02-22
Is it an internal drive?  You will need to edit your fstab file
You will need to edit and add a line like
```
sudo mkdir /media/*newmountpoint*
gksudo gedit /etc/fstab
```
```
/dev/sdb1 /media/*newmountpoint* ext3 defaults 0 0
```
Where *newmountpoint* is whatever you want to call it (no spaces please).
Then mount all:
```
sudo mount -a
```

Where I have written "defaults" you can modify it.  Check out this guide on how to fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by asmoore82 on 2008-02-22
^^this fstab stuff is excellent advice if you your new drive is internal;

If the drive is external; mounting/ejecting should be fairly "automagic" from "Places -> Computer"

I use an external 500GB Western Digital; and while using ext3 is great for Linux compatibility and speed,
you run into some good old school UNIX permissions decisions:
Rather than cook up an elaborate scheme to give my own username unlimited access to the drive,
I simply(with root access) created a folder on the drive named the same as my username and
gave myself ownership and full permissions to just that one folder;
more or less a makeshift "second home folder" for myself.

---

### Post by BassKozz on 2008-02-22
Thanks Rocket2DMn,
Worked like a charm :D

Just a quick follow up quesiton:
how come my NTFS partition (sda1) isn't listed in fstab, yet I can still navigate to it in Nautilus ?

---

### Post by asmoore82 on 2008-02-22
> **B/-\ssKozz said:**
> Thanks Rocket2DMn,
Worked like a charm :D

Just a quick follow up quesiton:
how come my NTFS partition (sda1) isn't listed in fstab, yet I can still navigate to it in Nautilus ?

[SIZE="2"][COLOR="Blue"]This is just an educated guess:[/COLOR][/SIZE]

This may be because the ntfs-3g drivers are FUSE-able (FUSE=Filesystem in USErspace)
but ext3 is old school *NIX.

---

### Post by Rocket2DMn on 2008-02-22
> **B/-\ssKozz said:**
> Thanks Rocket2DMn,
Worked like a charm :D

Just a quick follow up quesiton:
how come my NTFS partition (sda1) isn't listed in fstab, yet I can still navigate to it in Nautilus ?

It could be automatically mounted through HAL.  You can also specify in fstab if it's an internal drive so you can tell it exactly where to mount rather than it's default mount point.
ex:  I mount my windows partition at /media/windows
and my fstab looks like this for that partition:
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
NOTE that it may actually be already listed in fstab using a UUID rather than a /dev/sda* location.
```
ls -l /dev/disk/by-uuid
```
will show you the link between the uuid and the /dev location

---

### Post by BassKozz on 2008-02-22
> **Rocket2DMn said:**
> It could be automatically mounted through HAL.  You can also specify in fstab if it's an internal drive so you can tell it exactly where to mount rather than it's default mount point.
ex:  I mount my windows partition at /media/windows
and my fstab looks like this for that partition:
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
NOTE that it may actually be already listed in fstab using a UUID rather than a /dev/sda* location.
```
ls -l /dev/disk/by-uuid
```
will show you the link between the uuid and the /dev location
Here is the results of "*ls -l /dev/disk/by-uuid*":
```
~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-02-21 19:40 7da4ce12-3e10-4256-b9af-564667ed6120 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-02-21 19:40 848e4473-41c7-4d0a-acc5-4aca64117868 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-02-21 19:40 86C044FFC044F6C9 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-02-21 19:40 ad1c7fb1-a306-490d-8cd8-593420068929 -> ../../sda5

```
This is all WAY over my head, I think I'll just leave as is for now I was just curious.
> **B/-\ssKozz said:**
> Thanks Rocket2DMn,
Worked like a charm :D
Wait a second, I think I might have spoke too soon...
I don't have permission to write to it (**sdb1** mounted via fstab to **/media/extra_storage1/**) :(
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/extra_storage-permissions.png[/IMG]
Any idea's?

---

### Post by BassKozz on 2008-02-22
> **B/-\ssKozz said:**
> Wait a second, I think I might have spoke too soon...
I don't have permission to write to it (**sdb1** mounted via fstab to **/media/extra_storage1/**) :(
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/extra_storage-permissions.png[/IMG]
Any idea's?
Nevermind...
I had to ```
sudo chown -R <user> /media/extra_storage1/
```
where **<user>** is my username and **/media/extra_storage1/** is the mount point of ***sdb1*** that I set in fstab...
[LIST]
[*][B]Is this right, should I be using another variation?
[*]Is it ok to set my username as ownership of this mount/hard drive or will that make me susceptible to attacks[/B]?
[/LIST]

---

### Post by Rocket2DMn on 2008-02-22
From the guide:
> Linux native file systems: Use defaults or users. To change ownership and permissions, mount the partition, then use chown and chmod.
I've never had an extra ext3 partition myself, so I can't say for sure, but it seems like you have it right.  You can test it by unmounting the drive and remounting it to see that the permissions stuck.

---

### Post by BassKozz on 2008-02-22
Thanks for confirming Rocket...
> **Rocket2DMn said:**
> From the guide:
BTW, what is "the guide" ?

---

### Post by Rocket2DMn on 2008-02-22
> **B/-\ssKozz said:**
> Thanks for confirming Rocket...

BTW, what is "the guide" ?

The forum thread I listed in post #3 - [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
I suggest bookmarking that page, it's an excellent resource.  Just another one from my large list of bookmarks I use when helping out around here :)

---

