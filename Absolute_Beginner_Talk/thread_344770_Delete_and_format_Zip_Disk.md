---
title: "Delete and format Zip Disk"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Tweedicus on 2007-01-23
Hi,

I have a USB Zip disk 100

Edgy recognises it no problem, and I can transfer file from the computer and vica versa.

The problem is deleting and formating.

I delete the files to trash and they vanish from the disk, but my disk space does not change, so I can't put anything else on the disk. What's the work around?

2.) So I go into gparted and delete the disk, create a new partition and format (I've tried different formats: FAT16 ext2, ext3 etc).

The disk is now deleted but when I try to write onto it won't let me, saying I don't have permission. There is also a strange folder put on the zip disk called 'lost and found' which I can't move. I went into properties and it said the owner of the disk is root and I don't want to have permission.

All I want to do it to be able to delete the contents of the disk so I can use it over and over, and if necessary format it, thought the latter is not essential.

Thanks,

Tweed

---

### Post by taurus on 2007-01-23
1.  Try to empty your trash bin as well.

2.  Where do you mount the zip drive?  You just need to change the ownership so you can write it to since it's now owned by root.
```
df -h
```

---

### Post by Tweedicus on 2007-01-23
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              22G  8.6G   12G  43% /
varrun                316M  136K  315M   1% /var/run
varlock               316M  4.0K  316M   1% /var/lock
procbususb             10M  124K  9.9M   2% /proc/bus/usb
udev                   10M  124K  9.9M   2% /dev
devshm                316M     0  316M   0% /dev/shm
lrm                   316M   18M  298M   6% /lib/modules/2.6.17-10-386/volatile
/dev/sdb1              92M  1.6M   85M   2% /media/zip


That's the outcome. The zip is /dev/sdb1

How do I change ownership? And why that funny lost and found file that is being written to it. Is there a simple way just to format and delete, or a least set it up so root isn't written to it.

Thanks

---

### Post by taurus on 2007-01-23
The lost+found directory created when you formatted the drive to ext3.  It's there in case it needs to recover some corrupted data so it can save it in there.  Leave it alone since it's not taking up any space at all.

Now, _assuming_ your login name to your machine is **tweedicus**, do

```
sudo chown -R **tweedicus**:**tweedicus** /media/zip
sudo chmod -R 755 /media/zip
ls -la /media
```

---

### Post by Buck2348 on 2007-01-23
```
sudo chown -R Tweedicus /media/zip
```
taurus can give you better/more complete help when he returns.

Edit:  Oops--should have known he is faster than I am.

Buck

---

### Post by Tweedicus on 2007-01-23
I'm getting this response from terminal:


ahmedweir@ahmedweir-laptop:~$ sudo chown -R ahmedweir:ahmedweir /media/zip
Password:
ahmedweir@ahmedweir-laptop:~$ sudo -R 755 /media/zip
sudo: illegal option `-R'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
ahmedweir@ahmedweir-laptop:~$

---

### Post by stijn_pol on 2007-01-23
```
sudo **chmod** -R 755 /media/zip
```
hint: if your not sure about commands, type:
```
man chmod
```
This wil show the manual for the chmod command

---

### Post by Tweedicus on 2007-01-23
Oops sorry about that.

Ok that seems to have done the trick.

Though it's still abit convoluted in that I have to drag a file I want to delete into the Trash, then I have to empty the trash, then I have to eject the disk so it's written to, then I have to resinsert the disk in order for the files to have been deleted and recognised as being deleted.

2.) Everytime I format a disk, do I have to go through the whole process again?

I really appreciate your help but it does seem an awful lot to do just to delete a file from an external disk.

---

### Post by Tweedicus on 2007-01-23
In other words can I just format or erase from gparted (or anything else if there's a better way) without setting up the disk needing root permissions to write to. It seems gparted it doing this automatically for some reason.

Ahmed

---

### Post by Buck2348 on 2007-01-23
For deleting files and folders, you can make it more direct by opening any nautilus window (such as /home/your-name) and selecting Edit -> Preferences -> Behavior Tab -> Under Trash checkmark "Include a Delete command that bypasses Trash."  Now when you right-click on a file or folder icon you will have a "Delete" option as well as "Send to Trash," and any file you delete this way will be permanently removed.  I can't help you much with the other questions.  I don't have a zip drive, but when I hot-plug a flash card reader, the system mounts it automatically with my username as owner and I'm able to read from and write to it like a hard disk.

Buck

---

### Post by Tweedicus on 2007-01-23
Thank for that. I've just done that.
Tweed

---

### Post by ricardisimo on 2007-01-23
> **taurus said:**
> The lost+found directory created when you formatted the drive to ext3.  It's there in case it needs to recover some corrupted data so it can save it in there.  Leave it alone since it's not taking up any space at all.

Now, _assuming_ your login name to your machine is **tweedicus**, do

```
sudo chown -R **tweedicus**:**tweedicus** /media/zip
sudo chmod -R 755 /media/zip
ls -la /media
```

Same problem here. Here's the basics:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              38G   35G  343M 100% /
varrun                252M  112K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                252M   48K  252M   1% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-10-386/volatile
/dev/sda1             984M  370M  615M  38% /media/usbdisk
```

I ran the commands above, substituting my user name and drive name, of course. No dice. Still can't change permissions. Does the "-R 755" not apply to me? TIA.

---

### Post by taurus on 2007-01-23
> **ricardisimo said:**
> Same problem here. Here's the basics:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              38G   35G  343M 100% /
varrun                252M  112K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
procbususb             10M  100K   10M   1% /proc/bus/usb
udev                   10M  100K   10M   1% /dev
devshm                252M   48K  252M   1% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-10-386/volatile
/dev/sda1             984M  370M  615M  38% /media/usbdisk
```

I ran the commands above, substituting my user name and drive name, of course. No dice. Still can't change permissions. Does the "-R 755" not apply to me? TIA.

```
sudo fdisk -l
```

---

### Post by Buck2348 on 2007-01-23
Did you get any ouput or error messages when you ran chown and chmod on your drive?  Could you post the output from ```
ls -la /media
```?

---

### Post by ricardisimo on 2007-01-23
> **taurus said:**
> ```
sudo fdisk -l
```

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4910    39439543+  83  Linux
/dev/hda2            4911        4998      706860    5  Extended
/dev/hda5            4911        4998      706828+  82  Linux swap / Solaris

Disk /dev/sda: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)

---

### Post by ricardisimo on 2007-01-23
> **Buck2348 said:**
> Did you get any ouput or error messages when you ran chown and chmod on your drive?  Could you post the output from ```
ls -la /media
```?

No errors. Here's "ls -la /media":
total 28
drwxr-xr-x  4 root    root     4096 2007-01-23 11:58 .
drwxr-xr-x 21 root    root     4096 2006-11-30 21:59 ..
lrwxrwxrwx  1 root    root        6 2006-09-01 13:14 cdrom -> cdrom0
drwxr-xr-x  2 root    root     4096 2006-09-01 13:14 cdrom0
drwx------  4 ricardo ricardo 16384 1969-12-31 16:00 usbdisk

---

### Post by taurus on 2007-01-23
Sorry but you cannot use chmod for fat32 (or ntfs).  You can try these though.

```
sudo umount /dev/sda1
sudo mount -t vfat /dev/sda1 /media/usbdisk -o iocharset=utf8,umask=000
```
Now, see if you can write or save stuff to /media/usbdisk.

---

### Post by ricardisimo on 2007-01-23
I could already move files to and from just fine, and still can now. The only difference now appears to be that I get an error when I try to change the permissions:
```
The permissions could not be changed.
Sorry, couldn't change the permissions of "usbdisk".
```
I didn't before; it would just snap back to "None".

One bit of progress, however: I took the other guy's advice to "Include a Delete command that bypasses Trash." That's working. However, all of the files I had previously moved to trash are clearly still there and I can't see or access them.
There's something that I can't get my brain around... why wouldn't root-nautilus let me do whatever the heck I want with this drive, whether it's allowing me to clean it up or set permissions? Wouldn't that be the most logical way around this problem? Also, I'm assuming there is no Linux correlate to "format disk", correct? Truth is, I don't even know what "format disk" means. Never made any sense to me. Thanks again.

---

### Post by randiroo76073 on 2007-01-23
Format disk means simply, setup disk for a file system, ie:  ntfs, fat32, ext3, reiserfs, it kind of removes previous data and sets up new file system.

---

### Post by Buck2348 on 2007-01-23
> **ricardisimo said:**
> However, all of the files I had previously moved to trash are clearly still there and I can't see or access them.

If you want to see the .Trash folder and its contents, in Nautilus and in the root directory of the drive, press <ctrl>H or select View -> Show Hidden Files.  Then you should be able to get inside the .Trash and delete whatever you like.  To make hidden files always visible, in Nautilus select Edit -> Preferences -> Views Tab -> Default View -> Show Hidden and Backup Files.

Buck

---

### Post by ricardisimo on 2007-01-23
> **Buck2348 said:**
> If you want to see the .Trash folder and its contents, in Nautilus and in the root directory of the drive, press <ctrl>H or select View -> Show Hidden Files.  Then you should be able to get inside the .Trash and delete whatever you like.  To make hidden files always visible, in Nautilus select Edit -> Preferences -> Views Tab -> Default View -> Show Hidden and Backup Files.

Buck

Thanks! Two things, though... Firstly, even after setting preferences to show hidden files, I still had to hit <CTRL>H in the drive window before they would show. Odd, that. Secondly, this is theoretically a 1G drive (and my Windows comp seems to recognize and use it as such), but after deleting everything I'm at 831.2 MB here on my Edgy comp. What's up with that?
Also, any other ideas on changing the permissions? Thanks again for everyone's help.

---

### Post by Buck2348 on 2007-01-23
Sorry--had to go eat.  Taurus must be eating too.:grin:  I suspect you had to close all Nautilus windows and then open one again for your preference change to take effect.  As to the disk, I'm fairly new to this and probably can't help you much.  You posted the result of  sudo fdisk -l  a while ago.  It says the partition has different logical and physical endings.  I'm not sure exactly what that means but I suspect that's the problem with disk capacity, and that you need to reformat it to fix that.  As to permissions--you are the disk owner and have full permissions--rwx--now.  If there is something else you want to change about the way the disk mounts, you would probably have to add a line in the file /etc/fstab to fix it.  If I was doing that on my machine here it would probably take me half the night, though it's actually not very complicated.  If I can give you any more help post again and I'll do what I can.

Buck

---

### Post by ricardisimo on 2007-01-23
This is a bit curious... I ejected the stick and re-inserted it, and now it's gone back to how it had been earlier, where there was no error report when I would try to change permissions, it just snaps back to "none" for me or anyone else. I'm very confused at this point. Whether I'm logged in as root or not I can't set permissions for myself and others. Bizarre. Thanks again.

---

### Post by Buck2348 on 2007-01-23
Right--Taurus pointed out that you cannot change permissions on a vfat filesystem.  But you as the owner have all the permissions anyway.  ```
ls -la /media
``` can verify that.

---

### Post by ricardisimo on 2007-01-23
Here's what I got just now:
```
drwx------  3 ricardo ricardo 16384 2007-01-23 16:03 usbdisk
```
whereas before (you can see above) for some reason it said
```
drwx------ 4 ricardo ricardo 16384 1969-12-31 16:00 usbdisk
```
What's that all about. It seems anything that comes anywhere near this stick is wrapped in mystery... at least it's mysterious to me.
So basically, fat32, ntfs, etc., is designed with Windows in mind and I just have to get used to it, right?
Finally, how do I reformat? I know how to do it on XP at home. Should I just do it there, or on both compootors? Thanks bunches. You rock.

---

### Post by Buck2348 on 2007-01-23
You should be able to repartition/format the disk using Gparted, included with Edgy.  System -> Administration -> Gnome Partition Editor.  It should be nearly the same as when you set up partitions when installing Ubuntu, just quicker.  You shouldn't have any problems using the fat32 filesystem, which is readable and writable in Ubuntu.  NTFS is not writeable without some "experimental" software called ntfs-3g.  I've installed that in Ubuntu four times and never had any problem.  I assume you want to use the stick in both Windows and Ubuntu, so one of those two should be your choice, although it's not very hard to get Windows to access ext2/3.

The reason for that odd date in the /media list is a mystery to me too--could your system have not had the correct date?

Again, I've told you most of what I know :biggrin: but if I can help any more I'd be glad to.  Remember you can send private messages here.  I will probably see anything you post on this thread but another thread would be iffy.  But you probably need better help anyway.

Edit:  I just played around with a 128 MB SD card.  After I deleted the one partition on it and made a new one, it shows only 116 MB available, so I don't know what's up with that.  You probably don't really need to reformat your stick if you can read and write to it.

Buck

---

