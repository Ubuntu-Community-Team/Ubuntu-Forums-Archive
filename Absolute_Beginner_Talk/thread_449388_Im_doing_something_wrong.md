---
title: "Im doing something wrong"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by namrocks on 2007-05-20
I'm trying to place my home directory in a separate partition. First I boot into qparted , create an extended partition and create 3 logical ext 3 partitions (/, swap/ home). When I get to the partitioner I select the partition for the home directory. I Click "Edit Partition". I type the size in the "New Partition Size" box. I select ext 3 in the "Use As" box. I select /home in the "Mount Point" box. When I boot into Ubuntu after the installation, the home directory partition is nowhere to be found. I even tried a clean install without formatting the home partition and my personal files were wiped out. I'm hoping someone can see what I am doing wrong. Thanks

---

### Post by Kobalt on 2007-05-20
If you created the partition and gave them the size you wanted, before clicking on 'Edit partition', you don't need to specify their size once again in that menu. Once you select a partion, let's say the one for your /home, you click on 'Edit partition'. From there, you only need to select the mount point and the partition type (ext3, ext2, etc.).

---

### Post by namrocks on 2007-05-20
Thank you. What would be the correct "Use As" selection. I chose the default ext 3 but have no idea of that is right.

---

### Post by Borzo on 2007-05-20
you need to edit /etc/fstab.conf and add a mountpoint for /home
plus, if you have not done that already you also need to create a filesystem for your new home partition with mkfs.ext3 /dev/hdxx ( hdxx=your drive and partition )

p.s. why are you creating a swap partition? you should already have one?

---

### Post by Kobalt on 2007-05-20
It's the default partition format for / and /home in Ubuntu, you can leave it this way... 

PS: if you want to learn more about [ext3]("http://en.wikipedia.org/wiki/Ext3").

---

### Post by namrocks on 2007-05-20
Thank you. I'll get busy with these suggestions.

---

### Post by namrocks on 2007-05-20
> **Borzo said:**
> you need to edit /etc/fstab.conf and add a mountpoint for /home
plus, if you have not done that already you also need to create a filesystem for your new home partition with mkfs.ext3 /dev/hdxx ( hdxx=your drive and partition )

p.s. why are you creating a swap partition? you should already have one? 

I don't know how to edit etc/fstab and add a mount point nor how to create a file system for my new home partition. I would like to try if anyone is willing to be more specific. If not I understand. I am pretty green and can survive without a home partition.

---

### Post by seshomaru samma on 2007-05-20
[**_this_**]("http://www.psychocats.net/ubuntu/separatehome") guide is what you need

---

### Post by Borzo on 2007-05-20
1 create your partition, using cfdisk gparted or other tools

2 boot into you ubuntu

3 in console "sudo fdisk -l" to have a list of your drives and partitions, find your newly created one for /home ( let's say it's  hda3 )

4 in console "sudo mkfs.ext3 /dev/hda3" to create a filesystem on your new partition

5 in console sudo "vol_id /dev/hda3" will give you a UUID number for your new partition

6  edit fstab for example "sudo nano /etc/fstab" and add:
UUID=the_number_given_by_vol_id          /home       ext3        defaults,errors=remount-ro 0     1
save

6 edit mtab for example "sudo nano /etc/mtab" and add ( where /dev/hda3 is the example partition, enter yours here )
/dev/hda3 /home ext3 rw,errors=remount-ro 0 0
save

7 reboot

---

### Post by namrocks on 2007-05-20
Thanksso much, Borzo. I made it through the first 3 steps. When I did number 4 I got:

mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda5 is mounted; will not make a filesystem here!

Before attempting this I did a clean install without formatting the home partition.

---

### Post by Borzo on 2007-05-21
Hmmm, that's strange, are you sure that /dev/sda5 is your *newly* created partition for the /home directory?
Your error message comes from the fact that you cannot create a filesystem ona mounted partition, since /dev/sda5 is mounted it means it is already used by the system... your newly made partition shouldn't be monted since the system knows nothing about it and it has no filesystem.

It would help if you could post your fstab here, then i'll tell you what partitions are currently in use by your system ( you do not want to touch those )

and maybe the result of sudo fdisk -l

---

### Post by namrocks on 2007-05-21
Thank you. Here is what happened.

 If I do a clean install, formatting the root and home partitions, the home partition does not show on the desktop as mounted. If I then do another clean reinstall, deleting and editing only the root partition but leaving the home partition alone, the home partition then shows on the desktop as mounted.

 I tried this procedure again, since my last post - installed by deleting and editing both the root and home partitions, then reinstalled deleting and editing just the root partition. And just like before, the home partition showed as mounted, though now it is called sda7. Further, when I clicked on the sda7 drive icon on my desktop, it contained my home directory with the same folders and files as my root partition home directory. Plus, when, I launched Firefox for the first time, establishing a .mozilla folder in my root partition home directory, a .mozilla folder was also established in the home directory on my sda7 partition.

