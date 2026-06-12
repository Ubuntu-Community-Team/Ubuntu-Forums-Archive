---
title: "External HDD problems caused by Ubuntu update?"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-12-18
I've been looking around a while for a solution to my Iomega external FAT32 - HDD - permission problem, and have found some answers. But nothing works! I've noticed others too having the same problem, exactly similar to mine and starting at the same time as my problems did. Is it possible that there was an update or something that played havoc with my and others permissions? My external FAT32 - HDD was working perfectly until I did an update some days ago, then the whole mess with "read - only" and "permission denied" started! Is there something else going on than just "normal" Ubuntu - bugs? Anyone?

I'm just asking, as I want to get this to work! I want to use my HDD again!

---

### Post by taurus on 2006-12-18
Can you paste the output of these two commands here?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```
And I assume you are running Edgy!

---

### Post by lodravah on 2006-12-18
Dapper Drake: 2.6.15-27-686
IOMEGA 320Gb External Harddrive FAT#" - Fileformat is plugged in and on:

lodravah:~$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3560    28595668+  83  Linux
/dev/hda2            3561        3648      706860    5  Extended
/dev/hda5            3561        3648      706828+  82  Linux swap / Solaris

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641    b  W95 FAT32



lodravah:~$ cat /etc/fstab
'# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I've been around this dance already. I keep hearing that my external HDD doesn't show up in fstab, and indeed it seems it does not! But it is plugged in, and I am using it to stream "Battlestar Galactiga" as I type! It was working fine, then it stopped working fine. I've tried chmod, chown, editing fstab.. But make suggestions, by all means. It will not let me do anything to change permissions or write to the HDD..

---

### Post by lodravah on 2006-12-18
Of course i meant FAT32...

---

### Post by taurus on 2006-12-18
With fat32/vfat, chmod & chown won't work because those two commands only work for Linux filesystem...  Do you plan to plug that external HD to the machine all the time or do you plan to plug and unplug it while Ubuntu is still running?

If it connects to your machine all the time, then the best way is to modify /etc/fstab and add an entry to it with read/write.  Otherwise, you can mount it by hand every time you plug it in...

---

### Post by lodravah on 2006-12-18
I was planning on mounting/unmounting as I use it, because I have an, shall we say not exactly state-of-the-art, laptop with only two USB's. But please, give me both ways to try to get permission to write to it again.. I don't quite know how to mount manually. Should be HDD be connected and on, or disconnected?

---

### Post by lodravah on 2006-12-18
bumping this a bit.. been struggling with this for a while and would really like to get a solution..

---

### Post by taurus on 2006-12-18
For /etc/fstab:
```

/dev/sda1   /media/share   vfat   iocharset=utf8,umask=000   0   0

```

For commandline:
```

sudo mount -t vfat /dev/sda1 /media/share -o umask=000

