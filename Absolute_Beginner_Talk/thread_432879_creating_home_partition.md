---
title: "creating /home partition"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by HeyItsMatt on 2007-05-04
Hi everybody!

I am planning to move my /home folder to a seperate partition so I can reinstall Ubuntu more easily in the future (and just for the experience of doing it).  I am looking at the psychocats “create a separate /home partition” page, but it confuses me a bit.    [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Under the heading “using the new partition” there are command line instructions that confuse me.  Why am I creating two new directories called /old and /new, and then moving the original Linux partition to /old and the newly created partition intended for /home to /new?  Is this somehow a part of moving my original /home folder contents so that I will put them back onto the new separate /home partition?  Lastly, how is this going to affect my actual partitions if I am doing these things from a Live CD?  I thought the Live CD basically ran everything from the CD only and could not affect anything on your hard drive?

Just out of curiosity, are there other ways I could do this?  For instance, I remember I just had to enter a mount command in the terminal and modify fstab in order to mount my windows partition into the /media folder (I dual boot Windows / Ubuntu).  Could I do pretty much do the same thing and mount a newly created ext3 partition into the /home directory, and then add a line to fstab? (after backing up /home files, and then putting them back in the new /home partition).  Or is that what basically what the psychocats resource is doing?  I guess I am just getting confused the more I try to interpret some of those command line directions.

Thanks for reading!

---

### Post by lakersforce on 2007-05-04
Perhaps you could use the recovery mode or a livecd and use the graphical partition editor GParted instead? Would be the easiest solution (but not much of an learning experience, of course).

---

### Post by laidback on 2007-05-04
Don't know about the particular issue you raise but I can tell you that you will need to do the repatitioning/adjustments from the Live CD as you cannot alter a mounted partition, i.e. one that is in use, as your would be if you just boot up into it.

---

### Post by uantuzri on 2007-05-09
> **HeyItsMatt said:**
> Hi everybody!

I am planning to move my /home folder to a seperate partition so I can reinstall Ubuntu more easily in the future (and just for the experience of doing it).  I am looking at the psychocats &#8220;create a separate /home partition&#8221; page, but it confuses me a bit.    [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Under the heading &#8220;using the new partition&#8221; there are command line instructions that confuse me.  Why am I creating two new directories called /old and /new, and then moving the original Linux partition to /old and the newly created partition intended for /home to /new?  Is this somehow a part of moving my original /home folder contents so that I will put them back onto the new separate /home partition?

I found that guide as well and I have just the same doubt as you. Looking around I found this other guide that might be helpful: [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")


 > **HeyItsMatt said:**
> Lastly, how is this going to affect my actual partitions if I am doing these things from a Live CD?  I thought the Live CD basically ran everything from the CD only and could not affect anything on your hard drive?

A live cd runs everything from the CD, but when you mount your hard drives, you can read and write on it. You can't run programs from it, but you can modify files or whatever.

---

### Post by uantuzri on 2007-05-09
One more thing. Those guides aren't prepared for Feisty on the part about fstab.

Remember to put the UUID before the line you add, so it looks like something like this:
```
UUID=bb82134b-63dc-484c-3863-3a5e716e38d0 /home     ext3    defaults        0       2
```

You will know your partitions UUID by typing 
```
blkid
```

copy and paste without the **"**

Hope this helps

---

