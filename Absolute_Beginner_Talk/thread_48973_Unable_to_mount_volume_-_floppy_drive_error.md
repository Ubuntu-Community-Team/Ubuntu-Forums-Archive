---
title: "Unable to mount volume - floppy drive error"
date: 2005-07-14
forum: Absolute Beginner Talk
---

### Post by Run Away on 2005-07-14
[mntent]: line 13 in /etc/fstab is bad
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: I could not determine the filesystem type, and none was specified

Those are the details it gives me...
How do I fix line 13 or whatever?
Thanks in advance

---

### Post by Lord Illidan on 2005-07-14
Run => "sudo vi /etc/fstab" from a terminal (without the quotes), and give us the contents of the file.

---

### Post by Run Away on 2005-07-14
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdb1       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb2       /mnt/windows    vfat    uid=1000,gid=100,dmask=002,users 0 0
/dev/hdb1 <TAB> /mnt<location <TAB> vfat <TAB>rw,uid=1000,uid=1000 <TAB> 0 <TAB> 0
~
~
~
~
~
~
~
~
~
Type  :quit<Enter>  to exit Vim                               1,1           All

Thanks for the quick reply

---

### Post by Run Away on 2005-07-15
Can anyone else help?
What is line 13 supposed to read?
THanks

---

### Post by black hole sun on 2005-07-15
[QUOTE=Run Away]Can anyone else help?
What is line 13 supposed to read?
THanks[/QUOTE]
 Line 13 is bad, as it says; just delete it. It's not causing the problem, though; mount ignores bad fstab lines.

I'm not really sure why it can't be mounted, the line starting with /dev/fd0 is responsible for mounting the floppy and it looks right to me.

What you might try is changing "auto" to "vfat" on the same line (the one beginning with /dev/fd0)

---

### Post by Run Away on 2005-07-15
Okay I changed it and it reads:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdb1       /home           ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0
/dev/hdb2       /mnt/windows    vfat    uid=1000,gid=100,dmask=002,users 0 0
  

If I just close it will it save automatically?

---

### Post by Run Away on 2005-07-15
I'm an idiot, I can't edit from there.

sudo gedit /etc/fstab

I used that, got rid of line 13 and changed it to vfat not auto and voila, my floppy drive works.
Thanks everyone!

---

### Post by arjay1 on 2005-07-23
Run Away - if you are still subscribing to this thread.

Presumably, the change from auto to vfat allowed you to read win/dos disks?  Did you have to change it to ext2 or ext3 to read linux disks?  I'm old time win and dos and newbie to linux!

Thanks

---

### Post by black hole sun on 2005-07-23
[QUOTE=arjay1]Run Away - if you are still subscribing to this thread.

Presumably, the change from auto to vfat allowed you to read win/dos disks?  Did you have to change it to ext2 or ext3 to read linux disks?  I'm old time win and dos and newbie to linux!

Thanks[/QUOTE]
 arjay, I dont think any linux program will format a floppy disk as ext2 or ext3, I think everything uses FAT (including windows and linux)

---

### Post by arjay1 on 2005-07-23
Ah - thanks for the info.

The reason I asked is that I could not read any of the disks I put into my floppy even though it was mounted etc.  When I followed the posters suggestion and changed auto to vfat, I could read windows disks but still not read any linux disks.

Still no idea why!

---

### Post by black hole sun on 2005-07-23
[QUOTE=arjay1]Ah - thanks for the info.

The reason I asked is that I could not read any of the disks I put into my floppy even though it was mounted etc.  When I followed the posters suggestion and changed auto to vfat, I could read windows disks but still not read any linux disks.

Still no idea why![/QUOTE]
 How did you make the linux disks? With what program?

---

### Post by arjay1 on 2005-07-23
A couple were formatted with Kfloppy and 2-3 others were from various previous distros I had lying about which I used for test purposes.

The Kfloppy formatted ones work just fine in another Ubuntu computer on the same network so I know they are Ok (the floppy drive on the other computer can also read the old disks).  

I can read all the disk using CLI commands.  It is the mounting and reading in /media/floppy that is the problem I think.  I created a directory in /media called floppya and then modified the line in fstab as follows:

