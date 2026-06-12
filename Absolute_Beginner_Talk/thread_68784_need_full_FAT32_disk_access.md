---
title: "need full FAT32 disk access"
date: 2005-09-24
forum: Absolute Beginner Talk
---

### Post by dalani on 2005-09-24
I need to have full access to my FAT32 disk and despite following the HOW-TO instructions, I can only obtain read-only privileges to my hda1 disk. This disk is repository of my data and I need read/write acccess. Below is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext2    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb1       /media/windows2  vfat    iocharset=utf8,umask=000   0       0

any help would appreciated.

---

### Post by xmastree on 2005-09-24
[QUOTE=dalani]/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb1       /media/windows2  vfat    iocharset=utf8,umask=000   0       0[/QUOTE]That looks ok, can you write to hdb1?

what do you get for ```
ls -l /media/
``` See if the permissions for the mount points are different. FWIW, my FAT32 mount point (/mnt/shared/) is 777
```
drwxrwxrwx  17 root root  16384 1970-01-01 08:00 shared
dr-xr-xr-x   1 root root   4096 2005-08-15 06:41 windisk
```

---

### Post by Copter on 2005-09-24
hi

here my fstab entry on fat32 partition```

/dev/hdc8 /mnt/shared vfat rw,auto,users,exec,uid=copter,umask=0022 0 0
```it has been set so only i (copter) can read and write to it. others can only read (umask setting).

good luck!

copter :]

---

### Post by bored2k on 2005-09-24
[QUOTE=dalani]I need to have full access to my FAT32 disk and despite following the HOW-TO instructions, I can only obtain read-only privileges to my hda1 disk. This disk is repository of my data and I need read/write acccess. Below is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext2    defaults,errors=remount-ro 0       1
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
/dev/hdb1       /media/windows2  vfat    iocharset=utf8,umask=000   0       0

any help would appreciated.[/QUOTE]
 Please refer to my instructions here: [http://ubuntuforums.org/showpost.php?p=368701&postcount=3](http://ubuntuforums.org/showpost.php?p=368701&postcount=3)

---

### Post by dalani on 2005-09-24
[QUOTE=bored2k]Please refer to my instructions here: [http://ubuntuforums.org/showpost.php?p=368701&postcount=3](http://ubuntuforums.org/showpost.php?p=368701&postcount=3)[/QUOTE]

I did that first and the result is I can read and write to my hdb fine but not hda (read only). I don't want to move my files (should not have to).  I want user read-write access to that partition. 

BTW can I use samba to access if I make the folders in that partition shared.???




------------------------------------------------------------------------------------------------------------------------------------
developers take note: in 99% cases users migrate to ubuntu with intentions of keeping prior OS and data intact in dual boot mode.

---

### Post by dalani on 2005-10-01
Still not solved: 

my fstab has the following lines:

> /dev/hda1 /media/windows vfat iocharset=utf8,umask=000 0 0
/dev/hdb1 /media/windows2 vfat iocharset=utf8,umask=000 0 0

both line are identical for each of my FAT disks. Yet I can only read/write to hdb1!!
As asked previously, how do I access hda1 with full user read/write access???

any help would appreciated

---

### Post by katu on 2005-10-01
I edited the line in my fstab to look like this:
```
/dev/hda1       /media/hda1     vfat    defaults,user,umask=000        0       0
```
I remounted as a user and at first I thought I couldn't write to the drive as well. but then I noticed that the directories I was trying to use (My Documents and so on...) have user permissions set only to r-x. I changed this to rwx (using Krusader) and then I was able to write in the directory.  
My win installation is xp. I have no idea what the above can do to it so becareful.
[COLOR="Red"]update:[/COLOR]
you can also use 
chmod +w  "name of directory" 
to change the permissions. The procedure once implemented works after a reboot in my case. 
hope this helps.

---

### Post by SilentCacophony on 2005-10-01
Dalani, if you've previously had hda1 mounted with less permissions, I find that unmounting it first, before trying to remount all partitions works. On mine, the vfat partitions were mounted with root as the owner, and only one with write permission. So:

**sudo umount /media/windows** to unmount it

**sudo nano /etc/fstab** so that the umask=000 option is there, if not already ...

**sudo mount -a** to make the change

then **ls -l /media** should show *drwxrwxrwx* for the permissions.

Alternatively, a reboot should also work.

Edit -typos

---

### Post by dalani on 2005-10-08
[QUOTE=SilentCacophony]Dalani, if you've previously had hda1 mounted with less permissions, I find that unmounting it first, before trying to remount all partitions works. On mine, the vfat partitions were mounted with root as the owner, and only one with write permission. So:

**sudo umount /media/windows** to unmount it

**sudo nano /etc/fstab** so that the umask=000 option is there, if not already ...

**sudo mount -a** to make the change

then **ls -l /media** should show *drwxrwxrwx* for the permissions.

Alternatively, a reboot should also work.

Edit -typos[/QUOTE]

I did as above and the following message appears at terminal: 
```
umount: /media/windows: device is busy
umount: /media/windows: device is busy
```

??

---

### Post by dalani on 2005-10-08
[QUOTE=katu]I edited the line in my fstab to look like this:
```
/dev/hda1       /media/hda1     vfat    defaults,user,umask=000        0       0
```
I remounted as a user and at first I thought I couldn't write to the drive as well. but then I noticed that the directories I was trying to use (My Documents and so on...) have user permissions set only to r-x. I changed this to rwx (using Krusader) and then I was able to write in the directory.  
My win installation is xp. I have no idea what the above can do to it so becareful.
[COLOR="Red"]update:[/COLOR]
you can also use 
chmod +w  "name of directory" 
to change the permissions. The procedure once implemented works after a reboot in my case. 
hope this helps.[/QUOTE]
---------------------------------------------------------------------------
Here is what I get afer doing the fstab change:
```
$ chmod +w /media/windows
chmod: changing permissions of `/media/windows': Read-only file system
```

Still no write access so I'll reboot now and report later....BTW doing a chmod on a FAT filesystem doesn't seem possible since only  UNIX filesystems like ext2 keeps track of perms. I might be wrong on that..

---

### Post by SilentCacophony on 2005-10-08
> Still no write access so I'll reboot now and report later....BTW doing a chmod on a FAT filesystem doesn't seem possible since only UNIX filesystems like ext2 keeps track of perms. I might be wrong on that..

It would just be changing the permission on the *mount point* (/media/windows), which is just a directory within the linux filesystem.

> I did as above and the following message appears at terminal:

umount: /media/windows: device is busy 
umount: /media/windows: device is busy

That's a problem. Do you know if any program running is using the partition in question for anything? If so, try killing that app beforehand.

Shouldn't really be this much of a problem, so I'd think something else could be interfering, just don't know what it'd be. My only other idea would be to try in rescue mode commandline.

---

### Post by Mustard on 2005-10-09
You could always try 

```
sudo umount -l /media/windows
```

Thats the 'lazy unmount' switch, which can force a busy drive to unmount.

---

### Post by dalani on 2005-10-09
After the lazy mount which returned no error, I did the following:

$ sudo mount -a
mount: /dev/hda1 already mounted or /media/windows busy

and now I cannot access my FAT32 partition!!!

---

