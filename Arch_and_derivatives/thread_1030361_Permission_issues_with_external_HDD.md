---
title: "Permission issues with external HDD"
date: 2009-01-04
forum: Arch and derivatives
---

### Post by gjoellee on 2009-01-04
For christmas I got  an 1TB extternal HDD. I works fine on a Windows machine, but I have Arch Linux on my computer and I get permission issues with the external HDD. How do I get perimission to use my own external HDD? 

I have tried right click and changing permissions as root but I does not work. I see whats in the external HDD when I am root, but can't create a folder!

The same happens in Ubuntu etc... if you wonder...

---

### Post by fwojciec on 2009-01-04
How is it formated -- what's the filesystem?  How are you trying to mount it (hal/fstab)?

---

### Post by gjoellee on 2009-01-04
> **fwojciec said:**
> How is it formated -- what's the filesystem?  How are you trying to mount it (hal/fstab)?

I guess it is Fat32 (Windows file system) because it works fine with Windows, If you need an output you must give me a full comand. (I don't know how to mount suff like that, I just plug it in)

---

### Post by fwojciec on 2009-01-04
Can you post the output of "fdisk -l" (as root) and "cat /etc/fstab"?  Where is the drive usually mounted to?

---

### Post by Barrucadu on 2009-01-04
Have you tried:
```
# chown yourusername /media/whatever
# chmod 777 /media/whatever
```
(obviously substituting 'yourusername' and 'whatever' for the correct values)

---

### Post by gjoellee on 2009-01-04
> **fwojciec said:**
> Can you post the output of "fdisk -l" (as root) and "cat /etc/fstab"?  Where is the drive usually mounted to?

fdisk -l
```
# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008b1af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241    5  Extended
/dev/sda5               1         243     1951834+  82  Linux swap / Solaris
/dev/sda6             244        2067    14651248+  83  Linux
/dev/sda7            2068       14593   100615063+  83  Linux

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001    7  HPFS/NTFS

```

cat /etc/fstab
```
# cat /etc/fstab
# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


/dev/cdrom /media/cdrom   auto    ro,user,noauto,unhide   0      0
/dev/cdrom1 /media/cdrom1   auto    ro,user,noauto,unhide   0      0
/dev/dvd /media/dvd   auto    ro,user,noauto,unhide   0      0
/dev/dvd1 /media/dvd1   auto    ro,user,noauto,unhide   0      0
UUID=10512ef5-9c47-46a7-9602-f9137ea11d82 swap swap defaults 0 0
UUID=9656f93a-365f-4dee-a00e-301fa58001c6 / ext3 defaults 0 1
UUID=af63f66e-d508-49e8-8bdf-9d1160a6b24b /home ext3 defaults 0 1

```

---

### Post by gjoellee on 2009-01-04
> **Barrucadu said:**
> Have you tried:
```
# chown yourusername /media/whatever
# chmod 777 /media/whatever
```(obviously substituting 'yourusername' and 'whatever' for the correct values)

sorry that does not work. I think it is the FAT32 and UNIX (ext3 for me) filesystem that don't have the same permission setup.

---

### Post by Rumor on 2009-01-04
> **gjoellee said:**
> fdisk -l
```
# fdisk -l

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001    7  HPFS/NTFS

```

cat /etc/fstab


I'd say this is your external drive, and it is being identified as an NTFS file system, which will work fine under Windows as you have noted, but not under Linux.

Herte is a link to the Arch wiki on enabling NTFS write support: [http://wiki.archlinux.org/index.php/NTFS_Write_Support](http://wiki.archlinux.org/index.php/NTFS_Write_Support)

Hope this helps.

---

### Post by gjoellee on 2009-01-04
Ok, I can mount the HDD when I am logged in as root... however I am still not getting the permissions (I have tied chmoding as showed above)

I am just asking...does making the HDD to Ext3 save me from a lot of trouble? I am wondering if I should do that, I am only going to use it with Linux and maybe Mac (I am not sure abotu the Mac)

---

### Post by mips on 2009-01-04
> **gjoellee said:**
> 
I am just asking...does making the HDD to Ext3 save me from a lot of trouble?

My external drive is formatted to Ext3 and I have no hassles with it. I also access it from WinXP machines with a additional driver.

Have a look at ext2fsx & macfuse maybe, I know nothing about macs.

---

### Post by gjoellee on 2009-01-04
My HDD works fine when I am root user now... (still NTSF)

---

### Post by hrod beraht on 2009-01-04
> **gjoellee said:**
> Ok, I can mount the HDD when I am logged in as root... however I am still not getting the permissions

When you mount it, you have to specify the owner as you, not root. Use the **-o** options flag to set the owner with **uid=**. Similar to:
```
mount -t ntfs /dev/sde1 /media/externaldrive -o uid=gjoellee
```
Bob

---

### Post by gjoellee on 2009-01-05
> **hrod beraht said:**
> When you mount it, you have to specify the owner as you, not root. Use the **-o** options flag to set the owner with **uid=**. Similar to:
```
mount -t ntfs /dev/sde1 /media/externaldrive -o uid=gjoellee
```Bob

it says:
```
# mount -t ntfs /dev/sde1 /media/hdd -o uid=gjoellee
ntfs-3g: Failed to access volume '/dev/sde1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.
```
and /dev/sde1 is correct

---

### Post by gjoellee on 2009-01-05
Thanks to a guy in the Arch Linux forums I am now able to mount mt hard drive as a normal user. I made a tutorial of what i did because I could not find any tutorial that was very good. Take a look here: [http://kshoster.net/content/howto-mount-external-hard-drive-and-get-permissions-ntfs-file-system](http://kshoster.net/content/howto-mount-external-hard-drive-and-get-permissions-ntfs-file-system)
(it is how I solved to problem)

---

### Post by fwojciec on 2009-01-05
You either use fstab/mount or you use hal.  If you use hal the drive should be mounted automatically without any commands, if you need a command line interface for hal use pmount-hal/pumount, but normally thunar/nautilus or whatever it is that you use will take care of interacting with hal for you.

If you use fstab/mount method then you have to use regular mount/umount commands as root, but you also don't need the custom hal policy you describe in your tutorial.  What's important is that if a drive is defined in /etc/fstab it will not be accessible to hal at all, so if you want to mount through hal you should completely remove any reference to that drive from fstab.

---

