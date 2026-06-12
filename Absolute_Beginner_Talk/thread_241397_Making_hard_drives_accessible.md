---
title: "Making hard drives accessible"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by yustr on 2006-08-22
Brand new user here so please have patience! 

I’ve successfully installed 6.06. I’m pretty happy so far. Internet access was a pain (new computer, new location, new cable - so many places to check) until I downloaded the Linux drivers from the MB manufacturers site. 

I'm struggling to understand how the Linux file system works. I've been experimenting with it but so far I'm no closer to an understanding. I’ve been able to mount and access some drives but I really don’t know how it’s done.

I have 2 HD’s: hda and hdb. Hdb is my old windows HD (120G) that I have as a slave. It's split into two partitions (as it was when I was running XP) hdb1 = 30G and hdb2 = 80G. I can access the NTFS partition (80G) no problem but I can't write to it. (I understand that this is typical and I'm not ready to undertake the gymnastics necessary to be able to.)

The second partition (hdb1) I have formatted as ext3.

What I want to do is copy the MP3's that are on the NTSF portion (hdb2) to the ext3 partition (hdb1) and then reformat the NTSF as ext3 to recapture the space. Then I want to use the 80G portion to host my files (pics, text, etc.) 

But I can't seem to figure out how to mount hdb1 so I can access it. I've tried going through Admin>Disks and I can set the path and make it accessible, but even if I put it on my desk top, when I try to copy a file to it, I'm told that I don't have permission to write to it...???? 

Do I have to set up the file structure first?

Is there another way to do this? 

Thanks for the help. I'm happy to be a Linux user even though it's been tough at times.

---

### Post by gargoyle on 2006-08-22
Hi yustr,
You are probably getting no responds because most people belive you should have searched for answer and read up on how to do it first then ask a spefic question instead of genenal howto do something.
I did a search under google linux here is just one of many pages on the subject
[Howto mount and unmount]("http://linux.about.com/od/linux101/l/blnewbie4_2_3.htm")
Like you I a new to this mount and unmount stuff. However there are a couple of way to mount a harddrive.
1) Is  you mount the drive when ever you need it, I believe this the common way of doing thing in Linux base system, unlike Windows where your drives are always mounted.
2) Is to have you hard drive mount on starup like in Windows. To do this you need to edit you fstab file.
This file is located in the folder named /etc
This is an Admenistror file so you would need to use the syper user to edit it also it would have to be done from a terminal window.
Example sudo gedit /etc/fstab
It will ask you for your password then start the editing program gedit.
But before you do this I would recommond learning how to mount and unmount the hard drives manually. The reason for this so that you can find the exact name of the drives.

Example I have two hard drives. One is for windows only (2 partitions C:drive and D:drive) the other is for Ubuntu.

So my fstab look like this for automounting
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy  auto    rw,user,noauto  0       0
/dev/hda1 /home/ed100/fat_c vfat iocharset=utf8,umask=000 0 0
/dev/hda5 /home/ed100/fat_d vfat iocharset=utf8,umask=000 0 0

The last 2 lines mount the windows hard drives when I start Ubuntu. They need to have folder to mount them so I create a folder for each one in my home directory.
Yes there is a lot of stuff that is not to easy to understand when you come from a window envoriment.

I would read up on the subject them come back if you can not totally figure it out. 
Good Luck

---

