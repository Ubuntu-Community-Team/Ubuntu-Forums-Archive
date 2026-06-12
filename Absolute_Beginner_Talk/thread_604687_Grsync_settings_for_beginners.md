---
title: "Grsync settings for beginners?"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2007-11-06
Greetings, community!

I am trying to use Grsync to backup my home folder to an External Hard Drive, but am only having partial success so far...

As far as I can see, all the home folder gets transfered to my EHD OK & I can go in & open files OK, so minimum requirements are met.

But, every time I run, I get a red "Completed with errors" message & a red list of 2500 errors!

If I try to use Grsync to restore (just as a test) then I can restore whole folders (like Desktop) OK but not individual files, which are greyed out.

I so far failed to find any explanations of the different setting available in Grsync.
They look like nice plain English, but I am not sure enough of what they may mean or do.

First I tried the settings suggested in: [http://ubuntuforums.org/showpost.php?p=3448164&postcount=2](http://ubuntuforums.org/showpost.php?p=3448164&postcount=2) 
(Check Preserve time, Verbose and Show transfer progress. Leave the rest unchecked.) & got error messages like: 
"backup/.nautilus/metafiles/.file:%2F%2F%2Fhome%2Fchris%2Fmenu.lsts.xml.8eMCI3" failed: Invalid argument (22) "

Another post suggested also checking: 
Preserve permissions, Preserve owner, Delete on destination & Preserve devices, but with that I get error messages like:
"rsync: chgrp "/media/LACIE/Rsync backup/.evolution" failed: Operation not permitted (1) "

Basically, two questions:
[LIST=1]
[*]Is there anywhere I can find understandable explanations of the selectable settings for Grsync? (I Googled for hours)
[*]Any suggestions about the error messages or the greyed-out files?
[/LIST] 

Thanks in advance!

---

### Post by timcredible on 2007-11-06
make sure the external hard drive is formatted as ext3 so you get file permissions - they usually come pre-formatted with fat32, which doesn't support file permissions.  

i've been using grsync for quite a while, and this post has me thinking i should add a how-to about it at 

[http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=50&Itemid=1](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=50&Itemid=1)  

I'll have a nice how-to with screenprints by tomorrow this time for you, please check it out in 24 hours.

---

### Post by 2CV67 on 2007-11-06
Astonishing service!

Thanks  :)

---

### Post by 2CV67 on 2007-11-08
Timcredible:

Thanks very much for such a good clear & simple How-To at amazing speed!

Grsync seems to be working for me now, but I still have several questions & comments, which may help me & anybody else following this thread...

Refering to your How-To:
My external hard drive was all FAT32 & I had seen several threads saying this was OK except for files over 4Go (which I don't have) but I never had a clean run until I created an ext3 partition, as you said.

I remember using gparted during installation, but it must have been on CD so I had to install it via Synapt.
Thanks for the big red warning to avoid wiping the main drive!
I found my EHD OK, but it took me a couple of minutes to figure out I needed to click on it then select Partition > Unmount before I could start to resize it.
I then created a new partition as ext3 but when I came to "Apply" the 2 changes, I got a big warning "error: resize could not be applied".
It looked as though it had been applied to the original partition, but the new partition not created, so I did that again & "Applied" OK this time.

Your terminal session note on directory structure goes somewhat over my head for now...

The Custom Launcher on the Panel for Grsync was a beautiful idea but I got bogged down finding that Grsync was located in /usr/lib (or somewhere) then was unable to find the right Ikon. I then found the easy way was to right-click on the Grsync button in Applications > Internet then select "Add this launcher to panel" when it appears immediately with the right Ikon.

Grsync never asks me for a password!
Is this a problem & how can I set it to ask?
I am fiddling with sbackup in parallel with Grsync & sbackup always asks for a p/w.

I used your suggested settings (except "skip newer" which I don't have) but would still like to understand what they all imply...

Clicking on execute showed a whole bunch of errors (error 13) & the new folder I thought I had created did not appear.

I then shifted to root (by opening a session as root - I know this is frowned on) & ran a Grsync of my (home) Desktop to a new folder in EHD ext3 OK.

I emptied that folder (but left it there) & shifted back to my own desk, when I was able to Grsync my desktop & then home folder no problem.

So now it seems to work (in the backup direction anyway) but I am not sure about the "root" effect.

Thinking about restoring from the EHD, I see that individual files (stuff on my desktop for instance) are grayed out in Grsync so cannot be recovered individually, though they are perfectly openable & readable in a file browser.
Is that usual?

My new partition somehow got called "disk" & I can't find how to rename it - all attempts are refused with no explanation...

Many many thanks again for the How-To!

---

### Post by 2CV67 on 2007-11-08
In trying to rename my new ext3 partition (currently media/disk & /dev/sda2) I found e2label didn't see it at all & found "bad magic numbers" for my other partitions. (see below)
Then I saw that neither the new partition, nor the main partition on that external hard drive figure in fstab.

I suppose these findings are not normal & indicate problems somewhere?

All this is way over my head, so I would really appreciate any explanations & fixes!

These are copies from terminal:

mount - shows sda1 & sda2
chris@DESKTOP:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda4 on /media/hda4 type vfat (rw,utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda2 on /media/disk type ext3 (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/LACIE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
chris@DESKTOP:~$ 

cat /etc/fstab - does not show sda1 or sda2
chris@DESKTOP:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=06ae7fc3-93b0-44ca-a63a-cbf18a8e8277 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=2B1B-1302  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/hda4
UUID=4578-5BC4  /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=5c873d64-3194-4b1c-b5ad-fb0c949a689a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
chris@DESKTOP:~$ 

e2label - "magic numbers" for others - nothing for sda2
chris@DESKTOP:~$ sudo e2label /dev/hda1
Password:
e2label: Bad magic number in super-block while trying to open /dev/hda1
Couldn't find valid filesystem superblock.
chris@DESKTOP:~$ sudo e2label /dev/sda2

chris@DESKTOP:~$ sudo e2label /dev/sda1
e2label: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
chris@DESKTOP:~$

---

### Post by 2CV67 on 2007-11-10
Maybe all that was too verbose, so try something simpler...

To restore something I've backed up with Grsync, should I be able to restore individual files?

So far, it looks like I can restore whole folders OK but if I try to go deeper, the actual files are grayed out & cannot be selected.
All these files are present on the External Hard Drive & can be opened OK by file browser.
If I recover a folder with Grsync, the files inside are OK.

Thanks for any clarification!

---

