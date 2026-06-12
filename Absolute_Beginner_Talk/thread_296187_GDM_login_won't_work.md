---
title: "GDM login won't work"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2006-11-09
When I installing .tar.gz files into the "Login Window Preferences," it says that it's not a .tar.gz file (though it is) and then I can only open the file with text editor (and it's a blank document). It used to work before, but I don't know what happened. Can someone help?

---

### Post by taurus on 2006-11-09
Would you mind to show us what file it is and where did you download it from?  There could be a problem with that file!

---

### Post by Najand on 2006-11-09
Hmm, seems to me like your file is broken.... Like what Taurus said, whould you mind telling us more details?

---

### Post by kbsuperstar on 2006-11-09
I'm trying to download GDM and GTK2.x themes from Gnome-look.org 'cause I did it to my laptop last night, and I've done it on my desktop before, too. For some reason whenever I try installing the theme or the login window, it says the file format is invalid, even though I downloaded them as .tar.gz files.

---

### Post by Najand on 2006-11-09
Hmm, can you "gunzip" and "tar -xf" your file, in the terminal? Then use the image file inside for your login window.

---

### Post by kbsuperstar on 2006-11-09
I'll try

---

### Post by kbsuperstar on 2006-11-09
As soon as I download it, it immediately turns into a text file and has nothing in it.

---

### Post by kbsuperstar on 2006-11-09
Actually, I think the problem is that I download everything to my external HD. When I download it to my home folder, on my internal HD, it's fine. What the f***? How do I fix this?

---

### Post by Najand on 2006-11-09
The tar.gz2 file turns into a text file? What do you mean by that?

---

### Post by kbsuperstar on 2006-11-09
No, they're not tar.gz2, they're .tar.gz files. I mean, when I put my mouse over them, it goes from the archive file icon to a text file icon and then I can only open it with a text editor.

---

### Post by darrenm on 2006-11-09
Sounds like your drive isnt mounted correctly.

Try ```
sudo umount -a && sudo mount -a
``` dont worry about the errors.

Then try resaving the files to the external drive.

---

### Post by kbsuperstar on 2006-11-09
Well, what's -a and -a && ? Will this unmount my external drive?

---

### Post by taurus on 2006-11-09
I don't think it's such a good idea to do the "sudo umount -a" because it will unmount everything in /etc/fstab, including your / partition!!!  The question should be is your external harddrive a ext3 or fat32!  If not sure, let's have a look at your /etc/fstab then...

```
cat /etc/fstab
```

---

### Post by Najand on 2006-11-09
Ok, can you use the following commands about the "tar.gz" file you are using, in the terminal (console)?
```

$ gunzip FILENAME.tar.gz
$ tar -xf FILENAME.tar

```
If it goes well, see if you see anything inside the directory folder it just made or not?

---

### Post by kbsuperstar on 2006-11-09
My external is FAT32 and my internal is ext3...

---

### Post by taurus on 2006-11-09
If your external HD is FAT32 and you try to save .tar.gz to it, that could be your problem there...

---

### Post by Najand on 2006-11-09
Hmm, I think the problem is not because of mounting the external HD he has... If so he could not download the file in it. There must be a problem avoiding the file to be copied on the Ext. HD correctly.

---

### Post by kbsuperstar on 2006-11-09
Any ideas on how I could fix it?

---

### Post by darrenm on 2006-11-09
> **taurus said:**
> I don't think it's such a good idea to do the "sudo umount -a" because it will unmount everything in /etc/fstab, including your / partition!!!  The question should be is your external harddrive a ext3 or fat32!  If not sure, let's have a look at your /etc/fstab then...

```
cat /etc/fstab
```

Heres what happens when you run sudo umount -a:

```
darrenm@darrenmansell:~$ sudo umount -a && sudo mount -a
Password:
umount: /media/store: device is busy
umount: /dev: device is busy
umount: /proc/bus/usb: device is busy
umount: /var/run: device is busy
umount: /sys: device is busy
umount: /: device is busy

```

---

### Post by darrenm on 2006-11-09
> **kbsuperstar said:**
> Any ideas on how I could fix it?

As I said. sudo umount -a then sudo mount -a

or reboot.

---

### Post by punx45 on 2006-11-09
looks like /media/store is the external in question.. 
try unmounting and remounting just that drive.

like taurus said.. umount -a will unmount the / partition which is sort of necessary for the system to operate!

---

### Post by kbsuperstar on 2006-11-09
Umount -a doesn't do anything. All it says is that the devices are busy. I tried disconnecting + reconnecting the drive, and rebooting. But no luck

---

### Post by darrenm on 2006-11-09
> **punx45 said:**
> looks like /media/store is the external in question.. 
try unmounting and remounting just that drive.

like taurus said.. umount -a will unmount the / partition which is sort of necessary for the system to operate!

No it wont! In this case it didnt seem to fix it either but umount -a wont do anything bad.

---

### Post by Najand on 2006-11-09
It won't umount all mounted devices, but it is not advised. Anyway... there might be a problem with your "/etc/fstab" file. Is it possible to copy and paste it here? A copy of the output of "sudo fdisk -l" is nice too, if you don't mind.

---

### Post by kbsuperstar on 2006-11-09
/etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```



sudo fdisk -l

```
Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2167    17406396   83  Linux
/dev/hda2   *        2861        3497     5116702+   c  W95 FAT32 (LBA)
/dev/hda3            3498        3649     1220940    5  Extended
/dev/hda5            3498        3649     1220908+  82  Linux swap / Solaris

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11549    92759310    b  W95 FAT32
/dev/sda2           11549       11694     1164681+  82  Linux swap / Solaris
/dev/sda3           11694       12188     3976087   83  Linux

```

---

### Post by Najand on 2006-11-09
Did you mount it manually? If so copy/paste the output of "mount" command too, please.

---

### Post by kbsuperstar on 2006-11-09
```
kyle@kyle-desktop:~$ sudo umount -a && sudo mount -a
Password:
umount: /media/usbdisk: device is busy
umount: /dev: device is busy
umount: /var/run: device is busy
umount: /: device is busy

```

---

### Post by Najand on 2006-11-09
Well, not "*sudo umount -a && sudo mount -a*", just "*mount*" without anything else after it.

---

