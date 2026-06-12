---
title: "Permissions on a firewire drive?"
date: 2006-06-08
forum: Absolute Beginner Talk
---

### Post by hotstovejer on 2006-06-08
Hi all,

I have an external FW drive, and when I go to use Gnome Partition Editor, it won't let me format it to the format I want. It was a MacOS drive, but for some reason, I can't write to either that drive, or my other USB external, or to the NTFS IDE drive that I am TRYING to copy info over from so I CAN format it (but I understand the problem with the NTFS one)

Here is a copy of my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda3       /media/hda3     ext2    defaults        0       2
/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Now, I don't even see the NTFS drive in there (hdb1), but I don't know if that's commonplace or not.

Also, would a Firewire drive come up as a different device if it was on firewire, vs USB?

Thanks for any help!

Jeremy

---

### Post by Sutekh on 2006-06-09
[quote=hotstovejer]
Now, I don't even see the NTFS drive in there (hdb1), but I don't know if that's commonplace or not.
[/quote] If you haven't added anything to your /etc/fstab then it is commonplace to find that there is no entry there.

You will need to determine the location of your firewire device and then edit the /etc/fstab to allow you to access it.

If you enter this command in a Terminal (Applications -> Accessories menu) you should be shown a list of all the partitions that you can mount
```
sudo fdisk -l
```From there it is an easy matter of editing the /etc/fstab.  I'll need the output from the *fdisk* command, but I can show you how to mount the NTFS drive now.


To start you should create a mount folder for the NTFS drive.  I'll use /mnt/hdb1 for the sake of this example.  You can change it if you wish.  

Then you need to backup the file, then edit it with the editor of your choice.  
```
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Then you need to add a line like this
```
/dev/hdb1     /mnt/hdb1    ntfs    nls=utf8,umask=0222    0    0
``` Save the file and exit.  Then mount the NTFS drive using
```
sudo mount /media/hdb1
``` OR```
sudo mount -a
``` 
Once we know the location and format of the Firewire, I imagine it should be a similar process to mount it.

---

