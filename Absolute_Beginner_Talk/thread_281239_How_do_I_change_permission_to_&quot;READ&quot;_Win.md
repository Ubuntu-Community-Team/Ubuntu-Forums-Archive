---
title: "How do I change permission to &quot;READ&quot; WinXp partiton"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-10-20
Hello, I'm sorry to post twice but I wrote the title wrong and mis-printed the code I was asking about for giving me permission to "Read" the media 1 WinXp partiton.

This is my more /etc/fstab and df -h:

me@me:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             9.2G  2.9G  5.9G  33% /
varrun                248M   80K  248M   1% /var/run
varlock               248M  4.0K  248M   1% /var/lock
procbususb             10M  128K  9.9M   2% /proc/bus/usb
udev                   10M  128K  9.9M   2% /dev
devshm                248M     0  248M   0% /dev/shm
lrm                   248M   18M  230M   8% /lib/modules/2.6.17-10-386/volatile
/dev/hda1              33G  5.8G   27G  18% /media/hda1
/dev/hda2              13G  3.8G  8.5G  31% /media/hda2
me@me:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=14d5392f-bc2a-4a0e-bbb5-410d6410172e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=e3f559c9-f006-4a21-9398-23d4c4bb5ad8 /media/hda2 ext3 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=4210b1ee-905e-40be-8676-707ea3095150 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
me@me:~$ /dev/hda1 /media/hda1 ntfs defaults,umask=0222 0 0
bash: /dev/hda1: Permission denied

I was told this earlier when I was in Dapper:

/dev/hda1 /media/hda1 ntfs defaults,umask=0222 0 0

Do I want to change it to:

/dev/UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults,unmask=0222 0 0

and if that is right, would I just enter it as that code in terminal, or would I have to change it in some other way?

Thanks,
-c.

---

### Post by aysiu on 2006-10-20
This is what you do--paste (do not retype) these commands into the terminal:

Unmount the drive (it appears to be mounted now): ```
sudo umount /media/hda1
``` Edit the /etc/fstab while also making a backup copy: ```
sudo nano -B /etc/fstab
``` Change this line: ```
UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0 0
``` to this line ```
UUID=B444EE8344EE47A6 /media/hda1 ntfs nls=utf8,umask=0222 0 0
``` Then save (Control-X, Y, Enter) and finally ```
sudo mount -a
``` to remount it. Should work now.

---

### Post by crimesaucer on 2006-10-20
thank you, the "-B" command, is that a back up command.

and do you know of a link to a list to all of the terminal commands.

I would love to learn these all.

---

### Post by crimesaucer on 2006-10-20
I got this back after crtl x, y, enter.

:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/B444EE8344EE47A6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I tried again and also tried some other suggestions from another post:

me@me:~$ sudo umount /media/hda1
Password:
me@me:~$ sudo nano -B /etc/fstab
me@me:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/B444EE8344EE47A6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

me@me:~$ sudo umount /media/hda1
umount: /media/hda1: not mounted
me@me:~$ sudo nano -B /etc/fstab
me@me:~$ sudo mount -o remount /media/hda1
mount: /media/hda1 not mounted already, or bad option
me@me:~$ sudo mount -o remount UUID=B444EE8344EE47A6 /media/hda1
mount: you must specify the filesystem type
me@me:~$ sudo mount -o remount UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults,unmask=0222 0 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
me@me:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/B444EE8344EE47A6,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by aysiu on 2006-10-20
That's weird. Can you post the output oof these commands? ```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by crimesaucer on 2006-10-20
sure, but I did some changes after I had problems with your tips, I'm a little impatient, I'm sorry.

these are those results:

Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4256    34186288+   7  HPFS/NTFS
/dev/hda2            4257        5958    13671315   83  Linux
/dev/hda3            5959        7174     9767520   83  Linux
/dev/hda4            7175        7296      979965    5  Extended
/dev/hda5            7175        7296      979933+  82  Linux swap / Solaris
me@me:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=14d5392f-bc2a-4a0e-bbb5-410d6410172e / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=e3f559c9-f006-4a21-9398-23d4c4bb5ad8 /media/hda2 ext3 defaults 0 2
# /dev/hda5 -- converted during upgrade to edgy
UUID=4210b1ee-905e-40be-8676-707ea3095150 none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


I tried to also edit it with these commands and none of them worked:

UUID=B444EE8344EE47A6 /media/hda1 ntfs umask=0222 0 0

and then this after saving: mount -o remount /media/hda1

then after the options list(was that correct) was shown, I tried to use this code: sudo mount -a

and I got the same fs error, or one close to it.
I save all of my terminal actions from that session if you would like to see it.

I also tried as:UUID=B444EE8344EE47A6 /media/hda1 ntfs defaults,umask=0222 0 0

