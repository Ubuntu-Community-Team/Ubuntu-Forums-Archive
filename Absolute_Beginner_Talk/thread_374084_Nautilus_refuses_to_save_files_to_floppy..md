---
title: "Nautilus refuses to save files to floppy."
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-02
I am a one week Linux user. I have been trying to figure out why Nautilus will not copy a file to my floppy drive. You see the message I get in the attachment. Does anyone have a suggestion what may be wrong? :confused: 

This is a fresh install. I thought that maybe I had messed something up in my novice state. In this fresh install, I have added the automatic updates. Other than that, I have only added Firefox and Thunderbird. 

I understand there is a way to copy files to a floppy through Terminal. Anyone know how to do this? Maybe that will work.

Hope you can help. Thanking you in advance for your asssitance. :)
kh

---

### Post by alienexplorers on 2007-03-02
Did you mount the floppy before trying to copy to it.  To mount it use the command sudo mount /dev/fd0 /media/floppy.

---

### Post by kittyhawk63 on 2007-03-02
> **alienexplorers said:**
> Did you mount the floppy before trying to copy to it.  To mount it use the command sudo mount /dev/fd0 /media/floppy.

I tried it yesterday, but couldn't figure how to do it.  I didn't have a terminal command prompt. I will try the sudo command you posted. Thank you.

---

### Post by kittyhawk63 on 2007-03-02
Terminal reports back:

kittyhawk63@kittyhawk63:~$ sudo mount /dev/fd0 /media/floppy
mount: you must specify the filesystem type
kittyhawk63@kittyhawk63:~$

What do I tell it?

---

### Post by aberry5555 on 2007-03-02
type "vfat" on the end of that line

---

### Post by kittyhawk63 on 2007-03-02
> **aberry5555 said:**
> type "vfat" on the end of that line

Thank you. Sorry that I did not get back to you. I had a program malfunction and had to reload Ubuntu this morning. I will now give your "vfat" a try. I'll let you know how it went, should you check back.
kh

---

### Post by kittyhawk63 on 2007-03-02
quote=aberry5555;2235295]type "vfat" on the end of that line[/quote]

aberry555 gave me the following command prompt:
sudo mount /dev/fd0 /media/floppy
That didn't work so aberry5555 told me to add vfat to the end of the line.

I tried adding it, but I am not sure how to include it at the end of the line. I asked aberry555, but aberry555 must have left my post. I have not heard back from aberry555. 

I tried the two ways given below, but I get a request for "**you must specify the filesystem type**". I have no idea what that could mean as it relates to a floppy drive or what to do about it. 

I've tried these two commands with vfat: I don't know which is correct. They both could be wrong. However, I get the same result. 

kittyhawk63@kittyhawk63:~$ sudo mount /dev/fd0 /media/floppy/vfat
Password:
mount: you must specify the filesystem type
kittyhawk63@kittyhawk63:~$

kittyhawk63@kittyhawk63:~$ sudo mount /dev/fd0 /media/floppy_vfat
kittyhawk63@kittyhawk63:~$ sudo mount /dev/fd0 /media/floppy_vfat
mount: you must specify the filesystem type
kittyhawk63@kittyhawk63:~$

I need help in mounting my floppy to copy some files from my desktop. Anyone know how to instruct Terminal to mount a floppy?  ](*,)

I tried to drag a file onto the floppy in Nautilus and it gave me the statement in the second attachment. How do I get permissions? Does that mean that I have to go through Terminal with a sudo command? If so, I am back to where I started. Pleasssse..SOMEONE...help me!

---

### Post by kittyhawk63 on 2007-03-02
Just in case you missed one of my last post, I included this comment.

I tried to drag a file onto the floppy in Nautilus and it gave me the statement in the second attachment. I included that attachment here. 

How do I get permissions? Does that mean that I have to go through Terminal with a sudo command? If so, I am back to where I started. Pleasssse..SOMEONE...help me!

---

### Post by george29 on 2007-03-02
Open a terminal and type the following

```
sudo mkdir /media/floppy0
```
then hit enter - if the mount point already exists, don't worry just continue with the next steps.
then type
```
sudo nano /etc/fstab
```

Type or paste the following line into the bottom of the file.
```
/dev/fd0    /media/floppy0  auto   rw,user,noauto   0   0
```



You can press Ctrl-X to exit, Y to save, and then Enter to accept the file name.


from this post
[http://ubuntuforums.org/archive/index.php/t-67987.html](http://ubuntuforums.org/archive/index.php/t-67987.html)

---

### Post by Maestro23 on 2007-03-02
Here's another post discussing floppy that I dug up: [http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy)

---

### Post by kittyhawk63 on 2007-03-02
> **george29 said:**
> Open a terminal and type the following

```
sudo mkdir /media/floppy0
```then hit enter - if the mount point already exists, don't worry just continue with the next steps.
then type
```
sudo nano /etc/fstab
```Type or paste the following line into the bottom of the file.
```
/dev/fd0    /media/floppy0  auto   rw,user,noauto   0   0
```

You can press Ctrl-X to exit, Y to save, and then Enter to accept the file name.


from this post
[http://ubuntuforums.org/archive/index.php/t-67987.html](http://ubuntuforums.org/archive/index.php/t-67987.html)

Permission is denied. How do I get permission?

---

### Post by kittyhawk63 on 2007-03-02
I get this reply. It still will not save files to floppy.
Anyone see what is wrong in the following?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0    /media/floppy0  auto   rw,user,noauto   0   0
/dev/fd0    /media/floppy0  auto   rw,user,noauto   0   0

---

### Post by alienexplorers on 2007-03-02
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2	/home		ext3	defaults	0	0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
[COLOR="Red"]/dev/fd0        /media/floppy0   auto    rw,user,noauto  0       0[/COLOR]

Only one line with the fd0 information is needed.

---

### Post by kittyhawk63 on 2007-03-02
> **Maestro23 said:**
> Here's another post discussing floppy that I dug up: [http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy)

No success so far. 

Thanks Maestro23. I will look over the link very carefully. I am downloading another copy of Ubuntu just in case the first CD that I received has some uncorrectable errors. I have had to go into Windows to download it because I could not get Nautilus to burn an ISO to CD. It messed up one CD so that I can't use it. So back to Windows to try to get the ISO burned onto CD. It is taking threes times longer to download the file from the same website as it did in Linux. That says a lot about the superiority as far as a downloader. I'm using the default downloader in Linux.

I will try the fix recommended before I decide to reload Ubuntu with the new downloaded file.

Thanks again Maestro23.
kh

---

### Post by kittyhawk63 on 2007-03-03
> **alienexplorers said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2    /home        ext3    defaults    0    0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
[COLOR=Red]/dev/fd0        /media/floppy0   auto    rw,user,noauto  0       0[/COLOR]

Only one line with the fd0 information is needed.

Thanks Alienexplorers

---

### Post by kittyhawk63 on 2007-03-03
> **Maestro23 said:**
> Here's another post discussing floppy that I dug up: [http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy](http://www.ubuntuforums.org/showthread.php?t=104259&highlight=floppy)

Thanks Maestro23. You've come through with a great link for mounting a floppy drive. Three gold stars for your report card. :KS:KS:KS:KS  I never was good in math. :)

kh

---

