---
title: "All I want is read/write access on my new Ext3 partition..."
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Giggity on 2006-10-03
*Sigh*  I thought that the "rw" option in /etc/fstab gave read-write access on a mounted partition.  I must have not understood correctly.  I still can't create folders on my new Ext3 partition, which I created for use as document/media storage.  I've tried adding the defaults and user options as well, but no success.

I can see it mounted at /media/storage, but there's just a lost+found folder (which I can't access), and I can't create new folders without sudo, which I was trying to avoid (since this partition won't be used for system files).

I've tried searching for help on this subject, but I get nothing but NTFS mounting instructions, which I've already successfully accomplished, but NTFS just fragments too much!  I'm sorry if this is too simple to ask.  Here's my fstab, with the partition I'm talking about in bold.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  	<options>  			<dump>  <pass>
proc            /proc           proc    	defaults        		0       0
/dev/sda2       /               ext3    	defaults,errors=remount-ro	0       1
/dev/sda5       none            swap    	sw              		0       0
**/dev/sda4	/media/storage	ext3		rw				0	0**
/dev/hda        /media/cdrom0   udf,iso9660 	user,noauto     		0       0
# NTFS Partitions to be mounted using the NTFS-3G module
/dev/sda1	/media/ntfs-c   ntfs-3g     	silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other    0    0
/dev/sda6	/media/ntfs-d   ntfs-3g     	silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other    0    0
/dev/sdb1	/media/ntfs-e   ntfs-3g     	silent,umask=0,locale=en_US.utf8,no_def_opts,allow_other    0    0
```

---

### Post by orb9220 on 2006-10-03
This the entry for my seprate /home partition
/dev/hda4   /home      ext3    defaults        0       2
I don't think your fstab is correct.
Try
/dev/sda4 /media/storage  ext3	defaults       0	0

and do you have a folder in /media called storage? you need to make one if not.

---

### Post by Jussi Kukkonen on 2006-10-03
Well, you may have correct filesystem permissions, but if the files/directories are owned by root, you won't be able write to them as a user -- this is by design...

Use *chown* to 'own' a directory created by root in the mounted partition, and try to write there...

---

### Post by Giggity on 2006-10-03
Good show, Jussi!  I navigated and executed:
```
rob@rob-desktop:~$ cd /media/storage
rob@rob-desktop:/media/storage$ sudo chown -R rob ./
```
That's working so far.  I was able to create a new folder called "newfold" in /media/storage.  I'll tell you later if I was able to save anything important in it.

Thanks a lot, when do you folks sleep?!

---

### Post by jaboua on 2006-10-03
However, you should consider giving the lost+found folder back to root

---

### Post by CatKiller on 2006-10-03
The way I've had similar is to have all the folders owned by root, but everyone has read/write permissions. But then I am using a multi-user system.

---

### Post by Giggity on 2006-10-03
> **jaboua said:**
> However, you should consider giving the lost+found folder back to rootI'll do that.  I'll also look up what the lost+found folder actually *is*, so I'll know why!

Thought I'd let y'all know that I have successfully saved a large new file directly to the new partition, and it reads back perfectly fine, so thanks for the help!

---

### Post by bodhi.zazen on 2006-10-03
There are several issues:

First you should keep your mount point owned by root:root

Second, the ownership and permissions of the mount point will change automatically when you mount a partition.

Third, IMO the easiest fstab entry is:

```
/dev/sda4	/media/storage ext3 users,rw,auto 0 0
```

Change auto to noauto if you do not want the partition to be mounted at boot.

Don't believe me? try it with my fstab entry.

umount /media/storage
sudo chown root:root /media/storage

Edit fstab.

ls -l /media | grep storage
Who owns the mount point ?

Now:
mount /media/storage (no sudo)
ls -l /media | grep storage
Now who owns the mount point? Permissions?

---

### Post by Giggity on 2006-10-04
Interesting, following your instructions, it seems that even though the mount point is owned by root, ownership of the mounted partition changes to me once the drive is mounted.  Is this the correct interpretation?

Thanks for the lesson!
```
rob@rob-desktop:~$ umount /media/storage
rob@rob-desktop:~$ sudo chown root:root /media/storage
Password:
rob@rob-desktop:~$ ls -l /media | grep storage
drwxr-xr-x 2 **root root**  4096 2006-10-03 00:29 storage
rob@rob-desktop:~$ mount /media/storage
rob@rob-desktop:~$ ls -l /media | grep storage
drwxr-xr-x 6 **rob  root**  4096 2006-10-03 14:22 storage
```

---

### Post by bodhi.zazen on 2006-10-04
Yes. It is a finer point of fstab I am trying to disseminate.

The ownership and permissions of the mount point are modified at the time of the mount, so if you set fstab correctly all your problems are solved.

If you understand this it is much easier. Some make it out to be harder then it has to be.

[[color=blue]How to fstab[/color]](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by crispy_420 on 2006-10-04
An easy way I found has been to use nautilus as root to allow all to read/write.

sudo nautilus

Then navigate to directory and change permissions. That is just my way but then again I love using a gui.

---

### Post by TheMono on 2006-10-04
Use gksudo instead of sudo for graphical programs. And that would work fine to change permissions, exxcept that nautilus doesn't do recursive permissions (yet). You can always try thunar?

"sudo apt-get install thunar"

---

### Post by Giggity on 2006-10-05
I like the way bodhi instructed me to use... running Nautilus/Konqueror as root would allow me to really screw up my system if I made a mistake.

Thanks for the assistance!

---

