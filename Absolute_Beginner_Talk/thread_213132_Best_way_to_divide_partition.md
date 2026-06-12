---
title: "Best way to divide partition?"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by qdvubun on 2006-07-10
Hi, I just install ubuntu today after tried out the CD, it look very stable and easy to understand for me. What is the best way to divide a hard drive for Ubuntu?

for example: my window xp I made a partition call temp so all the temps and internet temp files go in there? is it a good idea to do something like that for Ubuntu?

---

### Post by aysiu on 2006-07-10
[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by raldz on 2006-07-10
You could start by separating your root partition and home partion.. GParted is a good partition editor in Linux.. your root parition is "/" and the home partition is "/home", in that way, all your files in the /home partition will be intact in case you want to reinstall Linux..

---

### Post by molly_001 on 2006-07-10
qdvubun --
For the machine in question, do you plan to have Windows XP on the same hard drive?  You mentioned what you do for Windows XP, but it isn't clear whether you plan to put both XP and Ubuntu on a dual-boot set-up.  I'm asking because you might want a shared FAT32 partition accessible to both Windows XP and Ubuntu in read-write permissions.

---

### Post by DigitalXpert on 2006-07-10
Like was said above... DEFINETLY make a seperate partition for /home.  This is where all your settings, docs, etc will go.  Including temporary internet files.

One more recommendation I can give is to not forget to add a swap partition.  Linux doesn't use swap as heavily as windows does but if you have little memory or are doing a ton of stuff it may need some.  If you forget to add a swap partition and you run into this situation linux will probably crap out.  I've never done it myself but I'm sure it can't be good at all.

I have 1 gig or RAM and have my swap set to 2 gigs.  I think the general rule is twice the size of your installed RAM.

---

### Post by qdvubun on 2006-07-10
thanks for the replies, here is the set up I did:

currently have a 100gb drive (master): set for windows XP
partitions are temp, windows, programs, documents, and share

Ubuntu is on a totally different drive 10gb: so Ubuntu all go in this drive. 

The idea of making a /root and /home partition sound good, I will do that incase need to reinstall Ubuntu then still have the documents in /home

so say if I use Partition magic in windows xp to do the partition on the 10gb drive, I would make 3 partitions right? swap, home, and root?

that'll be all for questions :D

---

### Post by DigitalXpert on 2006-07-10
No, its not /root its just / with nothing after it.  /root is something totally differrent.  Its the root user's home folder.  Ubuntu setup would have caught it anyways since you cant have linux with no / in the file system.

So make a / and a /home and a swap.  The swap is special partition type so its not /swap or anything like that.

I'd use the partitioner that ubuntu provides during setup.  Not Partition Magic.  You'll know for sure that it's done correctly if you let Ubuntu do it.

I would, however, use partition magic to shrink the windows partition on the other disk a bit.  Then create a fat32 partition in the remaining space for transferring files between the two OSs.

Also, keep alert when it comes to installing the grub bootloader.  Make sure it goes on the 10GB disk where Ubuntu is going.  Then just select what hard drive to boot from in your motherboard's bios.  If it goes on the windows disk you may loose your windows install.  

I had a setup like you're putting together back before I moved completely over to linux.  It worked great.

---

### Post by raldz on 2006-07-11
No, don't use Partition Magic to create Linux partition, use the built in partition editor of Ubuntu.. basicaly, when you format the partitions that you create it should be mounted as: "/" and "/home" "linux-swap"

---

### Post by qdvubun on 2006-07-11
ok thanks!

---

