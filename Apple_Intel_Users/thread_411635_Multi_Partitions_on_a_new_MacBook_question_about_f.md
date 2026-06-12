---
title: "Multi Partitions on a new MacBook question about format and beryl"
date: 2007-04-17
forum: Apple Intel Users
---

### Post by thenetduck on 2007-04-17
Hey guys, 
   Well I did it, today I got my new shinny MacBook! Its awesome super thin and well pretty dang sweet (Just had to brag ;) sorry) 

Cutting to the chase, I will be dual booting this fancy machine with Ubuntu on the 19th would like to have it set up like this:

MacBook with 80gb HD

40GB - Music, Programming, Storage 
20GB - Ubuntu Parition
20GB - OSX Partition

I would like to do this so I don't have to copy music and photos from one location to another if I am using a different OS. (I do programming and business on my Linux partition and my media stuff on my MacOS) First off, what file extension should I use to do this? and will this even work? I don't want to create a lot of busy work by clicking a lot of times to get information. 

A quick question, I will be using Beryl on my Ubuntu partition and was wondering what would be best, using the 32 bit version of Ubuntu? or the 64 bit? Would the 64 bit give me better performance? or would their be too many bugs in it? Thanks a bunch guys,

 The Net Duck

---

### Post by viciouslime on 2007-04-17
I think by file extension you maybe mean format/partition type? If so then fat32 is the only format that can be reliably read from and written to by both operating systems. Ext2/3 can be accessed through mac os x, but support is still experimental and completely unofficial. In my experience though it works quite well.

I have not tried writing to hfs (mac's format) through ubuntu, it can be done, but i believe this is regarded as experimental still and considerably less reliable than having os x access ext2/3.

---

### Post by viciouslime on 2007-04-17
You might also want to read through this thread: [http://ubuntuforums.org/showthread.php?t=406504]("http://ubuntuforums.org/showthread.php?t=406504")

---

### Post by ronocdh on 2007-04-17
> **viciouslime said:**
> I think by file extension you maybe mean format/partition type? If so then fat32 is the only format that can be reliably read from and written to by both operating systems. Ext2/3 can be accessed through mac os x, but support is still experimental and completely unofficial. In my experience though it works quite well.

I have not tried writing to hfs (mac's format) through ubuntu, it can be done, but i believe this is regarded as experimental still and considerably less reliable than having os x access ext2/3.

I can testify to the stability of the ext2ifs for OS X; I routinely read and write to my Ubuntu partition from OS X, and haven't run into any trouble at all. Of course, sharing with my FAT32 WinXP partition is just as painless, but something about running Linux on FAT32 gnaws at my soul. ;)

---

### Post by ronocdh on 2007-04-17
> **thenetduck said:**
> Hey guys, 
   Well I did it, today I got my new shinny MacBook! Its awesome super thin and well pretty dang sweet (Just had to brag ;) sorry) 

Cutting to the chase, I will be dual booting this fancy machine with Ubuntu on the 19th would like to have it set up like this:

MacBook with 80gb HD

40GB - Music, Programming, Storage 
20GB - Ubuntu Parition
20GB - OSX Partition

I would like to do this so I don't have to copy music and photos from one location to another if I am using a different OS. (I do programming and business on my Linux partition and my media stuff on my MacOS) First off, what file extension should I use to do this? and will this even work? I don't want to create a lot of busy work by clicking a lot of times to get information. 

A quick question, I will be using Beryl on my Ubuntu partition and was wondering what would be best, using the 32 bit version of Ubuntu? or the 64 bit? Would the 64 bit give me better performance? or would their be too many bugs in it? Thanks a bunch guys,

 The Net Duck

Sorry Net Duck, I ignored your later questions. Whether to use the 64-bit version is based on your hardware; the Core2 Duo is a 64-bit architecture and so would benefit from a 64-bit OS, but the Core Duo, while dual core, still needs the x86 (i386) version. I recommend you check out the 64-bit forums for any specific questions you may have; I can say that there are solutions for just about everything, and I love the community there! Look up some posts by Kilz; he has some very helpful scripts in his sig, and there's a great package called Simple64 that gets new users up and running quickly, too.

So know your hardware, and you'll know which OSes you can use. Using the 32-bit Ubuntu on a C2D is totally fine, I did it on my MacBook Pro for a while. You won't be getting the most out of your hardware, though.

---

### Post by thenetduck on 2007-04-17
Ok so it's a core 2 duo processor so I think I will try out the 64 bit this go arround. Even with my normal Linux box (built by mua) I was using the 32 bit because I didn't feel there was a lot of support of 64 bit a couple years ago. I can't wait until Thursday! 

 So I should be able to just use the ext3 just fine for linux/mac?

---

