---
title: "fstab"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by lunar7 on 2008-03-29
OK,

So I should have just left it alone....

But is there any way to recreate /etc/fstab ?

Or is there a way re run and install with out going back to the CD then having to download 200 updates ?

---

### Post by bumanie on 2008-03-29
What did you change? Are you able to post a copy of your present fstab or is it completely gone? As far as I know it is possible to write fstab from scratch, but you need to be clear what partitions everything was on and of course correct syntax must be used. I can do basic edits, but don't feel confident to help with a complete rewrite. This link may help
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by louieb on 2008-03-29
If it ain't broke tweak it till it is. :)
Got a live CD? 
Need to find out 2 things 1st. 
What partition Ubuntu is installed in?
What partition is swap?

Is /etc/fstab complety gone? or just mesed up?
going to need at least **/proc, /**, and if you have a seperate home **/home**

Heres an exmple to get started back on the right track?
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2      /home           ext3    defaults          0       2
/dev/sdb2      none            swap    sw                0       0                    
/dev/scd0      /media/cdrom0   udf,iso9660 user,noauto   0       0
/dev/fd0       /media/floppy0  auto    rw,user,noauto    0       0
```

and a page that explains what all that is.
[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131")
[How to edit and understand /etc/fstab]("http://www.tuxfiles.org/linuxhelp/fstab.html")

Thats short of it.

---

### Post by Kevbert on 2008-03-29
Have a look at these pages:
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

