---
title: "Trouble mounting slave drive. mount: wrong fs type [Resolved]"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by MoonTeC on 2007-02-02
Hi,

I'm having trouble mounting a slave drive in the system, the command I'm trying to use is:

sudo mount /dev/hdb1 /root/store -t ext3 -o nls=utf8,umask=0222

I know hdb1 the drive, /root/store is the mount point and ext3 a Linux partition.

Once executed I receive this error:

error message
root@Ubuntu-Box:~# sudo mount /dev/hdb1 /root/store -t ext3 -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This the system fdisk -l info:

root@Ubuntu-Box:~# fdisk -l

Disk /dev/hda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         747     6000246   83  Linux
/dev/hda2             748         784      297202+   5  Extended
/dev/hda5             748         784      297171   82  Linux swap / Solaris

Disk /dev/hdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1216     9767488+  83  Linux

I also have QTParted installed, I formated the drive to ext3 and set to active.

If anybody could give me a hand that would be great!

---

### Post by po0f on 2007-02-02
MoonTeC,

I'm almost positive "nls=" isn't a valid mount option for ext3 filesystems, I think it's only used for vfat/ntfs filesystems.  Try mounting it with just the default options:

```
[FONT="Courier New"]$ sudo mount -t ext3 -o defaults /dev/hdb1 /root/store[/FONT]
```

---

### Post by pseudonym on 2007-02-02
The options 'nls=utf8,umask=0222' aren't valid for ext3, hence your error message. Also, why have you created your mount point in /root? If you want other users to use this filesystem, best to create the mount point elsewhere, eg. /media, then change the permissions on the directory to allow read/write - ```
sudo mkdir /media/store
sudo mount -t ext3 -o defaults /dev/hdb1 /media/store
sudo chmod 666 /media/store
```
Then if you want to make the change permanent you need to edit /etc/fstab like this - ```
# /dev/hdb1
UUID=8bc2c0e7-b680-4198-a137-0983a9b27e54  /media/store     ext3    defaults        0       0
```
Your 'UUID' will be different. Run 'blkid' in a terminal to get this disk identifier for /dev/hdb1 and amend accordingly.

---

### Post by MoonTeC on 2007-02-02
Thanks for the reply, I entered the code. All went good till the last part,

root@Ubuntu-Box:~# UUID=a8690e53-ee45-435e-8918-17b3783d51fc  /media/store     ext3    defaults        0       0
bash: /media/store: is a directory

Not sure what to do here.

---

### Post by aysiu on 2007-02-02
That code isn't a command. It's a line that goes in the /etc/fstab file.

```
sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
``` Paste that line in at the end of the file; then save (Control-X, Y, Enter), and apply the changes: ```
sudo mount -a
```

---

### Post by MoonTeC on 2007-02-02
So by editing the fstab the changes are there when i restart?

The /media/store folder now has 9 GB free. That means it works right?

It doesn't show as a icon when i open "computer" should it?

---

### Post by aysiu on 2007-02-02
If you go to your computer and then type /media/store in the address bar, you should see files. If not, then reboot and see if anything's in /media/store.

---

### Post by po0f on 2007-02-02
MoonTeC,

You could also just type `mount` at a terminal to show mounted filesystems, `mount | grep hdb1` should return something if it's properly mounted (or mounted at all, for that matter).

---

### Post by MoonTeC on 2007-02-02
**mount | grep hdb1** returned :
/dev/hdb1 on /media/store type ext3 (rw)

So it's all good, I modifyed the fstab file and saved it, does this mean the drive will mount at start up automatically.

---

### Post by pseudonym on 2007-02-02
Yep, you've made it so the drive/partition is mounted automatically on startup. :)

---

### Post by aysiu on 2007-02-02
Yes. It'll mount on startup.

---

### Post by po0f on 2007-02-02
MoonTeC,

It should.  If not, post back.

---

### Post by MoonTeC on 2007-02-02
You guy's ROCK, Thanks

---

