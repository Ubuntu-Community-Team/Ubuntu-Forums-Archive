---
title: "Defragging and junk files"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by gunston on 2006-10-20
Hi All
Is there any need to defrag Ubuntu and does it build up junk files and temp files causing it to run slow like Windows?
I'm using Dapper Drakeand it might be in my mind but, it seems to be running a little slow. ie loading programs, Firefox seems slow even on cable.
Should I be concerned?

Thanks
Regards
Chris:-k

---

### Post by aysiu on 2006-10-20
There's no need to defragment Ubuntu. It doesn't get severely fragmented. [quote=gunston]I'm using Dapper Drakeand it might be in my mind but, it seems to be running a little slow. ie loading programs, Firefox seems slow even on cable.[/quote] Has it *always* been slow, or has it seemed to slow down considerably only recently? What are your computer's specs?

---

### Post by hearnden on 2006-10-20
Some people say ext2/3 systems don't need to be defragged.  I don't quite see the logic behind that, but in my experience fragmentation in Linux or Ubuntu has never been a problem, but that's not to say things wouldn't be better if I did defragment.

There is a package called 'defrag' in the repositories if you feel so inclined.

---

### Post by Sef on 2006-10-20
Ext3 automatically defrags every 30 boots.

---

### Post by gunston on 2006-10-20
Thanks for the replies.
My system is a P4 with 512 megs of ram.
I've had Ubuntu on for about 6 months now and it just seems to be running a bit slow over the last month or so.


Regards
Chris

---

### Post by mssever on 2006-10-20
> **gunston said:**
> Hi All
Is there any need to defrag Ubuntu and does it build up junk files and temp files causing it to run slow like Windows?
I'm using Dapper Drakeand it might be in my mind but, it seems to be running a little slow. ie loading programs, Firefox seems slow even on cable.
Should I be concerned?

Thanks
Regards
Chris:-k
Temp files are in /tmp, which gets cleaned during every reboot.

---

### Post by Grey on 2006-10-20
> **hearnden said:**
> Some people say ext2/3 systems don't need to be defragged.  I don't quite see the logic behind that, but in my experience fragmentation in Linux or Ubuntu has never been a problem, but that's not to say things wouldn't be better if I did defragment.

There is a package called 'defrag' in the repositories if you feel so inclined.

The big difference between Ext2/3 and FAT/NTFS is how free space is treated.  On Windows, the free space is used in order.  If you want to save a 30MB file to a 30GB partition, then it will find the first free place to save it to, and save it there.  Linux, on the other hand, will install it smack dab in the middle of the free space.  Then the next file will be installed in the middle of that.  Then so on and so forth.  And another thing that Ext3 does is reserve large chunks of free space, in the anticipation that you are going to save a big file in that free space.

At any rate, the main difference is that deleting a file in windows will produce a small hole in your hard drive mapping, while in Linux, it will usually produce a much bigger hole, which is more easily filled on subsequent inserts.

However, I do with that there was a defrag tool available (there are methods, but they aren't fancy).  Ext3 is not prone to fragmentation, but it does happen, especially when the drive is mostly full.

---

### Post by xyz on 2006-10-20
I run this command line to change the number of check disk options:```
sudo tune2fs -c 50 /dev/hdx@
```
where 50 means it will check disk at the 50th boot. If you want 10, just change 50 to 10.

---

### Post by anaconda on 2006-10-20
> **mssever said:**
> Temp files are in /tmp, which gets cleaned during every reboot.

What about the installation files downloaded using apt or synaptic? They can also take lots of space.. 

I dont think they are in /tmp

---

### Post by xyz on 2006-10-20
You should find some in /var/cache/apt

---

