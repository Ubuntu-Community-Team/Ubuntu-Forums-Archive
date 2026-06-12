---
title: "Mount with fstab"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by cmol on 2007-01-20
Hey..

So i found out how to mount my 2. hard drive manually, into a dir that i couldn't access because i made it as root. Then i wanted to write it in to the fstab file, but i can't seem to access it for writing.

So in short terms:
How do i create a dir to mount my drive into that a user can access (rw), and how do i access the fstab file so i can automaticly mount hdb1.

(hmm.. was that short?..)

---

### Post by taurus on 2007-01-20
How did you mount them by hand?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by anaconda on 2007-01-20
you will get the read-write permissions if you type 
sudo nautilus 
in terminal. (it opens file prowser with admin rights.)

---

### Post by cmol on 2007-01-20
> **taurus said:**
> How did you mount them by hand?  What's the output of this command from a terminal?

```
sudo fdisk -l
```

The output is:
```

Disk /dev/hda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1162     9333733+  83  Linux
/dev/hda2            1163        1216      433755    5  Extended
/dev/hda5            1163        1216      433723+  82  Linux swap / Solaris

Disk /dev/hdb: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3739    30033486   83  Linux

```

I mounted it this way

```

mkdir /mnt/mydisk2
mount -t ext3 /dev/hdb1 /mnt/mydisk2 -o rw,user

```

---

### Post by taurus on 2007-01-20
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /mnt/mydisk2   ext3   defaults   0   1
```
Save it.  Since it's an ext3 filesystem, you can change the ownership of it so you can write (and delete) to it. 

_Assuming_ your login name is **cmol** (change it to whatever it actually is, okay), do

```
sudo chown -R **cmol**:**cmol** /mnt/mydisk2
```
Reboot and see if you can write to /mnt/mydisk2 as **cmol**.

---

### Post by Canis familiaris on 2007-01-20
In case you have to share a FAT32 partition and share data:

Open fstab with root priviledges:
```
sudo nano /etc/fstab
```
Then scroll to the last line and add:
```
/dev/hda2     /mnt/shared   vfat   noauto,user 0 0
```
where /dev/hda2 is your drive (replace it with your own drive)
/mnt/shared is the mount point

Now whenever you want to access it, mount it with your command:
```
mount -t vfat /dev/hda2 /mnt/shared
```

Alternatively you can replace the previous line with the following line in fstab to get rid of mount command:
This will automatically mount it at bootime with you as the user**:
```
/dev/hda2 /foldername vfat uid=anurag,gid=anurag 0 0
```
Of course you replace anurag by your username

**This would mean only you can acess it.

TO create the dir, go to terminal:
```
sudo mkdir /mnt/shared
```

Now to finish off. Type in terminal:
```
mount -a
```

---

### Post by taurus on 2007-01-20
> **Anurag_panda said:**
> Open fstab with root priviledges:
```
sudo nano /etc/fstab
```
Then scroll to the last line and add:
```
/dev/hda2     /mnt/shared   vfat   noauto,user 0 0
```
where /dev/hda2 is your drive (replace it with your own drive)
/mnt/shared is the mount point

Now whenever you want to access it, mount it with your command:
```
mount -t ext3 /dev/hda2 /mnt/shared
```

Alternatively you can replace the previous line with the following line in fstab to get rid of mount command:
This will automatically mount it at bootime with you as the user**:
```
/dev/hda2 /foldername vfat uid=anurag,gid=anurag 0 0
```
Of course you replace anurag by your username

***This would mean only you can acess it.

TO create the dir, go to terminal:
```
sudo mkdir /mnt/shared
```

Now to finish off. Type in terminal:
```
mount -a
```

You can't mount /dev/hda2 since it's an extended partition.

---

### Post by cmol on 2007-01-20
> **taurus said:**
> Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /mnt/mydisk2   ext3   defaults   0   1
```
Save it.  Since it's an ext3 filesystem, you can change the ownership of it so you can write (and delete) to it. 

