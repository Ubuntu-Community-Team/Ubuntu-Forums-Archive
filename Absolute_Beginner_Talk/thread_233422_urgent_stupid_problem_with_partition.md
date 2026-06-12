---
title: "urgent:: stupid problem with partition"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-08-10
hi,
i'm desperade.
in the previous installation (with breezy) i had made a partition
for the root, one for the swap and the rest of the disk in a partition for the home. The i did a big mistake and i had to reinstall everything. I took the occasion to install dapper. Seen that the home was full of important data i didn't format it. I formated instead the root and i installed dapper. The problem is that i hadn't created an new home partition and the installer has put the new home inside the root that is small (10gb).  The old home is seen as an partition with name home.  Now i moved the important data in the new home, but i filled it completely. Is it possible now ,without formatting the root and reinstalling, turn the old home as it was the new and move the data of the new home to the old in order to have the situation i had before (so 3 partition /, swap and home)? 
I wouldn't format the root because i've a 56k modem and i spent the latest 3 weeks to update the system :(

---

### Post by timhaughton on 2006-08-10
Hi, I guess a nice "quack quack oops" sound would come in useful here :)

I'm not a Linux expert so you might want to confirm this. Basically, you should be able to edit the /etc/fstab file and add your old partition as a mount point for /home.

A quick man fstab (I think) might help, although I dont't have a linux to hand at the minute to check. It might be easier to do this in a single user mode by booting to the CD. It's entirely doable, so don't panic.

A guru might be able to give you step by step instructions.

Tim

---

### Post by ubunlilluz on 2006-08-10
i'm at work now i can't try.
but if i boot by the live cd, will it see the home of the hd and the file system directory or only the ones of the cd?

---

### Post by ubunlilluz on 2006-08-10
:(

---

### Post by coffeecat on 2006-08-10
I can't give you a detailed reply, as I haven't got time at the moment, but I can describe the steps I believe you need to take. First - care is needed because there are hidden configuration files in /home and these may differ between your old Breezy install and Dapper. If you mix them up you will get serious problems. These are the steps I would take, but do at your own risk.

1 Copy your personal data from the Breezy /home partition to the Dapper /home folder. Or if there's not room to an external HD (see 2).

2 Delete everything in the Breezy /home partition. (Back it up to an external drive as well just in case.)

3 Copy everything (including hidden files and folders) from the Dapper /home to the /home partition. If you copied your personal files to an external device, copy them back.

4 Edit /etc/fstab so that it mounts the /home partition as home

5 Delete the /home folder in your root partition. (**Please** make sure everything is backed up!)

6 Create a symlink folder called /home in your root partition linking to the /home partition.

7 Reboot.

I'm sure I've got this right, but you might want to see if anyone else comments. If you need to know what line to put in fstab, post back with details of your partition layout.

**Afterthought**, Yes you'll need to use the live CD because you'll probably run into all sorts of problems if you try to delete your /home folder from within the installed Dapper.

---

### Post by ubunlilluz on 2006-08-10
tomorrow is my last working day, then ufficially i'll be on holiday so i'll try it. thanks

---

### Post by coffeecat on 2006-08-10
I thought I'd make one mistake and I find I have. Hope you pick this up. It's to do with steps 4, 5 and 6. I've got the principles nearly right but not the details. Don't delete the whole of /home in your root partition, just the contents of /home, leaving an empty /home folder in your root partition. Don't bother with 6 - you don't need a symlink. Then, when you add your fstab line, use /home (in the root partition) as the mount point.

I'm more confident with that, but I'd be happier if someone else were to comment.

Best of luck.

---

### Post by ubunlilluz on 2006-08-13
i did it, but i have a little problem . At login, aAfter inserting user and password
it appears this message (i've translated it in english)

Home/.dmrc of the user is ignored. This avoid the saving of the session and
predefinite language, the file'd have to be of the propriety of the user and havig as permission 644.
The directory $Home of the user must be of the propriety of the user and not writeble by others.


i tried to do "sudo chmod 644 ./dmrc" and "sudo chown -R lillux:lillux /home/lillux" but the problem, if i rebbot, remains.

the new fstab is :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hdb5       /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb7       /home     ext3    defaults        0       2
/dev/hdb6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  vfat    rw,user,noauto  0       0


thanks

---

