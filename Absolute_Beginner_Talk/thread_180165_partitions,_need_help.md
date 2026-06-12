---
title: "partitions, need help"
date: 2006-05-21
forum: Absolute Beginner Talk
---

### Post by IsKall on 2006-05-21
Hi all!

I have made an partition (ext3) to make more space for the linux, but how do I make it accessible as the / parttion ?

my fstab is:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    noauto,user,exec,ro,umask=0222 0       0
/dev/hda2       /media/hda2     ntfs    noauto,user,exec,ro,umask=0222 0       0
/dev/hda5      	/media/hda5	ext3    defaults,users  0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I did read about this on "man mount" but there way to much information, I only want to the partition to be accessible as the "/" partition, so I can save some things there.

I'm trying to change hda5, so it is accessible as the "/" partition) i, my last try was:

```

/dev/hda5      	/media/hda5	ext3    defaults,users  0       0

```

Anyone who can help me?

---

### Post by Ramses de Norre on 2006-05-21
You want that partition to be /? Is ubuntu installed to it? It doesn't seem a good idea to me, maybe you should just use it as /home?

If you're sure about it make the line to ```
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
```

And set another mountpoint for /dev/hda4.

---

### Post by IsKall on 2006-05-21
no I don't want to make it to an "/", only want to make it accessible, without typing any password at System > Disks :)

I am sry for my lack of description (or what it is called). :???:

---

### Post by Mustard on 2006-05-21
[QUOTE=IsKall]no I don't want to make it to an "/", only want to make it accessible, without typing any password at System > Disks :)

I am sry for my lack of description (or what it is called). :???:[/QUOTE]

Have you created the mount point /media/hda5 ?
```
sudo mkdir /media/hda5
```
After you edited the fstab file did you sudo mount -a ?
```
sudo mount -a
```

Please show any error messages you get when you do sudo mount -a.

I assume you mean you want it to mount automatically at boot so you don't need to use System > Disks, as the Disk Administration tool will always require a password.

---

### Post by IsKall on 2006-05-21
yeah exactly! How do I do that?

---

### Post by IsKall on 2006-05-21
ah okey

---

### Post by IsKall on 2006-05-21
I tried that now, it shows the hda5 now, but I can't copy any files to that directory
it says:

Error while copying to "/media/hda5".
You do not have permissions to write to this folder.

---

### Post by Mustard on 2006-05-21
[QUOTE=IsKall]I tried that now, it shows the hda5 now, but I can't copy any files to that directory
it says:

Error while copying to "/media/hda5".
You do not have permissions to write to this folder.[/QUOTE]

I'm not exactly sure what the options are to get an ext3 filesystem set up for read/write by a user.  If I was to guess it would be..


```
/dev/hda5      	/media/hda5	ext3    defaults,rw  0       0
```

If noone comes along with a better suggestion, you might try reading over the manual with this command.  Reading over the manual it seems to say that 'defaults' implies rw, but maybe if you state it explicitly it might help.

```
man mount
```

---

### Post by Poirot on 2006-05-22
I have this /etc/fstab> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext2    defaults,errors=remount-ro 0       1
/dev/sda2       /datashare      vfat    defaults        0       0
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
I want write access to my FAT32 partition (datashare) that I also access via WinXP. I can read from it fine but would like to use it as a shared drive across both WinXP and Ubuntu.

How can I do that?

---

