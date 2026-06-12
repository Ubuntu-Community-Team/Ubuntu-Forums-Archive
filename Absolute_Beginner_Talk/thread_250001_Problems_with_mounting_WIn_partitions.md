---
title: "Problems with mounting WIn partitions"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by valterxxx on 2006-09-03
Hi,
i have two hard drives of which one is split into three partitions and the other one is not split. I tried mounting these partitions but I get this response in the terminal:

valter@ubuntu:~$ sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/sda1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/sda1 is mounted on /media/sda1

I hope someone can help me with what I'm doing wrong because when I try to open these partitions it doesn't allow because I do not have permission to view the contents.

---

### Post by jorn on 2006-09-03
Seems to be mounted already.
Will you paste your:
> sudo cat /etc/fstab
-t ntfs -o nls=utf8,umask=0222 I'm not sure abou this, havn't tried it myself. Always put it into fstab.
If you open filebrowser and go to /media/ is there no sda1?

---

### Post by blent07 on 2006-09-03
well, this is probably a little above me, but i'll try any help anyway. 

first, if anything is mounted it should appear on your desktop. so question 1 is: are the mounted partitions on your desktop? 


Secondly, I've tried mounting things that were already mounted by accident, and I got that same message. 

Thirdly, let me clarify: when you try to access /media/sda1 (perhaps using Nautilus) it won't let you explore those directories? that's what i understood it as.

If so, you  can try navigating via Terminal. You can use the following commands:

pwd     ---lists where you are
cd      ---changes directory, i.e.  cd /home/valter/Desktop    
cd ..   ---move you up one directory
ls -l   ---lists the contents of each directory


so you can try using: ~$ sudo cd /media/sda1
and then use the "ls -l" commands to list what's there and see if it is indeed one of the partitions. 


lastly, use System -> Administration -> Disks to make sure you're trying to mount the right partions. For me, hda1 is a Dell Utilities partition, and hda2 is my windows. 


Oh, and lastly, that reminds me, sda1 is a USB for me. so, is it an external harddrive or what?

---

### Post by valterxxx on 2006-09-03
> **jorn said:**
> Seems to be mounted already.
Will you paste your:

-t ntfs -o nls=utf8,umask=0222 I'm not sure abou this, havn't tried it myself. Always put it into fstab.


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sda5       /media/sda5     ntfs    defaults        0       0
/dev/sda6       /media/sda6     ntfs    defaults        0       0
/dev/sdb1       /media/sdb1     ntfs    defaults        0       0
/dev/sda8       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

> **jorn said:**
> If you open filebrowser and go to /media/ is there no sda1?

There is, but all the sda's have the little sign over them.. i suppose the sign would mean "not permissible".

---

### Post by valterxxx on 2006-09-03
> **blent07 said:**
> 
first, if anything is mounted it should appear on your desktop. so question 1 is: are the mounted partitions on your desktop?

Yes, all the sda's are on the desktop.

> **blent07 said:**
> Thirdly, let me clarify: when you try to access /media/sda1 (perhaps using Nautilus) it won't let you explore those directories? that's what i understood it as.

Yes, that's it.


> **blent07 said:**
> 
If so, you  can try navigating via Terminal. You can use the following commands:

pwd     ---lists where you are
cd      ---changes directory, i.e.  cd /home/valter/Desktop    
cd ..   ---move you up one directory
ls -l   ---lists the contents of each directory


so you can try using: ~$ sudo cd /media/sda1
and then use the "ls -l" commands to list what's there and see if it is indeed one of the partitions. 


This is what i get: sudo: cd: command not found

> 
valter@ubuntu:/media$ dir
cdrom  cdrom0  floppy  floppy0  sda1  sda5  sda6  sdb1  windows
valter@ubuntu:/media$ cd sda1
bash: cd: sda1: Permission denied


> **blent07 said:**
> lastly, use System -> Administration -> Disks to make sure you're trying to mount the right partions. For me, hda1 is a Dell Utilities partition, and hda2 is my windows. 


Oh, and lastly, that reminds me, sda1 is a USB for me. so, is it an external harddrive or what?

This is what's interesting. If I go to Disks and use Browse a certain partition I can browse it and see everything on it. If i close the File Browser and open the File Browser in itself (without going to System ->...) I don't have the permission to access partitions!

