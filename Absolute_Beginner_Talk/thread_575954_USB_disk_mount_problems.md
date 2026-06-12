---
title: "USB disk mount problems"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by Randulf on 2007-10-14
Hi!
I installed ubuntu for the first time and so far it has worked great except for my fake raid that I couldn't get working. I have previously used Fedora for a shot while but found it to messy and quite quickly reverted to windows.
This time however I skipped dual boot, so I have no alternative but to learn Linux.

Now, I have some strange problem with automount.
When I plug in my USB pen drive there is no problem reading and writing to it. If I ls -l /media i get:
```
drwx------  3 nisse root 16384 1970-01-01 01:00 DISK_IMG
```
Which I suppose mean that the user nisse has read and write permissions
But when I plug in my USB drive (NTFS formatted, and I can't ext3 format it scince I'm using it at work with win2k and can't install drivers) I get:
```
dr-xr-xr-x  1 root  root 45056 2007-10-09 08:19 FreeAgent Drive
```


Why does this drive mount as root and why doesn't root have write permissions?

Following a guide I installed the automatrix NTFS 3G driver.
Do I have to tell Ubuntu to use that driver instead somhow?

Another question is about my NAS drive.
I have no problem mounting it using
```
sudo mount -t smbfs //nas/dir /mnt/nas_drive -o,rw,username="user",password="pass"
```
Though I can't mount it as a normal user and here is the same, I can read it but not write.
How do I mount it as user?
And how do I edit my fstab so it automounts at boot?
I have tried putting
> \\192.168.x.xxx\\Shared /home/user/nas smbfs user,defaults 0 0
and
> \\192.168.x.xxx\\Shared /home/user/nas smbfs username="User",password="pass",defaults 0 0
in the fstab but neither works.

Thanks
/Nils

---

### Post by bvmou on 2007-10-15
If you want to mount pluggable devices as a normal user, look at pmount.  So to mount a usb hard disk as a normal user the syntax would be 'pmount /dev/usbdevice /media/mountpoint'.  If you have trouble reading and writing you can change permissions as superuser, ie, "sudo chown -r nisse /media/mountpoint"

If you have trouble with the first, check that your user is listed after the "plugdev" entry in /etc/group

I don't know much about samba but I think the basic syntax for annotating the resource in fstab is "//server/share   /mnt/data   smbfs   credentials=/etc/samba/user,rw,uid=nisse   0   0"; there is more on that here:  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by Randulf on 2007-10-15
Ah ok, I have to try that. Right now I am at work so I will try it tonight.
But is there anyway I can get it to automount with pmount? Just like my USB pen drive does? Guess that the difference is that that one has fat32 and the disk have ntfs.

"uid=nisse"
Does that mean that it will mount as my user?

Thanks for your answer!

---

### Post by bvmou on 2007-10-15
The uid is what authenticates you to the server, it would be the server's own configuration that would set your privileges.  I don't know much about NTFS but there are probably a couple of ways to make your external device pop up -- check out autofs, for example.  The pmount rules are set in /etc/pmount.allow.  I was in your shoes when I first had to deal with an external ntfs usb drive, although I did reformat it.  The reliability of read-write NTFS support may be a little overstated.  VFAT may be a good option for interoperability.

---

### Post by Randulf on 2007-10-15
It worked with pmount and chown of dir but it's terribly slow.
Is that normal??
I remember reading about ntfs write support for mac also was slow. same for linux?
Maybe I have to reformat it after all, but it'll be a pain to get the technicians at work to install ext3 support on the office computer.

Now, hope I can get my nas-disk to mount at startup without problems.

Thanks for all the help!!

Btw, is there som script or something that always run at startup? Or how do I make one?

---

### Post by timcredible on 2007-10-15
reformat your flash drive as part fat (or part fat, part ext3).  all OSs can read fat, and then you have no compatibility issues.  beware though, that fat doesn't support file permissions.  also, you can partition your flash drive to be part ext3, part fat, so you can use part of it for linux and part of it for windows.  i split my 4gb flash drive up as 2gb ext, 2gb fat, so i can save my linux files with proper file permissions, and i can also access the fat partition with both linux and windows, thereby allowing me to share files.  i also did that with my 100gb backup drive (65gb ext3, 35gb fat).

---

### Post by bvmou on 2007-10-16
Yes, NTFS write is theoretically supported but not reliable or fast.  A file allocation table is supported by everything,  including win2k -- vfat should feel and work like any other filesystem for the use you're envisioning.  Read of NTFS is always fine, but writing is not so great, and actually risky in some cases.  Regarding the second part, the boot scripts I know about are in /etc/init.d -- there is an explanation of how to work with them here: [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28) ; don't know how current that is but probably a good starting point.

---

### Post by rickwookie on 2007-10-19
> **Randulf said:**
> It worked with pmount and chown of dir but it's terribly slow.
Is that normal??
I remember reading about ntfs write support for mac also was slow. same for linux?
Maybe I have to reformat it after all, but it'll be a pain to get the technicians at work to install ext3 support on the office computer.

Now, hope I can get my nas-disk to mount at startup without problems.

Thanks for all the help!!

Btw, is there som script or something that always run at startup? Or how do I make one?

What command did you use to pmount your NTFS usb drive?

I've tried pmount /dev/sda1 but nothing gets mounted in /media/

I have ivman installed and usb flash drives (FAT) automount fine into /media/ as sda1 sdb1 etc.

Cheers.

---

### Post by Randulf on 2007-10-21
> **rickwookie said:**
> What command did you use to pmount your NTFS usb drive?

I've tried pmount /dev/sda1 but nothing gets mounted in /media/

I have ivman installed and usb flash drives (FAT) automount fine into /media/ as sda1 sdb1 etc.

Cheers.

Im not really sure but i thing i just used:
pmount /dev/sda1/ /home/usb_disk -rw

The disk is at work so I can't try it out. I just mounted it once and realized that it was unusable, changing from one folder to another took abut 30 seconds.

---

### Post by Randulf on 2007-10-21
> **bvmou said:**
> Yes, NTFS write is theoretically supported but not reliable or fast.  A file allocation table is supported by everything,  including win2k -- vfat should feel and work like any other filesystem for the use you're envisioning.  Read of NTFS is always fine, but writing is not so great, and actually risky in some cases.  Regarding the second part, the boot scripts I know about are in /etc/init.d -- there is an explanation of how to work with them here: [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28) ; don't know how current that is but probably a good starting point.

Hmm, maybe a reformat to vfat will solve my problems.

---

### Post by phuchungbhutia on 2007-10-21
how to format usb drive ...

---

### Post by vilsu on 2007-10-24
Many distros currently have automount problems. At least ubuntu, kubuntu, Fedora and Debian are suffering from the same symptoms. No one seems to know the reasons for this behaviour. It was after some patching after which these problems started.  These problems have been around at least in ubuntu 7.04  and 7.10 versions and in Debian since April 2007. 

It would really be nice to hear a comment from someone at eg. ubuntu or debian development team

---