/dev/fd0        /media/floppya  auto    rw,user,noauto  0       0

I mounted the drive as normal and it reported it as being mounted.  However, a couple of times when mounting and umounting I have had conflicting reports that - for example - the drive was reported as already umounted as far as mtab was concerned but not fstab.  I don't know the difference, or what mtab is for - perhaps you could help there?  Is it anything to do with mtools - that was previously installed I think but I removed it (possibly not all?)

I tried changing auto to vfat and was able to read an old windows disk, but not the ones formatted in Kfloppy.

Does this help?

---

### Post by black hole sun on 2005-07-25
[QUOTE=arjay1]A couple were formatted with Kfloppy and 2-3 others were from various previous distros I had lying about which I used for test purposes.

The Kfloppy formatted ones work just fine in another Ubuntu computer on the same network so I know they are Ok (the floppy drive on the other computer can also read the old disks).  

I can read all the disk using CLI commands.  It is the mounting and reading in /media/floppy that is the problem I think.  I created a directory in /media called floppya and then modified the line in fstab as follows:

/dev/fd0        /media/floppya  auto    rw,user,noauto  0       0

I mounted the drive as normal and it reported it as being mounted.  However, a couple of times when mounting and umounting I have had conflicting reports that - for example - the drive was reported as already umounted as far as mtab was concerned but not fstab.  I don't know the difference, or what mtab is for - perhaps you could help there?  Is it anything to do with mtools - that was previously installed I think but I removed it (possibly not all?)

I tried changing auto to vfat and was able to read an old windows disk, but not the ones formatted in Kfloppy.

Does this help?[/QUOTE]
 Sorry for not getting back to you.

mtab shows _only_ the drives/partitions/disks that are currently mounted. fstab shows what is supposed to mount at boot-up, and is a general information pool for when you manually mount things. You never modify mtab, only fstab.

About "mtools"; this creats ms-dos floppies. I would reinstall that if I were you, it could probably help us solve your problem.

Anyway; find out what filesystem kfloppy is formatting disks with. Try looking in the options for kfloppy (I'm not using KDE atm so I can't look myself)

EDIT: okay after some googling, kfloppy appears to by default format with the DOS filesystem.

Try changing "auto" or "vfat", whichever is there,  to "msdos"

---

### Post by arjay1 on 2005-07-25
Nice to hear from you.  I'll try your suggestion in a couple of hours - I have to go down into my basement and fire up the problem computer.  At the moment I am tied up with a samba problem on my first one!!.  

(This linux stuff ain't so easy.  I can't believe that after all these years of development a distro can't monitor a floppy drive and automount/umount it when it detects the presence of a disk.  Ubuntu can do it for a USB camera, why not a flopy drive?

As to Kfloppy - it offers three options for the file system to format: DOS, ext2 and Minux.  I chose ext2 which I presumed was the linux format.

Anyway - I'll try changing vfat to mdos and see what happens.

---

### Post by black hole sun on 2005-07-25
[QUOTE=arjay1]Nice to hear from you.  I'll try your suggestion in a couple of hours - I have to go down into my basement and fire up the problem computer.  At the moment I am tied up with a samba problem on my first one!!.  

(This linux stuff ain't so easy.  I can't believe that after all these years of development a distro can't monitor a floppy drive and automount/umount it when it detects the presence of a disk.  Ubuntu can do it for a USB camera, why not a flopy drive?

As to Kfloppy - it offers three options for the file system to format: DOS, ext2 and Minux.  I chose ext2 which I presumed was the linux format.

Anyway - I'll try changing vfat to mdos and see what happens.[/QUOTE]
 You chose ext2? Well that explains it. Not exactly a usual floppy format, it certainly wouldn't be readable in windows.

Given this new knowledge, dont use "msdos" use "ext2".

---

### Post by arjay1 on 2005-07-26
Problem was - neither linux or windows were readable via konqueror on one machine but everything worked fine on the other (they are duplicate kubuntu set ups).  Also I had no trouble reading and writing to the disks using CLI.  That is what I am still using on this box although the other one is fine.

---

