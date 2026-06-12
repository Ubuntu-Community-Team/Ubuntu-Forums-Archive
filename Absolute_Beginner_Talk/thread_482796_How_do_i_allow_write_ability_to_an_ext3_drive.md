---
title: "How do i allow write ability to an ext3 drive?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Vodkayum on 2007-06-24
My ext3 formatted drive will only allow the root to access it, this sucks. Anyone know how to fix this?

---

### Post by 5-HT on 2007-06-24
Do you have it listed in your /etc/fstab? If so you can add the 'user' option to allow users to mount the drive in addition to root (default is nouser).

e.g., ```
device mount_point ext3 defaults,user 0 1
```If it's not in your fstab, you can explicitely mount it with the user option (or give pmount a try, but you'll need to add an entry in your fstab)

```
mount -t ext3 -o user [device] [directory]
```cheers,

---

### Post by Thorun on 2007-06-25
GREAT!
That was exactely what i was looking for!

Another question (without hijacking this thread) is: Does the fstab change if i update the kernel, or if i install NTFS-3g to enable rw on my ntfs-partitions?

when i add the defaults,user to the ext3-partition in fstab - will it become user:user in stead of root:root (when typing ls -l) ?

---

### Post by Inxsible on 2007-06-25
> **5-HT said:**
> (or give pmount a try, but you'll need to add an entry in your fstab)
 
cheers,
 
I dont think pmount requires an entry in the fstab. I never have entries in fstab for my external drives. If you have entries in fstab, it tries to automount them (depending on the options you have in there) and it gives a bunch of errors.
 
I use pmount for external drives and regular mount combined with fstab for my internal drives.

---

### Post by logos34 on 2007-06-25
> **Thorun said:**
> GREAT!
That was exactely what i was looking for!

Another question (without hijacking this thread) is: Does the fstab change if i update the kernel, or if i install NTFS-3g to enable rw on my ntfs-partitions?

when i add the defaults,user to the ext3-partition in fstab - will it become user:user in stead of root:root (when typing ls -l) ?

kernel updates won't change fstab but ntfs-3g will after you enable write capability to the windows partititons

---

### Post by 5-HT on 2007-06-25
> **Inxsible said:**
> I dont think pmount requires an entry in the fstab. I never have entries in fstab for my external drives. If you have entries in fstab, it tries to automount them (depending on the options you have in there) and it gives a bunch of errors.
 
I use pmount for external drives and regular mount combined with fstab for my internal drives. Yeah, my bad. :) Total lapse of thinking there...pmount specifically lets users mount drives without an fstab entry.

[quote=Thorun] when i add the defaults,user to the ext3-partition in fstab - will it become user:user in stead of root:root (when typing ls -l) ? [/quote]

Nope. Those are individual file ownerships and mounting the drive as any specific user will not change them. If you want to change file owners, chown  will do the trick.

cheers,

---

### Post by bodhi.zazen on 2007-06-25
I would not have done it quite like that, but well done.

Just for clarification :

1. Pmount is a command line tool that allows one to mount devices/partitions as a user outside of fstab (you can edit a config file and mount internal hard drives / partitions with pmount if you like). Pmount is supposed to look at fstab as a reference, but in my experience it is best to leave devices out of fstab if you want to mount them with pmount. Pmount mounts on /media.

pmount <device> mount_point
pumount mount_point

2. Ubutnu uses gnome-volume-manager to automount removable devices. Gnome volume manager also does not like it if you list the devices (other then CD/DVD) in fstab. Xfce uses thunar. I have not tried to mix and match thunar with fstab.

3. read/write depends on file system. vfat/ntfs = set permissions at time of mount or in fstab.
LInux native (ext2/3, reiser, etc) = set permissions at time of mount or after mounting with chown and chmod.

See also : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

