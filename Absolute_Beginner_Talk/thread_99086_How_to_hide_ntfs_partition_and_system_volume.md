---
title: "How to hide ntfs partition and system volume?"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Lancelot on 2005-12-04
Hi guys,

I have a dual boot ubuntu and xp and i want to hide the partition using the third party software(or if you have another way to hide it withoung knowing advance user), i know how to enable and disable ntfs partition in ubuntu..what would you recommend to hide it? my purpose is to hide it so that advance user could not use it without my permission..

Thanks a lot,

---

### Post by MetalMusicAddict on 2005-12-04
[QUOTE=Lancelot]Hi guys,

I have a dual boot ubuntu and xp and i want to hide the partition using the third party software(or if you have another way to hide it withoung knowing advance user), i know how to enable and disable ntfs partition in ubuntu..what would you recommend to hide it? my purpose is to hide it so that advance user could not use it without my permission..

Thanks a lot,[/QUOTE]
In a terminal type: **sudo gedit /etc/fstab** then put a **#** in front of the line that is your NTFS drive.

EXAMPLE
**#/dev/hdb        /media/ntfs   udf,iso9660 user,noauto     0       0**

---

### Post by Lancelot on 2005-12-04
[QUOTE=MetalMusicAddict]In a terminal type: **sudo gedit /etc/fstab** then put a **#** in front of the line that is your NTFS drive.

EXAMPLE
**#/dev/hdb        /media/ntfs   udf,iso9660 user,noauto     0       0**[/QUOTE]

hey, thanks a lot...

i googled fstab - now i know what it is..it's a configuration of all partitions and storage of a computer..

---

### Post by Ntweat on 2008-02-09
i did 

>  Originally Posted by MetalMusicAddict
In a terminal type: sudo gedit /etc/fstab then put a # in front of the line that is your NTFS drive.

EXAMPLE
#/dev/hdb /media/ntfs udf,iso9660 user,noauto 0 0

But the partitions are visible they jst get unmounted i need to hide so its not visible...

---

### Post by erfahren on 2008-02-09
open /etc/fstab and change the mount point of the volumes - that will prevent them from being seen in the side pane 

[b]for this example the volume you want to hide is /dev/sda1 

unmount it - create the new mount point (where ever you want) - change the fstab - remount it[/b]

back it up first (always a good idea)
```

sudo cp /etc/fstab /etc/fstab_back

```
```

sudo umount /dev/sda1

```
```

sudo mkdir /mnt/sda1

```
```

gksudo gedit /etc/fstab

```
EXAMPLE ENTRY - note: this is out of mine - it is my Windows recovery partition, so I made the permissions to be read-only by me and non-accesible by others - if you still want to read/write to it keep the umask at 007 
```

# /dev/sda1
UUID=7004581F16D9B5D2 /mnt/sda1     ntfs    defaults,umask=227,gid=46     0       1

```
```

sudo mount -a

```
you can delete the old mount point of /media/<whatever>
```

sudo rmdir /media/sda1

```

note: umask works reverted of regular file permissions 