At any rate, here is the info you requested from the fstab file. Thank you again.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=01e5a2c9-05bb-42c5-bb87-c4d1990c3bfa /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D7-010B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=B204F3D304F39895 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=67bc8b86-9b46-4999-b5f3-c504e7a0f8e0 /media/sda7     ext3    defaults        0       2
# /dev/sda5
UUID=e2643cc7-c667-45c6-b94f-9f815cd75148 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Borzo on 2007-05-21
according to your fstab, /dev/sda5 which you tried to create a filesystem on, is your swap partition... so that can't be your newly created home partition. When you create your new partition, you need to remeber what it is (/dev/sdxx ) or check fdisk -l ... then we will know where to create a filesystem, and what to insert into your fstab. This can't be done in any different way.

---

### Post by namrocks on 2007-05-22
I am sorry to be so new and uneducated but I am determined to learn this and if you are still willing to hang in with me I would be most appreciative. If it is too frustrating I totally understand. 

I went back to your step one - used gparted to delete and recreate 3 new partitions - installed Ubuntu designating sda5 as the new home partition, sda6 as the root, and sda7 as the swap. I then booted into Ubuntu and immediately, without doing anything else other than installing the Ubuntu updates, did your step 3 and then got this message at step 4:

mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda5 is mounted; will not make a filesystem here!

Here is the new fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=ecb1dffb-10d5-44c1-96fa-9464a3c60bd8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=44b992e3-7bde-4ab4-bdc5-c79948990816 /home           ext3    defaults        0       2
# /dev/sda1
UUID=07D7-010B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=B204F3D304F39895 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=1b916f11-4cee-4be9-be5c-3101c164b7a5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

I will now reboot into Windows and do nothing more with Ubuntu until I hear from you or determine that you have moved on to help someone who is not so uninformed and difficult. Thank you.

---

### Post by Borzo on 2007-05-22
Don't worry about being "uneducated" everyone learns at some point, to me, it is not important that you "do not know" but that you want to learn. I'm not frustrated, it's just hard sometimes to understand what is happening remotely, especially if someone on the other side is not experienced.

According to the fstab you posted now, your /home is on /dev/sda5, if it's not visible it could mean it has no filesystem.

you can create a filesystem by typing at console/terminal 
sudo umount /dev/sda5
sudo mkfs.ext3 /dev/sda5

reboot by typing: sudo reboot

see if it works

---

### Post by namrocks on 2007-05-22
Thank you. 

When I typed the first command I got  "" I got:

umount: /home: device is busy
umount: /home: device is busy

When I typed the second command  got:

mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda5 is mounted; will not make a filesystem here!

---

### Post by Borzo on 2007-05-22
well, it looks to me that your /home is already mounted on /dev/sda5 and fully functional. 
( the first linee indicates that it's in use )...so everything is Ok, you have /home on a seperate partition.

you can access it in console by typing 
cd /home

---

### Post by namrocks on 2007-05-22
Cool! When I type cd /home I get the home directory that is located on my root partition. Is it now possible to have Ubuntu use the home directory on my home partition and then delete the one on the root partition?

---

### Post by Borzo on 2007-05-22
> **namrocks said:**
> Cool! When I type cd /home I get the home directory that is located on my root partition. Is it now possible to have Ubuntu use the home directory on my home partition and then delete the one on the root partition?

your /home partition is mounted in on the root filesystem... it is **physically **at /dev/sda5 ,but it is a part of / , so is any windows partition,cd-rom etc.

In windows terms( this is simplified ofcourse ), it would be like having Program Files directory being a link to some hard drive or partition, so, you see it in C:\ but it is linked to somewhere else.

---

### Post by namrocks on 2007-05-22
Thank you for the Windows analogy. That actually helped. 

I've been learning Ubuntu by breaking it and then reinstalling which for me is the best way. I still can't quite believe an operating system plus drivers can install in 20 minutes, even though I've seen it many times with my own eyes. Having my data and settings intact after reinstalling is going to massively accelerate my learning curve, hence my motivation to get this particular piece before I really knew enough to get it on my own. 

I am assuming that the next time I reinstall all I have to do is boot from the live disk, choose the manual partition option, highlight the current root partition, select edit, select "/" , check the format box for that partition, leave the home and swap partitions alone click forward, then install and I'm all set.

I cannot thank you enough for your kindness and patience. You have been an excellent mentor.

---

### Post by Borzo on 2007-05-22
I suggest you read some documentation, the filesystem in linux is somewhat different in concept than what you know from windows. Also keep in mind that every command ( and some config files ) has it's man page ( a documentation ) available at console, you just need to type "man desired_command_here" for example "man mount" or "man fstab"

good luck! :)

---

