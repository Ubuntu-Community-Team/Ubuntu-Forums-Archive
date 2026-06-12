---
title: "Getting confused by the permissions"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by elpuerco on 2006-09-20
I think this might have something to do with the way I have my drive partioned?

sudo fdisk -l gives:

/dev/hda1 *   .......... NTFS
/dev/hda2     .......... W95 Ext'd (LBA) dunno what this is?
/dev/hda5     .......... Linux Swap
/dev/hda6 *   .......... Linux
/dev/hda7     .......... Linux (my data storage to be)
/dev/hda8     .......... NTFS (recovery XP partition)

cd /media and then ls -l gives:

root root cdrom -> cdrom0
root root cdrom0
root plugdev hda1
hda4 root root
hda7 root root

My problem is that I am unable to create any folders on hda7 obviously due to it being root.

But if I look at hda6 it too is root root and then looking at the permisions for my home folder no mention of write being there yet I can create folders 'O' plenty

Prior to my rebuild I had hda7 as hda8 number and was able to write to it right from intall.

The difference is that I had to partition magic the HDD and this resulted in Kubuntu erroring as it was trying to access a now NTFS drive as ext3.

I modified /etc/fstab as follows:

/dev/hda7   /media/hda7   ext3   defaults  0  2

and the errors stoped and I can mount and view the drive but cannot write.

Help please? :confused:

---

### Post by Jussi Kukkonen on 2006-09-20
mount point directories should generally be owned by root, that's not the problem. fstab looks fine also.

who owns the files in hda7? Do you have write access as that user (or root)? If you have reinstalled, the file ownerships could be screwed...

---

### Post by elpuerco on 2006-09-20
I get in /media

drwxr-xr-x 3 root root hda7

in hda7 there is one folder lost+found

drwxr-xr-x 2 root root lost+found

There are no other files.

When I right click in KDE to try to create anything I do not get the option CREATE

---

### Post by merlyn on 2006-09-20
I take it that /dev/hda6 is your /boot partition, that being the case /dev/hda7 will be mounted as / or the 'root' of the filesystem.

If you do a directory listing of your / partition you should see a /home directory. 

This /home directory is where individual users data, desktop settings etc are stored. For example user bloggs will have a directory 'bloggs' in the home directory, ie /home/bloggs

The users individual home directory is the only place where a user has the rights to store data.

I've provided a screenshot showing the / directory listing and /home directory listing below.

If I have confused you even more I'm sorry.

I'm just trying to provide some information on the Linux filing system in the hope that it will help you. You could also check out this [article]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") on Wikipaedia.

With regard to your drive partioning it seems fine to me given that you are dual booting on a single physical drive.

Cheers.

---

### Post by elpuerco on 2006-09-20
Hi, yes hda6 is my system partition, but hda7 is to be my data partition which I only have read access to.

I understand the HOME folder and the being allowed to right there, but as I say I want to store all my data on hda7 away from the system partition.

Also you will see from earlier that hda7 is mounted as

/media/hda7 off the / of had6

---

### Post by elpuerco on 2006-09-20
Aha....got it :D 

I did this...

cd /media/hda7

sudo mkdir data

sudo chown <myuserid> data

sudo chgrp <myuserid> data

budda bing...budda boom :D

---