sda are my s-ata hard drives.

---

### Post by x64Jimbo on 2006-09-03
You need to look at the settings in fstab. I have a strong feeling that there is something messed up there. Specifically, have a look at the umask number and re-post that here.

---

### Post by blent07 on 2006-09-03
This is what i get: sudo: cd: command not found

Quote:
valter@ubuntu:/media$ dir
cdrom cdrom0 floppy floppy0 sda1 sda5 sda6 sdb1 windows
valter@ubuntu:/media$ cd sda1
bash: cd: sda1: Permission denied



that's where you use sudo. instead of: 
valter@ubuntu:/media$ cd sda1

use:

valter@ubuntu:/media$ sudo cd sda1



Quote:
This is what's interesting. If I go to Disks and use Browse a certain partition I can browse it and see everything on it. If i close the File Browser and open the File Browser in itself (without going to System ->...) I don't have the permission to access partitions!


What happens there is when you open the Disks manager, you have to enter your password, which gives you root (superuser) privledges while you in it. That's why you can access those. 


Now I can't read an fstab and understand it all but here's mine:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2    /media/windows ntfs  nls=utf8,umask=0222 0    0
/dev/hda3    /media/bob vfat  iocharset=utf8,umask=000  0    0
/dev/sda1 /mnt/ipod vfat user,noauto,umask=000 0 0


hda2 is my windows ntfs, hda3 is my FAT partition on the same hard drive as windows, sda1 is my ipod, so it automatically mounts it when it sees it. I see all those "ntfs default 0 0" in your fstab, and that makes me think in your setup it has those mount points only accessible by the root, which you don't want.

You can try altering those. Use this link: 
[http://easylinux.info/wiki/Ubuntu_dapper#Windows](http://easylinux.info/wiki/Ubuntu_dapper#Windows)

and scroll down to find what you want (ntfs, fat, write, read-write, whatever). 


Also, in terminal use:  $gksudo nautilus    to gain use the file browser with root authority. However, heed the warning and don't mess with anything. Especially anyhting ntfs. Getting write support for ntfs is a big thing around the web, and there are several ways ppl claim to do it safely, but it's still always risky writing to ntfs. Reading from it's perfectly safe, though.

---

### Post by steve.horsley on 2006-09-03
Replace your /etc/fstab with this one:
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda7 / ext3 defaults,errors=remount-ro 0 1
/dev/sda1 /media/sda1 ntfs nls=utf8,umask=222 0 0
/dev/sda5 /media/sda5 ntfs nls=utf8,umask=222 0 0
/dev/sda6 /media/sda6 ntfs nls=utf8,umask=222 0 0
/dev/sdb1 /media/sdb1 ntfs nls=utf8,umask=222 0 0
/dev/sda8 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
You may notice that the only change is to replace **defaults** with **nls=utf8,umask=222**. This will give you read access to the NTFS partitions.

P.S. for reference:
[http://ubuntuguide.org/wiki/Dapper#Windows](http://ubuntuguide.org/wiki/Dapper#Windows)

---

### Post by blent07 on 2006-09-03
haha. sorry for the crappy quotes. i'm yet to figure out how to quote specific parts of a post, not just the whole post. ;)

---

### Post by valterxxx on 2006-09-03
This is what I get when trying to modify fstab...

> valter@ubuntu:~$ gksudo gedit /etc/fstab

(gksudo:10601): Gtk-WARNING **: Unable to locate theme engine in module_path: "gflat",

(gedit:10603): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

And it opens a blank fstab file. I should mention that I do not have /home/ partition set up. Could that be a problem?

---

### Post by blent07 on 2006-09-03
the latter warning is normal, i get that too, but missing the engine: "gflat" is new to me. 

i don't setting up /home would affect it, but i don't know about that.


Umm, try a different approach, like gksudo nautilus that i mentioned earlier and see if oyu can maually find and open fstab and see if that's blank too?

---

### Post by jorn on 2006-09-03
That's weird.
Go into nautilus. Find >/etc/fstab.
Is it really empty?
Try:
> locate fstab

---

### Post by steve.horsley on 2006-09-04
You're not using Kubuntu instead of Ubuntu are you? If so, try:
**kdesu kate /etc/fstab**
instead.

---

