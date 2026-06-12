---
title: "Size on Disk + Resize partitions"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by DiscoKiller on 2008-02-13
Hi all, 

Can anyone tell me roughly how big the standard install of ubuntu is at the moment? I have a partitioned disk in my laptop at the moment running windows but, as you might expect, I want rid of it (windows not my laptop!). The partition is roughly 5 gig, I used it to put the windows install on and used the rest of the admittedly small 40gig hd for data I wanna keep in a different partition. I`ve bought (yet am waiting to receive) a 250 gb hard drive so once i have that all my data will be kept there and the 40 gig drive will be for ubuntu, I just wanted to see if I could get away with setting up ubuntu before I get the new hard drive without having to back all my stuff up on dvd. 

Furthermore, once I have the new drive i`ll want to resize the partition i would be installing ubuntu to(the original 5gig partition). Is it possible to resize the '/root' partition once it is installed? i seem to remember being able to resize partitions with gparted, but cant remember whether it will have any implications on the main /root filesystem. I know for a fact that this would hump windows as it seems to save bits of files in a totally random arrangement, but it was my understanding that linux has a more linear...or...sensible approach to storing data which would allow for an addition/reduction to/in partition space without chomping huge lumps out of the installed programs...

anyway, my essay is over. If anyone can help me out then i`d be most grateful!

Cheers

DK

---

### Post by Crooksey on 2008-02-13
You could install ubuntu on the 5GB partition, and use it as /, then when your new HDD comes you could further partition, to allow more space for such mounts as /usr, /home and /tmp.

---

### Post by staticvoid on 2008-02-13
What you want is a gParted liveCD, you can resize the Ext3 and NTFS filesystems you were talking about. Its a 50 MB ISO download that you burn to a disc just like you would a livecd.

Ubuntu can install on 5 gb, that is enough space, you may want to try xubuntu to start with if you have slow hardware and low space and memory.

for gparted go here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

have at it! BE CAREFUL  ;) partitioning is messy

sv

---

### Post by staticvoid on 2008-02-13
oh and by the way, gparted liveCD works, i just resized my linux-swap partition and streched out my /

:)

i think swap has to be within extended partition.. which is Logical, the partion... rather then primary ;)

---

### Post by Crooksey on 2008-02-13
Swap can be a primary partition.

---

