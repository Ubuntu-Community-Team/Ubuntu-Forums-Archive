---
title: "paritioning problems with 7.10..help appreciated thanks!"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by littleasian on 2007-11-01
hey guys.

i just downloaded ubuntu 7.10 and popped it in my lapptop to see if it would work.  to my surprise, everything was working well, except no sound.

now when i went to click install, i ran into a little problem.  i have a 200 gb hd thats split up into 3 partitions already:  1 for vista install/progrmas, 1 for music/documents, and 1 for pics/videos.  There is 15 gb free space.

However, the hd when it showed up in thhe paritioner was like this:

/hda1:  music/docs
/hda2:  videos/pics
/unallocated space
/hda3:  vista install/programs.

So my free space is in the middle of teh hd...shoudlnt be a problem right?  but Im having trouble figuring out how to partition it.  I clicked manual partition, than highlighted the unallocated space.  Ubuntu says i need to create the "/" partition, the swap partition, as well as the /home partition.  But the partitioner makes the process seem not clear:  when i went to create the "/" partition,  i highlighted the space and typed in 3000 (for a space of 3 gb) and clicked ok.  Then it showed a partition that was /ext3 that was 3 gb, but the rest of the 12 gb bbecome "unpartitionable" or something, and I can't split it up to create the swap or the /home partition.  So i exited the partition and now I am seeking help!  

comp specs:
hp dv6500t
intel core 2 duo t7300 @ 2.0 ghz
2 gb ram
200 gb hd
nvidia geforce 8400M GS

Can somebody help me with this?  thakns! 

btw.  during the live cd boot, i noticed that there was no sound.  Is it because i need to install dedicated drivers or something?

---

### Post by Sef on 2007-11-01
You need to make that partition a logical partition and not a primary partition.   You can have only 4 primary partitions, but as many logical partitions as you want.   I would make the root partition bigger than 3 gb.  More like 5 - 6 gb, so there is enough room for the os.

---

### Post by littleasian on 2007-11-01
wait so are you saying my windows vista install (c), my music/docs (d), and my videos/pics (e) are all set as primary partitions?  And so now when I go to create the / partition, after assigning it as a primary one it won't let me create anymore?

So if i make the / partition a logical partition, as well as the swap and /home partition logical partitions, it will partition correctly?  Will creating these 3 partitions are logical partitions rather than primary partitions make a different in usability?  Like, will it mess up an install?

Judging by my comp's specs, what would be the ideal way to partition the 3 partitions in terms of size?  I will be using my music/docs through the already existing /hda1, /hda2, and /hda3 partitions due to gutsy's ability to read/write ntfs....

thanks! (for the quick reply, and for the help :)

---

### Post by littleasian on 2007-11-01
can anyone answer my questiosn??  pleasee??

---

