---
title: "USB hard drives mounted as read-only"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Zaen on 2007-01-22
I have a usb hard drive that I plugged in and started transferring files to when It came up with an error message saying it couldn't transfer the files because it was a read-only drive. I hadn't been messing with any of the settings for that. Now I can't write files to it, even though it comes up in the preferences menu as read-write-execute permissions. 

This might be useless information, but 
1. I have the same problem with other hard-drive based usb storage devices, but not flash based ones, and all internal hard drives seem unaffected. 
2. Any copied files have permission problems.(I.E. read-only, but supposedly read-write-execute permissions under the preferences menu)
3. All of the hard drives use fat32 file systems. 

I'm not really sure what to do, as when I searched the forums, all I found was a tip saying to go through system->preferences->removable Media (I'm probably not searching the right things). 

Thanks in advance, 
Zaen

---

### Post by taurus on 2007-01-22
Can you post these two commands here?

Applications -> Accessories -> Terminal
```
mount
df -h
```

---

### Post by Zaen on 2007-01-22
for mount

/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type ext3 (rw)
/dev/sda1 on /media/MP4 PLAYER type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)


and for df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              34G  7.3G   26G  23% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hdb1             184G   72G  103G  42% /media/hdb1
/dev/sda1              19G  214M   19G   2% /media/MP4 PLAYER

fyi, this is with the usb hard drive plugged in, it's the MP4 PLAYER

---

### Post by Zaen on 2007-01-22
sorry, accidental double post

---

### Post by Bachstelze on 2007-01-22
Could you please paste the contents of /etc/fstab, just to be sure ?

---

### Post by Zaen on 2007-01-22
command: cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb1       /media/hdb1/    ext3    defaults        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

is that what you wanted?

---

### Post by Bachstelze on 2007-01-22
Funny, your USB drive doesn't appear... Anyway, are you the first user you created when installing the system ? The drive is mounted with uid 1000 and umask 077 so user 1000 definitely should have write access to it. Could you please paste the output of this ?

```
cat /etc/passwd | grep $(whoami)
```

---

### Post by Zaen on 2007-01-22
Yes, I am the first user created on this computer, although I have set a root password ( sudo passwd root ). I haven't done anything with it besides aptitude, and I stopped doing that in favor of the sudo command.

here's the output:
alex:x:1000:1000:alex,,,:/home/alex:/bin/bash

---

### Post by Bachstelze on 2007-01-22
Now, that's becoming *really* weird. Your UID is 1000 and the drive is mounted with uid=1000 and umask=077 so you *definitely* should have write access to it. That space in the mountpoint annoys me too, but I don't think it's related... Anyway, try to just create a file in it, with something like

```
whoami > /media/MP4\ PLAYER/foobar
```

does that work or does it tell you "permission denied" ?

---

### Post by Zaen on 2007-01-22
I pasted in the command as you wrote it and it came up with the following:

bash: /media/MP4 PLAYER/foobar: Read-only file system

---

### Post by Happy_Man on 2007-01-22
Did you try just right-clicking the volume and selecting Properties? I've found that many a hard problem has been fixed that way... Just my two cents from a guy who has no understanding of computer language.

You might want to try that as root tho...otherwise you won't be able to edit the settings. 

```
sudo nautilus
```

---

### Post by Zaen on 2007-01-22
Yes, I have checked it, and the settings there should allow me to write to the drive. It's really weird because although I'm no genius at linux either, linux is usually straitforward enough that when it says it should work, it does.

Maybe it's the cd I burned although I have checked it and it came up error-free... I previously used the alternate install cd rather than the live install cd (the install I'm having the problem with)

---

### Post by Buck2348 on 2007-01-22
Is there any way the drive itself could be set as write-protected?  Can Windows write to it?

---

### Post by taurus on 2007-01-22
```
sudo umount /dev/sda1
sudo mount -t vfat /dev/sda1 /media/"MP4 PLAYER" -o iocharset=utf8,umask=000
```
Now, see if you can write/save to /media/"MP4 PLAYER".

---

### Post by Zaen on 2007-01-22
No, unfortunately not. I can succesfully write to the drive under windows. 
Thanks though

---

### Post by Zaen on 2007-01-22
Taurus:
The commands you suggested didn't come up with any errors, but it didn't work either.

