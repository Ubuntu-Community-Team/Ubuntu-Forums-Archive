---
title: "You know who i am? Im a noob too! And.. I need help (expected)"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Rizla on 2006-09-04
I feel like an idiot having to come here every 10 mintues to post about my lastest happenings.  But i'd like you to know, i've made some progress so far.  Im getting familiar with the new system.. very slowly (ive been at this for the past 10 hrs)

I'm currently having a problem mounting the FAT32 partition I made during the install.  I've successfully mounted the XP partition, and another one of my data drives (although, its not having the desired result).

Here's how my fstab file looks currently looks like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /XP_Drive     ntfs    nls=utf8,umask=0222       0       0
/dev/sda5       /Data_Drv     ntfs    nls=utf8,umask=0222       0       0
/dev/hda7       /Share_Drv        vfat    iocharset=utf8,umask=000  0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

The drive in question is /dev/hda7.  Its the partition i want to use to swap files between windows and linux.  When i mounted the other parititions using the "sudo mount -a", XP_Drive showed up on my desktop and so did "/Data_Drv" although it isnt showing up as "/Data_Drv", but rather "Sata Drive".  

First things first, how come I cant get the hda7 to show up as Share_Drv on my desktop? 

Secondly, why is the Data_Drv showing up as SATA DRIVE?

If i could get help with these two current issues i'd be grateful.  I'm even willing to repay you by offering you some future problems that you can help me solve.  Thanks

:cool:

---

### Post by nrwilk on 2006-09-04
Did you create a /Share_Drv/ directory?  The mountpoint must already exist before you try to mount the drive there.

I'm not sure how far you've gotten on this, so this is just a shot in the dark.

nrwilk

---

### Post by bodhi.zazen on 2006-09-04
> how come I cant get the hda7 to show up as Share_Drv on my desktop?
1. I think in order for you to do this automatically you need to change your mount point to:
/media/Data_Drv

2. I once saw a potential solution, have not tried this:
In a terminal:
```
cd ~/Desktop
ln -s /Data_Drv Data_Drv
```

You may need to re-start gnome for the second solution to work.

The first is probably preferable.

---

### Post by Rizla on 2006-09-04
Yea I did.. I see it in my directory along with the other ones.  Any idea why the Data_Drv is showing up as SATA DRIVE?

---

### Post by Rizla on 2006-09-04
So does that mean i should create a new dircetory called Share_Drv in the media folder?

---

### Post by bodhi.zazen on 2006-09-04
> **Rizla said:**
> So does that mean i should create a new dircetory called Share_Drv in the media folder?

Not sure Re: sata drive question.

Otherwise, yes, but I am not following which directory you are wanting on your desktop.

Assuming Share_Drv:
```
sudo umount Share_Drv
sudo mv Share_Drv /media/Share_Drv
```

Now:
```
sudo mount /dev/hda7 /media/Share_Drv
```

If this works, update fsdisk
```
/dev/hda7       /media/Share_Drv        vfat    iocharset=utf8,umask=000  0       0
```

Simmilar instructions for /Data_Drv ?

---

### Post by Rizla on 2006-09-04
> **bodhi.zazen said:**
> 1. I think in order for you to do this automatically you need to change your mount point to:
/media/Data_Drv

2. I once saw a potential solution, have not tried this:
In a terminal:
```
cd ~/Desktop
ln -s /Data_Drv Data_Drv
```

You may need to re-start gnome for the second solution to work.

The first is probably preferable.


Alright, i created that folder in the media folder and changed fstab to reflect the new path.  I logged out and logged back in, but only XP_Drive and SATA Drive show up.  SATA DRIVE should be Data_Drv.  Still no Share_Drv though.. Also, how come XP_Drive shows up as "/XP_Drive"?

---

### Post by bodhi.zazen on 2006-09-04
1. Starting with the obvious, did you unmount and then re-mount your drives?

2. Do you have a usb device pluged in (memory card, camera, anything?) showing up as sata drive?

3. What is the mount point of XP_Drive?

---

### Post by Rizla on 2006-09-04
> **bodhi.zazen said:**
> 1. Starting with the obvious, did you unmount and then re-mount your drives?

2. Do you have a usb device pluged in (memory card, camera, anything?) showing up as sata drive?

3. What is the mount point of XP_Drive?

1.) yes, i did a sudo umount -a (with the obvious ones not unmounting since they were in use i.e /home, /usr, etc)

2.) Nope, no usb devices plugged in or have been plugged in thus far

3.) I solved the /XP_Drive issue by moving the mount point to the media folder as well.  /media/XP_Drive  I unmounted all the drives then mounted again and it came up properly reading "XP_Drive"

Do i not have the right parameters set for the fat32 drive (Share_Drv)?

