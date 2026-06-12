---
title: "HDA1 wont give up permissions"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by Drew32 on 2006-01-04
I have my Windows partition mounted in /media/hda1 but only root can access it and i want my standard account to be able to access it.  Ive tried CHMOD 777 HDA1 which says it works but still wont let anything but root access it.  any suggestions?

---

### Post by amohanty on 2006-01-04
In your /etc/fstab in the line that mounts your windows partition
change the **default** to something like **ro,user,auto,umask=022**

The **default**  will be the fourth part of the line. If you are doubtful about it, post the contents of your /etc/fstab.

HTH
AM

---

### Post by Omnios on 2006-01-04
Here are couple of mounting windows partitions in Ubuntu from the onofficial starters guide they are known to work, there are 4 entries there pertaining to mounting window drives.

[http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows")

 Personaly I use
 
 ```
/dev/hda2       /media/vfat     vfat    rw,users,gid=users,umask=000,       0       0
```

 As it gives me good permissions and also shows up in the menu/ places/ computer and also on my desktop.

---

### Post by Drew32 on 2006-01-04
[QUOTE=amohanty]In your /etc/fstab in the line that mounts your windows partition
change the **default** to something like **ro,user,auto,umask=022**

The **default**  will be the fourth part of the line. If you are doubtful about it, post the contents of your /etc/fstab.

HTH
AM[/QUOTE]


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

not sure what you meant so here is my fstab

---

### Post by Omnios on 2006-01-04
in terminal type

sudo gedit /etc/fstab

this will open your fstab file with the gedit text editor, this is the file that automounts your drives when you boot up[

---

### Post by amohanty on 2006-01-04
Change this line:
> /dev/hda1 /media/hda1 ntfs defaults 0 0

to:
> /dev/hda1       /media/hda1        ntfs    ro,user,auto,umask=022        0       0

Whoops missed that one: follow Omnios directions to edit the file.

HTH

---

### Post by Drew32 on 2006-01-04
yea NVM guys thanks though, i followed the guide and unmounted HDA1 and created a new one called windows with new permissions and it worked!

but now how do i remove the old directory HDA1, RM doesnt work

---

### Post by amohanty on 2006-01-04
sudo rm -rf /media/hda1

---

### Post by Drew32 on 2006-01-04
[QUOTE=amohanty]sudo rm -rf /media/hda1[/QUOTE]

Awsome worked, thanks!

---

