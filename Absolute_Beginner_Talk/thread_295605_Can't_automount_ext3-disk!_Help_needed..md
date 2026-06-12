---
title: "Can't automount ext3-disk! Help needed."
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by Binnikemasken on 2006-11-08
Hi. As the title mentioned, I cannot mount my second disk.
I formated it and now it's an ext3. All I can do is mount it manually, but then it isn't read/writeable.
I added this line to the fstab, but still it doesn't work:
*/dev/hdb   /media/    ext3  defaults     0   0*

All it says is: 
Unable to mount the selected volume. 
error: device /dev/hdb1 is not removable

error: could not execute pmount

This is driving me nuts and I have been searching for an answer, but cant find anything. I appreciate help.
Thanks!

---

### Post by taurus on 2006-11-08
I see a couple of things wrong in your /etc/fstab.  If you only have on partition of your second harddrive, then it should have been /dev/hdb1, NOT /dev/hdb.  Also, you want to mount it somewhere like /media/share, NOT /media/...

So, either edit your /etc/fstab or paste the output of this command from a terminal then!

```
sudo fdisk -l
```

---

### Post by dannyboy79 on 2006-11-08
> **Binnikemasken said:**
> Hi. As the title mentioned, I cannot mount my second disk.
I formated it and now it's an ext3. All I can do is mount it manually, but then it isn't read/writeable.
I added this line to the fstab, but still it doesn't work:
*/dev/hdb   /media/    ext3  defaults     0   0*

All it says is: 
Unable to mount the selected volume. 
error: device /dev/hdb1 is not removable

error: could not execute pmount

This is driving me nuts and I have been searching for an answer, but cant find anything. I appreciate help.
Thanks!

is this a removable drive is my first question because you don't want to put removable devices into your fstab since there identifier can change? if not, it's most likely because you don't have the partition number on the hdb. post the output of [code=]fdisk -l[/code]
and also [code=]sudo cat /etc/fstab[/code] and i'll help ya out. just as an example, this is my extra ext3 partition that I use for storage: /dev/sda1       /home/daniel/400gb-ext3 ext3    defaults        0       2
 but yours of course would be something like /dev/hdb1 and then whereever you want to mount it. I wouldn't mount it in media, i think that's where removable devices get automounted and then what happens is that it puts an icon on your desktop which is like a shortcut to the folder unless that's what you're aiming for. so if you can figure it out without posting the output of the above commands than cool, if not, please post what I ask and i'll help ya get it working.

---

### Post by Binnikemasken on 2006-11-08
Thanks a lot for trying to help me out.
I made some minor things to the fstab (hdb1 instead of hdb, and changed the mount dir). But still it didn't work. The error message said I had to be root to mount the drive.

fdisk -l:
[I]Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10011    80413326    7  HPFS/NTFS[/I]

That's how it looks. And apparently it's still a NTFS system. Guess that's the problem?
And now since it didn't format and change the system correctly, how can I do that right?

---

### Post by taurus on 2006-11-08
Let's have a look at your /etc/fstab again if you don't mind!

```
cat /etc/fstab
```

---

### Post by dannyboy79 on 2006-11-08
you should be able to install gparted and use that. do sudo aptitude install gparted then after that, it should show up under system, administration, gparted I think. you can use gparted to format the ntfs partition to ext3 assuming there's nothing on it that you don't want.

---

### Post by Binnikemasken on 2006-11-09
[I]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults          0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw                0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto   0       0
/dev/hdb1       /haxbax/       ext3    defaults          0       0
[/I]
This is how my fstab looks now. Should I change the pass or something?
Now I'm also pretty sure the disk is ext3.

fdisk:
[I]Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10011    80413326   83  Linux
[/I]

It's getting mounted. But still with permissions, so I can't do a thing.

---

### Post by anaconda on 2006-11-09
You can write to it as user root
type in terminal
sudo nautilus
to get file-browser with root rights.

or you could edit your fstab-entry so that you have write rights. Loojk here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
the fat32 oartititon is mounted with read/write rights, so you can just use the same options in your fstab-file then in the example above..

---

### Post by taurus on 2006-11-09
> **Binnikemasken said:**
> [I]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults          0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw                0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto   0       0
/dev/hdb1       /haxbax/       ext3    defaults          0       0
[/I]
This is how my fstab looks now. Should I change the pass or something?
Now I'm also pretty sure the disk is ext3.

fdisk:
[I]Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10011    80413326   83  Linux
[/I]

It's getting mounted. But still with permissions, so I can't do a thing.
So you have converted your /dev/hdb1 from NTFS to ext3 now.  May want to modify the last line of your /etc/fstab a little...

```

/dev/hdb1  /haxbax  ext3  defaults  0  1

```
And if you want others to be able to read and write to that directory, /haxbax, then set the permission from a terminal with

```
sudo chmod -R 777 /haxbax
```

---

### Post by dannyboy79 on 2006-11-09
> **anaconda said:**
> You can write to it as user root
type in terminal
sudo nautilus
to get file-browser with root rights.

or you could edit your fstab-entry so that you have write rights. Loojk here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
the fat32 oartititon is mounted with read/write rights, so you can just use the same options in your fstab-file then in the example above..

anaconda, this is not true, there are totally different mount options for ext3 and vfat (also called fat32), ext3 doesn't except uid, gid, and lots of other that vfat uses. you need to read up on man fstab, then that refers to man mount. i used to just listten to what people would tell me to do, and it wouldn't work so I finally thought, why take some1's word for something when I just go to the bible and understand it better and learn what to do on my own. trust me, now I use "man" for a lot of things and I am on my way to learning linux way faster than when I started by simply posting questions because now I know the correct and for sure right answer.

---

### Post by bodhi.zazen on 2006-11-09
> **dannyboy79 said:**
> is this a removable drive is my first question because you don't want to put removable devices into your fstab since there identifier can change? 

dannyboy79: what you say is partially true.

You can give removable devices a label and mount by label

You can then put an entry in fstab> LABEL=flash_drive /mnt/flash auto users 0 0

This should not interfere with pmount or automount, although I use the cli with an alias:

> alias doc='mount LABEL=flash_drive && abiword /mnt/flash_drive/document_name.abw'
alias uflash='unmount LABEL=flash_drive'Alias in ~/.bashrc

You can mount and unmount from a "mini command line" faster then clicking with a mouse.

I hope you find this information at least interesting, if not helpful  !

---

### Post by bodhi.zazen on 2006-11-09
dannyboy79: what you say is partially true.

You can give removable devices a label and mount by label

You can then put an entry in fstab> LABEL=flash_drive /mnt/flash auto users 0 0

This should not interfere with pmount or automount, although I use the cli with an alias:

```
alias doc='quote mount LABEL=flash_drive && abiword /mnt/flash_drive/document_name.abw'
alias uflash='unmount LABEL=flash_drive'
```

You can mount and unmount from a "mini command line" faster then clicking with a mouse.

I hope you find this information at least interesting, if not helpful  !

Permissions for FAT and NTFS are set with uid=x, gid=y, and/or umask=xyz.

Permissions for linux native file systems aer set with chown and/or chmod xyz <mount.point> with the FS mounted.

For rw ntfs I prefer [ntfs-3g](http://doc.gwos.org/index.php/Write_ntfs)

---

### Post by Binnikemasken on 2006-11-13
Yeay! It's working as it should now. The "1" in the pass-column solved it all. Thank you all for the help! I appreciate it.

---

