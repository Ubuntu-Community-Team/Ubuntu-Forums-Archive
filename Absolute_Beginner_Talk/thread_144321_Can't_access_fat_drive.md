---
title: "Can't access fat drive"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-03-14
Hello everone,

I've tried many mount commands and edited my fstab file many times but I still can't write to my windows fat drivefrom Ubuntu. 

I get access denied can not access this drive.

Any help appreciated,

Don Cole

---

### Post by Sutekh on 2006-03-14
How have you tried to mount the FAT32 drive?

Have you tried this way.  First you need to open a Terminal window and  edit your /etc/fstab.  

You should create a backup of the fstab before editing it
```
sudo cp /etc/fstab /etc/fstab_backup
```
Then you can edit it using 
```
sudo nano /etc/fstab
```
Once you have opened the fstab then you need modify the lines for mounting the FAT32 partitions.  
For a FAT32 partition you probably have a line like this one
```
/dev/hda1 /media/hda1 vfat defaults 0 0
```
You should change it to this one
```
[COLOR="Blue"]/dev/hda1[/COLOR]    [COLOR="Red"]/media/windows[/COLOR]   [COLOR="Green"]vfat[/COLOR]   [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR]   0   0
```
 - [COLOR="Blue"]/dev/hda1[/COLOR] - is the location of the FAT32 partition

 - [COLOR="Red"]/media/windows[/COLOR] - this is the folder where the partition will be mounted.  If this folder doesn't exist you will need to create it yourself ```
sudo mkdir [COLOR="Red"]/media/windows[/COLOR]
```
**Note** you don't have to use [COLOR="Red"]/media/windows[/COLOR], in my system I use [COLOR="Red"]/mnt/os-shared[/COLOR], its up to you

 - [COLOR="Green"]vfat[/COLOR] - this specifies the filesystem as fat

 - [COLOR="DarkOrchid"]iocharset=utf8,umask=0000[/COLOR] - these options set the character encoding to utf8 (for special chars) and sets the **umask**.  [COLOR="DarkOrchid"]umask=0000[/COLOR] allows read, write and execute access to the partition.

Once you've modified the /etc/fstab, you can save it (Ctrl+X), exit (Ctrl+O) and issue the commands```
sudo umount [COLOR="Blue"]/dev/hda1[/COLOR]
sudo mount -a
```This unmounts the FAT32 partition [COLOR="Blue"]/dev/hda1[/COLOR] from it's old mount point (and settings) and then re-mounts the partitions.  All this can be achieved without you having to restart your computer.

Then you should be away

---

### Post by patrick.ubuntu on 2006-03-14
Thanks for that excellent reply!
I was beginning to wonder what I was doing wrong...
Why do all the how to guides say to do the mounting the other way?
Cheers,
Patrick (who'll be windows free once the ipod situation gets worked out)

---

### Post by Sutekh on 2006-03-14
Your welcome.  Glad it helped you.

As a matter of interset, what do other guides say?

My inspiration comes from this great web-site with plenty of Ubuntu mini howtos

[http://www.psychocats.net/]("http://www.psychocats.net/")

---

### Post by sudomania4 on 2006-03-17
Could this be stickied/pinned? It can help alot of people. It helped me.

---

### Post by jameswilmot2000 on 2006-04-13
Hello all,

I am a new user of Ubuntu and i am dual booting with Windows XP Pro.

At the installation i created a separate partition (Fat32) for all of my data to share between the Operating Systems. However i am having trouble mounting the drive. 

I finally figured out how too mount the drive manually using the command - 

sudo mount /dev/hda5 /media/fat -t vfat -o umask=000

and i can edit the drive but strangely cannot creat folders all files in the root directory ... i can however copy files to this directory and i can create and edit files inside the folders (strange ...) 

However when i alter the fstab file with the following - 

/dev/fda5     /media/fat      vfat     umask=000     0      0

When i go to remount this - 

sudo mount -a

I get the response - 

mount: special device dev/hda5 does not exist



Help is greatly appreciated

---

### Post by aysiu on 2006-04-14
Post the output of these three command: ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by jameswilmot2000 on 2006-04-14
i am a complete idiot ... (goes and hits head on desk)

the answer was right in front of me - 

/dev/[COLOR="Red"]fda5[/COLOR] /media/fat vfat umask=000 0 0

it was supposed to be hda5 ... 

ah well

---

### Post by Mustard on 2006-04-14
[QUOTE=jameswilmot2000]i am a complete idiot ... (goes and hits head on desk)

the answer was right in front of me - 

/dev/[COLOR="Red"]fda5[/COLOR] /media/fat vfat umask=000 0 0

it was supposed to be hda5 ... 

ah well[/QUOTE]

We've all been there before, staring at a line that has a glaring error in it and not being able to see it. ;)

---

### Post by gemma1 on 2006-09-30
I have been trying to get my second FAT32 harddrive accessable for hours now - I am progressing but this error has stumped me ...

I am using Sutekh "how to" above, but when do this:

```