_Assuming_ your login name is **cmol** (change it to whatever it actually is, okay), do

```
sudo chown -R **cmol**:**cmol** /mnt/mydisk2
```
Reboot and see if you can write to /mnt/mydisk2 as **cmol**.

Ok.. It's mounted automatically after the reboot, and i can access it as cmol, but not make dir's, or paste files and so on.

---

### Post by Canis familiaris on 2007-01-20
> **taurus said:**
> You can't mount /dev/hda2 since it's an extended partition.
I didn't mean his /dev/hda2 in this case, what I meant was mounting any vfat partition to be read/write in Linux.
I initially though he wanted to read/write a fat32 partition.
I did'nt really read his fdisk output. :frown:

---

### Post by taurus on 2007-01-20
> **cmol said:**
> Ok.. It's mounted automatically after the reboot, and i can access it as cmol, but not make dir's, or paste files and so on.

What's the outputs of these commands?

```
id
ls -la /mnt
```

---

### Post by cmol on 2007-01-20
> **taurus said:**
> What's the outputs of these commands?

```
id
ls -la /mnt
```

```

uid=1000(cmol) gid=1000(cmol) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),111(scanner),114(admin),1000(cmol)

```


```

total 12
drwxr-xr-x  3 root root 4096 2007-01-20 16:23 .
drwxr-xr-x 21 root root 4096 2007-01-20 16:11 ..
drwxr-xr-x  3 root root 4096 2007-01-18 22:21 mydisk2

```

---

### Post by taurus on 2007-01-20
Can you run this command from a terminal to change the ownership of /mnt/mydisk2 to cmol?

```
sudo chown -R cmol:cmol /mnt/mydisk2
```
Now, paste the output of this command here again.

```
ls -la /mnt
```

---

### Post by cmol on 2007-01-20
> **taurus said:**
> Can you run this command from a terminal to change the ownership of /mnt/mydisk2 to cmol?

```
sudo chown -R cmol:cmol /mnt/mydisk2
```
Now, paste the output of this command here again.

```
ls -la /mnt
```

This looks good..
Will it redo when i reboot?

```

total 12
drwxr-xr-x  3 root root 4096 2007-01-20 16:23 .
drwxr-xr-x 21 root root 4096 2007-01-20 16:11 ..
drwxr-xr-x  3 root root 4096 2007-01-18 22:21 mydisk2

```

---

### Post by taurus on 2007-01-20
Once you change the ownership, it will stay even if you reboot.  Run that command again and reboot.  Then, show me the output of "ls -la /mnt" again.

---

### Post by cmol on 2007-01-20
> **taurus said:**
> Once you change the ownership, it will stay even if you reboot.  Run that command again and reboot.  Then, show me the output of "ls -la /mnt" again.

```

drwxr-xr-x  3 root root 4096 2007-01-20 16:23 .
drwxr-xr-x 21 root root 4096 2007-01-20 17:01 ..
drwxr-xr-x  4 cmol cmol 4096 2007-01-20 17:10 mydisk2

```

---

### Post by taurus on 2007-01-20
Now, see if you can write/save stuff to /mnt/mydisk2.

---

### Post by cmol on 2007-01-21
> **taurus said:**
> Now, see if you can write/save stuff to /mnt/mydisk2.

It works :D 
Thanks alot =D>

---

### Post by cvmostert on 2007-02-09
> **taurus said:**
> Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb1   /mnt/mydisk2   ext3   defaults   0   1
```
Save it.  Since it's an ext3 filesystem, you can change the ownership of it so you can write (and delete) to it. 

_Assuming_ your login name is **cmol** (change it to whatever it actually is, okay), do

```
sudo chown -R **cmol**:**cmol** /mnt/mydisk2
```
Reboot and see if you can write to /mnt/mydisk2 as **cmol**.

I also had a little problem with this and did not want to sudo all the time to write to my /dev/hda2 and 3... 

will do the chown command... this must work. knew it was something with premissions..

thank you.

---