If it helps any, when I just right clicked on the files (not the drive) I noticed they were under the owner root, with all options to read, write, and execute greyed out. this is really weird. I know after the drive stopped letting me write files that I was able to play them, but this no longer is possible. I'm really confused how this happened. 

Although it may be a little extreme, to me a reinstall is not out of the question because it isn't that difficult to do, and I've wanted to shift a few things around in my computer anyways. it would be nice to get this straitened out though.

---

### Post by Happy_Man on 2007-01-22
As I thought...for some reason, Ubuntu has given your USB drive a root status. You'll need sudo nautilus to get write access. At least now we may have the problem down. Try manually going into properties under root nautilus and manually changing permissions.

---

### Post by taurus on 2007-01-22
Can you post these outputs here?

```
ls -la /media
sudo fdisk -l
```

---

### Post by Zaen on 2007-01-22
Happy_Man:
that's what it would seem like. what I want to know is why? also, when I typed sudo nautilus into the command line and go to the mp4 player, it now says the permissions can't be discovered. (but they are still the same when I go to the other places i checked).


Taurus:

ls -la /media
```

total 45
drwxr-xr-x  5 root root  4096 2007-01-22 21:08 .
drwxr-xr-x 21 root root  4096 2006-12-19 18:24 ..
lrwxrwxrwx  1 root root     6 2006-12-19 09:40 cdrom -> cdrom0
dr-xr-xr-x  1 root root   576 1999-12-07 06:00 cdrom0
drwxr-xr-x  4 root root  4096 2006-11-15 16:48 hdb1
drwxrwxrwx 22 root root 32768 1969-12-31 18:00 MP4 PLAYER

```

 sudo fdisk -l
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            9606        9729      996030   82  Linux swap / Solaris
/dev/hda3            5100        9605    36194445   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401   83  Linux

Disk /dev/sda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2431    19526976    c  W95 FAT32 (LBA)
```

---

### Post by taurus on 2007-01-22
```

sudo umount /dev/sda1
sudo mkdir /media/sda1
sudo mount -t vfat /dev/sda1 /media/sda1 -o iocharset=utf8,umask=000
ls -la /media
```

---

### Post by Zaen on 2007-01-22
ls -la /media
```

total 49
drwxr-xr-x  6 root root  4096 2007-01-22 21:50 .
drwxr-xr-x 21 root root  4096 2006-12-19 18:24 ..
lrwxrwxrwx  1 root root     6 2006-12-19 09:40 cdrom -> cdrom0
dr-xr-xr-x  1 root root   576 1999-12-07 06:00 cdrom0
drwxr-xr-x  4 root root  4096 2006-11-15 16:48 hdb1
drwxr-xr-x  2 root root  4096 2007-01-22 21:08 MP4 PLAYER
drwxrwxrwx 22 root root 32768 1969-12-31 18:00 sda1
```

I assume you wanted the output from that command. (I tried adding a directory through the gui after I had done all the commands, and it failed again).

---

### Post by Buck2348 on 2007-01-22
Did you try copying to /media/MP4 PLAYER or to /media/sda1?  Could you post the output of ```
df -h 
```again please?

---

### Post by bradford72 on 2007-01-23
I just got over a (what sounds like) a similar problem...I have an external usb hdd, and the icon for it shows on my desktop...I can look at what's there, but not make any directories on it, or save files to it except through sudo....when I checked properties tab, it told me I couldn't make any changes because I wasn't the owner!

Here's how I got it to work (finally)

open up the terminal and try this...

```
sudo chown "username" "/dirname/dirname"
```er, for mine, the username is bradford and the access path to my drive is /media/usbdisk...so my code looked like this
```
sudo chown bradford /media/bradford
```I tested it by creating a directory by right-clicking with nautilus, I also wrote a file in writer and saved it there, and right now I am ripping a cd to the drive...seems to work just fine now....hope this helped

---

### Post by Zaen on 2007-01-23
buck2348:
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              34G  7.3G   26G  23% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-27-386/volatile
/dev/hdb1             184G   72G  103G  42% /media/hdb1
/dev/hdc              361M  361M     0 100% /media/cdrom0
/dev/sda1              19G  214M   19G   2% /media/MP4 PLAYER


bradford72:
I tried to get the command to work, and when I typed in the following 

```
sudo chown "alex" "/media/MP4 PLAYER"
```

it came up with the error message:

```
chown: cannot access `/media/MP4 PLAYER': No such file or directory
```
I thought I had a solution, but back onto trying to find a solution

