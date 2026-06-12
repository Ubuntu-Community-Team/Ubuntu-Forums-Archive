---
title: "[SOLVED] How should I partition my hard drive for dual boot with windows?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by killertofu on 2007-10-12
I am getting ready for the Gutsy release, and I figured I should ask my questions now, any advice will be appreciated greatly.

I have a 180 GB HD, and I'd really like to have one partition for windows, one for linux, and one for shared files between the two.
I want to have videos, pictures...etc on a separate partition so that if I fubar my linux install I'll be able to just reinstall without too much fuss. (I am an uber Linux noob, but the only way to learn is to go for it)

I know I need a swap partition, a windows partition, a linux partition, a shared file partition, and maybe a /home partition. (Do I really need a /home partition? If I mess up linux, could I still do a clean reinstall without a /home partition?)

What size should all these partitions be? And should they be "primary" or "logical"? :confused:

I am so confused, any help will be appreciated.

---

### Post by Kobalt on 2007-10-12
A little reading that might come off handy : 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

(PS: about your /home partition, I always advice using one. It's very simple to do or undo and yet it is very very handy.)

---

### Post by thelocust on 2007-10-12
It's good to have a seperate home partition because thats where all of your setting and what not are stored. Also windows HAS to be on the 1st partition or it wont work you can make all of them primary except for your swap partition. As for sizes it's kind of a personal choice for linux your home partition will be the biggist and I have 20 gigs for my root partition but I think I am using about 2 Gigs of it. Hope this helps keep asking questions from as many different sources as possible until you got that warm and fuzy feeling.

---

### Post by hyper_ch on 2007-10-12
Well the size of the partitions great depend on how you want to use each...


(1) Do you really want a seperate shared file partition? By default you can access ntfs partitions from Linux and with ntfs-3g you even get write access... on the other side you can install the ext2/3 drivers in windows to read/write to the linux partitions... (I'd go for the ext2/3 drivers...)

(2) The swap partition should be about the double size of your ram... so that one's pretty much set and the max. 2 gb (which I assume) won't cause too much troubles...

(3) How much diskspcae do you need now in windows? what do you have installed? Will you install a lot more software?

(4) A seperate home partition is recommended... it is like the c:\documents and settings folder on windows... only that it's more advanced and that's very, very simpley to put on a seperate partition...

According to that you'd get about this:

2 Gb for SWAP
abou 10 GB from / (root)

and then you still have 168 GB to divide up between linux and windows...

The windows one needs to be primary (I could be wrong on that). However you can only have 4 primary partitions... with the above scheme you'd use all of them.

However I'd create the windows and swap partition as primary... then create an extended and have to linux root and home folder as logical partitions in there.

---

### Post by killertofu on 2007-10-12
> **Kobalt said:**
> A little reading that might come off handy : 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

(PS: about your /home partition, I always advice using one. It's very simple to do or undo and yet it is very very handy.)

Thanks, I'll use a /home partition for sure. :)

> **thelocust said:**
> keep asking questions from as many different sources as possible until you got that warm and fuzy feeling.

Thank you very much. :)

> **hyper_ch said:**
> Well the size of the partitions great depend on how you want to use each...


(1) Do you really want a seperate shared file partition? By default you can access ntfs partitions from Linux and with ntfs-3g you even get write access... on the other side you can install the ext2/3 drivers in windows to read/write to the linux partitions... (I'd go for the ext2/3 drivers...)

(2) The swap partition should be about the double size of your ram... so that one's pretty much set and the max. 2 gb (which I assume) won't cause too much troubles...

(3) How much diskspcae do you need now in windows? what do you have installed? Will you install a lot more software?

(4) A seperate home partition is recommended... it is like the c:\documents and settings folder on windows... only that it's more advanced and that's very, very simpley to put on a seperate partition...

According to that you'd get about this:

2 Gb for SWAP
abou 10 GB from / (root)

and then you still have 168 GB to divide up between linux and windows...

The windows one needs to be primary (I could be wrong on that). However you can only have 4 primary partitions... with the above scheme you'd use all of them.

However I'd create the windows and swap partition as primary... then create an extended and have to linux root and home folder as logical partitions in there.

1. I wanted to have windows separate from my personal files, so that if Windows is mean to me I can just reinstall it, and I won't lose my precious stuff, lol. However...I do plan to use Linux full time, since I hate Windows. I'm just keeping Windows around until I'm damn sure I can live without it. So, maybe my files would be safe on the same partition as Windows? What do you think?

2. I have 1GB of ram, so 2GB swap sounds lovely.

3. My current Windows install takes 13GB. I planned to give it 20GB just be be safe.

4. /home partition sounds awesome.

So, what if I had a Windows partition, a linux partition, a file and documents partition, a swap partition and a /home partition?

Would this work? If so, how much space does the linux partition need?

That would be 5 partitions...and if I can only set 4 as primary...which one should be "logical"?

Thanks again for all the replies, the help is awesome.

---

### Post by Duck2006 on 2007-10-12
> which one should be "logical"?

The linux swap partition.

---

### Post by killertofu on 2007-10-12
> **Duck2006 said:**
> The linux swap partition.

Thanks!

---

### Post by louieb on 2007-10-12
> **killertofu said:**
> 
That would be 5 partitions...and if I can only set 4 as primary...which one should be "logical"?.
Might want to read up a little on partitions. In order to get 5 partitions that you can store data in your actually going to need 6 partitions. (3 primary, 1 extended and 2 logical) The one you didn´t think of is the extended partition.  It serves as a container for logical partitions. And if you have one it counts as a primary partition.   The only partition that absolutely has to be primary  is the one Windows is installed in. Linux does not care if its installed in Primary or Logical partition.   
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")
[Disk partitioning - Wikipedia, the free encyclopedia]("http://en.wikipedia.org/wiki/Partition_%28computing%29")
[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018")

---

### Post by killertofu on 2007-10-12
> **louieb said:**
> Might want to read up a little on partitions. In order to get 5 partitions that you can store data in your actually going to need 6 partitions. (3 primary, 1 extended and 2 logical) The one you didn´t think of is the extended partition.  It serves as a container for logical partitions. And if you have one it counts as a primary partition.   The only partition that absolutely has to be primary  is the one Windows is installed in. Linux does not care if its installed in Primary or Logical partition.   
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")
[Disk partitioning - Wikipedia, the free encyclopedia]("http://en.wikipedia.org/wiki/Partition_%28computing%29")
[HowTo: Partitioning Basics - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?&t=282018")

Ah, thank you very much.
I've been reading a lot about partitioning...but I only succeeded in getting myself more confused.
It's so nice to be able to ask knowledgeable people questions, and to get such awesome answers.

I had no idea about any of this, I am so glad to know. *whew* :)

---

### Post by killertofu on 2007-10-13
Okay, this is what I came up with based on replies and lots of reading:

Partition 1: Windows XP NTFS 20GB Primary 

Partition 2: Documents and files NTFS Primary 118GB

Partition 3: Swap 2gb Primary

Partition 4: Extended Partition

Partition 5: Linux /root ext3 20gb Logical

Partition 6: /home ext3 20gb Logical

Is this correct? Any advice and suggestions would be wonderful. :)

---

### Post by thelocust on 2007-10-14
I would make my /home partition a little bigger. And your /root is going to take up a lot less space than your /home so it doesn't make much since to have them the same size.

---

### Post by strabes on 2007-10-14
> **thelocust said:**
> I would make my /home partition a little bigger. And your /root is going to take up a lot less space than your /home so it doesn't make much since to have them the same size.

Yeah, you absolutely don't need 20gb for your root partition, and if you're not storing files on your /home partition you also don't need 20gb. You could cut both of those in half.

Here's how I have mine set up:
20gb Windows
15gb Linux
2gb Swap
Rest of HD: Data

---

