---
title: "Command line help."
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by Chake99 on 2006-09-08
I can't boot my computer into proper ubuntu or XP currently, due to a problem (you can find more @[http://ubuntuforums.org/showthread.php?t=251768](http://ubuntuforums.org/showthread.php?t=251768) AKA "Help. Neither Ubuntu or XP will boot.").

Anyways I can boot my computer into the Linux command line as root, and before I try to restore my master boot record from a COMPLETELY LEGAL *cough* windows CD that I'm not sure if I trust, I want to try and back up some files that are on my NTFS partition in case it goes awry and my computer dies. I couldn't seem to access my ntfs partition while logged on to my computer in live cd mode however.

I was hoping to login to my computer as root and copy some directories to a usb key.

How would I do that from the command line?

So far my plan of action is:

cd /dev/hda1 . If I can't get in that way, something like:
mount -t /dev/hda1 ntfs /home
or
cd /tmp/disks-conf-hda1 and if I can't get past that
mount -t /tmp/disks-conf-hda1 ntfs /home

Once I get into my ntfs partition and I would then navigate until finding a folder I wished to save and then
mv *windows directory* /dev/sda/files (/dev/sda is my usb key)
or
mv *windows directory* /home/*location where usb key is mounted*

As you people can most like see, I am sort of confused, and when operating as root, I don't want to be in a situation where I don't know what I'm doing. 

So help?

What should I be doing?

Thanks in advance.

---

### Post by IYY on 2006-09-08
```
cd /dev/hda1
```

This will not work. The files in /dev are not directories but devices. If the device in question is a disk (like hda1), it must be mounted.

Here are instructions for what you're trying to do ( based on [http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)    ):

Assuming that your hard disk is indeed /dev/hda1 (it could be /dev/hda2 or something else).

```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

You don't need to be root to copy the files.

```
cd /media/windows
```

Find the directories you wish to transfer. Suppose /media/windows/MP3/TheBeatles/ is such a directory:

```
cp -r /media/windows/MP3/TheBeatles/ /media/whereverTheUSBisMounted
```

The only problem you have left is how to mount the USB device. I can't answer that from the top of my head because I usually just let Gnome handle that.

---

### Post by ewl1217 on 2006-09-08
> cd /dev/hda1 . If I can't get in that way, something like:
 mount -t /dev/hda1 ntfs /home
 or
 cd /tmp/disks-conf-hda1 and if I can't get past that
 mount -t /tmp/disks-conf-hda1 ntfs /home
 
 Once I get into my ntfs partition and I would then navigate until finding a folder I wished to save and then
 mv *windows directory* /dev/sda/files (/dev/sda is my usb key)
 or
 mv *windows directory* /home/*location where usb key is mounted*

I don't know much about mount commands, but otherwise it doesn't seem bad. There are only two problems I notice. The first is that /dev/sda should be /dev/sda1 (I'm assuming you have just one partition on the usb key.). The second is that you should use the "cp -r" command instead of "mv". The "mv" command will cut-and-paste the files instead of copy-and-paste them. This is bad because it will erase from the NTFS drive and may have odd results because while read support for NTFS is good, write support is flaky.

---

### Post by Chake99 on 2006-09-08
> 
This will not work. The files in /dev are not directories but devices. If the device in question is a disk (like hda1), it must be mounted.
Thanks. I thought that could be the case but wasn't sure.

> 
Here are instructions for what you're trying to do ( based on [http://ubuntuguide.org/wiki/Dapper#H...to_read_](http://ubuntuguide.org/wiki/Dapper#H...to_read_) only ):

Thanks a ton. This is exactly what I was looking for. 

> 
Assuming that your hard disk is indeed /dev/hda1 (it could be /dev/hda2 or something else).

The hard drive is indeed hda1

> 
You don't need to be root to copy the files.

But I can't login into ubuntu properly, only through a live cd or recovery mode. I'm not sure I can access the hard drive while in live cd mode and recovery puts me on a command line as root. 

Can one properly sudo from live cd? I guess I could try. 

> I don't know much about mount commands, but otherwise it doesn't seem bad. There are only two problems I notice. The first is that /dev/sda should be /dev/sda1 (I'm assuming you have just one partition on the usb key.). The second is that you should use the "cp -r" command instead of "mv". The "mv" command will cut-and-paste the files instead of copy-and-paste them. This is bad because it will erase from the NTFS drive and may have odd results because while read support for NTFS is good, write support is flaky. 

Thanks, but won't I need to write the files to the USB key in ntfs? EEEK. 

What could go wrong with the usb key? And is there anyway to make the write support more secure?

---

### Post by IYY on 2006-09-08
> But I can't login into ubuntu properly, only through a live cd or recovery mode. I'm not sure I can access the hard drive while in live cd mode and recovery puts me on a command line as root.

Can one properly sudo from live cd? I guess I could try. 

You can access the hard drive in Live CD mode after you mount it, and if you use it you will not be root but a user named 'ubuntu' who can sudo without a password. If you use recovery mode you will be root, but you can still follow all the steps in the exact same way, just without sudo.


> Thanks, but won't I need to write the files to the USB key in ntfs? EEEK.

What could go wrong with the usb key? And is there anyway to make the write support more secure?

I usually format my USB keys in FAT32. Reason? Most of the improvements on the new filesystems are due to the average size of these systems. 80 GB drives being the average. But a USB key is what, 512 MB? FAT32 is perfectly fine for that, and you can securely write from Ubuntu and Windows to it.

Anyway, even if your key is formatted in NTFS, I think the worst that could happen is that the data on it will become corrupted.

---

