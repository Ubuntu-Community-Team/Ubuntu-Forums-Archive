---
title: "Can I back up Ubuntu?"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-09-04
Hi! :) 

I was wondering if it is possible to do a backup of the entire OS complete with the installed programs, settings etc.? :-k  I have got my Dapper working quite well now, and if something goes wrong I don't really want to have to do it all over again.  I realize this is probably asking too much but just thought I would ask.  

Russty.

---

### Post by hopstah on 2006-09-04
sure, just ```
sudo rsync -aS
``` your root folder to a backup folder (or drive) and then if something gets screwed up, boot into the livecd, mount the drives, and do the reverse operation.

---

### Post by Russty of Oz on 2006-09-05
Wow!  Is it really that easy?  Will that save all the things I have already set up?  If so, that sounds great, I will do that.

Thanks.

Russty.

---

### Post by hopstah on 2006-09-05
yeah, rsync will preserve file permissions and everything.  i actually have two copies of my system on a backup hard drive waiting for use when i inevitably screw something up.

if you have any other mounted partitions though, like a music hard drive or videos or something, then there is a switch for rsync that will tell it only to back up the current partition and not back up things on mounted partitions.

---

### Post by Russty of Oz on 2006-09-10
> **hopstah said:**
> sure, just ```
sudo rsync -aS
``` your root folder to a backup folder (or drive) and then if something gets screwed up, boot into the livecd, mount the drives, and do the reverse operation.

I just tried this, but got  **error (code 1)**

I want to do a full backup of my Ubuntu system, is there another way, maybe to save it to a dvd?

Russty.

---

### Post by clarkth on 2006-09-10
I use Acronis True Image (boot off the disk and select the partition to make an image of).  Works great, I've had to restore from an image before and it works just like it does in windows.

---

### Post by Russty of Oz on 2006-09-10
The acronis true image looks good, they don't say anything about it working with Linux, but I will take you word for it. I was hoping for something that was designed for Linux, and hopefully free.  I know I am a Scrooge.

---

### Post by Russty of Oz on 2006-09-11
I have noticed some things in Synaptic with the names backup manager and backuppc, I was wondering if these are any good for doing a full backup of my Ubuntu OS so that I can install it, as-it-is, on my other computer and also to reinstall should this one crash?

Russty.

---

### Post by pacut on 2006-09-11
Well...I have been using ghost4Linux, when i used to use Mandriva. I have moved all my stuff under Ubuntu now and am happy to see that the program works fine even here (at the end Linux is Linux!).
It is an easy program that runs on a CD. 
I personally recommend it!
Ciao
paolo

---

### Post by Russty of Oz on 2006-09-11
> **pacut said:**
> Well...I have been using ghost4Linux, when i used to use Mandriva. I have moved all my stuff under Ubuntu now and am happy to see that the program works fine even here (at the end Linux is Linux!).
It is an easy program that runs on a CD. 
I personally recommend it!
Ciao
paolo

Thanks, I will have a look at that.

Russty

---

### Post by clarkth on 2006-09-11
> **Russty of Oz said:**
> The acronis true image looks good, they don't say anything about it working with Linux, but I will take you word for it. I was hoping for something that was designed for Linux, and hopefully free.  I know I am a Scrooge.

Unfortunately acronis is not free, but it works well with any partition (since I use it for other windows computers at home, i have the disk).  The system restore disk will boot linux with the true image program running.  From there you can back up, restore, or verify any partition or image that you have made.

---

