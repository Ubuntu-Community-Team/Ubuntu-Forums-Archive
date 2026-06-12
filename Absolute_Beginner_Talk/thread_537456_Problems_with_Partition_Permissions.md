---
title: "Problems with Partition Permissions"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by J2A. on 2007-08-28
Ive got a 120GB HD & im using Ubuntu/XP Dual-Boot,

I made a 10GB Partition which I used to install Ubuntu, theres another partition which is around 40GB FAT32 on which XP is installed, and I have a 3rd partition of around 50GB which im trying to give full-access to for use with Ubuntu.

Both the 50GB & 10GB (ext3) partitions have only 'read' permissions, so I cant copy files onto them, ive tried formatting the 50GB to ext3 and thought this would give me full access automatically but i'm getting the same problem, 'no permission to write'.

Please help, 1. How do I setup the partition to have full access via Ubuntu to read & write files of all types, 2. How do I setup the 10GB ext3 partition so that I can write to it also.

Thanks !  *thumbs up*

PS. The partition @ the moment is formatted as ext3 not NTFS so the NTFS add-on thing isnt suitable/necessary

---

### Post by splintercellguy on 2007-08-28
Can you post the contents of /etc/fstab?

---

### Post by Hobo Joe on 2007-08-28
I'm not sure if this will work with partitions, but I know it works with folders.

Alt + F2 for a run prompt, and type 'gksudo nautilus'. Go to preferences, then the permissions tab, and change all the options to full read and write permissions from your username.

---

### Post by J2A. on 2007-08-28
> **splintercellguy said:**
> Can you post the contents of /etc/fstab?

How do I do that :confused: (im a complete newbie)

> **Hobo Joe said:**
> I'm not sure if this will work with partitions, but I know it works with folders.

Alt + F2 for a run prompt, and type 'gksudo nautilus'. Go to preferences, then the permissions tab, and change all the options to full read and write permissions from your username.

Dnt thnk thats workin for the whole drive, tried that before, thanks anyway

---

### Post by splintercellguy on 2007-08-28
Go to Terminal, then type "cat /etc/fstab" without quotes. Then copy the output to a new post. As for the other respondent's post, a better way might be to do this:

sudo chown -R <your user name>:<your user name> /path/to/partition

---

### Post by J2A. on 2007-08-29
> **splintercellguy said:**
> Go to Terminal, then type "cat /etc/fstab" without quotes. Then copy the output to a new post. As for the other respondent's post, a better way might be to do this:

sudo chown -R <your user name>:<your user name> /path/to/partition

Ok thanks, here's the output I got...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1b033d2c-cc86-4d42-ad41-999e2a0f410d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=6f46b98f-57d6-4b31-b5f4-55f7e30806e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda3 /storage ext3 defaults 0 0

---

### Post by J2A. on 2007-08-29
Any suggestions anyone?

This partition which i'm trying to give read/write permissions to is empty, so I dont mind re-formatting it to whatever file system is most appropriate , im assuming its ext3 so I formatted it as that at the moment...

...pleease post any solutions

---

