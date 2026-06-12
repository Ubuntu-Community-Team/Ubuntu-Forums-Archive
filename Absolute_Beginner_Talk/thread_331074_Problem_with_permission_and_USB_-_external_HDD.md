---
title: "Problem with permission and USB - external HDD"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by lodravah on 2007-01-04
Heyall

I try once again looking for help with this one.. I'm stumped! I've tried before, and got some good help from "Taurus" here on this forum, but nothing so far has worked, so I try again! 

Here is the link to the previous thread: [http://ubuntuforums.org/showthread.php?t=321006&highlight=lodravah](http://ubuntuforums.org/showthread.php?t=321006&highlight=lodravah)

Please read the thread, and if there is anyone out there with an idea, let me know! I've been diddling around "fstab" right now, and it no longer automounts, even though I changed fstab back to normal. Please help, I am now_really_frustrated!

---

### Post by Ecthelion on 2007-01-04
From the other thread:

> Mokay.. I'll give edgy a try first then. 

Did you swiched to Edgy or are you still on Dapper Drake?

> First, I'm going to try installing Dapper on my dad's serously buggy, ISDN - connecting Win98 - box. Wish me luck :P

If that install did succeed, can you read your disk on this (or any other) pc?
Just to make sure that the problem lies in Ubuntu, not in the disk...

---

### Post by lodravah on 2007-01-04
No on both, I'm afraid :)

I'm just back from Christmas Holidays, and so just started working on the problem again. Still on Dapper. 

And my fathers PC only has 64 Mb RAM, so that's an Ubuntu - no go.. Might going to try the HDD at a friends Kubuntu-box later, but uncertain. Please give some hints if you have some.

---

### Post by Ecthelion on 2007-01-04
> Please give some hints if you have some.

It's hard to give hints after all those taurus gave and didn't worked (though i've learned some things there ;-) )

Only thing that I can advice is to copy the content of the disk and reformat it.
But since it's 320Gb that could be hard to do...

How much of the 320Gb is used?
Otherwise you could resize your partition, format the free space in ext3 or something, copy over files till it's full, make a new partition in the free space, ...

But that'll take time and messing with partitions is never 100% safe...

---

### Post by lodravah on 2007-01-04
Actually, I've now tried the HDD on my friends Kubuntu - box, about to try it on a winbox. I'm transferring the most important files from the HDD now, as I'm also going to reinstall ubuntu. As it turns out, I have the same problem on my firends pc. I'm thinking of formating the HDD, but how to do it? Should I format into ext3 or fat32? I would like to be able to use it on win - boxes as my girlfriend has one, and firends too. Hence I guess FAT32 is the best choice. 

Any thoughts?

---

### Post by gilbertr on 2007-01-04
If you want to use it on Win as well, you could go FAT32 but obviously you'll have the 4GB limit (OK for normal data and MP3s but not so handy for films and some backups...)
NTFS is out of the question as difficult to use with Linux.
Last option is ext3, very good for Linux and also useable by Windows by means of Ext2IFS ([http://www.fs-driver.org/)](http://www.fs-driver.org/)).  It mentions ext2 but works for ext3 also.
You would have to install Ext2IFS on each Windows machine used to access your HDD.

---

### Post by Ecthelion on 2007-01-04
> You would have to install Ext2IFS on each Windows machine used to access your HDD.

You could make a small fat32 partition with the drivers for ext 3 for windows on.
The rest in ext3 with your data.
Then you can use it on every computer as you always have the drivers & the data ;-)

---

