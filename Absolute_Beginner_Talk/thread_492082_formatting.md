---
title: "formatting?"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by shanerdaner on 2007-07-04
I have an external drive I used to use in windows I want to format it to the proper type for linux.. ext3 I think it is.  How do I do this?  I tried Gpart and it didn't want to work so do I just install ubuntu to the drive to get it to work?  TIA

---

### Post by trak87 on 2007-07-04
Generally speaking you want to find the device name of this external drive (be sure because you don't want to accidentally format the wrong drive). Then you want to make sure it is unmounted. Then format it at the command line with "sudo mkfs.ext3 <device>". If you need to restructure the partitions on the drive, use gparted, otherwise you may not even need it. You can use fdisk at the command line to delete and add partitions too but it can't do non-destructive partitioning like gparted can.

---

### Post by shanerdaner on 2007-07-04
> **trak87 said:**
> Generally speaking you want to find the device name of this external drive (be sure because you don't want to accidentally format the wrong drive). Then you want to make sure it is unmounted. Then format it at the command line with "sudo mkfs.ext3 <device>". If you need to restructure the partitions on the drive, use gparted, otherwise you may not even need it. You can use fdisk at the command line to delete and add partitions too but it can't do non-destructive partitioning like gparted can.
thanks I'll try it!:p

---

### Post by Hobo Joe on 2007-07-04
You need t boot into the live CD, figure out the name of your external drive, and then unmount it in GParted, then select 'format as', then 'ext3'.

Pretty simple really. :)

---

### Post by shanerdaner on 2007-07-04
> **Hobo Joe said:**
> You need t boot into the live CD, figure out the name of your external drive, and then unmount it in GParted, then select 'format as', then 'ext3'.

Pretty simple really. :)

that doesn't work

---

### Post by shanerdaner on 2007-07-04
it isn't working either of your ways I will post results for u

---

### Post by shanerdaner on 2007-07-04
> **Hobo Joe said:**
> You need t boot into the live CD, figure out the name of your external drive, and then unmount it in GParted, then select 'format as', then 'ext3'.

Pretty simple really. :)

How do I unmount in Gparted?  it won't let me

---

### Post by shanerdaner on 2007-07-04
ok I got it formatted however now I can't create new folders in the drive  any ideas???  I cant copy and paste to it either.

---

### Post by shanerdaner on 2007-07-04
My drives say the owner is root so I can not change the name of the drive or paste anything in it...  how do I fix that?  TIA

---

### Post by mlentink on 2007-07-04
```
man chown
```
Might this help?

---

### Post by shanerdaner on 2007-07-04
> **mlentink said:**
> ```
man chown
```
Might this help?
where do I put that at???

---

### Post by mlentink on 2007-07-04
Applications>Accessories> Terminal-window

Please excuse me if I haven't got it right, I use a dutch-language version. I tried to translate as best I can...


Edit: should've given some more info. Most command-line commands come with built-in explanation. At the command line, if you type "man" in front of the command, like: 
```
man ls
```
the system will tell you everything there is to know about the command to list files. Your own built-in manual.

Now, does Windows have that? ;)

---

### Post by shanerdaner on 2007-07-04
ok I did it but I dont really understand what to do with it can u explain how I can get permissions on the drives??  thanks!

---

### Post by trak87 on 2007-07-05
Try this (message #2):

[http://ubuntuforums.org/showthread.php?t=487179](http://ubuntuforums.org/showthread.php?t=487179)

It's a permissions problem. You need to go to the new partition's root directory, create a new directory and change its permissions to you as the owner.

---

### Post by shanerdaner on 2007-07-05
> **trak87 said:**
> Try this (message #2):

[http://ubuntuforums.org/showthread.php?t=487179](http://ubuntuforums.org/showthread.php?t=487179)

It's a permissions problem. You need to go to the new partition's root directory, create a new directory and change its permissions to you as the owner.

thanks but that is no help whats the mount point?   the drive is on my desktop mounted and it is called disc I also have disc-1 and disc-2

thanks

---

### Post by trak87 on 2007-07-05
If it's mounted, look in /etc/mtab and you should see the mount point (after the device name):

```
more /etc/mtab
```

Or possibly you can right click on the drive if it's on the desktop and Properties may show the mount point.

---

### Post by shanerdaner on 2007-07-07
I haven't had a chance to try your recommendation yet.  i will have more time mid-week though and thanks again!

---

### Post by shanerdaner on 2007-07-08
Thanks for everyone's help i got everything up and running just as I needed!  I appreciate it!

---

