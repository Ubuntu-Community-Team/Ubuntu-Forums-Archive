---
title: "[SOLVED] did i screw somethign up?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by shortybookit on 2007-09-03
i have windows/ubuntu dual boot

when i am in windows i only see the windows partition==== which is fine

when i am in the ubuntu partition i ALSO see the windows partition as hda1 which i do not like 
how do i write to the ubuntu partition from ubuntu?

another question since it is not being answered no were else

i have the compiz config manager in my preferences but i can not get anything to work--
i have an intel card that everyone says works with the 3d stuff but again it is not working

can i uninstall compiz and install something else that will work

like desktop effects is this similar? to get some cool looking effects?

---

### Post by agemon on 2007-09-03
from what i know, you can't write to ntfs partitions from ubuntu (you can write fat ones though ;) ), unless of course you have a special program; try searching for 'ntfs' in synaptic. If you do not want the ntfs partition to be in /media/hda1, make a backup of /etc/fstab then edit it and look for 2 lines that say:

# /dev/hda1
UUID=blablablabla /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

and change /media/hda1 to what ever you want, eg: /media/mywinpart, also, make sure you have the required folder in /media (in my example, you must have the 'mywinpart' in /media)

about compiz.. not sure, does the driver work properly?
also, do you have ubuntu 7.04? because it has some desktop effects of it's own system->preferences->desktop effects (or something like that) and yes, if you want, remove compiz and try beryl. On my computer it works on 7.04 but it didn't on 6.06

---

### Post by justleen on 2007-09-03
install the ntfs-3g tools, if you want to write to NTFS under linux.

---

### Post by nowshining on 2007-09-03
hi writing to filesystem is not acceptable requiring administrator privileges sine Ubuntu is linux - for security sakes you can only write to ur home folder - and only writing/adding/removing a file from the internals of the rest of the file system again like i said requre those privileges either directly sudo a file such as sudo gedit /etc/hosts for the hosts file  in the terminal and input your password or so..
 
for the NTFS thing like the others said download that
 
install
 
go thru the applications menu/start menu find it and if you need more help after that just ask... :)
 
again linux is not like windows where you can write to add/remove any file anywere in any folder even windows/system I used to be an windows user too..don't worry you'll get used to it and it becomes a normal reaction.. also don't worry the home folder is only viewable by you and root and so if one adds a user it is all defaulted and they cannot again see yours nor u see theirs.. :) but also don't worry unlike windows where everything requires Administrator privileges / root such programs in Ubuntu Linux do not so everything will run fine under the default user just fine with just about all options... - :)

---

