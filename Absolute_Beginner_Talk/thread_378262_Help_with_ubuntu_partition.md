---
title: "Help with ubuntu partition"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-03-07
Hi, i have a computer (laptop) with one 50 gig partition adn one 70 gig partition. 
The partition with 50 gig has vista on it, so i wan't to install Ubuntu on the 70 gig partition. 
So here is the question, if i install ubuntu on the 70 gig partition can i still save/browse/use files from that partition with vista. 
PS: i am not sure if it is one hardisk with 2 partitions or 2 hdd: 

And how to you easely find back to your own posts on this forum?

---

### Post by Janzuka on 2007-03-07
I think you can't browse the partition in which vista is installed (at least the partition where xp is installed cannot be browsed). But if it's on two partitions then you should see the one that doesen't include the OS. 

You can easily find your posts by using the advanced search: search for posts with your name.

Correct me if i'm wrong

---

### Post by ajmannen on 2007-03-07
Hmmmm... i need atleast 100 gig for the vista, do you sugest that i make a new partition?

---

### Post by Janzuka on 2007-03-07
Holy ****! I just tried, and the partition where XP is in can be browsed with Edgy. Earlier when i used Dapper i couldn't access it. But the files can't be deleted as far as i know, even if you try it as root.

---

### Post by ajmannen on 2007-03-07
Nice, but can i browse the Ubuntu partition with vista?

---

### Post by Janzuka on 2007-03-07
Of that i'm not sure :( But,however, bear in mind what i only later added to my earlier post: The files cannot be removed from the vista partition with ubuntu as far as i know.

---

### Post by ajmannen on 2007-03-07
)=, i need 100 gig of free space on vista :(

---

### Post by Janzuka on 2007-03-07
Why do you need so much for vista? You know you could use a common partition for both vista and ubuntu. I have an 90-gb-partition for which i use FAT32 as a filesystem. So far i've had no problems with it :) Maybe that could work for you, as well?

---

### Post by ajmannen on 2007-03-07
"FAT32"????
Comon partion, like have both Vista and Ubuntu on the same hdd. but then how do i start ubuntu if it is on the same partition as vista?

---

### Post by chewearn on 2007-03-07
1. Both Vista and XP use NTFS file system; ubuntu should not have any problem reading them.  On the other hand, to write to NTFS, you need NTFS-3G, which is not available in default ubuntu (you need to search around how to install)

2. Previously, there were some problems reported about dual booting Vista and ubuntu; I think these might have since been resolved, though I'm not positive.

2. Why would Vista need 100G?  You mentioned in your first post, you already have Vista in a 50G partition.  Sounds contradicting.

3. You can select in your forum profile, to add a thread you created into your subscription list.

4. Run this from LiveCD and it will tell you how many harddisks you have, how many partitions in each harddisks, and what are their sizes.

```
sudo fdisk -l
```Post the output here, if you are unable to understand it.

---

### Post by Janzuka on 2007-03-07
No,they wouldn't be on the same partition. Here's the plan: 
1)Create one partition that is Ubuntu root (marked "/") 
2)Create Ubuntu home partition (/home)
3) Create swap partition
4) and finally use the rest of the space to create a FAT32 partition for both windows and Linux.

And,of course, one partition for vista, too.
That is how my hard disk is divided into partitions - without vista, of course.

---

### Post by ajmannen on 2007-03-07
I need 100 gig of free space because ï share this computer and the one i share it with NEED vista, and they have a huge CD collection they wan't to transfer to the comp

---

### Post by ajmannen on 2007-03-07
Ok.
Now, how do i make partitions:lolflag:
( i feel like a noob)

---

### Post by buuntuu! on 2007-03-07
> **Janzuka said:**
> Holy ****! I just tried, and the partition where XP is in can be browsed with Edgy. Earlier when i used Dapper i couldn't access it. But the files can't be deleted as far as i know, even if you try it as root.

strange, i use dapper and can access my window$-partition...

however, ajmannen, if you do not want to waste space on a fat32 partition to swap files between vi$ta and ubuntu, consider [fs-driver,]("http://www.fs-driver.org/index.html") which gives windows read-write access to ext2/3 partitions. 
(no idea if it already works with vista though)

gparted will take care of the partitioning for you, it's on the live cd and runs once you hit "install"

EDIT: before doing anything potentially harmful to your system, get some basic information, [psychocat]("http://www.psychocats.net/ubuntu/") has a great site, you'll learn the basics there

---

### Post by ajmannen on 2007-03-07
Aaaaaaaaaaaaaa................
So complicated, so here is what you say i do, make another partition with Gparted (10Gig or is that to ltle)? 
and then use fs-driver to be able to browse the linux partition in windows

---

### Post by buuntuu! on 2007-03-07
not complicated at all, just seems to be! browse the forums and you'll learn in a hurry:)
for an ubuntu install 5 gig are ok, even 3 gig works, but its good to leave some room for programmes you might want to install afterwards. follow the link in my previous post, osychocat is a good guuide to follow (i did some months ago, as a complete noob, and had no problem at all)
it's a penguin's world! :)

---

