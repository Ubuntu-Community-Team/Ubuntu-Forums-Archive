---
title: "Help i ruined my fstab and i can't get it back to work"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by D_frag on 2006-09-16
I obviously made somthing so bad there that the X server is not opening so i login into command line mode always
i i tried copying a backup file /etc/fstab~ to the fstab but it says error fstab is read only i thought maybe it's a permissions thingy so i logged in as root and tried even editing using the vi editor it wont save i insert and then when i try :wq! i get error can't open file fstab .. what should i do ???

---

### Post by bulldog on 2006-09-16
Just let fstab be and be concerned about xorg.conf.

When X doesn't start it's usely an error in your xorg.conf.

Try in your console 

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by D_frag on 2006-09-16
i got creating symbolic link /etc/x11/x.dpkg-new to /usr/bin/xorg
still no use .. i know the problem is the fstab if i can only revert it to what it was before .. because the moment i changed it and then restarted i got this error and the x server wouldnt load the problem is 
@ the first line is the fstab proc i deleted defaults and put umask=000 didnt take care !!

---

### Post by bulldog on 2006-09-16
You have just learned how important it is to make a copy of any file you gonna alter.:) 

But i can only give you a copy of my fstab if that's usefull to you.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by D_frag on 2006-09-16
> **bulldog said:**
> You have just learned how important it is to make a copy of any file you gonna alter.:) 

But i can only give you a copy of my fstab if that's usefull to you.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


Actually i did make a copy which is /etc/fstab~ but i can't load it to /etc/fstab .. meaning the copy i made was useless am sure there must a way out of this someone should know how i can revert back to my copy ?! 
p.s I changed 'roc            /proc           proc    defaults        0       0' to 'roc            /proc           proc    umask=000      0       0' which i think is the reason for the problem

---

### Post by RoyArne on 2006-09-16
If you want to copy /etc/fstab~ to /etc/fstab you would use the command

```
sudo cp /etc/fstab~ /etc/fstab
```

---

### Post by bulldog on 2006-09-16
To put the copy back do this

sudo cp /etc/fstab-backup?? /etc/fstab

you have put the right name of your copy instead of fstab-backup??

Then is your fstab replaced with your copy.

---

### Post by RoyArne on 2006-09-16
> **D_frag said:**
> 
p.s I changed 'roc            /proc           proc    defaults        0       0' to 'roc            /proc           proc    umask=000      0       0' which i think is the reason for the problem

Can you do 

```
cat /etc/fstab~
```

and post the output? This is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,user_xattr,errors=remount-ro 0       1
/dev/mapper/sil_agaccfcdchfb1   /usr/local/share/raid   ext3    defaults,user_xattr     0       0
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by D_frag on 2006-09-16
when i try cp /etc/fstab~ /etc/fstab
i get 
cannot create regular file '/etc/fstab' read only file system 
 and actually the fstab is quite big because i have many partiotion but it's fine and i can't copy it cuz i have to login everytime ti windows inorder to post here and then restart and try on the ubuntu

---

### Post by bulldog on 2006-09-16
you must do 

sudo cp /etc/fstab~ /etc/fstab

You need root permission to write to the system.

---

### Post by D_frag on 2006-09-16
i looged in as root actually and i tried the sudo

---

### Post by bulldog on 2006-09-16
By default you can't login as a root.

But if you're root then you can't get the message you give me.

Root has all permissions even to ruine his install.
So you can copy with no problem.

---

### Post by D_frag on 2006-09-16
in the recovery mode i logged in as root and as well currently i dont even get the ubuntu welcome screen the failure takes place when loading the ubuntu and so it opens a command line interface and i type root and loggin 
p.s am sure i was logged in as root (i tried it again case my eyes fooled my for way too much ) and i made sure the cli was root@desktop#

---

### Post by RoyArne on 2006-09-16
> **bulldog said:**
> But if you're root then you can't get the messages you give me.

He can if the file system is mounted as **read only**

> cannot create regular file '/etc/fstab' *read only file system*

---

### Post by bulldog on 2006-09-16
Little explaination.

Ubuntu uses only a user account even in console.
You can be root however by logging in with your user name and password and do sudo.
Ubuntu asks again for your password and you become root for a limited time period.

You can be root for unlimited time by using the command  sudo -s and give your password again.

Before the '@' you can read root like root@user-desktop.

---

### Post by bulldog on 2006-09-16
Are you using the live cd??

If not you better try it and mount your install and try to copy your fstab.

---

