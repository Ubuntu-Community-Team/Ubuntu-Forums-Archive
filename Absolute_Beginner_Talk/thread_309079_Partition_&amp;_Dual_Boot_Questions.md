---
title: "Partition &amp; Dual Boot Questions"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by gingerj on 2006-11-29
Hi all I've been reading the official Ubuntu book, now that I've finally got the time. 

I'm currently running Win XP on a Laptop, and I've put the live CD in and had a play around. 

I've clicked the install icon on the desktop and proceeded to go through the menu.

But when I got to the bit to install it via a partition (clicked in the manual button) I'm now a bit confused as the screen shot in the book, selects a logical partition. 

But for some reason when doing the partition editing I can only create a extended or primary.

Is it ok to install Ubuntu on a extended partition? I dont want a primary partition as I'm sure my windows partition is a primay one?

Also how do you dual boot, the book literally makes one passing sentence and thats it. ](*,) Which is disappointing as I'm a bit clueless.

---

### Post by rlozano on 2006-11-29
yes, its definitely ok installing ubuntu in the extended partition. for dual booting, if you allow ubuntu to install GRUB in your MBR, it will handle your dual boot concern. once you boot again, you will a menu to select from, which OS you would want to boot.

just a note though, this will replace your current windows MBR, but once you decide to uninstall ubuntu at a later time, it would be easy to fix the MBR back.

hope this helps.

---

### Post by xyz on 2006-11-29
This is a good place to go to:
[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

---

### Post by Sef on 2006-11-29
If you are using the Live CD (i.e. Desktop CD) to install, read [Psychocat]("http://www.psychocats.net/ubuntu/installing")'s site.

---

### Post by CatKiller on 2006-11-29
Partitions as you first create them are either Primary or Extended. [This page]("http://en.wikipedia.org/wiki/Extended_partition") might give you more information.

Basically, you can have four partitions on a disk. One of those partitions can be an Extended partition and contain a large number of logical drives. So to create a logical drive, you'll first need to create an Extended partition to put it in.

I hope that helps.

---

### Post by gingerj on 2006-11-29
Ahh many thanks people for your help I'll have a read through on those links. The only thing that puzzles me is dual booting, I'm not really up to scratch with the apps so it's all kinda foreign to me.

Erm, just to get this straight after the installation is complete I have to install something else? Or do I have to go to an option somewhere? I'm a bit baffled sorry to sound to stupid. If there's a link knocking about somewhere that explains I'll be extremely happy.

It's a shame that the book I purchased completely ignores this subject.

---

### Post by xyz on 2006-11-29
As things are "kinda foreigh to you" as of now, I would humbly suggest you take it one thing at a time...so you won't feel too overwhelmed. There's nothing "scary" about all this but it's just better to go 1 step at a time.
Yes you will want to install more stuff after installation succeeded...like, for instance, codecs for audio/video/streaming or progs YOU would like to use.

Since you're using the Live CD, the link I gave you won't be useful right now. The other links are the ones you want.

I wanted to pass on that link (Illustrated Dual Boot) because it is visual and it might help you "to see" the install process.

Good luck and feel free to come back with more questions!

---

### Post by gn2 on 2006-11-29
Depending on the model of laptop, whether it's still under warranty and your own level of technical confidence and budget, you could replace the hard drive and try Ubuntu out on that? 
Keeping your Windows drive safe from harm for a while.

This is what I did at first. The original Windows HDD is now in a USB enclosure and gets used as additional storage.

---