```
(assuming your USB external drive is /dev/sda1 and you have /media/share mount point...)

---

### Post by lodravah on 2006-12-18
Okay thanks! But the HDD automounts when turned on. Should I then unmount it (in that case how? From terminal og right - clicking?) and then mount it from terminal again? Or is there another way?

---

### Post by taurus on 2006-12-18
You can unmount it from a terminal if you want.  You need to know either the partition name (i.e. /dev/sda1) or the mount point.  You can find out both with

```
df -h
```
Assuming again that it is /dev/sda1, then unmount it 

```
sudo umount /dev/sda1
```

---

### Post by lodravah on 2006-12-18
Okay

I unmounted by using your command: it worked.. 

Tried mounting using your previous command:
lodravah:~$ sudo mount -t vfat /dev/sda1 /media/share -o umask=000

Answer: mount: mount point /media/share does not exist

Okay, I open Home-folder, go into filesystems, then to /media/IOMEGA_HDD. Change the commandline into:

lodravah:~$ sudo mount -t vfat /dev/sda1 /media/IOMEGA_HDD -o umask=000

It mounts, but I am still not allowed to write to it, as I do not have permission. Under "properties" file owner and file group is "root." 

lodravah:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              27G  9.9G   16G  39% /
varrun                117M   84K  117M   1% /var/run
varlock               117M  4.0K  117M   1% /var/lock
udev                  117M  108K  117M   1% /dev
devshm                117M     0  117M   0% /dev/shm
lrm                   117M   18M  100M  16% /lib/modules/2.6.15-27-686/volatile
/dev/sda1             299G   51G  248G  17% /media/IOMEGA_HDD

Ideas?

---

### Post by taurus on 2006-12-18
Okay, what happens if you unmount it first,

```
sudo umount /dev/sda1
```
then add this entry to the end of /etc/fstab.

```
gksudo gedit /etc/fstab  <-- open a text editor as root
```
```
/dev/sda1   /media/IOMEGA_HDD   vfat   iocharset=utf8,umask=000   0   0
```
Save it and mount it again with

```
sudo mount -a
```
Now, see if you can write to it, /media/IOMEGA_HDD...

---

### Post by lodravah on 2006-12-18
Nope.. No permission to write to the HDD. I umounted it, added the line, mounted it "sudo mount -a." Even switched it off. Now it won't automount, so I sudo mount -a again. Still no luck. This is fstab from gedit:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1   /media/IOMEGA_HDD   vfat   iocharset=utf8,umask=000   0   0


Doesn't look right when pasted this in.. The only entry which is not in line with the others is the /dev/sda1. It it slightly out of place because of the long "IOMEGA" - name.

---

### Post by taurus on 2006-12-18
It has to be one line or "sudo mount -a" will complain about it...

```
/dev/sda1 /media/IOMEGA_HDD vfat iocharset=utf8,umask=000 0 0
```

---

### Post by lodravah on 2006-12-18
like this?

lodravah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1/media/IOMEGA_HDD   vfat   iocharset=utf8,umask=000   0   0

---

### Post by taurus on 2006-12-18
No.  There should be a space between /dev/sda1 and /media/IOMEG_HDD

```
/dev/sda1   /media/IOMEGA_HDD   vfat   iocharset=utf8,umask=000   0   0
```
I guess for now, you probably have to modify /media/IOMEGA_HDD with

```
gksudo nautilus
```

---

### Post by lodravah on 2006-12-18
lodravah:~$ sudo mount -a
mount: mount point vfat does not exist

Nope, guess not. How then do you mean? 

*Missed last post, trying now..*

---

### Post by lodravah on 2006-12-18
I edited the line in fstab again, now it mounts fine. Looks like this now, copied from terminal:

lodravah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1   /media/IOMEGA_HDD   vfat   iocharset=utf8,umask=000   0   0

Even with "gksudo nautilus" I am not allowed to write to the HDD because I do not have permission to do so.

---

### Post by taurus on 2006-12-18
> **lodravah said:**
> I
Even with "gksudo nautilus" I am not allowed to write to the HDD because I do not have permission to do so.

Not even with "gksudo nautilus"?  What's the output of this command, from terminal, then?

```
ls -la /media
```
Do you want to copy stuff to that USB IOMEGA drive?  Assuming you want to copy filename.txt to /media/IOMEGA_HDD, what happens when you run this command?

```
sudo  cp  filename.txt  /media/IOMEGA_HDD
```

---

### Post by lodravah on 2006-12-18
Here goes:

lodravah:~$ ls -la /media
total 48
drwxr-xr-x  5 root root  4096 2006-12-18 16:24 .
drwxr-xr-x 22 root root  4096 2006-09-20 20:31 ..
lrwxrwxrwx  1 root root     6 2006-05-08 18:16 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2006-05-08 18:16 cdrom0
lrwxrwxrwx  1 root root     7 2006-05-08 18:16 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2006-05-08 18:16 floppy0
drwxrwxrwx 15 root root 32768 1970-01-01 01:00 IOMEGA_HDD

Do the colours of the devices mean anything in above command?

copy - command:

lodravah:~$ sudo  cp  /home/lodravah/Desktop/Screenshot.png  /media/IOMEGA_HDD
cp: cannot create regular file `/media/IOMEGA_HDD/Screenshot.png': Read-only file system

I also get that inbetween the permission - problem..

---

### Post by taurus on 2006-12-18
When you browse to /media with nautilus, do you see a lock or something similar for /media/IOMEGA_HDD?

Also, I assume that USB drive is writable to, right!  You didn't happen to lock it (read-only)!

---

### Post by lodravah on 2006-12-18
Yes, in both "normal" nautilus and "root" nautilus there is a lock on all files/folders directly under /media/IOMEGA_HDD. However, subfolders from mainfolders in /IOMEGA_HDD do not have this lock - symbol.

---

### Post by taurus on 2006-12-18
Once there's a lock on /media/IOMEGA_HDD, I don't think you can write to anything under it.  Now, place a cursor in top of the icon for /media/IOMEGA_HDD and click the right botton.  You would see a menu and there is an option, Properties.  Check that and see if you can change the permission.  You may have to use "gksudo nautilus" to do that though...

And I assume there is no physical lock/switch on the drive that you can turn on (read/write) and off (read-only), right!

---

