---
title: "Swap partition"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by shankru85 on 2007-02-08
Hi everybody
I am a completely new user to ubuntu for that matter to linux itself...during installation i had not specified swap partition since i thought my 512 mb ram in itself would be enough...but recently i have been having freezes in my desktop and gnome automatically closes the window which is consuming lot of resources...so i thought whether the problem could be solved by specifying a swap partition so that my system will have some more memory to work with...now my doubt is that is there any way i can specify a swap partition without going for reinstallation??I am very much a newbie... so plz help me....

---

### Post by raul_ on 2007-02-08
You can create a swap file:

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/")

Where he says to login as root user, just ignore him. Type sudo in front of all the commands

---

### Post by Billy McCann on 2007-02-21
Hi.  I think I have the same problem as shankru - no swap partition.  I found the instructions on making a swap file, but before I did that, I want to make sure that I really don't have a swap partition.  

Here's my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=64bb050d-2452-44ec-bf2d-73483c2bbcb4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=fdca3c08-3d09-4e24-b422-92e9485ade10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

Here's the output of the command "free".
```
             total       used       free     shared    buffers     cached
Mem:        254572     241480      13092          0       1336      54696
-/+ buffers/cache:     185448      69124
Swap:            0          0          0
```

And the "System Monitor" reads "used swap" as "0 of 0".  All these things seem to point to the fact that I don't have a swap partition.  I'd rather use a little space from my FAT32 partition rather than create a swap file, but I'll make due if a swap file is preferable.  


Any comments much appreciated.

Billy

---

### Post by mikewhatever on 2007-02-21
As you can probably see, you do have a swap, it just isn't used, so it reads 0.
dev/sda5

---

### Post by Billy McCann on 2007-02-21
That's good news.  I found some instructions on how to activate it somewhere.  I'll see if I can find them again.  Thanks for the response.

---

### Post by Billy McCann on 2007-02-21
Found those instructions over [here]("http://www.ubuntuforums.org/showthread.php?t=358602").

Changed fstab line

```
UUID=fdca3c08-3d09-4e24-b422-92e9485ade10 none            swap    sw              0       0
```

to 

```
/dev/hda5 none swap sw 0 0 
```

"free" now reads 

```
             total       used       free     shared    buffers     cached
Mem:        254572     250516       4056          0       7236      98056
-/+ buffers/cache:     145224     109348
Swap:       337324          0     337324
```


Sweet goodness.  :)

---

### Post by Billy McCann on 2007-02-21
And Ubuntu is working much, much faster now.  :KS

---

### Post by mikewhatever on 2007-02-21
I'll try that too. Didn't know it needed to be activated manually.

---

