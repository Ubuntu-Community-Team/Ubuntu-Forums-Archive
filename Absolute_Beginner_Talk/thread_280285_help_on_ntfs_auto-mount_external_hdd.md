---
title: "help on ntfs auto-mount external hdd"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Nio on 2006-10-19
Hello,

i followed the guide at: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
to make my ntfs writeable.

Well now its not readable any more. (its not broken it works fine under windows)
normally i plug in my external hdd it takes some time and then gets automatically mounted and i can access the files.
now nothing happens at all
ubuntu knows there is a harddrive, but its not mounted somewhere anymore

what can i do?
i wanna either uninstall this changes to get my old system back! or make it working.
please help me!

---

### Post by xyz on 2006-10-19
Hi,
Could you please post the output of
```
 sudo gedit /etc/fstab
```

---

### Post by Nio on 2006-10-19
Thanks for your answer.

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


My removable hard drive is not listed there. (of course?)
I have 5 of them, before my try to install ntfs-3g I just had to plug them in and everything worked fine.

I am trying to install the "old" pmount and hal, but I cant find them anywhere. apt-get cant find them ...

---

### Post by xyz on 2006-10-19
Hi again-
This is what my fstab with r/w on my (Windows XP Home) NTSF partition (see **bold** line):
> <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
**/dev/hda1       /media/hda1     ntfs-3g defaults,locale=en_US.utf8   0    0** 


/dev/hda3       /media/hda3  vfat iocharset=utf8,umask=000 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



Maybe you made a typo in one of the command lines ...?

---

