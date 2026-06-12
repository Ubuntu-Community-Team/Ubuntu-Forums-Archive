---
title: "Mounting Partitions."
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by RizingDamp on 2007-03-28
Hello All,

When I partitioned my HD  for dual booting Ubuntu with XP I created a FAT32 partition so as to share files from both OS.  This is my /etc/fstab file so I can see that it did get created.:) 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
**/dev/hda6       /windows        vfat    defaults,utf8,umask=007,gid=46 0       1**
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Now on my Desktop I have an icon for my hda1 partition(xp).  Im thinking it is possible that I can have another icon on my desktp that shows my FAT32 partition?

Could one of you guys walk me through the process of achieving this as oppose to pointing me towards the Phycsocats site:)   I have had looked at it but Im not yet confident enough to decipher all that info as yet....Im still VERY new to Ubuntu(only 5 days old so far).  But I think it is along the /media statement.


Many thanks,

Andy.

---

### Post by motin on 2007-03-28
Can you see the share by visiting Places -> Computer?

If yes, drag that icon to the desktop and you are good to go. 

Otherwise, try System -> Administration -> Disks where you should be able to mount the share, and then drag it like above to your desktop.

---

### Post by RizingDamp on 2007-03-28
I cant see it in my Computer>Places Folder.  I can see it in my System>Administration>Disks window.  So how do I mount it from there??

Thanks Again,

Andy.

---

### Post by dsmaxwell on 2007-03-30
I'm having a similar problem, and am almost as new to Ubuntu and Linux as a whole.  I decided Windows sucks a long time ago and finally did something about it.  On my system I have 3 hard disks, each with one partition.  but only my linux drive will mount.  I've gone into my Administration > Disks and tried enabling both of the others but nothing happens, perhaps the solution might be similar?

---

### Post by anaconda on 2007-03-30
> **RizingDamp said:**
> Hello All,

When I partitioned my HD  for dual booting Ubuntu with XP I created a FAT32 partition so as to share files from both OS.  This is my /etc/fstab file so I can see that it did get created.:) 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
**/dev/hda6       /windows        vfat    defaults,utf8,umask=007,gid=46 0       1**
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Now on my Desktop I have an icon for my hda1 partition(xp).  Im thinking it is possible that I can have another icon on my desktp that shows my FAT32 partition?

Could one of you guys walk me through the process of achieving this as oppose to pointing me towards the Phycsocats site:)   I have had looked at it but Im not yet confident enough to decipher all that info as yet....Im still VERY new to Ubuntu(only 5 days old so far).  But I think it is along the /media statement.

Andy.

anything you mount under /media should appear on your desktop. So change the line in fstab to read:
**/dev/hda6       /media/windows        vfat    defaults,utf8,umask=007,gid=46 0       1**

and ofcourse you also have to create the directory /media/windows  othervice it wont work.
one way to do it is (from terminal):
sudo mkdir /media/windows
sudo chmod a+rwx /media/windows
first create the drectory, and then give everyone full rights to that directory.

after reboot the partition should be on your desktop.

---

### Post by rykel on 2007-03-30
Hi pals,

Not too sure if you happen to know how to help me... but recently, I set up an ext3 partition and it mounts on my Ubuntu Dapper desktop (ie. /media/sda6).

HOWEVER, I cannot use it as the owner is Root.

I know that I need to input something in /etc/fstab, but what exactly do I write there in order to enable all users to read and write to that partition?

Also, other than manually editing the fstab (which is easy, I admit), is there any GUI way to do it? For example, is there anything in gparted or "System/Administration/Disks" that can click and mount the partition, while updating fstab automatically?

Thanks!!

---

### Post by anaconda on 2007-03-30
well.. you can alwaus start filemanager with root rights.
press Alt-F2  (or open a terminal) and type: 
gksudo nautilus
and you will have root (admin) rights in your filebrowser.

another thing is to check that you have r/w-rights to the directory you mount it to.
eg. type
sudo chmod a+rwx  /media/sda6
in terminal..

(ofcourse you can change the permissions with nautilus too, if you prefer GUI-frontends)

---

### Post by rykel on 2007-04-01
> **anaconda said:**
> well.. you can alwaus start filemanager with root rights.
press Alt-F2  (or open a terminal) and type: 
gksudo nautilus
and you will have root (admin) rights in your filebrowser.

another thing is to check that you have r/w-rights to the directory you mount it to.
eg. type
sudo chmod a+rwx  /media/sda6
in terminal..

(ofcourse you can change the permissions with nautilus too, if you prefer GUI-frontends)

Hi,

Thanks for that idea up!

I managed to solve the problem by using "sudo nautilus" and changing the Owner to "<myself>" and Group to "plugdev" respectively. (I used "plugdev" for Group because my FAT32 partition, which can be written to, is under the "plugdev" group too.)

I noticed that my /etc/fstab file has NOT changed after the amendments made in Nautilus.

btw, what is "plugdev" group?

---

### Post by timbo8 on 2007-04-01
i am having a similar problem, but when i go system => administration there is no disks. i have tried updating, but to no prevail. do i need to be logged in as the root user? I am new to linux and would appreciate some help. please keep any terminal use to a minimum :)

---

