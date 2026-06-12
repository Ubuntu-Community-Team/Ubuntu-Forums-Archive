---
title: "Corrupt files on iPod"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by kevindubrow on 2008-03-19
Hey, I have some corrupt files on my iPod I could use some help getting rid of.

I am not able to just delete them. 
I tried defragmenting the hard drive with Windows (I don't know how to defrag with Ubuntu), but I got an error saying that the drive could not be drfragmented because there were corrupt files.

Does someone know how I can get rid of them? Thanks!

---

### Post by unutbu on 2008-03-19
Instead of defrag'ing, you need to use a program like fsck (on the linux side) or chkdsk / scandisk on the Windows side. The particular program you would want to use depends on the filesystem type on the ipod.

Do you know what filesystem type is on your ipod?
If not, plug the ipod in to your linux box and type
```

mount
sudo fdisk -l

```

and post the output here.

---

### Post by NR1224 on 2008-03-19
i believe that there is an ipod backup or restore utility availible from apple which should return an ipod to factory conditions(firmware wise). Just make sure to back up your music because i believe it does a complete ipod os reinstall

---

### Post by kevindubrow on 2008-03-19
Hey everyone. Thanks a lot for your replies.

I did some more searching online and found that if I hooked up the iPod to a Windows computer, I could right click on the drive and hit format. I did so and the iPod is fine now. I really don't like that I had to resort to using a Windows computer again. So I will remember the fdisk program for now on. How would I run that? Sudo fdisk?

Oh and I will look into that iPod utility too because I would like to update my iPod's OS too. 

Thanks so much for your help!

---

### Post by unutbu on 2008-03-19
Great. I'm glad you got your ipod back in order. Here is a little rundown of Linux tools you could use if you don't want to use Windows next time:

fdisk -- a tool for printing/manipulating partition tables. (Powerful, but for most purposes, gparted is arguably easier to use).

gparted -- like fdisk but (1) has a GUI, (2) can do some things fdisk can't like resize and format partitions.

Be sure you know what you're doing when using fdisk or gparted. In the wrong hands they can completely f**k your computer up. (It's called fdisk for a reason... :) ).

fsck, fsck.ext2, fsck.vfat, etc -- for checking/repairing corrupted filesystems. Not to be confused with fdisk. Use these when you want to repair the filesystem without losing all the data on the device. Tools like gparted don't repair filesystems. They only destroy, create or move them.

You can find more about any of these programs by googling or typing
```

man <command>

```

Hope this helps.

---

### Post by kevindubrow on 2008-03-19
Thanks so much! I appreciate the info!

---

