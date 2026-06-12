---
title: "How do you pick which partition to install on?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-14
Ok, this my first time out with Ubuntu,
I am in the Live CD mode. And I want to install Ubuntu.

I have 2 harddrives that are partition as follows.
Harddrive #1
(C: ) WinXp partition. (Primary)
(D: ) Data partition

Harddrive #2
(G: ) Data Partition (Primary)
(H: ) Data Partition
(I: ) Data Partition
(J: ) Ubuntu for Partition

What I would like to do is to have Ubutnu installed on the partition name Ubuntu. But I do not see how I do this.
All partition are formated with fat32, there is no unalloted space. Or do I have to have unalloted space for it to install?

How do I choose the Ubuntu partition?

---

### Post by skale on 2006-07-14
Ububtu woll not (as far as I know) install on a fat32 partition, as compatible as it is with reading and writing. You have to reformat the ubuntu partition into ext3 format. I do not know how on the live CD, but its worth a try, because on the Alternate CD it is easy. If live does not work, try that. What you will do is erase(or delete) the ubuntu partition, and then create an ext3 partition out of the free space. Be sure to also make an adequate swap partition.

---

### Post by wieman01 on 2006-07-14
First of all you should have your Ubuntu installation on your first/primary HD. Ubuntu comes with its own file system format so Windows won't be able to read or even recognize the partition. When opening the Explorer you won't see the partition at all.

Secondly there a many ways to configure your Linux' file system, but usually this is what I do (using partition magic to create the partitions I need):

1. One primary partition for "/" (root partition) with Linux FS format. ~5 GB.
2. One partition for "/home". Rougly 3 GB in size.
3 One SWAP partition (SWAP FS format) twice the size of your RAM.

Like I've pointed out, all these partition will stay hidden under Windows although Ubuntu will recognize you Windows & data partitions.

---

### Post by skale on 2006-07-14
I have ubuntu on the second partition with no problem.

Also, it might be easier to combine the / and /home partitions, so that there is less guesswork. However, I think I am alone in that regard. With your experience with partitions, it should be fairly easy.

---

### Post by Third Thoughts on 2006-07-15
> **skale said:**
> 
Also, it might be easier to combine the / and /home partitions, so that there is less guesswork. However, I think I am alone in that regard. With your experience with partitions, it should be fairly easy.

There is a definite advantage to keeping them seperate in the long term. If for some reason you ever need to re-install Ubuntu (ie, you screw something up, you want to make a clean upgrade, whatever) if you have a seperate /home and /root partition its a breeze. All your personal files are on your /home partition, so all do you is wipe the / partition and re-install. If they aren't seperate then you have to back everything up, move files around, install, then restore the back up. Much more awkward and much more potential for losing some files in the shuffle.

~Andrew S.

---

### Post by gargoyle on 2006-07-16
Ok, I was able to load Ubuntu after I deleted one of my partitions and created some unalloted space.
During the installation I pointed to my second harddrive where the space was.

It now resides on the last logical drive.

Thanks

---

