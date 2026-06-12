---
title: "Setting up 2nd disk, plus admin issues"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by PaulCheeseman on 2008-03-03
I have just added a second disk to my system, the OS runs from a 20Gb drive, 2nd is a 500Gb which will be used as shared storage (with 3 more added once I get this first working!)

the computer sees it, fdisk recognises it, ubuntu doesnt. I have no idea whatsoever how to set it up from command line, and cant find a way from the xubuntu GUI.

Help please!!

Is there an equivalent to 'Disk Management' in windows server ?

Also, I installed GParted, when I run it it asks for a password. I have tried both my own (I am in admin group) and the root password, all it says is:

[I]Failed to run GParted as user root.
The underlying authorisation mechanism (sudo) does not allow you to run this program.
Contact the system administrator.
[/I]

If I then try to run another system program, or GParted again after it fails first time, nothing happens. at all. I then have to reboot server before I can have another go at running GParted or what ever system program. Every attempt fails. So to me it seems that despite being in Admin group, I cant actually DO anything...

What do I have to do in order to log in as me, to the GUI, and manage basic tasks like disk addition, shares, users etc?? I am quite happy to learn command line usage, but at this moment dont have the time, and I need to get the server working, without spending months learning command lines for simple tasks that take very small amounts of time on both my windows and novell systems.

Regards

frustrated Paul :confused:

---

### Post by justleen on 2008-03-03
if fdisk sees it, all you need to to do is mount it.

```

$ sudo mount /dev/youdisk /media/yourdir

```

if its a ntfs disk, you need to add -t ntfs-3g, of -t vfat for a fat32 disk.

If that works, you can add it to /etc/fstab, to mount is at boot.

---

### Post by ruy_lopez on 2008-03-03
> **justleen said:**
> 
```

$ sudo mount /dev/youdisk /media/yourdir

```

That's assuming you formatted the drive. If you haven't, you'll want to run "mkfs.ext3" on the device (make sure it's the right device before proceeding).

---

### Post by justleen on 2008-03-03
yes.. true that.. i was assuming it has a formating of some kind! *blush*

---

### Post by PaulCheeseman on 2008-03-03
Spoke too soon ..... It wont mount with this code:

$ sudo mount /dev/sbd1 (from Gparted ) /media/storage1 (guessing this is what I want to call the volume?)

i get message

mount: mount point /media/storage1 does not exist 

is this the only way to mount a drive ?

Paul (less frustrated now :D )

---

### Post by LuisGMarine on 2008-03-03
You need to create that mount point, so do this:

```
sudo mkdir /media/storage1
```

then make sure you have the proper permissions, I use this for all my extra hdd's.

```
sudo chown -R username:username /media/storage1
```


Of course substitute username for your actual user name.  This gets all the permissions just right.

---

### Post by PaulCheeseman on 2008-03-03
> You need to create that mount point, so do this:

Code:

sudo mkdir /media/storage1

then make sure you have the proper permissions, I use this for all my extra hdd's.

Code:

sudo chown -R username:username /media/storage1


Of course substitute username for your actual user name. This gets all the permissions just right.

Ah, so the disk gets mounted to a pre made folder? ok, it worked anyway. 

Thanks for pointers guys, will make the other 3 disks easy! 

Paul (not frustrated now :) )

---

