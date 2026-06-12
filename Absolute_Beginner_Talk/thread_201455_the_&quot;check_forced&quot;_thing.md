---
title: "the &quot;check forced&quot; thing"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Somenoob on 2006-06-21
When I have not used this things, that occurs every time the system has been booted 30 times without it being used, know what i am talking about?

what is that?

---

### Post by DirtDawg on 2006-06-21
[QUOTE=Somenoob]When I have not used this things, that occurs every time the system has been booted without .

When I have not used this things, that occurs every time the system has been booted 30 times without it being used, know what i am talking about?

what is that?[/QUOTE]

This post is confusing, but I'm glad someone brought it up because this happens to me too. About every 30 boots or so, the system stops for a few minutes for a "force check". It's not a huge problem, but it is slightly annoying. 

Is a "check" the equivalent of a defragmentation? Also, is there some way to do this manually through the command line to pre-empt the boot-up interuption?

---

### Post by rai4shu2 on 2006-06-21
The tool involved here is "fsck" (which checks your file system for errors). If you are getting this every time you boot, check this thread:

[http://www.ubuntuforums.org/showthread.php?t=176595](http://www.ubuntuforums.org/showthread.php?t=176595)

---

### Post by Somenoob on 2006-06-21
[QUOTE=DirtDawg]This post is confusing, but I'm glad someone brought it up because this happens to me too. About every 30 boots or so, the system stops for a few minutes for a "force check". It's not a huge problem, but it is slightly annoying. 

Is a "check" the equivalent of a defragmentation? Also, is there some way to do this manually through the command line to pre-empt the boot-up interuption?[/QUOTE]

Sorry about that, i must have typed the same line twice by accident.

---

### Post by cidica on 2006-06-21
[QUOTE=DirtDawg]This post is confusing, but I'm glad someone brought it up because this happens to me too. About every 30 boots or so, the system stops for a few minutes for a "force check". It's not a huge problem, but it is slightly annoying. 

Is a "check" the equivalent of a defragmentation? Also, is there some way to do this manually through the command line to pre-empt the boot-up interuption?[/QUOTE]


The only time I see the check being forced is when the filesystem isnt unmounted properly. Say if my comp freezes due an overclock of my processsor then it will force the check on the filesystem. Also one time I had a harddrive go bad and it forced a check on every sector of my harddrive.  

[http://web.mit.edu/tytso/www/linux/ext2intro.html]("http://web.mit.edu/tytso/www/linux/ext2intro.html")
is great into to why this is done on ext2. 
[http://www.zip.com.au/~akpm/linux/ext3/ext3-usage.html]("http://www.zip.com.au/~akpm/linux/ext3/ext3-usage.html")
there I found the command for stopping the force check even if the filesystem is clean for the ext3 filesystem. 

Good luck not sure if that answered the Q but I tried. 8)

---

