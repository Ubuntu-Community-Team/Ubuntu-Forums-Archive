---
title: "mount xp dissapears"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by binary_dream on 2006-11-05
Hi folks,

after mounting winxp, when I restarted my notebook it was not there any more (media/windows)???

I had to run the same command on terminal as initially when I mounted xp for the first time, do I have to do this over and over again every time I start the notebook?

I have another question, I need to install the Intel graphics sharpener (915), when I went to Intel web they have the drivers only for Suse, does that work on Ubuntu? Without this driver I have not so good graphics as used in XP, it is a bit blurry.

Another question, I just downloaded Avast, how to I install it via terminal? when I do the command for unpacking do I have to be on the same dir where the the distros are?

thanx in advance

---

### Post by aysiu on 2006-11-05
This will help you get it mounted permanently:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by binary_dream on 2006-11-05
> **aysiu said:**
> This will help you get it mounted permanently:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

I tried that but when I do  this:
sudo nano /etc/fstab

I dont have hda1 on that file... I just have 


# /dev/hda2

/dev/hdb

very strange .... :(

---

### Post by taurus on 2006-11-05
What does your /etc/fstab look like then?

```
more /etc/fstab
```

---

### Post by binary_dream on 2006-11-05
I have ubuntu on notebook (no int connection), while I'm writting from my desktop which in on win. SO I guess I have to ype all that :(

ok anyways here it is:
```

# ect/fstab: static file system information
#
#<file system>  <mount point>  <type> <options>      <dump>  <pass>
proc             /proc          proc   defaults       0       0
# /dev/hda2
UUID=3392e58........./     ext3  defaults, errors=remount -ro 0 $ -ro 0    1
# /dev/hda5
UUID=5c46b...........      none  swap sw     0       0      0
/dev/hdb                  /media/cdrom0  udf,iso9660 user,noauto  0    0

```


this is it, these dots ...... I used instead of some number on UUID I hope they are not significant for this problem. I'll post them should this be required.

thanx

---

### Post by taurus on 2006-11-05
Okay, I assume your XP is on the first partition of the first harddrive, /dev/hda1.  edit /etc/fstab with

```
sudo nano -Bw /etc/fstab
```
and add the following line to the end of it.

```

/dev/hda1   /media/Windows   ntfs   defaults,umask=0222   0   0

```
Save it and run these three commands at the prompt.

```

sudo mkdir /media/Windows
sudo mount -a
df -h

```
You should see your XP in /media/Windows with the last command from above...

---

### Post by binary_dream on 2006-11-05
it is true that windows is on my first partition,
I already have created /media/windows 
I did mount it before but the problem is that it dissappears when I restart the system,
using this what u suggested will I have any problem next time I restart system?

---

### Post by taurus on 2006-11-05
If you edit your /etc/fstab, your Windows will be mount to /media/Windows (or change it to /media/windows if you wish but remember, /media/Windows is not the same as /media/windows since Linux/Unix is case sensitive) each time you boot Ubuntu.  Then, don't have to worry about mount an unmount again...

---

### Post by binary_dream on 2006-11-05
it is not working the commands you wrote above :(:(:(, I get this error message:
```

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In some cases.......

```

---

### Post by taurus on 2006-11-05
What the output of this command then?

```
sudo fdisk -l
```

---

### Post by binary_dream on 2006-11-05
```

Disk /dev/hda: 60.0 GB, 60011....... bytes
255 heads.........
Units= cylinders of 16065............


Device Boot   Start   End    Blocks    Id System
/dev/hda1 *     1     3925   31527513   7 HPFT/NTFS
/dev/hda2 ............................... Linux
/dev/hda3 ............................... Extended
/dev/hda5 ............................... Linux swap / Solaris



```

I used the dots instead of some figures.

---

### Post by taurus on 2006-11-05
And can I look at your /etc/fstab again?  

```
more /etc/fstab
```

---

### Post by binary_dream on 2006-11-05
```

# ect/fstab: static file system information
#
#<file system>  <mount point>  <type> <options>      <dump>  <pass>
proc             /proc          proc   defaults       0       0
# /dev/hda2
UUID=3392e58........./     ext3  defaults, errors=remount -ro 0 $ -ro 0    1
# /dev/hda5
UUID=5c46b...........      none  swap sw     0       0      0
/dev/hdb                  /media/cdrom0  udf,iso9660 user,noauto  0    0
/dev/hda1     /media/Windows  ntfs  defaults,unmask=0222   0   0


```

---

### Post by taurus on 2006-11-05
First, you said you have /media/windows but you put /media/Windows in /etc/fstab.  Again, /media/windows is not the same /media/Windows since Linux/Unix is a case sensitive.

Also, it should be "umask=0222" not "u**[SIZE="3"]n[/SIZE]**mask=0222" in /etc/fstab.  Make those two changes and see if you can mount it again.

---

### Post by binary_dream on 2006-11-05
thanx man, this worked, pardon my ignorance, the problem was with that unmask, by the way I had to windows with upper and lowercase, I created another with upper case when I followed your command, but this is not a problem, can you tell me on how to delete windows folder which is empty, meanwhile Windows is working fine.


thanx a lot, I was getting stressed a bit with this ... I'm very new to Linux.

---

### Post by taurus on 2006-11-05
Glad to hear that it is finally working.  I guess you can do a little victory dance now, eh!

If you want to remove /media/windows since you don't need it anymore, open a terminal and type

```
sudo rm /mnt/windows
```

---

### Post by binary_dream on 2006-11-05
rmdir /media/windows which I found it in google, I guess I shouldn't have asked such a simple question lol :D for removing directory, but I couln't really delete it with GUI it pop-s up a message error message - error while moving  .... you dont have permission to change it or its parent folder ...

---

### Post by taurus on 2006-11-05
You need to put "sudo" in front of it.

```
sudo rmdir /media/windows
```

---

### Post by binary_dream on 2006-11-05
yes I did, but for the sake of brevity I omitted in the last post, otherwise it wouldn't worked I guess.

another question I have which I hope you can help me with is that avast anti virus that I've downloaded, but I dont know on how, I have the package downloaded.

I tried the command sudo dpkg -i file_name.deb of course with correct file name but it doesn't work really. :(

---

### Post by taurus on 2006-11-05
Sorry but I don't use antivirus on my machines, never have and you probably don't need to.  So, you may want to create a new thread for it so people would know...

---

### Post by binary_dream on 2006-11-05
ok thankx I think I mamanged to unpack the distros by following instruction from this thread [http://ubuntuforums.org/showthread.php?t=229128](http://ubuntuforums.org/showthread.php?t=229128)

thank for walking me up through the steps for mounting win xp.

---

### Post by taurus on 2006-11-05
You're welcome.

---

