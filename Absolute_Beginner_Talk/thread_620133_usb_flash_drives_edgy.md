---
title: "usb flash drives edgy"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-11-22
Hi all. 

I've read every thread I can find on this matter.

The ones that have interested me the most relate to lost USB automount scenarios updating from Edgy to Feisty. 

Well, I don't know much, but accolades to everyone who got USB sticks automounted in Edgy, because I can't. But, my Feisty box accepts the USB stick like a seal hitting the water.

The closest I've got to a 'solution' is the rigmarole of gparted etc. which at least let me view the contents of the USB stick, but I can't do much else. I can read it, but i can't alter anything. I was at one stage able to ADD a file to the flash drive, using a series of copy/paste commands in terminal, but that's about it.

This problem re-iterates itself ad infinitum.

Surely there must be a terminal input as sudo which automounts any flash drive (all of mine are fat32/16) to enable user instead of root to access the silly little thing and use it for what it was meant for. as in collecting files and swapping them from one PC to another.

Why should this be complicated?

Maybe I've missed something, but I have spent many hours on this issue.

Cheers,
Mike.

---

### Post by overdrank on 2007-11-22
> **MichaelSM said:**
> Hi all. 

I've read every thread I can find on this matter.

The ones that have interested me the most relate to lost USB automount scenarios updating from Edgy to Feisty. 

Well, I don't know much, but accolades to everyone who got USB sticks automounted in Edgy, because I can't. But, my Feisty box accepts the USB stick like a seal hitting the water.

The closest I've got to a 'solution' is the rigmarole of gparted etc. which at least let me view the contents of the USB stick, but I can't do much else. I can read it, but i can't alter anything. I was at one stage able to ADD a file to the flash drive, using a series of copy/paste commands in terminal, but that's about it.

This problem re-iterates itself ad infinitum.

Surely there must be a terminal input as sudo which automounts any flash drive (all of mine are fat32/16) to enable user instead of root to access the silly little thing and use it for what it was meant for. as in collecting files and swapping them from one PC to another.

Why should this be complicated?

Maybe I've missed something, but I have spent many hours on this issue.

Cheers,
Mike.

HI maybe this link will help with Edgy
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by MichaelSM on 2007-11-22
Hello again, overdrank.

I had a go at what you suggested,.

michael@michael-desktop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
michael@michael-desktop:~$ sudo cp -a /etc/fstab /etc/fstab_backup
michael@michael-desktop:~$ sudo echo -e "/dev/sda\t/media/sda1 vfat\tiocharset=utf8,umask=000\t0 0" >>/etc/fstab
bash: /etc/fstab: Permission denied
michael@michael-desktop:~$ 

/dev/sda is I guess where the stick is before its mounted, according to gparted.
/media/sda1 is IT when mounted.

Why don't I have permission to execute the last command?

There ain't no other sudo on my computer.!!

Cheers,

Mike.

---