---

### Post by Maxtorm on 2007-01-23
For what it's worth, I have replicated this behaviour with an external USB HD (Seagate 320GB Barracuda).  I first thought that perhaps the NTFS drive was having problems with the partition size, so I split it into a bunch of 32 GB partitions.  No luck.  Nothing I did would give me write access to the drive.  I (1st) used root to specify ownership to the logged on user, (2nd) took ownership as root and attempted to write to the drive, (3rd) attempted to explicitly mount as read/write.  No matter what I did, Ubuntu reported the drive was read-only.  Usually I was simply attempting to "touch" a file in the root directory of the empty drive, but I verified each time using Nautilus and also gksudoing Nautilus.  Nothing.  Here's the thing though: I booted a live Knoppix CD and it could write to the drive with absolutely no complaints.  Not sure what the issue is, but it seems to be specific to Ubuntu/Debian.

UPDATE Jan 26 2007: Dumb user (me) - didn't realize that NTFS was only supported as a read-only mount.  I guess Knoppix is using ntfs-3g.  Ended up  formatting the USB HD as ext2 then installed the ext2 driver for Windows.

---

### Post by Kabatwa on 2007-03-26
Hey Zaen,

I don't know if you still have this problem but I recently had almost exactly the same situation that you describe here.
I know this sounds totally stupid but have you checked any kind of read only lock actually physically on your hard drives? Whether that be some kind of switch or in the menu? This is what was happening to me and it would not let me write to my drive (a mp3 player that showed up as a usb removable disk in ubuntu.) I hope that maybe this can possibly help you!


Tim

---

### Post by arbulus on 2007-03-26
I had the same problem a while back.  The solution was that I didn't have an entry for the drive in the fstab.  I found this great how to that really helped out.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Once you create the mount point and get the fstab set up correctly, then you should be able to change the permissions as you like.

---

### Post by scohar70 on 2007-06-11
Short version:  My drive is now working!  Thanks to the folks in this thread for helping me figure it out!!!

Long version:

> **arbulus said:**
> I had the same problem a while back.  The solution was that I didn't have an entry for the drive in the fstab.  I found this great how to that really helped out.

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Once you create the mount point and get the fstab set up correctly, then you should be able to change the permissions as you like.

This help page quoted above was _really useful._  It provided me with the clues to get my SEAGATE 300 GB FAT32 USB external drive working with read/write permissions.

The secret lay in getting the fstab entries EXACTLY right.  For this the man page for mount was also useful.

Notice the SEADISK300G entry in the mount output, particularly the mount options that are there by default.  SEADISK300G was what mounted automatically when I plugged in the drive.  What I wanted was to get /media/seadisk to be the mount point for the drive.

```

scott@jaguar:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
**/dev/sdb1 on /media/SEADISK300G type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)**

```

I was trying to set up my fstab to mount /dev/sdb1 into /media/seagate, but I couldn't get it to mount read-write, nor could I reset the permissions properly to allow myself access.  The key issues were the nosuid, and the umask.

After reading the URL above, and the man page for mount, I changed my /etc/fstab to be the following:

```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=a10d9bc6-ab54-45d2-8b85-69959b5790c6 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=861070d6-c4f8-4a99-8db1-5816c6dc2692 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
**/dev/sdb1 /media/seagate vfat user,rw,suid,umask=0000,utf8 0 0**

```

Then I performed the following commands to unmount and remount the drive with the new options:

```

sudo umount /media/seagate
sudo mount -a

```

After remounting it, the entry from the mount command looks good:

```

scott@jaguar:/media$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
**/dev/sdb1 on /media/seagate type vfat (rw,noexec,nodev,umask=0000,utf8)**

```

And of course, now the drive works.  Thanks for all the clues from everybody in this thread.  I finally got it working!   :guitar:

---

### Post by Basilius on 2007-06-24
Scohar, keep rockin'

Your solution worked perfectly for my Western Digital MyBook.  I was having the same read/only problem as in the rest of the thread.

Mostly just posting this in thanks and just in case someone searches on MyBook, the thread will appear.

Eric

---