sudo umount /dev/hda1

```

I recieve this error:

```

umount: /: device is busy
umount: /: device is busy

```

Any ideas? Thanks. Gem.

---

### Post by easyease on 2006-09-30
could you show us what your fstab looks like?

---

### Post by aysiu on 2006-09-30
Hm. Can you try this? ```
sudo umount -l /dev/hda1
```

If that doesn't work, you can try editing the /etc/fstab file and then rebooting.

---

### Post by CatKiller on 2006-09-30
I'm not sure that hda1 is the partition that you want. hda1 is the first partition on the first hard drive in your computer. This may well be the filesystem that you're using to run commands with, which is why it won't let you unmount it.

Given that you've described the partition you're after as your "second FAT32 harddrive", it's almost certainly something else.

EDIT: Wow, everyone types faster than me.

---

### Post by easyease on 2006-09-30
"Given that you've described the partition you're after as your "second FAT32 harddrive", it's almost certainly something else.
which is why im wondering what the fstab looks like......:D

---

### Post by gemma1 on 2006-09-30
> **easyease said:**
> "Given that you've described the partition you're after as your "second FAT32 harddrive", it's almost certainly something else.
which is why im wondering what the fstab looks like......:D

Yes, I did muck up my file system names, here is the fstab:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1    /media/windows   vfat   iocharset=utf8,umask=0000   0   0

```

I think I have it ... but I still get an error, now it is:

```

star@star:~$ sudo umount /dev/hdb1
umount: /dev/hdb1: not found

```

Thanks. Gem.

---

### Post by aysiu on 2006-09-30
Ah, that's why it's busy. Others were quicker to pick up on it.

/dev/hda1 is Ubuntu

/dev/hdb1 is your FAT32 drive, and it looks as if it already has the correct permissions.

What happens when you go the /media/windows directory?

---

### Post by gemma1 on 2006-09-30
> **aysiu said:**
> What happens when you go the /media/windows directory?

I can go to it but nothing is there:

```

star@star:~$ cd /media/windows/
star@star:/media/windows$ ls

```

Gem.

---

### Post by easyease on 2006-09-30
ok after giving hdb1 the new pwermissions did you....

 sudo mount -a

then try dragging and dropping a pic or something onto that drive.....

---

### Post by gemma1 on 2006-09-30
> **easyease said:**
> 
sudo mount -a


star@star:/media/windows$ sudo mount -a
mount: special device /dev/hdb1 does not exist

> 
then try dragging and dropping a pic or something onto that drive.....

I get "you do not have permissions to write to this folder".

Gem.

---

### Post by easyease on 2006-09-30
ok, it might be just something to do wuith the spacing in your fstab, try opening it again 

sudo nano -B /etc/fstab

 then removing the line regarding hdb1 that is there now and pasting this as it is here in its place

/dev/hdb1       /media/windows     vfat    iocharset=utf8,umask=000 0 0

funnily enough my hdb1 is a windows share to so i copied this straight from my fstab, make sure you save it then type....

 sudo mount -a

and try dragging and dropping something in there again. fingers crossed.

---

### Post by gemma1 on 2006-09-30
I restarted and it worked - now the hard drive appears on the desktop and I dropped a picture on it and it saved to it fine.

Now comes the fun of importing emails ... etc ...

Thanks for all the help - very sorry about the basic mistake in the first place ... Gem.

---

### Post by easyease on 2006-09-30
glad to be of help! no need to apologise, its all part of the learning curve.
 :D

---

### Post by CatKiller on 2006-09-30
Glad you got it sorted. I'd have posted more for you, but these guys are so crazily fast.

Welcome to the community.

---

