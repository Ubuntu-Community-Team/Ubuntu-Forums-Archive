---
title: "Is D Drive Accessable?"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by lylesiemens on 2006-11-12
Can I access my second internal drive or not? My external usb drive works fine but my D drive has a stop thing above it and won't open. I have a movie on it that I want to show the kids. Also is there any way to configure my ATI Radion 9250 pro? It seems to have installed.

---

### Post by bodhi.zazen on 2006-11-12
> **lylesiemens said:**
> Can I access my second internal drive or not? My external usb drive works fine but my D drive has a stop thing above it and won't open. I have a movie on it that I want to show the kids. Also is there any way to configure my ATI Radion 9250 pro? It seems to have installed.

You need to have the proper entry in [fstab](http://ubuntuforums.org/showthread.php?t=283131).

Setting permissions depends on what type of FS is on the partitions (ntfs, fat, ext3, etc...).

If you are having troubble please post more information (partition and FS type).

---

### Post by dannyboy79 on 2006-11-12
post results of sudo fdisk -l and we can help ya.

---

### Post by lylesiemens on 2006-11-12
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9447    75882996   83  Linux
/dev/hda2            9448        9729     2265165    5  Extended
/dev/hda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4998    40146403+   7  HPFS/NTFS

---

### Post by bodhi.zazen on 2006-11-12
> **lylesiemens said:**
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9447    75882996   83  Linux
/dev/hda2            9448        9729     2265165    5  Extended
/dev/hda5            9448        9729     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4998    40146403+   7  HPFS/NTFS


to mount:```
sudo mkdir /mnt/data
mount /dev/hdb1 /mnt/data -t ntfs
```

To mount at boot,```
sudo gedit /etc/fstab
```Add this line:> /dev/hdb1 /mnt/data ntfs auto,users 0 0

To have read-write access: [ntfs-3g](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)

---

### Post by lylesiemens on 2006-11-12
Thankyou for the code but where can I access my D drive now? Is there a particular directory?

---

### Post by bulldog on 2006-11-12
> **lylesiemens said:**
> Thankyou for the code but where can I access my D drive now? Is there a particular directory?

Have you any idea where you mounted your disk?

It's a good thing to watch carefully when you put in commands and try to understand what they mean.

That said,look in the folder mnt/data I think you find there what you're looking for.

And now when read back it won't be there,our dear friend bodhi made a typo in the line you have put in your fstab.```
/dev/hsb1 /mnt/data ntfs auto,users 0 0 
```
Open your fstab```
gksudo gedit /etc/fstab
```
Then alter the line you've added in```
/dev/hdb1 /mnt/data ntfs auto,users 0 0
```
The hsb1 should be changed in hdb1.

---

### Post by lylesiemens on 2006-11-12
I am soo very sorry for my ignorance but where is mnt/? I am not trying to be stupid but I followed the directions above. Please point me on where to click. The main reason why I installed Umbuntu was to learn this very different OS. Maybe it's easier than I think.

---

### Post by bulldog on 2006-11-12
Did you read my above posting and altered your fstab??

There is a little typo in it which should be corrected.

To find /mnt go in your menu to Places-->Computer and click it.
Then click on filesystem and select the folder named mnt.
In this folder should be a folder named data and that is the disk your looking for.

But first edit your fstab as discribed!! and reboot to make it effective.

---

### Post by lylesiemens on 2006-11-12
This is what happened[ATTACH]19255[/ATTACH]

[ATTACH]19256[/ATTACH]

[ATTACH]19257[/ATTACH]

---

### Post by lylesiemens on 2006-11-12
It would seem that since I installed Ubuntu that I would have full permission to do everything??

---

### Post by lylesiemens on 2006-11-12
lyle@lyle-desktop:~$ /dev/hdb1 /mnt/data ntfs auto,users 0 0
bash: /dev/hdb1: Permission denied
lyle@lyle-desktop:~$  ???????????](*,) ](*,) ](*,) ](*,)

---

### Post by bodhi.zazen on 2006-11-12
> **bulldog said:**
> There is a little typo in it which should be corrected.

Ooops :redface:

Thanks bulldog. That (fstab entry) shoud be:> /dev/hdb1 /mnt/data ntfs auto,users 0 0 

PS: I corrected my earlier type too !

---

### Post by bodhi.zazen on 2006-11-12
> **lylesiemens said:**
> lyle@lyle-desktop:~$ /dev/hdb1 /mnt/data ntfs auto,users 0 0
bash: /dev/hdb1: Permission denied
lyle@lyle-desktop:~$  ???????????](*,) ](*,) ](*,) ](*,)

That should be:```
**sudo** mount /dev/hdb1 /mnt/data -t ntfs
``` if you have not updated fstab.

If you have updated fstab it is eaven easier:```
mount /mnt/data
```

---

### Post by lylesiemens on 2006-11-12
lyle@lyle-desktop:~$ sudo mount /dev/hdb1 /mnt/data -t ntfs
mount: /dev/hdb1 already mounted or /mnt/data busy
mount: according to mtab, /dev/hdb1 is already mounted on /mnt/data
lyle@lyle-desktop:~$ mount /mnt/data
mount: /dev/hdb1 already mounted or /mnt/data busy
mount: according to mtab, /dev/hdb1 is already mounted on /mnt/data
lyle@lyle-desktop:~$ 

WTF?? the data folder has a red X on it and won't open, because I am aparently not the grand owner of something](*,) :evil: I just installed it under my name thats all, no one else installed it!

---

### Post by bodhi.zazen on 2006-11-12
OK 
[list=number][*]Can you post /etc/fstab
[*]Let's unmount & re-mount:```
sudo umount /dev/hdb1
sudo umount /mnt/data

# Now re-mount

mount /mnt/data

# Now check permissions

ls -l /mnt | grep data
```[/list]

---

### Post by lylesiemens on 2006-11-13
lyle@lyle-desktop:~$ sudo umount /dev/hdb1
Password:
lyle@lyle-desktop:~$ sudo umount /mnt/data
umount: /mnt/data: not mounted
lyle@lyle-desktop:~$ mount /mnt/data
lyle@lyle-desktop:~$ ls -l /mnt | grep data
dr-x------ 1 root root 4096 2006-11-07 21:00 data
lyle@lyle-desktop:~$

---

### Post by lylesiemens on 2006-11-13
Still doesn't let me in. Did I do something wrong?

---

### Post by lylesiemens on 2006-11-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=5f53e2c5-3eca-4507-af4a-f2f061b0e21d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6254cd56-8c4b-449c-ab7b-e6b03aea83e2 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1 /media/windows ntfs umask=0222 0 0
/dev/hdb1 /mnt/data ntfs auto,users 0 0
/dev/hda1 /media/hda1 ntfs-fuse auto,gid=1002,umask=0002 0 0

---

### Post by bodhi.zazen on 2006-11-13
> **lylesiemens said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/hda1 /media/windows ntfs umask=0222 0 0
/dev/hdb1 /mnt/data ntfs auto,users 0 0
/dev/hda1 /media/hda1 ntfs-fuse auto,gid=1002,umask=0002 0 0

Your fstab entry looks a little off. Are you trying to mount rw or ro?

to mount ro ```
/dev/hdb1 /mnt/data ntfs auto,users,umask=0222  0 0
```

to mount rw, if fuse is working for you:```
/dev/hdb1 /mnt/data ntfs-fuse auto,gid=1002,umask=0002 0 0
```

Or use [ntfs-g3](http://doc.gwos.org/index.php/Mount_NTFS_volumes_with_write_support)```
/dev/hdb1 /mnt/data ntfs-g3 auto,gid=1002,umask=0002 0 0
```

Again, after updating fstab umount and then re-mount /mnt/data

---

### Post by lylesiemens on 2006-11-13
I don't care really as long as I can access my D drive, heres what I get.

lyle@lyle-desktop:~$ /dev/hdb1 /mnt/data ntfs-g3 auto,gid=1002,umask=0002 0 0
bash: /dev/hdb1: Permission denied
lyle@lyle-desktop:~$ /dev/hdb1 /mnt/data ntfs auto,users,umask=0222  0 0
bash: /dev/hdb1: Permission denied
lyle@lyle-desktop:~$ /dev/hdb1 /mnt/data ntfs-g3 auto,gid=1002,umask=0002 0 0
bash: /dev/hdb1: Permission denied
lyle@lyle-desktop:~$

---

### Post by lylesiemens on 2006-11-13
I've done this so many times......is there any way?????Please

---

### Post by bulldog on 2006-11-13
Well I can give you a manner which will work,**but you will be root,and if you make a mistake you can be very sorry afterwards**

So think very carefully before you alter anything!!!!!!
You have been warned!!!!!

Hit ALT>>F2,
Type in the box```
gksudo nautilus
```
Type your login password and navigate to your mnt/data folder.

---

### Post by bodhi.zazen on 2006-11-13
> **lylesiemens said:**
> I don't care really as long as I can access my D drive, heres what I get.

lyle@lyle-desktop:~$ /dev/hdb1 /mnt/data ntfs-g3 auto,gid=1002,umask=0002 0 0
bash: /dev/hdb1: Permission denied
lyle@lyle-desktop:~$ /dev/hdb1 /mnt/data ntfs auto,users,umask=0222  0 0
bash: /dev/hdb1: Permission denied
lyle@lyle-desktop:~$ /dev/hdb1 /mnt/data ntfs-g3 auto,gid=1002,umask=0002 0 0
bash: /dev/hdb1: Permission denied
lyle@lyle-desktop:~$

None of these are commands to be entered into a terminal. **One** of these should be added or modified to /etc/fstab.

In a terminal:```
sudo gedit /etc/fstab
```

Modify and save the file.

then use the command mount:```
mount /mnt/data
```

Please read this thread: [how to fstab](http://ubuntuforums.org/showthread.php?t=283131)

I am sorry you are frustrated, but you will need to read to solve your problems. If, after you have read the thread, you have a question, please ask.

Bulldog's solution will also work, as long as the partition is mounted. Otherwise you will have to mount it first.

---

### Post by lylesiemens on 2006-11-13
Thankyou, it worked, but will it self destruct or something??

---

### Post by Henry Rayker on 2006-11-13
whose solution worked?

Bulldog's solution could cause you some trouble. If, say, you want to delete the entire / directory...well, it won't stop you.

All that talk about being the owner...that's the protection against that kind of thing. A lot of files are "given" to the root user. Anyone without root access can't touch them; anyone WITH root access can do whatever they want: be it delete them, replace them all with pictures of kittens or rearrange and move them around.

---

### Post by bulldog on 2006-11-13
Yes it will explode after 5 minutes!!

Serious,you work as a root and if you exidently throw away a critical system file,it will do it without further asking.
So you can mess things really bad.

So be very carefull when you work as a root!!!

EDIT:
Well bodhi,this will work for a period of time, I know I should have known better................

---

### Post by lylesiemens on 2006-11-13
Can I transfer files to a external drive? Isn't it similar to Windows without the option to be sure you want to delete?

---

### Post by bulldog on 2006-11-13
> **lylesiemens said:**
> Can I transfer files to a external drive? Isn't it similar to Windows without the option to be sure you want to delete?

Please,please read bodhi.zazen's latest post and alter your fstab!!!

I would hate myself if you destroyed your Ubuntu,and I'm sure you will.

Again take action on the instructions bodhi.zazen has given you.

EDIT:well no reply,did my best,if this backfires on you don't come whining!

---

### Post by bodhi.zazen on 2006-11-13
> **bulldog said:**
> I would hate myself if you destroyed your Ubuntu,and I'm sure you will.


:lol: Bulldog, don't worry, be happy. Either he edited fstab or he will learn to respect root. At least you did not tell him how to activate the root account :)

Why, if I had a penny for each Ubuntu install I trashed..... :-({|=

But NOT on my production box ! [-X

lylesiemens: It you are using root I think that is fine as a short term solution, reduce your frustration.

I would urge you to learn a little about the OS before your circumvent the secutity. Be careful with root as small errors can trash your OS.

See these links:

[mount](http://www.tuxfiles.org/linuxhelp/mounting.html)

[fstab](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by bulldog on 2006-11-13
I saw other postings from this user and I have very little faith.
Well indeed,if he trashes Ubuntu,and I'm very sure he will,it will teach him a little lesson.

He's very impatient and won't read or listen.

---

### Post by iLoVe.cF- on 2006-11-13
[http://www.ubuntuforums.org/showthread.php?t=298200&highlight=mount+ext3](http://www.ubuntuforums.org/showthread.php?t=298200&highlight=mount+ext3)

;)..

Read that one.. may be answering some questions.. did for me..

But anyway.. Automounting disabled.. can u enable it ?

---

### Post by bodhi.zazen on 2006-11-13
> **iLoVe.cF- said:**
> [http://www.ubuntuforums.org/showthread.php?t=298200&highlight=mount+ext3](http://www.ubuntuforums.org/showthread.php?t=298200&highlight=mount+ext3)

;)..

Read that one.. may be answering some questions.. did for me..

But anyway.. Automounting disabled.. can u enable it ?

LOL Automount at boot is handled by editing fstab :lol:

Or do you mean gnome-volume-manager ?

---

### Post by bulldog on 2006-11-13
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
Look here and you know how to do it..:D

---

### Post by lylesiemens on 2006-11-13
I was able to access my "root"? for the D drive the bulldogs way. But I tried the other way through the tutorial and would not even pick it up?? I want to transfer all data from D: or hdb in Ubuntu language so that I can install Windows XP on it so that I can use my ATI Radeon to watch video on my TV and keep Ubuntu on my C drive. I am greatly saddened that nothing has worked yet, thanks for your time but I may have to go back to XP if I can't get this straightened out soon. I have soo many other issues that need to be resolved too. I like Umbuntu, but it seems that I have wasted 3 days just to try to get it to work. I learned all the basics of Windows overnight! Is there a way to tranfer my D: data to my external drive?

---

### Post by bodhi.zazen on 2006-11-13
> **lylesiemens said:**
> I was able to access my "root"? for the D drive the bulldogs way. But I tried the other way through the tutorial and would not even pick it up?? I want to transfer all data from D: or hdb in Ubuntu language so that I can install Windows XP on it so that I can use my ATI Radeon to watch video on my TV and keep Ubuntu on my C drive. I am greatly saddened that nothing has worked yet, thanks for your time but I may have to go back to XP if I can't get this straightened out soon. I have soo many other issues that need to be resolved too. I like Umbuntu, but it seems that I have wasted 3 days just to try to get it to work. I learned all the basics of Windows overnight! Is there a way to tranfer my D: data to my external drive?

I doubt you learned windows "overnight". Windows is familiar, but how much experience do you have with the OS?

Ubuntu works well out of the box. Give it as much time as you have to windows and then compare . Until then, read, read, read....

---

