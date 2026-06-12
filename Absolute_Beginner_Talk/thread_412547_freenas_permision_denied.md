---
title: "freenas permision denied"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by meekey on 2007-04-18
i am very new to ubuntu about a week now but getting used to it. but seem to having problems.
i made my old computer into a freenas box. it all seems to working fine, works great in windows xp, but in ubuntu it will only allow me to read and write files to freenas through ftp. when i try any other method i get this sort of message.
----

Could not open the file smb://freenas/disk1/nfs%20stuff.txt.
You do not have the permissions necessary to open the file.
----

i know that this seems to be a simple matter of changing the permissions, but how do i do this, 

i was reading a few articles about this and think it is to do with editing fstab but what address do i put in 

this is a copy of my fstab file 

----
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e8ecb0d5-d132-4b04-b459-8817e9a34275 /               ext3    defaults,acl,errors=remount-ro 0       1
# /dev/hdb5
UUID=e5b1ea35-e50e-431b-98d6-7fe5cb979af2 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
------

where do i find the path to my freenas box, and wot am i supposed to put in this file if anything.

---

### Post by Seisen on 2007-04-18
Do you have samba or nfs installed on Ubuntu.?

---

### Post by meekey on 2007-04-18
it seems that i have both installed 

i have it sort of working but it seems very slow i now have an extra drive on my desktop which allows me to read write and delete files from my nas drive.
i found a solution at this link 

[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