### Post by lodravah on 2006-12-18
Using nautilus and right-clicking on one of the folders in /IOMEGA_HDD, i get the properties which say: I am not the owner, so I am not allowed to make any changes to the permissions. When I right-click and properties the USB - HDD icon on my desktop, it says nothing. Both state that the owner is root. In nautilus I cannot right-click the icon to the left, the one together with "desktop" and "file system." I only get greyed "remove" and "rename" options. 

No, it is not any physical write-lock on it. If that had been the problem, and I did no see it, I would not be fit to boil an egg :)

I gksudo nautilus:

When right-clicking the folders in /IOMEGA_HDD I can the tick-boxes are not greyed out as in "normal" nautilus, but I am not allowed to make any changes as it is "on a read - only disk." I am not allowed to copy anything to the HDD because I do not have permission to do so. When navigating to IOMEGA_HDD's icon under "file system" /media/IOMEGA_HDD: the lock - icon is there, and I am not allowed to make any changes as it is a read - only disk..

---

### Post by lodravah on 2006-12-18
I used to be able to copy/paste files in /usr - folder before as well, without being root. For instance changing the "distributor-logo.png" Then suddenly I had to use gksudo nautilus do do it. Could this of importance? An permission - error within nautilus with regards to whom is root?

---

### Post by lodravah on 2006-12-18
*bumping*

---

### Post by lodravah on 2006-12-18
Taurus was helping me here, but seems to have gone away.. Does anyone else know a solution to my problem?

---

### Post by lodravah on 2006-12-18
a quick recap of problem: I am unable to write to my external USB - IOMEGA HDD. Nautilus and terminal says I do not have permission, but it also sometimes says I am not allowed to change permission when I am root, because the HDD is a read - only device (which it is_not_!). The HDD was working perfectly, and then I didn't..

Please help, and also read the above posts for more info. All attempts so far have failed, and I am close to the egde.. 

lodravah

---

### Post by lodravah on 2006-12-19
*bump*

---

### Post by taurus on 2006-12-19
> **lodravah said:**
> Taurus was helping me here, but seems to have gone away.. Does anyone else know a solution to my problem?

Taurus stepped away for few hours because he had to go to work to pay the bills!!!  ;) 

Not sure exactly why it wouldn't let you write to it even though you use sudo!  And you said that happened after you update!  Remember what was being updated?

---

### Post by lodravah on 2006-12-19
Work schmork, Ubuntu gotta take precedence :) Had an exam today myself. Did go to it, though..

I am not sure it is an update that caused this, but the two last actions I did before it started acting weird was an update, might have been glib or something. Did an kernel-image update earlier, I think. or it might have been that one. The second one was transferring all my mp3's to the HDD.. 

Did I tell you about the earlier problems? I used to be able to edit files in /usr when not in root. Like changing "distrubutor-logo.png" to make custom menus in panel.. But suddenly I was not able to that anymore because of permission - problems. Then I had to do it via root - nautilus... But this was a lot earlier. Just for info.

Good to have your help back :)

---

### Post by taurus on 2006-12-19
Not sure why you could edit /usr without using sudo (or logged in as root) though...

---

### Post by lodravah on 2006-12-21
I'm not sure either.. Do you think there might me something strange with nautilus? Was thinking of doing a clean install from Dapper - LIVE - CD. I wonder if that is going to help? I ran Ubuntu from the LIVE - CD, and then had the same problems. Is that a sign that it will not work? Do you have anymore ideas?

Sorry for late reply. Went home for christmas, been out of touch a while.

---

### Post by taurus on 2006-12-21
If you plan to reinstall, I recommend Edgy Eft then.  Don't forget to reformat those partitions before you install it so you would have a clean system when it's done.

---

### Post by lodravah on 2006-12-21
What do you mean, exactly? That I need to format the FAT32 -system on my portable HDD, or make sure that it is a clean Edgy - install?

---

### Post by taurus on 2006-12-21
Make sure it's a clean Edgy install, formatting the partitions where you plan to install Edgy on.  Leave the FAT32 alone unless you have a reason to reformat it as well, after backup important files on that FAT32 partition!

---

### Post by lodravah on 2006-12-21
Mokay.. I'll give edgy a try first then. But that won't be until after Christmas. First, I'm going to try installing Dapper on my dad's serously buggy, ISDN - connecting Win98 - box. Wish me luck :P

---

### Post by taurus on 2006-12-21
> **lodravah said:**
> First, I'm going to try installing Dapper on my dad's serously buggy, ISDN - connecting Win98 - box. Wish me luck :P
Good luck...  [-o<

---