### Post by D_frag on 2006-09-16
> **RoyArne said:**
> He can if the file system is mounted as **read only**
so this means this is a dead end ??

---

### Post by D_frag on 2006-09-16
> **bulldog said:**
> Are you using the live cd??
no i installed ubuntu on my harddisk

---

### Post by bulldog on 2006-09-16
Boot from the live cd and mount your ubuntu and copy the fstab.

sudo mkdir /mnt/ubuntu
sudo mount /dev/?? /mnt/ubuntu

---

### Post by RoyArne on 2006-09-16
> **D_frag said:**
> so this means this is a dead end ??

No, it means that I don't know how to fix your problem. But I'm sure there is a way. Do you have the livecd?

Perhaps you can boot the livecd and then mount the partition containing fstab? If you can get write access from there, you could restore your /etc/fstab (?)

---

### Post by D_frag on 2006-09-16
> **bulldog said:**
> Boot from the live cd and mount your ubuntu and copy the fstab.

sudo mkdir /mnt/ubuntu
sudo mount /dev/?? /mnt/ubuntu

can you explain more please sorry but i just started usin linux 1 month ago .. i would insert the cd and load it and then make the directory /mnt/ubuntu  then sudo mount /dev/? <<-- whats that?
 and where am i atually in these lines am i fixing the problem /mnt/ubuntu is an empty directory ??

---

### Post by bulldog on 2006-09-16
It means that you have to fill in the partition where your Ubunu install is.

I don't know the config of your computer and you should.

If you can copy your fstab and put it on the forum I can tell you what to fill in.

Just boot your live cd then and come back to the forum and I tell you what to do.

---

### Post by D_frag on 2006-09-16
Sorry for bieng soo noobish but would doin that set me back where i started installing ubuntu 1 month ago ??

---

### Post by bulldog on 2006-09-16
Nope it gives you the opportunity to copy back your fstab~.

And if that's the reason Ubuntu won't start then is all saved.

Just put here a copy of your fstab~ and boot from the live cd and come back here.

---

### Post by D_frag on 2006-09-16
ok now am on the live cd how can i find my fstab~ 
it's not there @ /etc i think i have to go to a certain hard disk ?

---

### Post by bulldog on 2006-09-16
Yep you must mount your existing install on your hdd.
But you didn't give me your fstab~ so I can't decide wich partition you need to mount.

you can make a dir with

sudo mkdir /mnt/ubuntu

then you have to mount your install by

sudo mount /dev/?? /mnt/ubuntu

Where ?? stands for the partition where your install is.

Do you have one hdd?
How many partitions?
Is there another OS?

Try this instead:

code:


sudo grub


This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

---

### Post by RoyArne on 2006-09-16
> **D_frag said:**
> ok now am on the live cd how can i find my fstab~ 
it's not there @ /etc i think i have to go to a certain hard disk ?

There is a graphical tool, **System->Administration->Disks**. Try to see if you can find the correct harddisk/partition there. Hard disks have names line /dev/hda and /dev/sda. Partitions are named /dev/hda1 for the first partition on the /dev/hda harddisk. You need to find the one that your fstab is on.

---

### Post by bodhi.zazen on 2006-09-16
D_frag:

Open a terminal

Type```
fdisk -l
```

That is a small "L" not the number 1.

Post the output (this will list your partitions).

---

### Post by bulldog on 2006-09-16
> **bodhi.zazen said:**
> D_frag:

Open a terminal

Type```
fdisk -l
```

That is a small "L" not the number 1.

Post the output (this will list your partitions).

Must be sudo fdisk -l

But you are right it's quicker.
Too much time on the forum,I seem to forgot the simple things.:roll:

[offtopic How do you the codebox?]

---

### Post by D_frag on 2006-09-16
ok i know now  the root directory is on /hdb9

how can i view a copy of my fstab backup on the live cd ?

---

### Post by bodhi.zazen on 2006-09-16
sudo to fdisk /dev/xy,

but do not need to sudo to "fdisk -l"

---

### Post by bulldog on 2006-09-16
Let's try:p 

mount /dev/hdb9 /mnt/ubuntu

---

### Post by bulldog on 2006-09-16
> **bodhi.zazen said:**
> sudo to fdisk /dev/xy,

but do not need to sudo to "fdisk -l"
 
When I do fdisk -l I get nothing in return.


@TS

When you did the mounting you can do

sudo cp /mnt/ubuntu/etc/fstab~ /mnt/ubuntu/etc/fstab

That should put it back.

---