note2: you can hide the volumes from being visible on the desktop with the gnome-configuration-editor - launch it with "gconf-editor" - look (somewhere) under Apps > Nautilus > Desktop (maybe under Gnome - I can't recall exactly).

note3: if you set up another user account, they shouldn't be able to access the volumes from that account anyway.

I have put in links to other information on this post: [http://ubuntuforums.org/showpost.php?p=4229726&postcount=9](http://ubuntuforums.org/showpost.php?p=4229726&postcount=9)

--- hope that helped

---

### Post by geo909 on 2008-02-09
Hi,

I know that it is frustrating to get "alternative" answers, but I will just mention a tool that may help you:

 In synaptic, or by apt-get you can install a little tool written in python, called "Pysdm"
(Python Storage Device Manager).

 That has a GUI which you can find under "System->Administration->Storage Device Manager"

From there you can regulate many things regarding your storage devices. You just select the partition, press the "assistant" tab and check/uncheck anything you want, it's really easy.
Maybe you will find such a setting, I can't say for sure.


 On the other hand, it's good to learn one thing or two about fstab and get used to edit configuration files, so if you have the time just do so. I would prefer to have in mind what's exactly going on in fstab instead of letting frontends do the job. 

 I would say, ignore my post for the moment, do your job as erfahren suggest and if you don't get it to work, try pysdm,

---

### Post by erfahren on 2008-02-09
I just noticed that the original post was ~3yrs. old - I guess you really dug this thread up Ntweat! - lol

anyway - there's another thread similar to what I was saying [here](http://ubuntuforums.org/showthread.php?t=415702) - (I wished I remembered having that bookmarked - oh well!)

---

### Post by mikewhatever on 2008-02-09
Hi erfahren, could you clarify which of the settings actually hides the partition. Is it the change in mount point, umask 227 or something else?

---

### Post by erfahren on 2008-02-09
> **mikewhatever said:**
> Hi erfahren, could you clarify which of the settings actually hides the partition. Is it the change in mount point, umask 227 or something else?
just changing the mount point prevents it from showing in the side pane of Nautilus (and on the desktop) 


The umask just  basically just sets the permissions to control the access.

I probably didn't explain the umask options that well. It works the opposite of file/folder permissions - It's explained fairly well [here](http://www.linuxforums.org/security/file_permissions.html) - towards the bottom, under *"Setting the default file creation permissions : umask"*  - [this Fedora forum post](http://forums.fedoraforum.org/archive/index.php/t-32096.html) explains the permissions for Windows fstab entries well.

I just realize that I left out the group ID in that fstab line I put on my previous post (the "gid=46").  (The group can be found by "cat /etc/group") - I need to fix that.

---

### Post by geo909 on 2008-02-09
> **erfahren said:**
> I just noticed that the original post was ~3yrs. old - I guess you really dug this thread up Ntweat! - lol

:lolflag:
Hadn't noticed that!!
Do you think Lancelot is still worried about that?  :mrgreen:
He must have turned into a geek by now...


Hmm.. I'm leaving, I have a few unanswered  threads lost in time, I'll go and check them out, you never know!!

---

### Post by Ntweat on 2008-02-09
Guyz it was a do and die situation....... so i hunted for it....

thanks for all u help.... i m a very small geek.. so i think will try geo909's 1st...


BTW how to get "Pysdm"

---

### Post by mikewhatever on 2008-02-09
Thanks erfahren. Linux file permissions are pretty confusing, but, if I understand correctly, umask=227 translates into 777-227=550 which in turn means -r-xr-x---, that is no write permission to anyone. Is that right?

---

### Post by erfahren on 2008-02-09
> **mikewhatever said:**
> Thanks erfahren. Linux file permissions are pretty confusing, but, if I understand correctly, umask=227 translates into 777-227=550 which in turn means -r-xr-x---, that is no write permission to anyone. Is that right?yep - that's correct - (I got the file permissions figured out fairly well going by the numerical way - I still have to stare at the "-r-xr-x---" way awhile for it to "compute" in my brain.  Too many dashes sometimes!- lol )


**- @ Ntweat**
it's in the repos - search for it in Synaptic Package Manager or just do:
```

sudo apt-get pysdm

```
you'd need to launch it with root permissions - it might not show up in your menu, so launch it with: (use "gksudo" since it is a GUI based application)
```

gksudo pysdm

```
-- I took a look at it and it is pretty good, but you might need a basic understanding of the fstab. You'd probably be able to reset the mount point without too much trouble - that part seems pretty basic. I'll make a new post with basic instructions to do that.

---

### Post by Ntweat on 2008-02-09
i m getting the following error


> ntweat@ibm:~$ gksudo pysdm
QFile::writeBlock: File not open
QFile::writeBlock: File not open
QFile::writeBlock: File not open


around 20 times :(

---

### Post by erfahren on 2008-02-09
--- I was just about to post this ....

> **erfahren said:**
> ... I'll make a new post with basic instructions to do that.
@Ntweat - I take that back. I apologize, but I think it would take me as long (or longer) to explain how to use that than it took me to explain it the other way. 

-- forget about that program for now. the other way I explained it probably looks more difficult than it really is. If what I said about the permissions (and all that) confuses you just do this:

tell me what partitions you want to hide - whether or not *you* want to read and/or write to them

... and post the output of:
```

cat /etc/fstab

```

---

### Post by Ntweat on 2008-02-09
> ntweat@ibm:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb10 :
UUID=ace24c67-cb8d-448e-9ef0-ad48f0696e6d / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb9 :
UUID=86b9ecb6-46b9-4b6e-a7bb-f9d118c22c58 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sdb8 /media/d ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb7 /media/h ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb6 /media/i ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb5 /media/f ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb1 /media/g ntfs-3g defaults,locale=en_IN 0 0
/dev/sda1 /media/c ntfs-3g defaults,locale=en_IN 0 0


i knw i have many partitions... i want read write on all jst dont want them to be shown on system:/media..

Even if read write goes no probs...

and plz tell how to make them visible again caz i wanna make them go aaway for a few days....

the partions i want hidden are::

/media/sda1
/media/sdb6
/media/sdb7
/media/sdb1
/media/sdb8


Thanks for your help!!!

Sorry my net is dam slow!!

---

### Post by mikewhatever on 2008-02-09
> **erfahren said:**
> yep - that's correct - (I got the file permissions figured out fairly well going by the numerical way - I still have to stare at the "-r-xr-x---" way awhile for it to "compute" in my brain.  Too many dashes sometimes!- lol )

I found a nice tool to convert between the two not too long ago, just have to learn a bit more theory. [http://catcode.com/teachmod/numeric2.html](http://catcode.com/teachmod/numeric2.html)

---

### Post by erfahren on 2008-02-09
> **Ntweat said:**
> 

/media/sda1
/media/sdb6
/media/sdb7
/media/sdb1
/media/sdb8


**ok - do this line by line -**
```

sudo umount /dev/sdb8

```
```

sudo umount /dev/sdb7

```
```

sudo umount /dev/sdb6

```
```

sudo umount /dev/sdb1

```
```

sudo umount /dev/sda1

```

**make new mount points**
```

sudo mkdir /mnt/sda1

```
```

sudo mkdir /mnt/sdb1

```
```

sudo mkdir /mnt/sdb6

```
```

sudo mkdir /mnt/sdb7

```
```

sudo mkdir /mnt/sdb8

```

**make a backup of /etc/fstab and open it**
```

sudo cp /etc/fstab /etc/fstab_back

```
```

sudo gedit /etc/fstab

```
**highlight *all* the lines below the "/dev/fd0 /media/floppy0" and replace with the following**
```

/dev/sda1 /mnt/sda1 ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb1 /mnt/sdb1 ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb5 /media/f ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb6 /mnt/sdb6 ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb7 /mnt/sdb7 ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb8 /mnt/sdb8 ntfs-3g defaults,locale=en_IN 0 0

```
**now remount all**
```

sudo mount -a

```
**they should be hidden now (hopefully) let me know how it turns out**

your file should now look like:
```

# /etc/fstab: static file system information.
#
# -- This file has been automaticly generated by ntfs-config --
#
# <file system> <mount point> <type> <options> <dump> <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb10 :
UUID=ace24c67-cb8d-448e-9ef0-ad48f0696e6d / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb9 :
UUID=86b9ecb6-46b9-4b6e-a7bb-f9d118c22c58 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sda1 /mnt/sda1 ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb1 /mnt/sdb1 ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb5 /media/f ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb6 /mnt/sdb6 ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb7 /mnt/sdb7 ntfs-3g defaults,locale=en_IN 0 0
/dev/sdb8 /mnt/sdb8 ntfs-3g defaults,locale=en_IN 0 0


```
(you didn't include /dev/sdb5 so I didn't change it)

---

### Post by Ntweat on 2008-02-09
no change still visible still mounted... tried rebooting also

---

### Post by applegrew on 2008-02-09
Hey erfahren u really are trying to help Ntweat... BTW he uses KDE.... I believe KDE uses fdisk etc..to detect the drives and show them, in the system context, which is visible by typing system:// in Konqueror's location bar.

---

