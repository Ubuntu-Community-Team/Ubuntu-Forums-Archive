---
title: "ntfs partitions not mounted automatically"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by p.i.m.p on 2006-12-22
Hello,

I installed ntfs-3g using apt-get as described at [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)  and made the required changes to my fstab. However, the ntfs partitions are not mounted when I bootup. Curiously, typing sudo mount -a, mounts the partitions so the problem can't be in my fstab. Anybody? ](*,)

---

### Post by yabbadabbadont on 2006-12-22
Just in case, please post the contents of your /etc/fstab.  I agree that it doesn't sound like it is the source of the problem, but go ahead and post it anyway for completeness.  :)

---

### Post by yabbadabbadont on 2006-12-22
Also, there is a large howto thread with a lot of troubleshooting tips here:

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by p.i.m.p on 2006-12-22
Hi, here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=8bc286f4-0749-405b-a44c-18efeeff1af3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda10
UUID=8bece4e6-638f-48f6-b46c-9d4a20037e3c /home           ext3    defaults        0       2
# /dev/sda13
UUID=165C0B135C0AED75 /media/data     ntfs-3g    silent,umask=0,locale=en_US.utf8 0       1
# /dev/sda7
UUID=4550-4CB3  /media/documents vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=454C-A12F  /media/music    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4531-6CD9  /media/share    vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=d4775e2a-667a-43a3-8085-52e271b78e06 /media/software ext3    defaults        0       2
# /dev/sda1
UUID=5220A22520A20FD1 /media/xp       ntfs-3g    silent,umask=0,locale=en_US.utf8 0       1
# /dev/sda11
UUID=503629fa-ec59-402a-869f-0922087255dc /tmp            ext3    defaults        0       2
# /dev/sda12
UUID=9fee502e-1a6b-45d7-b217-06a4812986ab /usr            ext3    defaults        0       2
# /dev/sda8
UUID=7e6b0ee8-b748-40ae-9e56-9432e82facca none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

---

### Post by po0f on 2006-12-22
p.i.m.p,

Shouldn't the umask setting be "umask=000"?

---

### Post by p.i.m.p on 2006-12-22
Oh sorry, it was like that before, that's just me messing around trying to get it to work. :p However, changing it to 000 doesn't solve the problem either

---

### Post by yabbadabbadont on 2006-12-22
Try removing the silent mount option (which the mount manpage doesn't even list) and replace it with "defaults".  If that works, then try adding the "silent" option after the "defaults" option.

---

### Post by p.i.m.p on 2006-12-22
No, that doesn't work either :(

---

### Post by po0f on 2006-12-22
p.i.m.p,

Your entry for the NTFS partition in /etc/fstab doesn't reflect what is on the wiki.  Have you tried it with what is posted there?
```
[FONT="Courier New"]/dev/hda1    /media/windows    ntfs-3g    defaults,locale=en_US.utf8    0    0[/FONT]
```

Try to work it out from here.

---

### Post by yabbadabbadont on 2006-12-22
Just as an experiment, try commenting out the UUIDs for your ntfs partitions and put in the correct /dev/XXXX values.

---

### Post by p.i.m.p on 2006-12-22
Hi, I started out doing everything as the wiki says. I think I found the error. Here is the output of the cat /var/log/boot command :- 
```

Dec 22 13:27:16 rcS:  * Mounting local filesystems...
Dec 22 13:27:16 rcS: mount: unknown filesystem type 'ntfs-3g'
Dec 22 13:27:17 rcS: mount: unknown filesystem type 'ntfs-3g'
Dec 22 13:27:17 rcS:    ...fail!

```

And I do have 'fuse' in /etc/modules Any suggestions?

---

### Post by Step on 2006-12-22
Doesnt the umask needs to be 2222? I have a mounted partition of NTFS (without the g3 or something) on booting ubuntu edgy eft (had it on dapper too).

If youre willing to wait I will post my fstab here to show you how i mounted it. (I really did not do anything except geditting the fstab, i did not install anything else).

Hope this helps!:KS

---

### Post by p.i.m.p on 2006-12-22
that would be nice, thanks! i got ubuntu to mount the partitions on startup by a rather crude approach - i put mount -a in  /etc/rc.local :P The partitions mount, but no icons on the desktop :(

---

### Post by Famicommie on 2006-12-22
The system docs have a method that worked for me. I didn't have to install anything, and it boots the partition right at start up (though I elected to take the icon off of the desktop via Nautilus)

1. Make a directory where the partition can be mounted:
```
sudo mkdir /media/windows
```

2. Back up your configuration file and open the file in a text editor with root priveledges:
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
```

3. Append the following line at the end of the file:
```
/dev/hda1 /media/windows ntfs umask=0222 0 0
```

Obviously, you need to replace /dev/hda1 with whatever the correct location of your NTFS partition is.

---

### Post by Step on 2006-12-22
Famicommie is right, it was umask=0222;) 

I'll still post my fstab this evening in around 6 hours...:KS

---

### Post by Famicommie on 2006-12-22
> **Step said:**
> Famicommie is right, it was umask=0222;) 

I'll still post my fstab this evening in around 6 hours...:KS

Before I ask any questions on the boards, or decide to answer any, I always check my system docs :D

---

### Post by po0f on 2006-12-22
Famicommie,

The method that the OP is trying uses ntfs-3g and experimental write support.  The method you posted allows only read support.  I believe that the OP would like to get the former working.  :)

---

### Post by p.i.m.p on 2006-12-22
Yes, that is correct, the partitions were mounted automatically with read support with the default install. As I said, I've managed to get it mounted on startup without the desktop icons so it's alright.  Thanks for all the help guys!

---

### Post by Famicommie on 2006-12-22
> **po0f said:**
> Famicommie,

The method that the OP is trying uses ntfs-3g and experimental write support.  The method you posted allows only read support.  I believe that the OP would like to get the former working.  :)

Eep, I type like I talk: quicker than I think :oops: I hope the umask information was helpful, at least...

---

### Post by Step on 2006-12-23
I do not know if this helps but here's my fstab output:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
/dev/hda1       /home/step/ExtraHD    ntfs    defaults,umask=0222        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Where hda1 is my ntfs disk mounted to a folder in my home directory called ExtraHD.

I'm not sure if this helps but it auto mounts for me!

//edit:
I just read with the experimental stuff...I'm so slow! sorry!

---