### Post by RoyArne on 2006-09-16
> **bodhi.zazen said:**
> sudo to fdisk /dev/xy,

but do not need to sudo to "fdisk -l"

Plain "fdisk -l" does not work on my computer, must use sudo. But thanks for pointing out the fdisk command! very useful.

---

### Post by D_frag on 2006-09-16
> **bulldog said:**
> Let's try:p 

mount /dev/hdb9 /mnt/ubuntu
]
i did that

---

### Post by bodhi.zazen on 2006-09-16
> bodhi@Arch:~$ fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+  83  Linux
/dev/sda2            1825        3648    14651280   83  Linux
/dev/sda3            3649        5472    14651280   83  Linux
/dev/sda4            5473       30401   200242192+   5  Extended
/dev/sda5            5473        7296    14651248+  83  Linux
/dev/sda6            7297        9120    14651248+  83  Linux
/dev/sda7            9121       10944    14651248+  83  Linux
/dev/sda8           10945       12768    14651248+  83  Linux
/dev/sda9           12769       14592    14651248+  83  Linux
/dev/sda10          14593       16416    14651248+  83  Linux
/dev/sda11          16417       18240    14651248+  83  Linux
/dev/sda12          18241       20064    14651248+  83  Linux
/dev/sda13          20065       20307     1951866   82  Linux swap / Solaris
/dev/sda14          20308       30401    81080023+  83  Linux

Disk /dev/sdc: 32 MB, 32768000 bytes
3 heads, 32 sectors/track, 666 cylinders
Units = cylinders of 96 * 512 = 49152 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         667       31983+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1000, 2, 32) logical=(666, 1, 31)
bodhi@Arch:~$

Must be an Arch thing....

---

### Post by bulldog on 2006-09-16
@TS

When you did the mounting you can do

sudo cp /mnt/ubuntu/etc/fstab~ /mnt/ubuntu/etc/fstab

That should put it back.

---

### Post by bodhi.zazen on 2006-09-16
If that does not work please post fstab.

---

### Post by D_frag on 2006-09-16
thank you guys very  very very much .. i am currently on my system replying ..can't thank you enuff .. really without this forum i couldnt have stayed so far using ubuntu 
and here is my fstab 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb9       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb10      none            swap    sw              0       0
/dev/hdc        /mnt/cdrom   udf,iso9660 user,noauto     0       0
/dev/hda1       /mnt/windows  vfat    defaults           0      0 
/dev/hda8       /mnt/windows1  vfat    defaults           0      0
/dev/hda9       /mnt/windows2  vfat    defaults           0      0
/dev/hda10      /mnt/windows3  vfat    defaults           0      0
/dev/hdb5       /mnt/windows4  vfat    defaults           0      0
/dev/hdb6       /mnt/windows5  vfat    defaults           0      0
/dev/hdb7       /mnt/windows6  vfat    defaults           0      0
/dev/hdb8       /mnt/windows7  vfat    defaults           0      0

To make this right now i want to enable writing on my windows volumes .. for a special user is that possible if not , then i will make it for all users using umask=000 instead of defaults , i should do so as well for db9 right ??

---

### Post by bulldog on 2006-09-16
Glad to be of some help.

I'm off for now.

---

### Post by D_frag on 2006-09-16
Thank you bulldog 
Can someone explain to me what happened here what did mount /dev/hdb9 /mnt/ubuntu do ? and how was there /etc/fstab~ inside /mnt/ubuntu which was made

---

### Post by bodhi.zazen on 2006-09-16
> **D_frag said:**
> To make this right now i want to enable writing on my windows volumes .. for a special user is that possible if not , then i will make it for all users using umask=000 instead of defaults , i should do so as well for db9 right ??
Example of such a fstab entry:
```
/dev/hda1 /mnt/windows vfat noauto,user,gid=0,uid=<user ID #>,umask=0077 0 0
```

Replace <user ID #>  with the ID number of your "special user".

Your "special user" will be able to mount and unmount without root/sudo access. When mounted, listing (ls -l) of the mount point will look like this:

> drwx------  4 <user_name> root  16384 1969-12-31 17:00 <mount_point>

---

### Post by bodhi.zazen on 2006-09-16
> **D_frag said:**
> Thank you bulldog 
Can someone explain to me what happened here what did mount /dev/hdb9 /mnt/ubuntu do ? and how was there /etc/fstab~ inside /mnt/ubuntu which was made

See here [mount](http://wiki.linuxquestions.org/wiki/Mount)

or just [color=brown]man mount[/color] in a terminal.

---

