---
title: "Hard Drive Problems....."
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by XLostSpartanX on 2006-07-01
Ok, well I have a 2nd HDD that I have a bunch of files and stuff on, but when I try to open it and see the files it give me this....

[IMG]http://i4.tinypic.com/16awby1.png[/IMG]

---

### Post by bikeboy on 2006-07-01
Post you fstab for us by going Applications > Terminal: cat /etc/fstab Copy and paste it here so we can have a look.

---

### Post by XLostSpartanX on 2006-07-01
Sure thing.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by woedend on 2006-07-01
what filesystem is on this unmounted hard drive?
you could do
sudo mkdir /media/sdb1

then add to you fstab
/dev/sdb1 /media/sdb1 filesystemtype defaults 0 0

where filesystem type naturally is
ext2, ext3, vfat, ntfs, etc etc....

---

### Post by XLostSpartanX on 2006-07-01
[QUOTE=woedend]what filesystem is on this unmounted hard drive?
you could do
sudo mkdir /media/sdb1

then add to you fstab
/dev/sdb1 /media/sdb1 filesystemtype defaults 0 0

where filesystem type naturally is
ext2, ext3, vfat, ntfs, etc etc....[/QUOTE]
I dont understand how to do that?  How do I add it to the fstab?

---

### Post by bikeboy on 2006-07-01
Open a terminal.
```
cd /etc
sudo cp fstab fstab.bak
sudo nano fstab
```
Use nano to edit the file, then Ctrl + X, y.
If you make a bad mistake, press "n" when promted to save. If it still goes bad, you have a backup to restore from a live cd or recovery mode.

---

### Post by woedend on 2006-07-01
right...sorry...from terminal, use
gksudo gedit /etc/fstab

then just copy and paste or type in that line, but replace filesystemtype with the file system type, naturally. 
fstab works like this
(device name) (where to show the files) (file system type) (options) (dump) (pass)
/dev/sdb1 is the device name
where to mount(show the files) is up to you, in my last example I just made up a folder name.  But the folder MUST exist(it will not be created automatically).  my sudo mkdir example above was making the directory for you.  

 save the file, then reboot.
let me know if you need further help

---

### Post by Apple 101 on 2006-07-01
In a terminal: *gksudo gedit /etc/fstab*

Hmmm... Bit slow for this thread...

---

### Post by Herman on 2006-07-01
First, you will probably find the folder for the partition in /media, two floors up from your /home/username folder. Open that, and see if there is any other folders in it other than cd-rom and flopy drive that might be your mount point for your other fileystem If there is one, open it and look.

 If not, go system/administration/disks and click partitions tab and click the differnent partitions to see if it is NTFS, FAt32, or EXT3 or Reiserfs or whatever.
Then, before you do anything too complicated, just try clicking the 'enable' button there with your mouse and see if anything happens first.
Then look in your media folder again. If there's a new folder, click on it.

If it is another Linux partition, you may need to do what has already been explained. Here's what to do with illustrations,[ *click here*]("http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu").
This shows how to edit /etc/fstab for another Linux operating system on ext3.
If it isn't ext3, it will need a different line to be added instead of that one.
See how you go now with illustrations,
Regards, Herman :D

---

### Post by u.b.u.n.t.u on 2006-07-01
To edit fstab use gedit. It is heaps more use friendly.

sudo gedit /etc/fstab

To find out what file system your HDD has:

System > Administration > Disks

Here is my fstab to give you a better idea of what one looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/storage  ext3    defaults        0       0
```

hdb1 is my 2nd HDD that is used for storage.

my hda is a XP / Ubuntu dual boot.

Post your fstab, and your HDD details from "Disks" as I have suggested above.

---

