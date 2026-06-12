---
title: "Going Insane! Partition/Folder Permissions!"
date: 2007-01-05
forum: Absolute Beginner Talk
---

### Post by CreatorAmongFriends on 2007-01-05
I need some help here. I've been trying to do this for some time and have gotten no where. Heres my dilemma.

I have a 160gb hard drive. From there i had to transfer my old data off of it and now im ready to put it back on. Its been partitioned into three partitions, Music, Movies, Data. So when i go to transfer the data back into their respective folders it gives me a hassle saying that i do not have permission to do such a thing. Access denied. Im gonna scream, im great with computers but im getting stonewalled here. Any help at all would be grand!

---

### Post by Bachstelze on 2007-01-05
What filesystem(s) are the partition formatted in ?

---

### Post by CreatorAmongFriends on 2007-01-05
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=08950e58-50cb-4d89-bcde-3b1d4dbaa6d5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=91781596-b42d-410e-a633-38545c540e02 /data/          ext3    defaults        0       2
# /dev/hdb2
UUID=22cce879-b3d0-42a0-88ae-a5e7dbc8ab72 /movies/        ext3    defaults        0       2
# /dev/hdb3
UUID=b9d83ce0-3b80-4286-be56-536592960e87 /music/         ext3    defaults        0       2
# /dev/hdb4
UUID=3a672b57-265f-4778-a0ba-cee5774f500b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


its the "hdb1-4" thats giving me issues!

---

### Post by bodhi.zazen on 2007-01-05
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```

_Linux_: [Psychocats Mount Linux](http://www.psychocats.net/ubuntu/mountlinux)
To set permissions, mount the partition, then chmod```
sudo chmod 777 /mount/point
```

To mount at boot you will need to edit /etc/fstab (as outlined in the links above).
For an overview of fstab see: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

_For access to ext2/3 from windows see_ : [http://www.fs-driver.org/](http://www.fs-driver.org/)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by Henry Rayker on 2007-01-05
use the mv command with sudo permissions? Or, if you really trust yourself, open your file manager windows with the gksudo permission

ex:```
gksudo nautilus
```

EDIT: Just re-read the question and realized you should probably have ownership of these partitions. Do the sudo chmod 777 [name of mount point]

---

### Post by Peturrr on 2007-01-05
Looks like you mounted your folders on the root filesystem. So, I think the solution wil be something like this:

In a terminal:```
sudo chown *username* /*foldername*
```
This way the folders will be made yours instead of root. Repeat this command for every folder.

I am not entirely sure about the exact command, but somebody else will probably help you if this won't work.

---

### Post by CreatorAmongFriends on 2007-01-05
okay i tried the;
matt@Sic6:~$ sudo chown -R matt:matt /music
matt@Sic6:~$ sudo chown -R matt:matt /music/
matt@Sic6:~$ sudo chmod -R 755 /music/

and it didnt work at all. I dont understand. I do things exactly as asked of me and still nothing. I dont know what to do here. Should i add that im running the 64bit version of Ubuntu 6.10

---

### Post by taurus on 2007-01-05
```
sudo chmod -R 777 /music
```

---

### Post by Bachstelze on 2007-01-05
CHMOD to 777 is very insecure, please don't do it unless you enjoy playing with fire. Instead, set ownership to you and CHMOD to someting more reasonable, e.g. :

```

sudo chown xxx:xxx /data /movies /music
sudo chmod 755 /data /movies /music
```

replace xxx with your username of course ;) Also, the -R switch to chown/chmod will set ownershir/permissions for the dir as well as any file/subdir it contains.

---

### Post by bodhi.zazen on 2007-01-05
```
sudo chown user:group /directory
sudo chmod 777 /directory
```

Where user:group are say user_name:user_name or user_name:users

If you are paranoid, use user_name:user_name and chmod 770

---

### Post by CreatorAmongFriends on 2007-01-05
it still says the owner is root and its greyed out, my god. Im going nuts!

---

### Post by Bachstelze on 2007-01-05
Curse nautilus, run *ls -l /* and paste what you get :)

---

### Post by CreatorAmongFriends on 2007-01-05
im sorry i dont quite follow, im on hour 4. Trying everything i can read. Could you possibly clarify a but more please?

---

### Post by CreatorAmongFriends on 2007-01-05
matt@Sic6:~$ ls -l /music
total 48
drwxrwxrwx 2 matt matt 49152 2007-01-05 16:55 lost+found

thats what i get. Makes no sense to me. Clarity!?

---

### Post by Bachstelze on 2007-01-05
What I'm saying is that nautilus perhaps needs a restart or something else to get aware of the ownership change, so one way to make sure the chages have been applied is to open up a console and run :

```
ls -l /
```

EDIT : Please chmod to 755 ! Otherwise, everything worked, it was just Nautilus that didn't understand it :p Why do you think people still use the console ;)

---

### Post by CreatorAmongFriends on 2007-01-05
oooh okay. So you suggest a restart on my computer? What does what i posted mean. Does it mean i finally have permission to use the folder?

---

### Post by Bachstelze on 2007-01-05
Yes, and of course you don't need to restart your computer, just Nautilus :)

---

### Post by Frak on 2007-01-05
> **HymnToLife said:**
> Yes, and of course you don't need to restart your computer, just Nautilus :)
i.e. Ctrl+Alt+Backspace

---

### Post by CreatorAmongFriends on 2007-01-05
well i'll sound like a total n00b but i dont know what Nautilus is but i restarted the whole computer and its perfect. Thanks so much guys! You all are the reason im in the Ubuntu/linux camp. Windows is horrible but worse off, no support. Keep up the good work and and i'll definately pass on what knowledge i learn. Thanks so much!

---

### Post by Bachstelze on 2007-01-05
For information, Nautilus is your file browser (assuming you're running GNOME), so all that was needed was closing and reopening it :) In Linux, you never need to reboot unless you install a new kernel.

---

### Post by CreatorAmongFriends on 2007-01-05
God Bless Linux and their nifty ideas...haha. Thanks for the info!

---

