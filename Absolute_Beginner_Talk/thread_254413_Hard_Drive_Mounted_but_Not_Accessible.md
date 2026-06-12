---
title: "Hard Drive Mounted but Not Accessible"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Gomez_Adams on 2006-09-09
I have tried to install a second hard drive and can not make it visible in the File Browser.  fdisk, mount, GPARTED and Disk Manager show it is there, but I can not acees it in the File Browser.  I tried it with two different drives, known to be good.  In Disk Manager, when I try to browse contents of the disk, I get shot back to the folder the drive is mounted to rather than to the drive itself.  Here is what I did:

Partition and Format to ext3 using GPARTED.
Create new folder in /mnt and made the folder read and write using chown and chmod per [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html).
Edit /etc/fstab to point to the mount point.
Run sudo mount -a to mount the drive.

The disk shows up in File Manager when I first install and format it, but disapears when I reboot.  Following are contents of fstab.  /mnt/40G is the added directory.  ALso tried with Pass setting of 2.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1       /mnt/40G        ext3    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


I have searched the forums on the topic of Hard Drives with no success.  Any suggestions?

---

### Post by orb9220 on 2006-09-09
You do have a folder called 40G as in /mnt/40g or /mnt/40G watch for typo's on case sensitive issue that was my boo-boo.

---

### Post by Gomez_Adams on 2006-09-09
No typos.  Verified 40G for both fstab and folder name.

---

### Post by bodhi.zazen on 2006-09-10
> **Gomez_Adams said:**
> No typos.  Verified 40G for both fstab and folder name.

Obviously someting is not right.

Start by logging out and then back in.

If that is ineffective, unmount the dirve and re-mount it.

Error messages?

Try changing fstab to:
/dev/hdb1 /mnt/40G ext3 users,auto,rw 0 0

If still stuck re post fstab with outpt of
ls -l /mnt | grep 40

---

### Post by Gomez_Adams on 2006-09-10
Changed content of fstab to following and rebooted with no change in situation.  Contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1       /mnt/40G        ext3    users,auto,rw   0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Here is result of command:

gomez@gomez-desktop:~$ ls -l /mnt | grep 40
drwxr-xr-x 2 gomez gomez 4096 2006-09-09 22:44 40g
drwxr-xr-x 3 gomez gomez 4096 2006-09-09 22:42 40G
gomez@gomez-desktop:~$

I also tried unmounting and remounting the drive with no effect.  BTW, initial attempt used 40G for the folder name, but I also tried 40g in case uppercase in a folder name was verboten.  Will delete unused folder one I get this worked out.

---

### Post by bodhi.zazen on 2006-09-10
My mistake. :oops:

try the optins **user**,auto,rw

Like this
```
/dev/hdb1 /mnt/40G ext3 **user,auto,rw** 0 0
```

Unmount and you should be able to re-mount as a user.

---

### Post by Gomez_Adams on 2006-09-11
Umount'ed and mounted and also re-started and still no-go.  The problem is not with mounting.  BIOS and all system tools (fdisk, mount, GPARTED and Disk Manager) indicated it is physically present and mounted.  The drive just does not show up in Nautilis file manager, so that I can add/remove files to/from the drive.

Here is what I get when I check space available from command line:

gomez@gomez-desktop:~$ df /dev/hdb1
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb1             39516244    131232  37377692   1% /mnt/40G
gomez@gomez-desktop:~$

Also tried cp and mkdir commands on /dev/hdb1 and received error messages: 

cp: target `/dev/hdb1' is not a directory

mkdir: cannot create directory `/dev/hdb1/data': Not a directory

---

### Post by bodhi.zazen on 2006-09-11
LOL :lol: I get it now.....

You do not access the partition via /dev/hdb1

You access it via the mount point or /mnt/40G

Try:
```
mkdir /mnt/40G/test
```

You should not get an error message. You will "see" the partition in Nautilus is you go to /mnt. It will appear as a "folder" with a label "40G". The "40G" directory will similarly contain a directory "test".

---

### Post by Gomez_Adams on 2006-09-11
Added directory /mnt/40G/test, rebooted and still no-go.  Just for laughs, I'll try the procedure on a third hard drive and record everything I can before I reboot and it disappears.

---

### Post by catlett on 2006-09-11
First lets try to mount the partition manually. Open /etc/fstab with```
 sudo gedit /etc/fstab
``` and comment out the line for the drive
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
#/dev/hdb1 /mnt/40G ext3 users,auto,rw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0 
Restart so the drive is not noticed by /etc/fstab or the system
Now lets make a new directory and then mount it manually there. If this works then we can just add to /etc/fstab and that is it but if it fails, something else is going on.
Enter these 2 commands
```
sudo mkdir /media/40g
```
```
sudo mount /dev/hdb1 -t ext3 /media/40g
```
If this works, there may be an icon on the desktop or if not go to Places<Computer<Filesystem and look in the Media folder for the 40g folder.
If this fails, post the error plus the output of this command ```
sudo fdisk -l
```

---

### Post by bodhi.zazen on 2006-09-11
> **Gomez_Adams said:**
> Added directory /mnt/40G/test, rebooted and still no-go.  Just for laughs, I'll try the procedure on a third hard drive and record everything I can before I reboot and it disappears.

LOL :lol: Do you "see" the partition in nautilus now? That was the original question.

You need to unmount the drive or you will "loose" data. This is because, unlike windows, Linux does not write data to the drive right away.

also if the drive is not mounted, yo will write data to the /mnt/40G directory, but not the drive.

Add "sync" to the list of options in fstab.

Changing your mount point to /media/40 G is a good suggestion.

---

### Post by Gomez_Adams on 2006-09-11
Strangeness.  Proceeded as directed and was able to mount the drive manually.  Could not access the drive, so did:

gomez@gomez-desktop:~$ sudo  chown -R gomez:gomez /media/40g
gomez@gomez-desktop:~$ sudo chmod -R 755 /media/40g

Was able to access the drive and copied a whole folder of graphics files to the drive.  Edited /etc/fstab to uncomment the line /dev/hdb1 (changed mount point to /media/40g), restarted and drive was still there.  Can acces, R & W.  PFM.  They ought to write this stuff down somewhwere.  Happy.  Thank you.

---

### Post by catlett on 2006-09-11
Glad you knew how to change the permissions. I didn't want to clutter the post or get too "into it". I just wanted to start trouble-shooting by attempting to manually mount the drive. Anyways, glad you're up amnd running. Also you now see how the ubuntu forum works. Now you will be the one to answer the "help cannot access drive" posts. If you are up to it, you can post a how to someday about mounting here [http://www.ubuntuforums.org/forumdisplay.php?f=100](http://www.ubuntuforums.org/forumdisplay.php?f=100)
Take care.

---

### Post by Gomez_Adams on 2006-09-13
Remarked out the line that adds the hard drive in fstab, restarted and was able to manually mount it.  After setting permissions to the added mount directory, I restored the hdb1 line to fstab, restarted and the filesystem loaded automatically.  Installed yet another drive as slave to CD-R drive on IDE2 port as hdd using the same procedure and both have remained accessible after several reboots.

---

### Post by Gomez_Adams on 2006-09-13
Supplemental:

Sorry I missed the previous response and repeated myself, though I did note success with a second added hard drive.

I would like to do a little more experimentation before I post any recommendations, such as whether the issue was caused by using mnt folder instead of media etc...

Thanks to all for the help.  I'm sure I'll be back soon.

---

