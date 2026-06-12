---
title: "How do I change permission on ext3 formatted drive"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by kpel on 2007-04-22
I have a drive I formatted to ext3 from the LiveCD (Feisty) before I installed Ubuntu.  Unfortunately I cannot read or write from the drive (though I can mount it) because it apparently formatted with the permission set to root.  Not that it is a surprise, considering I was doing it from the LiveCD without a defined user.  Hey, I'm new. :? 

How do I set it so I can have access to the drive?  I don't want to create a root user just to change the permissions, and I've already tried to do it by using

```
gksudo nautilus
```

though it didn't get me anywhere.  I started to get a bit worried I'd break something as I wandered around the filesystem as root.

I've read posts that used chown, fdisk and mount commands from the terminal, but that's still a bit over my head at the moment.  Since the drive is currently empty I was hoping the easiest way would just be to reformat it and set the permission correctly.

---

### Post by jhenager on 2007-04-22
Install Gparted from System>Administration>Synaptic Package Manager.
Make sure the drive is not mounted.
Delete any partitions, create as desired and format with EXT3.

---

### Post by heimo on 2007-04-22
Formatting it won't help. Check these:
[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by kpel on 2007-04-22
It would appear that I can't format it again anyway as GParted insists on mounting the volume and opening a file browser window each time I try to, and then gives me an error because the drive is mounted.  :confused: 

The other problem is that my fstab file only shows the filesystem drive and my two optical drives.  Any other suggestions?

---

### Post by heimo on 2007-04-22
```
sudo fdisk -l
```
lists partitions. Then you can add it to fstab manually. You can also format it from command line if necessary, if you need to repartition, always boot from live-CD and never touch mounted partitions.

---

### Post by kpel on 2007-04-23
fstab- l gives me this for the drive I'm having trouble with:

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9964    80035798+  83  Linux

Disk /dev/sdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```

Unfortunately the fstab file uses UUIDs for the drives which fstab -l does not list.  Here's the fstab for the filesystem:

```
# /dev/sdd1
UUID=cd625eb3-59d2-4f3c-82f9-8ba61e9698c1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdd5
UUID=ced277a2-f4a6-48f3-b9d9-dca192afc478 none            swap   
```

I think I'm just going to make a root user, log in, right click the mounted drive and change the permissions and then nuke the root user account.  Don't know if it'll work, but I'm running out of ideas.

---

### Post by Woody@N87 on 2007-04-23
i'm new at this as well but here is what i just did, it worked (pre req) the drive is formatted ext3 and mounted at /media/hdf1,  (hdf1) is the name i gave the hard drive.

sudo -i  

this will get you to the root prompt (use your administrative user password when prompted)

chown -hR dave /media/hdf1

  -hR refers to the mounted drive and subdirectories ( i think) and the dave is my username.  After these two commands were completed i was able to use the second hard drive without any problems.   Good Luck,
Mike

---

### Post by kpel on 2007-04-23
> i'm new at this as well but here is what i just did, it worked (pre req) the drive is formatted ext3 and mounted at /media/hdf1, (hdf1) is the name i gave the hard drive.

!

\\:D/ 

I'd hug you if I could. ;)


This is what I ended up using, just for my own reference (I'll likely need the command again) and for anyone else with this problem:

```
sudo chown -hR kevin /media/disk
```

---

### Post by Unetwork on 2007-04-23
Great thanks did have the same problem ;)

---

