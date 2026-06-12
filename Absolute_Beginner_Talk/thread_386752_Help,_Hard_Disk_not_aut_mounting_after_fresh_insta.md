---
title: "Help, Hard Disk not aut mounting after fresh install"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by kinson on 2007-03-17
Hi guys, I just formatting my previous Ubuntu AMD64 to Ubuntu i386.

I have 2 physical hard disks. Hard disk a (80gb), and hard disk b (200gb).

I formatted it this way:

Hard disk A:
/ = 30 gb
swap = 1gb
unused partition(for random stuff) = 40+ gb

Hard disk b:
/home = 200gb

But after installing, I boot into my desktop, and I can't seem to find my home partition, or the unused partition. :(

Before this when I installed Ubuntu to automatically make space with windows xp installed, it detected the drives normally. Any help here?

Here's my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I can see my "home" partition there under /dev/hdb1, but I still don't see my random/unused partition. :(

Thanks in advance :)
Kinson

---

### Post by taurus on 2007-03-17
What format is that 40GB on the master drive?  You need to add an entry for it in /etc/fstab so it would mount each time you boot Ubuntu.

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by kinson on 2007-03-17
oops, I forgot to mention that ! They're all formatted in ext3.

The output is

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3824    30716248+  83  Linux
/dev/hda2            3825        9599    46387687+  83  Linux
/dev/hda3            9600        9729     1044225   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401   83  Linux
kinson@kinbuntu:~$
```

This is my first time manually handling the partitioning(previously I just went auto). So I'm not sure whether I mucked up somewhre :/

Cheers,
Kinson

---

### Post by taurus on 2007-03-17
Okay, you need to edit /etc/fstab with

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hda2   /media/hda2   ext3   defaults   0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/hda2
sudo mount -a
df -h  <-- You should see /dev/hda2 mounted to /media/hda2 at the bottom of the output.
```
Now, if you want to write to /media/hda2, you can change the ownership from root to your login name.  Therefore, do

```
sudo chown -R **username**:**username** /media/hda2
ls -la /media
```
Remember, replace the **username** with the actual name that you log in with.

---

### Post by kinson on 2007-03-17
I tried it. but:

```
kinson@kinbuntu:~$ gksudo gedit /etc/fstab

(gedit:9398): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
kinson@kinbuntu:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

kinson@kinbuntu:~$
```

It seemed fine(except for the GnomeUI warning), but when I tried to "mount -a", it gave that error.

I've edited the fstab file as you told me to:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /home           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2   /media/hda2   ext3   defaults   0   1
```

I tried aligning the columns to see whether it made any difference...it didnt :P

:(
Thanks

---

### Post by meborc on 2007-03-17
which error? are you sure you used "sudo mount -a" not "mount -a"
and are you sure you did "sudo mkdir /media/hda2" before?

---

### Post by taurus on 2007-03-17
Is there anything on /dev/hda2?

---

### Post by kinson on 2007-03-17
> **meborc said:**
> which error? are you sure you used "sudo mount -a" not "mount -a"
and are you sure you did "sudo mkdir /media/hda2" before?

Yeah, i made sure I had already made the folder, which can be seen here:
```

kinson@kinbuntu:/media$ ls
cdrom  cdrom0  hda2
kinson@kinbuntu:/media$

```

As you can see from my previous post, I did put "sudo" before "mount -a" (i.e. "sudo mount -a"). When I tried that, it gave the error:

```
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```



Any other ideas? :(

Cheers,
Kinson.

---

### Post by taurus on 2007-03-17
> **kinson said:**
> 
Any other ideas? :(

Cheers,
Kinson.

Is there anything on /dev/hda2 right now?

---

### Post by kinson on 2007-03-17
> **taurus said:**
> Is there anything on /dev/hda2?

Do you mean whether I have any files in the hda2 drive? No.

I can't double click on /dev/hda2 in nautilus either :(

Btw, we've been talking about "hda2". But I also noticed that even though I can access my /home folder, but its not listed in my "/media" folder. So I just follow the previous steps to add the home drive to /media?? Sorry if I sound confused/confusing...I'm a little lost myself :p

Cheers,
Kinson

---

### Post by meborc on 2007-03-17
no need... it is mounted directly to /home folder :)

sorry for not helping you much

---

### Post by kinson on 2007-03-17
> **meborc said:**
> 
sorry for not helping you much

No problem, man :) Any help is help :)

Thanks,
Kinson

---

### Post by meborc on 2007-03-17
you could try changing the line from ```
/dev/hda2   /media/hda2   ext3   defaults   0   1
``` to ```
/dev/hda2   /media/hda2   ext3   defaults   0   0
```

---

### Post by taurus on 2007-03-17
If there is nothing on /dev/hda2 right now, you can reformat it to ext3 again and see if you can mount it this time.

```
sudo mke2fs -j **/dev/hda2**
sudo mount -a
df -h
```

---

### Post by kinson on 2007-03-17
> **taurus said:**
> If there is nothing on /dev/hda2 right now, you can reformat it to ext3 again and see if you can mount it this time.

```
sudo mke2fs -j **/dev/hda2**
sudo mount -a
df -h
```

Hrmm...interesting, it seemed to do the trick :)

```
kinson@kinbuntu:/media$ sudo mke2fs -j /dev/hda2
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
5799936 inodes, 11596921 blocks
579846 blocks (5.00%) reserved for the super user
First data block=0
354 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
        4096000, 7962624, 11239424

Writing inode tables: done
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 25 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
kinson@kinbuntu:/media$ sudo mount -a
kinson@kinbuntu:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              29G  1.9G   26G   7% /
varrun                506M   84K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  116K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile
/dev/hdb1             184G  146M  174G   1% /home
/dev/hda2              44G  129M   42G   1% /media/hda2
```

Thanks a lot. I wonder what went wrong though, this installations been a bit weird to be honest :P When I first booted into desktop after installation I had some weird error when trying to use sudo...said something about timestamp too far in the future, lol. A reboot solved that. Also in "places", it doesn't seem to show that "extra partition" that I just mounted(Any suggestions on this?), lol.

I've also changed the permissions on that drive:
```

kinson@kinbuntu:/media$ sudo chown -R kinson:kinson /media/hda2
kinson@kinbuntu:/media$ ls -la /media
total 16
drwxr-xr-x  4 root   root   4096 2007-03-18 01:43 .
drwxr-xr-x 21 root   root   4096 2007-03-18 08:38 ..
lrwxrwxrwx  1 root   root      6 2007-03-18 08:37 cdrom -> cdrom0
drwxr-xr-x  2 root   root   4096 2007-03-18 08:37 cdrom0
drwxr-xr-x  3 kinson kinson 4096 2007-03-18 02:16 hda2
```

Thanks :)

btw, thre's a "lost+found" folder in that drive...can I just delete it? :p

Cheers,
Kinson.

---

