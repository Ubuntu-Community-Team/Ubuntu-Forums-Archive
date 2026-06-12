---
title: "Giving Ubuntu a try, got a few questions."
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Wolydarg on 2007-04-20
Hey guys, I've recently become interested in trying out linux as I've reached the point in high school where there's nothing to do. After seeing beryl in ubuntu on my friend's laptop, I thought I'd give this a try. I tried dapper drake out on the LiveCD and wanted to install it. But all those HowTo's and assorted guides online all have different methods of partitioning the drive, claiming ubuntu isn't friendly to files already on the hard drive when it partitions the drive. 

Anyways, most of the HowTo's detail backing up files, defragging the harddrive, partitioning, then setting up grub or something like that and ubuntu should be good to go. Seemed simple enough. Yet at the second step, I'm stuck :confused: 

[IMG]http://img.photobucket.com/albums/v38/Wolydarg/Defrag.jpg[/IMG]

That little verticle line on the right is supposed to be on the left side, and after using DirMs and PerfectDisk, the picture above is the closest I got all my files to the front of the drive. Should I keep defragmenting with Dirms or Perfectdisk in hopes that they'll move that lone piece or is there something you guru's out there know that can help me out?

Thanks plenty.

---

### Post by diatribe on 2007-04-20
I think it shouldnt matter much that that piece is there, just put the ubuntu partition as the end of the drive and you'll be fine

---

### Post by jiminycricket on 2007-04-20
I think Ubuntu only is "bad" with Vista's partitions.  With XP it should be fine (although you do need to use chkdsk /r on your drive before, maybe defragement).  You can also use GParted on the livecd.

But no matter what, make a backup of important files.

---

### Post by rccharles on 2007-04-20
I do not know the specifics of how NTFS works, but I have read the filesystems put data in the middle of the disk so that the read/write arm is always half a platter from the data.  I seems to recall that NTFS puts directory information in the middle of the platter.

If you want to be safe, just create a 30gig partition to the right.

Robert

---

### Post by Wolydarg on 2007-04-22
After screwing everything up (don't worry, lesson learned), I've decided to just do a fresh install on another comp first. So I have a fresh install of XP, and I'm going to dual boot that with Feisty. I get to about here and then a problem happens.

[IMG]http://img204.imageshack.us/img204/4940/screenshotinstallhb1.png[/IMG]

Clicking "Forward" gets me > No root file system is defined.

Please correct this from the partitioning menu.

and then I'm clueless. I'm scared to really experiment on what might be the cause because I'm still lucky that the last time I did that I didn't lose all my music. Anyways, help would be appreciated, thanks.

---

### Post by ofek on 2007-04-22
The partition u want fiesty on should be "/" and not  "/home" like I suspect u thought, better asking than freaking out ;)

---

### Post by Nythain on 2007-04-22
chang sda5 from /home to just /... basically its saying you need a root (/) partition, wich at the moment you dont... /home isnt root... you could make another partition for /home if you want but dont need to, the only two you really need is / and swap

---

### Post by Wolydarg on 2007-04-22
Thanks a ton, guys. If I wasn't so insecure about my manhood I'd kiss you all. Installation went smooth, look forward to being a part of this community.

---

