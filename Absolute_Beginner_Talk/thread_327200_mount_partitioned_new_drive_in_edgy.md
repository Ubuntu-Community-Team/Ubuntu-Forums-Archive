---
title: "mount partitioned new drive in edgy"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by tordan on 2006-12-28
I have partitioned my new hard drive and activated it in Qtparted but I can not figure out how to mount it to the proper file. What program is used on edg8) y eft to do this. Please help...

---

### Post by tordan on 2006-12-28
stupid rebelious smiley faces!

---

### Post by taurus on 2006-12-28
Paste the output of these two commands here from a terminal, Applications -> Accessories -> Terminal, and I can show you how to mount your new harddrive.  Basically, you want to edit /etc/fstab and add an entry for that new harddrive so that it would be mounted automatically each time you boot.

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by tordan on 2006-12-28
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7297    58613121   83  Linux
tordan@tordan-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=18255e6e-4cc9-4101-a00e-14285a198d27 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=2854e147-966f-4ba8-bc94-b0eee82e3739 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


The new one is 55 gigs and I partitioned it in qtparted.

I gotta go for a little while but please help. I'll repost as soon as I get back (about 45min).

---

### Post by tordan on 2006-12-28
oops, I mean 60 gigs

---

### Post by taurus on 2006-12-28
Okay, here we go...

You need to open a text editor so you can edit /etc/fstab.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll all the way to the end and add the following line to it.

```

/dev/hdb1   /media/hdb1   ext3   defaults   0   1

```
Save it.  Then create a mount point and mount it with

```
sudo mkdir /media/hdb1
sudo mount -a
df -h  <-- you should see your /dev/hdb1 on /media/hdb1...
```

---

### Post by tordan on 2006-12-28
Sorry for the delay. Hope yer still around.

Am I going to enter the last three lines of code at the terminal or in the fstab program? (and is the last line going to be presented to me after I enter the first two?)

---

### Post by DaBigEd on 2006-12-28
> sudo mkdir /media/hdb1
sudo mount -a
df -h  

This goes in the command prompt, 1 command at a time.

---

### Post by tordan on 2006-12-28
Is that it?

I'm still only showing the 13g free space from my original hard drive when I access Places>Computer.

---

### Post by DaBigEd on 2006-12-28
Do a 

df -h

in terminal. And paste the output. 

If it has mounted correctly  and you want it to show up on the desktop/places menu (im sure there is a fancy command, but i would just) restart the computer

---

### Post by tordan on 2006-12-28
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  3.1G   14G  19% /
varrun                189M   84K  189M   1% /var/run
varlock               189M     0  189M   0% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   18M  172M  10% /lib/modules/2.6.17-10-generic/volatile
/dev/hdc              685M  685M     0 100% /media/cdrom0
/dev/hdb1              56G  181M   53G   1% /media/hdb1
tordan@tordan-desktop:~$

---

### Post by DaBigEd on 2006-12-28
The drive is located on /media/hdb1
Next time you start your computer you should see it on the desktop

---

### Post by tordan on 2006-12-28
It is there!
But... I cant create a folder, its locked!

---

### Post by taurus on 2006-12-28
> **tordan said:**
> It is there!
But... I cant create a folder, its locked!

It's because root is the current owner.  You just have to change the permission so you can read and write to it.  From a terminal, do

```
sudo chmod -R 777 /media/hdb1
```

---

### Post by tordan on 2006-12-28
Did it.
No change.
Do I need to restart?

---

### Post by taurus on 2006-12-28
What's the output of this command then?

```
ls -la /media/hdb1
```
You can reboot if you wish...

---

### Post by tordan on 2006-12-28
Output:
total 24
drwxrwxrwx 3 root root  4096 2006-12-28 15:48 .
drwxr-xr-x 6 root root  4096 2006-12-28 19:42 ..
drwxrwxrwx 2 root root 16384 2006-12-28 15:48 lost+found

I'll try rebooting now.

---

### Post by tordan on 2006-12-28
All is good and well in the world and you are a saint.

As far as I can tell, its should be working. Thanks.

---

### Post by taurus on 2006-12-28
Yes, you should be able to write to it.

---