And now I just tried to enter into my main xubuntu/ubuntu partition /hda2, and it wouldn't let me log in. I have those error messages written down if you would like to see them, but they basically say,"that my home directory is listed as '/me/me' but it does not appear to exist. Then it asks if I want to log in with the /root directory as the home directory. then it says use Failsafe, which I tried to change it to, then it says, "User's $HOME/.dmrc file is being ignored this prevents the default language and session from being saved. Files should be owned by user and have 644 permissions. User's HOME directory must be owned by user and not written by others.

it also said I could be out of disk space which seems wrong because I just installed in the 14gb free space. Or it might be an installation problem which seems weird because it was working fine before. But it was the 2nd install, and it is the first time I've been back to Dapper since I installed my 3rd partition of edgy.

I don't know if I caused this when I was trying to change the read permissions for the WindowsXp while in Edgy, or if something happened when installing the third partition of Edgy.

---

### Post by aysiu on 2006-10-20
Well, first of all, you've got to fix what's going on with the other stuff.

You backed up your /etc/fstab before editing it, right? Can you restore the backup?

---

### Post by crimesaucer on 2006-10-20
I'm real new to this, so could you explain the proper steps please, and thank you for your help.

Also, I used your code: sudo nano -B /etc/fstab

for all of my changes, so would there be a few back-up copies, or did I mess up and re-write it each time i wrote that code into terminal.

I also changed it back to the original way it was written and it has the blocked sign on the icon in my file systems media file.

---

### Post by aysiu on 2006-10-20
Yes, unfortunately.

When you do ```
sudo nano -B /etc/fstab
``` it creates a new file in /etc called fstab~

The backups aren't dated or unique. So you'll have /etc/fstab (your current one) and /etc/fstab~ (the one right before your current one).

---

### Post by crimesaucer on 2006-10-20
if I changed it back to exactly how it was, then will it be the same?

---

### Post by aysiu on 2006-10-20
Should be.

This whole *UUID=B444EE8344EE47A6* business is new to Ubuntu (starting with Edgy). In the past, they've always done human-readable entries like ```
/dev/hda1 /media/hda1 ntfs defaults 0 0
```

---

### Post by crimesaucer on 2006-10-20
So about dapper, I went and tried to log in so I could try to unmask the media 1 file in dapper to see if it was easier than dapper, and I couldn't log in. This was the error:

"The error messages basically says,"that my home directory is listed as '/me/me' but it does not appear to exist. Then it asks if I want to log in with the /root directory as the home directory. then it says use Failsafe, which I tried to change it to, then it says, "User's $HOME/.dmrc file is being ignored this prevents the default language and session from being saved. Files should be owned by user and have 644 permissions. User's HOME directory must be owned by user and not written by others.

it also said I could be out of disk space which seems wrong because I just installed in the 14gb free space. Or it might be an installation problem which seems weird because it was working fine before. But it was the 2nd install, and it is the first time I've been back to Dapper since I installed my 3rd partition of edgy."- from a few entries back.

---

### Post by aysiu on 2006-10-20
Are you typing *unmask* or *umask*?

I'm really confused. I don't know what you're trying to do.

And you're using Dapper? Not Edgy? I could have sworn Dapper had normal names for partitions and drives instead of that gibberish.

Why couldn't Ubuntu just mount drives properly the way Mepis does...? Yikes!

---

### Post by crimesaucer on 2006-10-20
good question, let me look. I've been known to do stupid things like that.

---

### Post by aysiu on 2006-10-20
The output of ```
cat /etc/issue
``` should let you know whether you're running Dapper or Edgy. This is what mine looks like: ```
cat /etc/issue
Ubuntu 6.10 \n \l

```

---

### Post by crimesaucer on 2006-10-20
I think that I wrote unmask, I'm sorry for wasting your time, I'll try again.

And I'm in my 3rd partiton of 6.10...but when I restarted and tryed to log in to the 2nd partiton with the Dapper 6.06 kernel, I got that error and I don't know if I just did that when trying to edit the fstab, or if I ruined it when doing the 3rd partition install of edgy which is by the way, working incredibly well. Even better than dapper so far.

The windows partiton is still working fine.

---

### Post by crimesaucer on 2006-10-20
umask worked. Thank you.

Do you think there is a way to save my ubuntu/xubuntu partition2.

I can't even log in to it. Is there a way to fix it from my 10gb 6.10 xubuntu partition3 which is working perfectly.

Thanks again for the help, and you're pretty good to notice that I was misspelling umask as "unmask".

---

### Post by aysiu on 2006-10-21
I'm not sure what's wrong, but you can mount partition 2 from within partition 3. If by "partition 2," you mean /dev/hda2: ```
sudo mkdir /media/recovery
sudo mount -t ext3 /dev/hda2 /media/recovery
gksudo nautilus
``` Then go to the /media/recovery directory.

---

### Post by crimesaucer on 2006-10-21
just write that simple code and it will try and fix my hda2 from within hda3?

I don't know why I was unable to log in on the 6.06 log in page after selecting the 6.06 kernel while in GRUB?


Thank you very so much for the help and time.

---

