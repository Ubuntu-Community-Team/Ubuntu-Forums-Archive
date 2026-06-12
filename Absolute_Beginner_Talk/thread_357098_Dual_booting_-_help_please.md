---
title: "Dual booting - help please"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2007-02-09
I got my Dapper discs a while back.  I want to install it on my pc, along with the Windows 2000 already on it.  But my pc only has 128MB of RAM, and to run the live disc then install from it I need 256MB...

Luckily, I also have a set of Breezy discs.  Unfortunately, my brain is not working.  Can someone tell me in NICE EASY LANGUAGE how to do the dual installation... or maybe give me a link to an idiot's guide tro dual installing?  Thanks!

---

### Post by chuckyp on 2007-02-09
Okay the first thing you would need to do is resize your partition for Windows 2000.  Basically there are a number of tools you can use to do this partition magic etc...  You just need to make some free space available for the ubuntu system.  Once you have that accomplished the dapper install will take care of the rest if you tell it to install to free space.

I would recommend defragging your Windows 2000 drive prior to resizing it.

---

### Post by gr0kzer0 on 2007-02-09
My Windows 2000 is currently on a 10GB partition.  There's a 9GB partition left (conveniently in FAT format).  Also, I won't be installing Dapper - it's gonna be Breezy (due to lack of RAM).  Will this make a difference?  Oh, and where can I get Partition Magic or whatever from?

---

### Post by xpod on 2007-02-09
This place will help if your having to use an alternate cd

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

EDIT:Xubuntu would probably be better too

---

### Post by pay on 2007-02-09
Theres the alternate installation disc on anyone of the Ubuntu mirrors that will allow you to install a version of Ubuntu with less than 256mb of ram.
EDIT: It seems everytime I have posted today, someones posted the same thing as me 2 seconds before I do :P

---

### Post by timlewis242 on 2007-02-09
Typically the way to dual boot used to be that you would install windows first (which you already have) and then using a tool like Partition Magic or some other program (you'll have to search for it or one like it) you create a new partition to place the linux on. You may be able to use Windows drive manager to create the partition, I don't recall.

Most newer linux distros will now do the partition for you though. I don't know about the one you are using but the only way to find out is to begin the install with the linux cd and see if it asks you to create partitions from your free space. If you have one of those distros, you won't need to partition it yourself, the linux cd will do it for you. If you get an error, you'll have to create the partition yourself and then the linux cd will format it to the correct filing system.

---

### Post by gr0kzer0 on 2007-02-09
Thanks Pay, thanks Tim... and everyone else who's been so helpful and so[I]quick[I] in getting back to me.

One more thing, Pay... if you don't mind giving a little more help to a lazy know-nothing... could you possibly post a link to one of the mirrors that I can get the Install CD from?

---

### Post by pay on 2007-02-09
Pick a mirror from [here.](http://www.ubuntu.com/products/GetUbuntu/download#currentrelease) The torrent can be found [here](http://releases.ubuntu.com/6.10/ubuntu-6.10-alternate-i386.iso.torrent).

---

