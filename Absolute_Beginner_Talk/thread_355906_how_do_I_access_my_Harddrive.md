---
title: "how do I access my Harddrive?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by timmins on 2007-02-07
Hi I've done a search but couldn't find exactly what I need.  Ubuntu is  on my 40 GB "slave drive", I can see my 160 GB "master" drive with all of my media on it. here is what I got:


Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS


How do I access this HD? I know it's NTFS but I'd prefer not to reformat but would consider doing it, should you see it as necessary.

I tried to use this link:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

The drive does show up on Gparted, but I can't access it.

Thanks

---

### Post by timmins on 2007-02-07
A link to another thread regarding this would be fine, I  firgure this question has already been asked a million times.

---

### Post by timmins on 2007-02-07
bumpity bump

---

### Post by mkoyle on 2007-02-07
ntfs-3g is what you want.  It will allow read and write to your ntfs drive without a reformat.  If this is a critical application, you might consider a reformat (i.e. copy the data, reformat and copy it back).  For most things, ntfs-3g is pretty decent now.  If you are running AMD64 you might have more trouble, but I doubt it-- I have it working.

[http://ubuntuforums.org/showthread.php?t=355429&highlight=ntfs-3g](http://ubuntuforums.org/showthread.php?t=355429&highlight=ntfs-3g)

--Matthew

---

### Post by i-am-me on 2007-02-07
If you want to access a NTFS file system from within Linux, then you could try one of two ways (I haven't tried them yet, so I don't guarantee anything):

Download and install [Captive]("http://www.jankratochvil.net/project/captive/"), or you could go [here]("https://wiki.ubuntu.com/ntfs-3g") and get [ntfs-3g]("https://wiki.ubuntu.com/ntfs-3g"). Hope this helps.:)

---

### Post by timmins on 2007-02-07
I'm having trouble installing that program, I had the HD on my computer before without that program. I'm going to try and mount it  I'll come back if I come accross any problems.

---

### Post by timmins on 2007-02-21
Hi, I am following these directions:[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
But I'm stuck on the direction that says,
"Once in there, I should add in this line:

/dev/hda5 /storage ext3 defaults 0 0

Then I can save (Control-X), confirm (Y), and exit (Enter)."

Where do I add this line?

The harddrive that I'm looking to mount is /dev/hda1

here is nano:
                                                        

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=9407e5e9-bf44-4336-bffd-1ecb70d49f45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=50baeda0-000c-4320-a14b-df95a9e1ac84 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0



^G Get Help         ^O WriteOut         ^R Read File        ^Y Prev Page        ^K Cut Text         ^C Cur Pos
^X Exit             ^J Justify          ^W Where Is         ^V Next Page        ^U UnCut Text       ^T To Spell

---

### Post by timmins on 2007-02-21
sorry for the quick bum, but i'd hopefully like to fix this before I go to bed.

---

### Post by timmins on 2007-02-21
bump again

I substituted hda1 with hd5 and entered:
/dev/hda1 /storage ext3 defaults 0 0

so nano looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=9407e5e9-bf44-4336-bffd-1ecb70d49f45 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=50baeda0-000c-4320-a14b-df95a9e1ac84 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1/ storage ext3 0 0What am I doing wrong please


I ge this error, after I type in sudo mount -a

kyle@kyle-desktop:~$ sudo mount -a
mount: mount point storage does not exist


Thanks

---

### Post by letitsnow on 2007-02-21
> /dev/hda1/ storage ext3 0 0What am I doing wrong please


try typing 
```
mkdir storage
```
then
```
sudo mount -a
```

---

### Post by timmins on 2007-02-21
Thanks for the reply, unfortunately I get this error

kyle@kyle-desktop:~$ sudo mount -a
mount: special device /dev/hda1/ does not exist
       (a path prefix is not a directory)

---

### Post by timmins on 2007-02-21
kyle@kyle-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by timmins on 2007-02-21
b to the umpo

---

### Post by letitsnow on 2007-02-21
try replacing
> /dev/hda1/ storage ext3 0 0
with
```
/dev/hda1/ /storage ntfs defaults 0 0
```

---

### Post by timmins on 2007-02-21
It didn't work, I got
mount: special device /dev/hda1/ does not exist
       (a path prefix is not a directory)


It seems pretty self exlaintory doesn't it? " a path prefix is not a directory"

-Kyle

---

### Post by timmins on 2007-02-21
wake up bump.

---

### Post by timmins on 2007-02-21
bump.

---

### Post by letitsnow on 2007-02-21
```
/dev/hda1/ /storage ntfs defaults 0 0
```
remove the / after /dev/hda1, so it looks like
```
/dev/hda1 /storage ntfs defaults 0 0
```

---

### Post by timmins on 2007-02-21
Hi, I've tried every combination possible(including yous) and I continue to get an Identical error:

kyle@kyle-desktop:~$ 
kyle@kyle-desktop:~$ sudo cp /etc/fstab /etc/fstab_backup
kyle@kyle-desktop:~$ sudo nano /etc/fstab
kyle@kyle-desktop:~$ sudo mount -a
mount: mount point ntfs does not exist
kyle@kyle-desktop:~$ sudo cp /etc/fstab /etc/fstab_backup
kyle@kyle-desktop:~$ sudo nano /etc/fstab
kyle@kyle-desktop:~$ sudo mount -a
mount: mount point ext3 does not exist
kyle@kyle-desktop:~$ sudo cp /etc/fstab /etc/fstab_backup
kyle@kyle-desktop:~$ sudo nano /etc/fstab
kyle@kyle-desktop:~$ sudo mount -a
mount: special device /dev/hda1/ does not exist
       (a path prefix is not a directory)

---

### Post by timmins on 2007-02-22
idiot noob needs help.

---

### Post by letitsnow on 2007-02-22
could you post your fstab?

edit: you could try this line if you havn't already
```
/dev/hda1 /storage ntfs nls=utf8,umask=0222 0 0
```

---

### Post by timmins on 2007-02-22
Hi, tried it and got this:

kyle@kyle-desktop:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by timmins on 2007-02-22
here is fdisk Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4664    37463548+  83  Linux
/dev/hdb2            4665        4865     1614532+   5  Extended
/dev/hdb5            4665        4865     1614501   82  Linux swap / Solaris


under gparted it says that the HD is an ext3 extension.

---

### Post by timmins on 2007-02-22
to the top

---

### Post by letitsnow on 2007-02-22
it looks like the system thinks it's ext3. i really have no idea anymore. someone more knowledgable is gonna have to try.

---

### Post by timmins on 2007-02-22
thanks man, does anybody else have any ideas, thanks.

---

### Post by timmins on 2007-02-22
I won't be such a pest on this site if someone helps me, I promise :p

---

### Post by timmins on 2007-02-24
one more bump, should I start a new thread.

Thanks

---

### Post by mkoyle on 2007-02-27
I was looking at givré's thread again ([http://www.ubuntuforums.org/showthread.php?t=217009&page=112](http://www.ubuntuforums.org/showthread.php?t=217009&page=112))

I know it feels like you have tried everything, but did you install ntfs-3g? (sudo apt-get install ntfs-3g). If you did, then try the following line in your fstab file:

/dev/hda1 /storage ntfs-3g defaults,locale=en_US.utf8 0 0 

notice that it will use ntfs-3g instead of the standard ntfs filesystem driver (not sure that is the right word).

Anyway, if that doesn't fix it, I would go post at the end of givré's post to get help from him.  It is 144 pages long now, so why not add one more post ;)

--Matthew

---

