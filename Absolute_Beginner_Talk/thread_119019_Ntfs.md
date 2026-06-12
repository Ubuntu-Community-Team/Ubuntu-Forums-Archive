---
title: "Ntfs"
date: 2006-01-18
forum: Absolute Beginner Talk
---

### Post by shnoza on 2006-01-18
hi i used this site for trying to access my NTFS drive  [http://www.psychocats.net/linux/mountwindows.php](http://www.psychocats.net/linux/mountwindows.php)
but i still can manage to access it.

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2480    19920568+  83  Linux
/dev/hda2            4764        9728    39881362+   f  W95 Ext'd (LBA)
/dev/hda3   *        2481        4763    18338197+  83  Linux
/dev/hda5            4865        9728    39070048+   7  HPFS/NTFS
/dev/hda6            4764        4864      811219+  82  Linux swap / Solaris


when this comes up it says its NTFS but then when i go to change it ,it comes up with vfat.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /media/windows  vfat    nls=utf8,umask=0222   0       0



 can someone help me to access it please as all my music/photos are there and they are very important.
thank you.

---

### Post by mcduck on 2006-01-18
Here are the steps for automounting NTFS drive:

1. 'sudo mkdir /media/windows' - create a directory whre you'r drive will be monted. I suppose you have already done that.
2. 'sudo cp /etc/fstab /etc/fstab_backup' - backup your old fstab
3. 'sudo gedit /etc/fstab' - open fstab for editing
4. add line '/dev/hda5  /media/windows  ntfs  nls=utf8,umask=0222 0  0' and save & exit gedit.
5. 'sudo mount -a' - remount all drives. You could also reboot, but that wouldn't be as cool ;)

---

### Post by shnoza on 2006-01-18
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
is error comes up when i try to remount the drivers

---

### Post by mcduck on 2006-01-18
You should leave all the other lines as they are, and only change the one with /dev/hdc5, as that's the one with your NTFS partition..

You're not supposed to make your fstab _exactly_ like the one in that guide you linked in your first post.

---

### Post by shnoza on 2006-01-18
how do i redo everything back to normal then?

---

### Post by mcduck on 2006-01-18
if you followed the guide exactly, it told you to do a backup of fstab. (sudo cp /etc/fstab /etc/fstab_backup). If you did that, you can 'sudo cp /etc/fstab_backup /etc/fstab' to get your original fstab back.

After that, follow the steps I posted and this time only change (add) the line about your NTFS partition..

edit: based on your first post, correct fstab for you would be like this:```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hda5 /media/windows ntfs nls=utf8,umask=0222 0 0
```
(This assuming that you have Ubuntu installed in hda3, and you don't want hda1 and hda2 to be mounted)

---

### Post by Vlammetje on 2006-01-18
You Did Back It Up As He Said Right?

---

### Post by quonsar on 2006-01-18
*tumbleweed*

---

### Post by jonathanm on 2006-01-18
surely, even if you didnt back it up you can still edit the new fstab, (the one with vfat), if this is gone the just make a new fstab and paste the fstab thats on this forum into it.

---

### Post by Rasymas on 2006-01-18
[QUOTE=mcduck]add line '/dev/hda5  /media/windows  ntfs  nls=utf8,umask=0222 0  0'[/QUOTE]

I type /dev/hda1.... and when I mount a disk it says that this one doesn't exsist. anyway, how to know what really the number is the ntfs partition?

---

### Post by mcduck on 2006-01-19
you should do 'sudo fdisk -l' to get a list of all your partitions.

---

### Post by aysiu on 2006-01-19
[QUOTE=shnoza]mount: wrong fs type, bad option, bad superblock on /dev/hda1[/QUOTE] Notice how it says bad superblock on /dev/hd**a1**? It's not /dev/hda5 that has the problem. If you change it to ntfs instead of vfat, it should be fine.

Something's off with your Linux partition on /dev/hda1, though.
Odd that it's not even in your /etc/fstab file.

---

### Post by shnoza on 2006-01-19
ive got it to work but dont know how. how would i fix that linux partition on /dev/hda1?

---

### Post by Rasymas on 2006-01-19
[QUOTE=mcduck]Here are the steps for automounting NTFS drive:

1. 'sudo mkdir /media/windows' - create a directory whre you'r drive will be monted. I suppose you have already done that.
2. 'sudo cp /etc/fstab /etc/fstab_backup' - backup your old fstab
3. 'sudo gedit /etc/fstab' - open fstab for editing
4. add line '/dev/hda5  /media/windows  ntfs  nls=utf8,umask=0222 0  0' and save & exit gedit.
5. 'sudo mount -a' - remount all drives. You could also reboot, but that wouldn't be as cool ;)[/QUOTE]

Thanks buddy for simple howto, it worked for me. I mean I had to edit smth. Here's what I did:

[b]'sudo mkdir /media/windows'
'sudo cp /etc/fstab /etc/fstab_backup'
'sudo gedit /etc/fstab'
'sudo fdisk -l'[/b] I was unsure what's the number of my ntfs partition, so I've checked it out. saw smth like this hdb1
added this line ->
[b]'/dev/hdb1  /media/windows  ntfs  nls=utf8,umask=0222 0  0'
'sudo mount -a'[/b]

and it worked. THanks buddy, you saved my skin :P

---

### Post by Rasymas on 2006-01-21
I gotta problem, can anyone help me?

I have my Windows partition of 9.99 GB, and I was really short of space. I've copied my stuff to Linux partition. Now I want to go to my friend and transfer some stuff to his computer, the reason is that I can't copy the info back to my windows partition. It says that I don't have owner rights or permision. So is it possible to copy stuff back to windows partition? 

Thanks in advance :)

ps. this is pretty urgent, so help me if you can :roll:

---

### Post by ysse on 2006-01-21
Hi, as I understand it, the state of affairs right now is that you can read an NTFS partition from inside Linux, but writing is still very experimental.

One common way is to set up a FAT32-partition that's writable for both Linux and Windows, but it seems that your disk space is a little too limited for that.

I did find a few pointers to another solution: making your Linux file systems readable from Windows.

[http://linux-ntfs.sourceforge.net/info/ntfs.html#3.2workaround](http://linux-ntfs.sourceforge.net/info/ntfs.html#3.2workaround)

Give it a go!

---

### Post by Rasymas on 2006-01-21
Thanks mate for the useful link. I appreaciate it :WT

*reading in progress* lol

---

### Post by cosine7 on 2006-06-27
[QUOTE=mcduck]You could also reboot, but that wouldn't be as cool ;)[/QUOTE]
Thanks heaps worked first go! I am soooo cool now... none of this windows goes up, windows goes down, windows goes up window..... u get the point thanks heaps!!!

---

### Post by Apple 101 on 2006-06-27
[QUOTE="mcduck"]you should do 'sudo fdisk -l' to get a list of all your partitions.[/QUOTE]
The *df* command does the same thing.

---

