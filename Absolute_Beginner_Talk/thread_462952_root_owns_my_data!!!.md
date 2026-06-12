---
title: "root owns my data!!!"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by enfantterrible on 2007-06-03
hello all...

i have all my data (mp3s, pics, etc) on a second hard drive located in /media/hdc1 

i can't download to there because the folder is owned by root and i dont have write/change permission. actually that hard drive is gonna be the share between xp and ubuntu and i really want to be able to write there ! 

how do i switch the ownership to me? 

must be easy, i tried some sudo chown but apparently nothing happens ?

---

### Post by drs305 on 2007-06-03
Did you use this command? (changing user and group ownership)

```
sudo chown -R username:groupname /media/hdc1
```

Example: sudo chown -R drs1:drs1 /media/hdc1

The -R changes ownership of all subdirectories and files as well.

---

### Post by YoG%*@ on 2007-06-03
hi

what filesystem does the second drive have?
can you post the outputs of 
```

sudo fdisk -l
mount

```

---

### Post by whizbaby on 2007-06-03
I guess u have to set the permissions at mounting time. For doing that type
man mount
and look out for the options 'user' or 'umask' (if the drive is formatted fat32 (not ntfs) search for 'fat').
U can search in the manual by hitting '/' and inserting your search string behind, e.g. /umask RETURN_KEY. With the 'n' key u can jump to the next occurence, with 'N' u jump backwards.

---

### Post by pappapump on 2007-06-03
Go to applications, add/remove then type ntfs in the search window and install ntfs tools.
Then find it in system tools and click it to name your mount point and all will be well.
Enable read/write to be able to have full access.

---

### Post by slick1537 on 2007-06-03
Don't forget you need to install NTFS write support for ubuntu to write to a NTFS partition.  By default most linux distributions will only read NTFS.  Search for NTFS-3g in synaptic for the driver and automatic install.

---

### Post by enfantterrible on 2007-06-03
hi thanks everybody for so many answers!

the second drive is FAT32 and linux reads it perfectly. now, i'd say my best option would be to change the owner from root to myself, so i can do what i want to that drive.

when i try the  "sudo chown -R username:groupname /media/hdc1" i get asked for a password. i give root password and it's wrong then i try my password and it starts listing each file in the directory + "Operation not permitted"

---

### Post by drs305 on 2007-06-03
My bad for not picking up it may not be ext3 in your first post. You can't use chown on FAT32. You can change your fstab settings to get read/write permissions. I'll do some research and post if someone else doesn't get you the answer faster.

Edited: Here is an example of a FAT32 fstab with permissions. You will have to edit the /dev/hda2 line for your setup. The uid/gid give permissions to the user and group whose IDs are 1000:

/dev/hda2       /media/hdc1 vfat iocharset=utf8,umask=000,uid=1000,gid=1000 0 0

---

### Post by enfantterrible on 2007-06-03
sorry i guess my linux level is not enough but i am not sure what to do with that command!

i have tried text editing the file /dev/hda2 but it's not a file  (?) i guess that after this is done my next step will be finding a good guide on linux filesystem and basics... 

but now i want to get my basic tools workings!
thx for help

---

### Post by Outrunner on 2007-06-03
That line would be found in /etc/fstab.Please post the output of

```
cat /etc/fstab
```

---

### Post by vanadium on 2007-06-03
This might help you

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows)

---

### Post by enfantterrible on 2007-06-03
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=31f31b0b-ec14-4678-8d6c-bf9876c11b6f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3162-1DDB  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=1C0E-1768  /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=16fa2749-91aa-4942-b6ba-98e8f23a77ce none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by drs305 on 2007-06-03
Once you provide us with the output of the command Outrunner asked you for, you will run two commands. The first will back up your /etc/fstab file so you will have a copy should something go wrong with the editing. The second command will open up a text editor so you can change the fstab settings to allow you to write to a FAT32 partition.

The fstab file is read during boot and assigns permissions and mount points to your partitions. So that is the file we will have you edit. The commands are:

```
sudo cp /etc/fstab /etc/fstab-backup
gksudo gedit /etc/fstab
```

Once it is open, we will edit the line which contains your FAT32 partiton. If you already know the location, you would edit that line in fstab. If not, we'll tell you which line to change when we see what your fstab currently looks like.

---

### Post by drs305 on 2007-06-03
```
sudo cp /etc/fstab /etc/fstab-backup
gksudo gedit /etc/fstab
```

Change:
UUID=1C0E-1768 /media/hdc1 vfat defaults,utf8,umask=007,gid=46 0 1

To:
UUID=1C0E-1768 /media/hdc1 vfat iocharset=utf8,umask=000,uid=1000,gid=1000 0 1

Save and close the file. To refresh fstab and get the new settings to work, run:
```

sudo umount -a
sudo mount -a

```

---

### Post by enfantterrible on 2007-06-03
ok, the output is the following

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=31f31b0b-ec14-4678-8d6c-bf9876c11b6f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3162-1DDB  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc1
UUID=1C0E-1768  /media/hdc1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=16fa2749-91aa-4942-b6ba-98e8f23a77ce none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



as far as i understood, the drive is /media/hdc1 (whose label is DATASHARE)
i made the backup copy, but i have no clue on what should i change (and on which logic)!

---

### Post by enfantterrible on 2007-06-03
ok thanks... IT WORKED !!

i think i got some of the logic behind (uid=userid and guid=group id) but have a long way to go... i will start with a good manual, probably the one suggested earlier on.

thanks all !
r

---

### Post by enfantterrible on 2007-06-03
ooooopps i spoke too quick: the drive itself is writeable now, but some folders (my pictures, and some other) are still locked (there's a lock symbol on the top-right of the folder icon, if that might help)...

---

### Post by silkstone on 2007-06-03
First back up fstab (cp /etc/fstab /etc/fstab.bak)

Then...

```
sudo umount /media/hdc1
```

```
gksudo gedit /etc/fstab
```

And change the line to something like this :

```
/dev/hdc1 /media/hdc1 vfat users,auto,uid=user_name,gid=users,umask=007 0 0
```

(Replace user_name with your username. ;) )

Then mount with

```
mount /media/hdc1
```

That should give you ownership of hdc1 and everything in it.

---

### Post by enfantterrible on 2007-06-03
cool :)

now some folders were still locked, but i became the owner and was able to unlock them read/write/xcute..

thanks all !

---