Here's my new fstab output:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/XP_Drive   ntfs    nls=utf8,umask=0222       0       0
/dev/sda5       /media/Data_Drv   ntfs    nls=utf8,umask=0222       0       0
/dev/hda7       /media/Share_Drv  vfat    iocharset=utf8,umask=000  0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


```

---

### Post by bodhi.zazen on 2006-09-04
I'm sorry but I can not follow.

What is the problem? is it only with the Share_Drv? and is it that Share_Drv shows up as a SATA drive?

---

### Post by Rizla on 2006-09-04
> **bodhi.zazen said:**
> I'm sorry but I can not follow.

What is the problem? is it only with the Share_Drv? and is it that Share_Drv shows up as a SATA drive?

Sorry its easy to be confused by whats going on, i sure am.

The SATA Drive that shows up should be Data_Drv.  Its an NTFS partition I had with a bunch of my movies, music, etc.  I can access all my data.  Im just curious to know why its not being mounted as "Data_Drv".  Its just a stickler, but not a major issue.

My main issue is why the Fat32 parition i created in hda7 isnt mounting as Share_Drv.  Everything looks right.  I can even unmount the drive successfully, but its not showing up on my desktop like the rest...

---

### Post by Rizla on 2006-09-04
Just for my own clarification.  WHen a drive or partition is mounted does that mean it will show up on the desktop as a harddrive icon? Or will it just be a folder?  

If i browse to the media folder they show up there as folders, but on my desktop i only have two disk drives showing up: SATA DRIVE and XP_Drive

---

### Post by bodhi.zazen on 2006-09-04
Thank you for clarification.

> Just for my own clarification. WHen a drive or partition is mounted does that mean it will show up on the desktop as a harddrive icon? Or will it just be a folder?

If i browse to the media folder they show up there as folders, but on my desktop i only have two disk drives showing up: SATA DRIVE and XP_Drive

Err.. yes/no/maybe ???
/media is a directory or "folder" and contains other directories, say XP_Drive.
As a directory XP_Drive will show up as a "folder" when you browse to the media directory (folder) independent of mount status of your partition.

With me so far?
On your desktop, if a drive is mounted it wll show up on the desktop as a harddrive icon.
If the drive is mounted the directory of /media/XP_Drive will NOT be empty.
If the drive is not mounted the directory /media/XP_Drive will be empty.

> The SATA Drive that shows up should be Data_Drv. Its an NTFS partition I had with a bunch of my movies, music, etc. I can access all my data. Im just curious to know why its not being mounted as "Data_Drv". Its just a stickler, but not a major issue.

My main issue is why the Fat32 parition i created in hda7 isnt mounting as Share_Drv. Everything looks right. I can even unmount the drive successfully, but its not showing up on my desktop like the rest...

I am not sure what is wrong. 

Unmount the drive and then:

Try modifying the lines in fstab:
```
/dev/sda5       /media/Data_Drv   ntfs    auto,users,rw      0       0
/dev/hda7       /media/Share_Drv vfat    auto,users,rw      0       0
```

and then:
```
sudo chown root:users /media/Data_Drv
sudo chmod 770 /media/Data_Drv
```
If you are not as paranoid as I am you can use chmod 777 rather then 770.

Ditto for /media/Share_Drv

Re-mount.

---

### Post by Rizla on 2006-09-04
> **bodhi.zazen said:**
> Thank you for clarification.



Err.. yes/no/maybe ???
/media is a directory or "folder" and contains other directories, say XP_Drive.
As a directory XP_Drive will show up as a "folder" when you browse to the media directory (folder) independent of mount status of your partition.

With me so far?
On your desktop, if a drive is mounted it wll show up on the desktop as a harddrive icon.
If the drive is mounted the directory of /media/XP_Drive will NOT be empty.
If the drive is not mounted the directory /media/XP_Drive will be empty.



I am not sure what is wrong. 

Unmount the drive and then:

Try modifying the lines in fstab:
```
/dev/sda5       /media/Data_Drv   ntfs    auto,users,rw      0       0
/dev/hda7       /media/Share_Drv vfat    auto,users,rw      0       0
```

and then:
```
sudo chown root:users /media/Data_Drv
sudo chmod 770 /media/Data_Drv
```
If you are not as paranoid as I am you can use chmod 777 rather then 770.

Ditto for /media/Share_Drv

Re-mount.


Thanks for the clarification.  I tried what you suggesed, but to no avail.  I actually lost permission to the Data_Drv (aka SATA DRIVE).  Im wondering if its because its NTFS.  Once i changed that back to what it was before, it was all set.

I think im going to throw in the towel for today.  Linux has thorougly whipped my *** today.  2 installs, 2 updates, countless tweaking.. and i can now finaly listen to some mp3's and watch some movies.. aaah they make it so easy.

I'll have to look more into this drive business, i dont even see my cdrom on my desktop...

---

