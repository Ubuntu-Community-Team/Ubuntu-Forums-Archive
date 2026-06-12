---
title: "permissions"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by SweetTeaTurner on 2005-07-28
I have been looking around for a while on how to change the permissions of my fat32 mounted hard drive. Nothing works. If I try to change the owner, or permissions in general, of it or anything on it, it simply wont do it. This is while in root mind you. I would really like to be able to write to my hard drive, so any help would be appreciated.

---

### Post by super on 2005-07-28
you have to change the permissions in the filesystem table (fstab)

follow these instructions:
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

the important part is the umask values.

---

### Post by SweetTeaTurner on 2005-07-28
this is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb1       /media/files  vfat    iocharset=utf8,umask=000   0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

I rebooted and now the directory (/media/files) has read and write permissions but none of the files in it.

---

### Post by SweetTeaTurner on 2005-07-28
The owner of that directory and everything in it is root, so i figure I need to change that, but it wont let me. I dont have permission to do so.

---

### Post by odin on 2005-07-29
If you can do it (I guess you can cause it looks like you are talking about your own computer) just enable the root account to change the permissions with:

sudo passwd root

change the permissions and then if you dont want the root account enable(something that almost everyone here will suggest you) just disable it with:

sudo passwd -l root

hope this is what you wanted  :grin:

---

### Post by super on 2005-08-01
sorry i took so long to follow up.  :( 


you need to add this to your fstab entry for hdb1:

/dev/hda5 /media/shared vfat **rw,user**,iocharset=utf8,umask=000 0 0

the rw,user allow users to write to the drive

---

### Post by bim54 on 2005-08-05
I'm trying to follow these Instructions:

[B]Q: How to mount Windows partitions (FAT) on boot-up, and allow all users to read/write?
   1. Read General Notes
   2. Read How to list partition tables?
   3.e.g. Assumed that /dev/hda1 is the location of Windows partition (FAT)
     Local mount folder: /media/windows
   4.

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

   5. Append the following line at the end of file

/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       0

   6. Save the edited file (sample)
   7. Read How to remount /etc/fstab without rebooting?
[/B]
and in trying to edit the /etc/fstab I'm finding I can't write to it. So I went on a search to see how to do it, which brought me to this thread and I did this: (above post by Odin)

I[B]f you can do it (I guess you can cause it looks like you are talking about your own computer) just enable the root account to change the permissions with:

sudo passwd root

change the permissions and then if you dont want the root account enable(something that almost everyone here will suggest you) just disable it with:

sudo passwd -l root

hope this is what you wanted

[/B]

How do I reverse the "sudo passwd -l root" that I did?
And...how do I edit the /etc/fstab to where I can write those changes?

If I'm not being clear in my explantion, please forgive...it's been a long day and I should have quit working on this earlier.
Thanks in advance

---

### Post by odin on 2005-08-05
Ok maybe I didnt explain it right.When you enable the root account do the following.Go to the menu System->management(I am not sure if this is what you have in your menu cause mine is not in english but it should be the second tab)->configuration of the login screen(again the second one and not sure about the tranlation) and finally in the security tab allow root to login.

After this you log out and log in again as root.Go to a terminal and edit fstab(vi /etc/fstab) and add the line for mounting the partition.Then just save it log out and log in with your normal user,disable the root account and that should be it.To enable root again it should be enough with sudo passwd root again.

---

