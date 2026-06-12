---
title: "Something Hitting Disk every 5 seconds"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-03-09
Hi
 i have noticed that  something is hitting my hard drive about every 5 seconds , is there some way to find out what it is ?

Thanks

---

### Post by Brunellus on 2006-03-09
that's the journal being written, I'll bet.  It provides a bit of a a safety-net for whatever was being written/read, in case your computer should fail.

---

### Post by kent41 on 2006-03-09
[QUOTE=Brunellus]that's the journal being written, I'll bet.  It provides a bit of a a safety-net for whatever was being written/read, in case your computer should fail.[/QUOTE]

Is there a name for this file and can i look at it ?

---

### Post by gord on 2006-03-09
its part of your filesystem (EXT3), its not a file persay

---

### Post by kent41 on 2006-03-09
[QUOTE=gord]its part of your filesystem (EXT3), its not a file persay[/QUOTE]

Ok I think I understand but can I change the interval so it's not quite so often?
every 5 second does not seem reasonable.

---

### Post by Lord Illidan on 2006-03-09
It could be Reiser FS too, the same thing should happen on any journalling file system. And the journal cannot be read by users, I believe, as it is a critical file system file.

Are you worried about low performance by any chance? Because it shouldn't interfere much with normal processes. 
On my pc, which is currently downloading a bunch of p2p, I only get these spikes every 5 seconds, which doesn't seem to interfere with anything.
Have you enabled dma? [https://wiki.ubuntu.com/DMA?highlight=%28dma%29]("https://wiki.ubuntu.com/DMA?highlight=%28dma%29")

EDIT : And no, I don't think you can edit this feature.. Otherwise, switch to a non journalling file system, like ext2.

---

### Post by kent41 on 2006-03-09
[QUOTE=Lord Illidan]It could be Reiser FS too, the same thing should happen on any journalling file system. And the journal cannot be read by users, I believe, as it is a critical file system file.

Are you worried about low performance by any chance? Because it shouldn't interfere much with normal processes. 
On my pc, which is currently downloading a bunch of p2p, I only get these spikes every 5 seconds, which doesn't seem to interfere with anything.
Have you enabled dma? [https://wiki.ubuntu.com/DMA?highlight=%28dma%29](https://wiki.ubuntu.com/DMA?highlight=%28dma%29)[/QUOTE]

 No I have not enabled DMA. The more I learn about Linux it seems just about everything and every variable is changable. I would think that the write interval to a journal should also be changable.

Thanks for all the help

---

### Post by Lord Illidan on 2006-03-09
Ok, I did some research. Search for journal + commit + interval + ext3 in Google.

I came up with this site : [http://www.ussg.iu.edu/hypermail/linux/kernel/0208.1/0464.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0208.1/0464.html)

and this one : [http://lwn.net/Articles/5584/](http://lwn.net/Articles/5584/)

However, they are both hard to understand, even for me.
You will have to compile kernel,etc. Enabling dma should provide a larger boost than just increasing the interval between journal updates, and is far less risky too.

---

### Post by kent41 on 2006-03-09
[QUOTE=Lord Illidan]Ok, I did some research. Search for journal + commit + interval + ext3 in Google.

I came up with this site : [http://www.ussg.iu.edu/hypermail/linux/kernel/0208.1/0464.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0208.1/0464.html)

and this one : [http://lwn.net/Articles/5584/](http://lwn.net/Articles/5584/)

However, they are both hard to understand, even for me.
You will have to compile kernel,etc. Enabling dma should provide a larger boost than just increasing the interval between journal updates, and is far less risky too.[/QUOTE]

Great information thanks for your effort it gives me something to work on.
The knowledge available on this forum is unbelievable.  THANKS

---

### Post by Lord Illidan on 2006-03-09
[quote=kent41]Great information thanks for your effort it gives me something to work on.
The knowledge available on this forum is unbelievable.  THANKS[/quote]

You're welcome...It is a learning experience for us all.

---

### Post by stanz on 2006-03-09
Hi All,
I'm kinda following your lead here,...after checking & noting my box has dma support, i ran the code & noticed it was off, and also an error in there.
/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 [COLOR=Red]HDIO_GETGEO failed: Invalid argument[/COLOR]
------------------------
Anyone know what it means?
something to be concerned about?
Thanks... in advance~ it's kewl to learn, with kewl people!

---

### Post by Lord Illidan on 2006-03-10
```
 /dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 [COLOR=Red]HDIO_GETGEO failed: Invalid argument[/COLOR]
```

Is /dev/hdd a cd rom/dvd drive? Because that is what you get when you run hdparm on a drive with no media loaded. Put a cd into /dev/hdd and run hdparm again.

---

