---
title: "Just installed Feisty - some questions"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by SapiensFossor on 2007-04-30
Hi there,

I just installed Feisty and I like it a lot.  I have a couple questions.

1) I have a fat32 partition where I keep my music and I tried to create a new folder in it and drag files into it but it won't let me, saying I don't have permissions.  I right clicked the drive on the desktop and tried to change the permissions but it won't let me.  How do I change permissions to give me full access?

2) GAIM doesn't blink when I get a new IM (maybe it's just my theme).  How do I make it so it flashes bright yellow so I can see it?

Thanks a lot for any help :)

---

### Post by taurus on 2007-04-30
How did you mount your fat32/vfat partition?  Did you mount it through /etc/fstab?

Applications -> Accessories -> Terminal
```
cat /etc/fstab
```

---

### Post by GrueTamer on 2007-04-30
> **SapiensFossor said:**
> 2) GAIM doesn't blink when I get a new IM (maybe it's just my theme).  How do I make it so it flashes bright yellow so I can see it?I don't know how to make it flash, but perhaps making it beep would do about the same thing.  I'll keep looking for how to make it flash though, and if I find it, I'll post again.

EDIT: doesn't gaim flash automatically when it's minimized?

---

### Post by Patrick-Ruff on 2007-04-30
it should.  there are many options for it however.

you should really watch out for Trillian Astra, it's going to work on linux and it surpasses gaim and a half ;).

---

### Post by SapiensFossor on 2007-04-30
> How did you mount your fat32/vfat partition? Did you mount it through /etc/fstab?

I didn't... it was automatically mounted.  It's located in /media/hdb2

> EDIT: doesn't gaim flash automatically when it's minimized?

Sorry for not clarifying, but GAIM actually does flash when a new IM comes.  It just flashes so lightly that it's really hard to tell it's flashing, especially when you're focused on another window.  I want to make it so that when it flashes it flashes bright yellow so that it's easy to see.

Thanks so much for everyone's help :)

---

### Post by taurus on 2007-04-30
Try remount it with

```
sudo umount /media/hdb2
sudo mount -t vfat /dev/hdb2 /media/hdb2 -o iocharset=utf8,umask=000
ls -la /media/
```

---

### Post by SapiensFossor on 2007-04-30
taurus,

Thanks for the help.  I entered those commands, restarted the computer, but nothing changed.  Still, in that partition, the option to create a new folder is grayed out and it wont let me transfer files into it.  I can do it with command line but other people use this computer who don't understand command line and need to be able to do it via the GUI.

---

### Post by taurus on 2007-04-30
If you restart your machine, then you need to run those three commands from a terminal again unless you modify your /etc/fstab to include an entry to mount /dev/hdb2.

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/hdb2   /media/hdb2   vfat   iocharset=utf8,umask=000   0   0
```
Save it and reboot.  Now, what do you see when you run this command from a terminal?

```
ls -la /media
```

---

### Post by SapiensFossor on 2007-04-30
The reason I rebooted is because after I did the commands I could no longer see the partition.

Here's the part for hdb2 in the fstab file now:

```
# /dev/hdb2
UUID=1340E43C5A78F239 /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

I notice it says ntfs... but I formatted the drive as fat32.  Should I replace this line with the one you posted?

And when I do the ls -la /media command now, I get:

```
total 32
drwxr-xr-x  7 root root    4096 2007-04-15 04:56 .
drwxr-xr-x 21 root root    4096 2007-04-29 13:20 ..
lrwxrwxrwx  1 root root       6 2007-04-29 13:04 cdrom -> cdrom0
drwxr-xr-x  2 root root    4096 2007-04-29 13:04 cdrom0
drwxr-xr-x  2 root root    4096 2007-04-29 13:04 cdrom1
lrwxrwxrwx  1 root root       7 2007-04-29 13:04 floppy -> floppy0
drwxr-xr-x  2 root root    4096 2007-04-29 13:04 floppy0
--wxr-x---  1 root root       0 2007-04-15 04:56 .hal-mtab-lock
dr-xr-x---  1 root plugdev 8192 2007-04-29 17:33 hdb1
dr-xr-x---  1 root plugdev 4096 2007-04-29 16:05 hdb2

```

---

### Post by taurus on 2007-04-30
If /dev/hdb2 is vfat now, why don't you replace the old entry in /etc/fstab with the new one that I included above?  Otherwise, post the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by SapiensFossor on 2007-04-30
taurus,

thanks again for helping me.

I replaced the line but now the /media/hdb2 folder is empty.

Here is the results of that command:

```
Disk /dev/hdb: 120.0 GB, 120060444672 bytes
16 heads, ** sectors/track, 232**2 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      13**45    6**43448+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2          13**46      171870    20979000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hdb3          171871      1**851     15**077+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/hdb4          1**851      232624    29**7812+  83  Linux
Partition 4 does not end on cylinder boundary.

```

It still thinks that the partition is NTFS but I could have sworn that I formatted it as fat32 :confused:

---

### Post by taurus on 2007-04-30
> **SapiensFossor said:**
> taurus,

thanks again for helping me.

I replaced the line but now the /media/hdb2 folder is empty.

Here is the results of that command:

```
Disk /dev/hdb: 120.0 GB, 120060444672 bytes
16 heads, ** sectors/track, 232**2 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1      13**45    6**43448+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hdb2          13**46      171870    20979000    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hdb3          171871      1**851     15**077+  82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.
/dev/hdb4          1**851      232624    29**7812+  83  Linux
Partition 4 does not end on cylinder boundary.

```

It still thinks that the partition is NTFS but I could have sworn that I formatted it as fat32 :confused:

Exactly how did you format /dev/hdb2 from ntfs to vfat?  And by the way, it should be empty after you format it.

---

### Post by SapiensFossor on 2007-04-30
I think we've found our problem.  I thought I'd created the partition as a fat32, but I guess I created it as NTFS ](*,)  Is there a way to convert this partition to fat32 without losing the songs on it (it'd take so long to transfer them format then retransfer them).  Or would it be easier to just make it so that I can write to the partition on NTFS (I don't know if that's possible).

Thanks again for the help :)

---

### Post by limitedmage on 2007-04-30
If you have Automatix, you could just install the package named "Read/Write support for NTFS".

Get Automatix at [http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29) if you want to.

---

### Post by SapiensFossor on 2007-04-30
I heard installing Automatix was bad?

---

### Post by SapiensFossor on 2007-04-30
No matter, I followed the directions here: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

I am able to write to the partition now :)

Anyone have any ideas on how to change it so that when I get an IM from GAIM it flashes bright yellow instead of dull blue?

Thanks for all the help.

---

