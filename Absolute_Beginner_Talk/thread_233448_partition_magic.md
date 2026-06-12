---
title: "partition magic"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-08-10
Well, tried to use partition magic to grow my XP partition to no avail
It (partition magic) complained with a 106 (or something) error, stating that it cuoldn't find the first partition (basically it just failed to load because of some configuration I have or a bug)
Any help? I am simply trying to increase the size of my primary XP partition?

---

### Post by Kobalt on 2006-08-10
Are you an Ubuntu user ? 
Why don't you try using a LiveCD and GParted ?

---

### Post by bigken on 2006-08-10
theres a gparted boot disc image you can burn to cdrom great tool ;)

[http://gparted.sourceforge.net/ ]("http://gparted.sourceforge.net/")

---

### Post by carverj on 2006-08-10
Oh sorry guys.
Here is original post

> Hi everyone,
Just wondering if it is possible to increase the size
of my primary ntfs XP partition to fit visual studio.
 So were talking extending the 
first 10 G partition to 15 G, thereby squashing the 
remaining
4 or so reamaining logical Ubuntu partitions from the current size of 30 G
to 25 G.
I tried to do this with the Dapper CD I d/led but 
I couldn't seem to accomplish this task!!?
Which tool will accomplish this?
Thanks team

So the Dapper install partitioner is GParted isn't it or am I getting the tools mixed up?
Has anyone used GParted or another tool to "grow" their primary ntfs partition?
Thanks

---

### Post by aeiah on 2006-08-10
i managed it without problems when using partition magic, so maybe it is a bug. i increased the size of my ntfs after the ntfs write drivers for linux came out properly. have you ran error checking software on your drive or something? maybe the only thing left to do, if you have enough space, is:

create an image of your whole ntfs partition
shrink your other partitions
delete ntfs
create new ntfs from the unallocated space you now have
insert your image

or perhaps simply shrinking your other partitions in one stage, rebooting, and resizing your ntfs afterwards may work. sometimes partitions can be funny things.

---

### Post by carverj on 2006-08-10
Yeah, partition magic alert
```
Init failed error 117
Partition's drive letter cannot be 
identified
``` apears upon runtime.

>  i increased the size of my ntfs after the ntfs write drivers for linux came out properly. 

Nice, how's that working out (easy to install drivers?)

> have you ran error checking software on your drive or something? maybe the only thing left to do, if you have enough space, is:

create an image of your whole ntfs partition
shrink your other partitions
delete ntfs
create new ntfs from the unallocated space you now have
insert your image


error checking?
image? what with ghost?

> or perhaps simply shrinking your other partitions in one stage, rebooting, and resizing your ntfs afterwards may work. sometimes partitions can be funny things.
yeah, will this work anyone?
Thanks

---

### Post by bigken on 2006-08-10
using qtparted you must also defrag your ntfs partions 1st the ghosting
sounds a good shout

---

### Post by steve.horsley on 2006-08-10
My understanding is that gparted can move the end of psrtitions to resize them, but is not able to move the start of partitions. So you could only grow your ntfs into empty space. Making the empty space is going to be the problem. I don't know how you could do that other than tarring up contents of your Linux partition, deleting it, resizing ntfs, creating and formatting a new Linux partition and then restoringfrom the tar file.

I don't know about PM, but I do think that PM has difficulties with ext3 partitions, and occasionally leaves them unreadable.

---

### Post by aeiah on 2006-08-10
> **carverj said:**
> 

Nice, how's that working out (easy to install drivers?)


i just followed the HOWTO on these forums. had a wee mounting problem but was easily sorted by forum searches. never had a problem since :cool: 

> 
error checking?
image? what with ghost?


yea a ghost backup image. and as far as error checking goes, maybe just a standard error check using the built-in winxp one will suffice


as steve stated, it could be that the partition software is struggling to decrease the size of the linux partitions from the start. i have a different setup, and i was decreasing the size of a shared FAT partition to make way for more NTFS. my linux partitions are on my backup drive which is a seperate physical hdd. so i havent had any experience decreasing the size of etx2/3 from the start of the partitions :|

if linux is smaller than your winxp, perhaps creating an image of your linux stuff and wiping those partitions and reapplying them will work out more efficiently, if you go down that route

---

### Post by carverj on 2006-08-10
mmm, it's fine for me to delete the entire Ubuntu section of that drive as my /home partiton is located on my secondary hdd & I'm backed up ready for full Dapper install.
 So can I wipe the Linux stuff altogether(which I am unsure if you can do with GParted) , extend ntfs to 15 G & install Dapper in the one go? or do I need to wipe the logical Breezy partitions a different way.
Really appreciate all the help by the way.
With your help ppl I am impressing my colleagues at uni : )

---

