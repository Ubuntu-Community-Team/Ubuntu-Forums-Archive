---
title: "Not Really a Newbie....But"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by OBnascar on 2005-11-28
I have been using ubuntu for about six months now and have read a lot of post on the question I am going to ask. Either I am slow or it is put in terms I can not follow.

I have never been able to get permission on the following:

I used "partimage" to create a image of my partition hdb3 (ubuntu-reiserfs) and had them sent and stored into hdb2 (reiserfs- free space), no problem there. The problem is now I want to get them off of the same HD that my ubuntu is on. I want to move them from hdb2 to hda1 (fat32-Winxp). Ok, I am owner of hdb2, hda1 ownership is root. Now........how do I set this up so I can move my image files ? I have tried these and other things that are to numberous to list:

'sudo chgrp system_groupname /location_of_files_or_folders'
'sudo chown myusername /location_of_files_or_folders'
'sudo chown -R myusername:myusername /location_of_files_or_folders'

But none of these works for me. Should these commands be ok ? Maybe I am getting the path of the "location_of_files_or_folders" wrong ?. I just can not seem to get it right after all this time. Any help, opinions, comments or suggestions will be greatly appreciated...........thanks

I have never been able to change ownership on my floppy drive either, because the ownership of that is root also. Again, have read post after post and nothing has helped me on this either. Never have been able to use my floppy drive. I'm sure if I can find help that I can understand to the one above, or find out what I might be doing wrong, I will be able to use my floppy also.

ubuntu 5.10

---

### Post by gord on 2005-11-28
have you tryed just doing:
sudo cp <old file location> <new file location>


also, are you sure that hda1 has write permitions at all? check your fstab

---

### Post by OBnascar on 2005-11-28
[QUOTE=gord]are you sure that hda1 has write permitions at all? check your fstab[/QUOTE]

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     vfat    defaults        0       0
/dev/hdb2       /media/hdb2     reiserfs defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
------------------------------------------------------------------------
My partimage files in hdb2 are not in a directory, the path is: "/media/hdb2"
Can that be a problem ? But when I drag & drop into Hda1 it tells me I do not have permission. Everything in the hda1 partition has root as owner and I can not change it. I do have permission on the partimage files themselves in hdb2.

---

### Post by gord on 2005-11-28
to make sure your vfat partition writable you'll need to use rw,users,gid=users,umask=000 instead of 'defaults'

but from what i can tell, you are actually trying to put one partition on your second harddrive (hdb2) actually into a partition on your first harddrive (hda1), you can't do that. the best you could do is copy all the files in hdb2 to hda1 but there is a good chance you would run into problems with that


if you don't mind getting rid of the partition on hda1 (or making it smaller) gparted (sudo apt-get install gparted) might be able to make an exact copy of hdb1 onto your first harddrive.

---

### Post by OBnascar on 2005-11-28
Ok gord, this worked:
obnascar@ubuntu:~$ sudo cp /media/hdb2/gtwubu~1.000 /media/hda1

thank you, thank you !

Can anyone help me yet with me not being able to use my floppy drive. It give me a message when I try to drag & drop a simple text file (example), it just tells me I do not have permission. I have read & write permission on the text file but the floppy drive root is owner, and of course permissions are grayed out.

---

### Post by OBnascar on 2005-11-28
[QUOTE=gord] **to make sure your vfat partition writable you'll need to use rw,users,gid=users,umask=000 instead of 'defaults'**[/QUOTE]

Ok, I didn't know this, those are over my head anyway so I will just leave it be.

> **the best you could do is copy all the files in hdb2 to hda1 but there is a good chance you would run into problems with that**

Oh, oh, I already moved one. What kind of problems may it create ?

> **if you don't mind getting rid of the partition on hda1 (or making it smaller) gparted (sudo apt-get install gparted) might be able to make an exact copy of hdb1 onto your first harddrive.**

I work out of my house and I don't dare mess with hda1 (WinXP), I have some exspensive design programs on that.

best regards, 
jerry

---

### Post by gord on 2005-11-28
well it depends on what you have in there, if it was just generall stuff nothin bad should happen, but, for example, since vfat doesn't have any permitions or owners of files, all that information would be lost.

---

