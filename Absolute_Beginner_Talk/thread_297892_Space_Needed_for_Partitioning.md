---
title: "Space Needed for Partitioning?"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by mfmbcpman on 2006-11-11
I am going to be installing both XP MCE and Ubuntu on my 80gb hard drive. How much should I allocate to each? I am hopefully going to be using ubuntu primarily and xp for the little things i need it for.

---

### Post by digby on 2006-11-11
It really depends on what all you plan to install on ubuntu.  If you only want the base system and a few other programs, 10 gig is more than sufficient.  If you plan to install other desktops like KDE, that 10 may start to get a little crowded.    If you plan to play games under ubuntu or store music and video files on your ubuntu partitions, you could need significantly more.  Let us know a bit more about how you intend to use it, and we can give you a better idea.

---

### Post by shadowphoenix on 2006-11-11
if u want to make Ubuntu as the primary partition.First u need to decide for what purpose you are using the Ubuntu forum.The minimum requirement for Ubuntu installation would be 5GB.I guess you can have a 60GB for Ubuntu and 20GB for Windows.

---

### Post by mfmbcpman on 2006-11-11
So can you access the same files within both operating systems. Like if I have a txt file in the WIndows partition can i open it in ubuntu?

---

### Post by digby on 2006-11-11
All your windows files will be *readable* from linux.  Linux is capable of reading and writing to FAT32 partitions with no problems.  We have also been able to *read* NTFS for a while.  Not long ago, someone released a new driver called ntfs-3g (I belive) which is supposed to allow error-free writing, but I haven't played with it.

From windows, you will need the ext3 driver to read/write to your linux partitions, but I haven't messed with that either.  Back when I was dual-booting, I had a large FAT32 partition between my two OSes that I would use to store mp3s, documents, etc.

---

### Post by mfmbcpman on 2006-11-12
> **digby said:**
> All your windows files will be *readable* from linux.  Linux is capable of reading and writing to FAT32 partitions with no problems.  We have also been able to *read* NTFS for a while.  Not long ago, someone released a new driver called ntfs-3g (I belive) which is supposed to allow error-free writing, but I haven't played with it.

From windows, you will need the ext3 driver to read/write to your linux partitions, but I haven't messed with that either.  Back when I was dual-booting, I had a large FAT32 partition between my two OSes that I would use to store mp3s, documents, etc.

So would it be better if I just setup both partitions as FAT32 so the space can be used by both OSs?

---

### Post by bigken on 2006-11-12
windows 15 gig ntfs 
ubuntu 10 gig (ext3)
swap twice your ram say 1 gig 
whats left extented 
/home 40gig (ext3)
fat32 14gig 

this just an idea of what you can do ;)

---

### Post by bigken on 2006-11-12
take a look at gparted liveCD  its in my signature ;)

---

### Post by groggyboy on 2006-11-12
> So would it be better if I just setup both partitions as FAT32 so the space can be used by both OSs?

I personally wouldn't set up the linux partition as fat32 - set that up as ext3 - if you are determined to access linux from windows, there are windows drivers available that will let you do that.  i'm not even sure the linux OS will run off fat32.

I use my own computer mainly for music and videos. my hard drive (60gigs):
10gigs - windows (fat32 - formerly ntfs)
8gigs - ubuntu (ext3)
2gigs - linux /home (ext3)
39gigs - shared partition (fat32 - has music, videos, pictures, etc)
1gig - linux swap

in the end, tho, it depends on what you plan on doing with your computer.  have fun, experiment, find what works best for you!

---

### Post by Sef on 2006-11-12
Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

