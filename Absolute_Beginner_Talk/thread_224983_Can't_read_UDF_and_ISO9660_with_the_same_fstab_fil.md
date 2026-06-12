---
title: "Can't read UDF and ISO9660 with the same fstab file"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-07-28
Hi,

I've had this problem since I first installed Ubuntu and I only found half a solution so far.

Here's my ***fstab***:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda7       /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda1       /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
With this one everything works fine except CDs and DVDs in UDF format. When I put one of these in the drive it gets mounted but when I try to access it all I can see is a text file advising that I'm supposed to read it in a system that has UDF drivers. :confused: 

Well, let me surprise you now. Check this ***fstab***:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda7       /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda1       /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660,udf user,noauto     0       0

```
Spot the difference? ;) In the last line, all I did was to swap the ***udf,iso9660*** bit in the original fstab with ***iso9660,udf***. And guess what, UDF discs work just fine now BUT ISO9660 discs don't work anymore!!! :shock: So what I've been doing so far was to edit the ***fstab*** each time depending on what discs i needed to use... :-s 

Now this is the weirdest problem I've had in linux so far. Please let me know if you've got a solution.

Thanks

---

### Post by ovimunt on 2006-07-28
*bump* :D

---

### Post by jimrz on 2006-07-29
have the same problem with UDF and the same "udf, iso9660 user" on both of my cdrom drives. appears that only the one with 'xxx user' works. not sure how to fix, but will be watching this thread hoping someone responds with a solution.

---

### Post by scxtt on 2006-07-29
don't know if this will be useful ...

[http://www.ubuntuforums.org/showthread.php?t=195403&highlight=udf%2Ciso9660](http://www.ubuntuforums.org/showthread.php?t=195403&highlight=udf%2Ciso9660)

---

### Post by ovimunt on 2006-07-29
This seems to be a very common problem. Is this an Ubuntu bug? If so, how can it be reported?

---

### Post by klytu on 2006-07-29
> Hi,

I've had this problem since I first installed Ubuntu and I only found half a solution so far.

Here's my ***fstab***:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda7       /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda1       /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
With this one everything works fine except CDs and DVDs in UDF format. When I put one of these in the drive it gets mounted but when I try to access it all I can see is a text file advising that I'm supposed to read it in a system that has UDF drivers. :confused: 

Well, let me surprise you now. Check this ***fstab***:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda7       /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda1       /media/WinXP    ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660,udf user,noauto     0       0

```
Spot the difference? ;) In the last line, all I did was to swap the ***udf,iso9660*** bit in the original fstab with ***iso9660,udf***. And guess what, UDF discs work just fine now BUT ISO9660 discs don't work anymore!!! :shock: So what I've been doing so far was to edit the ***fstab*** each time depending on what discs i needed to use... :-s 


I also find it strange that, looking at other related threads, the solution above works for some folks and not for others. For me, I don't seem to have any problems with an fstab like your first one. But I am not completely at ease because I have other weird problems with CDs, DVDs, CD-RWs mounting and burning on exactly one of my disc drives (I am POSITIVE there is nothing wrong with the hardware problem disc drive) which I had to workaround by mounting discs in that particular drive from the command line. I don't want to clutter this thread with the specifics of my problem, but I just wanted to point out that until this apparent bug is corrected you can always mount from the command line and you shouldn't have any trouble. That would probably be less inconvenient than changing your fstab every time you need to put in a different type disc!


> **ovimunt said:**
> This seems to be a very common problem. Is this an Ubuntu bug? If so, how can it be reported?

[https://launchpad.net/distros/ubuntu/+filebug](https://launchpad.net/distros/ubuntu/+filebug)

---

### Post by ovimunt on 2006-07-29
*bump*

---

### Post by ovimunt on 2006-07-29
Yupeee!!! FIXED IT!!! \\:D/

All you need to do is replace ***udf,iso9660*** with ***auto***, i.e.
```

/dev/hdc /media/cdrom0 auto user,noauto 0 0

```
It's THAT simple! :-D

---

### Post by klytu on 2006-07-30
> **ovimunt said:**
> Yupeee!!! FIXED IT!!! \\:D/

All you need to do is replace ***udf,iso9660*** with ***auto***, i.e.
```

/dev/hdc /media/cdrom0 auto user,noauto 0 0

```
It's THAT simple! :-D

Glad that worked for you! Maybe this will help out some other folks, too. According to the man pages there is a warning about the use of **auto**:

 > The auto type may be useful for user-mounted floppies. Creating              a file /etc/filesystems can be useful to change the probe  order (e.g.,  to  try vfat before msdos or ext3 before ext2) or if you use a kernel module autoloader. **Warning: the probing uses a heuristic (the presence of appropriate ‘magic’), and could recognize the wrong filesystem type, possibly with catastrophic consequences.  If  your  data  is  valuable,  don’t ask mount to guess.**

Maybe this is why Ubuntu doesn't set up fstab this way by default for CD and DVD drives?

---

### Post by ovimunt on 2006-07-30
I do get the picture but there's notghing to loose on a CD or DVD since you can't write on it as you do on a HDD of FDD... 

Anyway, bad news is that it's not damn working anymore! I don't know why... :confused: I've just noticed that I can't mount UDF discs, yet again... I can't understand what is happening there, behind the curtains, that messes up all my settings.

---

