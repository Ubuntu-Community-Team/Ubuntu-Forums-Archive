---
title: "installing parallels tools for linux"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by DrFarnsworth on 2007-12-11
well i finally got ubuntu installed on parallels i ended up uses 6.x because no mater what i tried 7 would just not install correctly for me. I think have found and looked over every tutorial for installing ubuntu 6 and 7. 

I am trying to install parallels tools for linux but i can not mount the disc in the terminal 

i found this 

11. At the root shell prompt, type the commands that you were shown to install the tools
mount /media/cdrom
cd /media/cdrom
sh parallels-tools.run
shutdown -r now

but all that does is tell me directory not found

i have also found this 

To install parallels tools you have to click "Install Parallels Tools" under "Actions" then
sudo mount /dev/cdrom /media/cdrom0
and
sudo sh /media/cdrom/parallels-tools.run

which just tells me it can not find the cd. 

the disk is mounted and i am sure i am missing something simple. I am completely new to linux so any help would be great.

---

### Post by irwa82 on 2007-12-22
Hi,

Bring a a terminal and execute the following command and it should tell you what device if any is listed in the fstab.

cat /etc/fstab|grep media

You will probably find you need to do the following:

mount /media/cdrom0
cd /media/cdrom0
sh parallels-tools.run
shutdown -r now


hope this helps you out.

[http://www.irwinresources.com](http://www.irwinresources.com)

---

