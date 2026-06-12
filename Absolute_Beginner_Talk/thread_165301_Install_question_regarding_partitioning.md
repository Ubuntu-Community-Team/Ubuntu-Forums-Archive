---
title: "Install question regarding partitioning"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by fenderliekomg on 2006-04-24
Hello all!

I've recently discovered Ubuntu and I downloaded the live CD, ran it, and WOW! :-D I am SO impressed!  This OS is amazing!  I've taken a look at the forums, and the community and its people seem to be so knowledgable and friendly.

I've decided to install it on my computer as a dual-boot with Windows XP.  I'm downloading the install ISO right now, but I have a question regarding partitioning.  Ha, and I thought I was a power user.  Well, maybe I was when it came to XP...

Forgive my ignorance and my lack of an ability to be able to use the search function on the forums.  What the heck is swap partitions and all of that stuff?  I've got a 120GB internal HD which is both large enough and fast enough to use for Ubuntu, and I've also got a 200GB external firewire HD which I will keep all of my photos and music (woohoo to open-source!  FLAC and OGG files only).  I figure it's best to use the internal drive for the installation.

My question is: how much space should I use for the Ubuntu partition?  This is a family computer, and I want to be able to boot up into Ubuntu for myself only.  I have all of my files stored on an external drive.  I do not need much space, but I'd like the ability to be able to download a large torrent every now and then.  How much should I set the swap at?  I heard that if computers have a bunch of memory, they don't need a heck of a lot.  I'm running at 512MB RAM right now, but I just bought 2 more 512MB sticks so I'll be running on more than enough.

Thanks to anyone for any information, and I hope to be cruising around the forums a lot more, soon!  You've got a great OS and I hope to be using it for as long as I can!  (Ooo the download is at 31%!  Can't wait!  211Ko/s - the server's so fast!)

---

### Post by OffHand on 2006-04-24
Ubuntu needs at least 3 GB for the operating system. 5 GB is better, 10 GB even more. SWAP is a bit like RAM but it uses your HD. I think 1024MB (or 1 GB) will be enough. I would advise you to make a seperate home partition so it will be easier to update/upgrade. This is the partion where all your files and settings go.

Ok so maybe something like:
5 GB - System
10 GB Home
1 GB Swap

---

### Post by fenderliekomg on 2006-04-24
Okay, that sounds decent.

Now I'm a bit confused as to the actuall partitioning.

I booted up with the install CD, and I was at the partition editor thing, and I selected manual adjusment, blah blah blah, but I didn't know where to go from there so I stopped and booted up in XP and here I am.

How do I go about creating a partition for Ubuntu?

I saw three selections.  One was my 120GB HD, then it had a dark smily face that again showed my hard drive and said 120GB blah blah blah, and then below it was something that said EMPTY SPACE.  I know that's what I want, but it was only 8.2MB in size.  Can someone guide me through it or point me towards a website that'll explain to me what I want to do to make a 5GB system, 10GB home, and 1GB swap?

---

### Post by jazzyt on 2006-04-24
[QUOTE=fenderliekomg]Okay, that sounds decent.

Now I'm a bit confused as to the actuall partitioning.

I booted up with the install CD, and I was at the partition editor thing, and I selected manual adjusment, blah blah blah, but I didn't know where to go from there so I stopped and booted up in XP and here I am.

How do I go about creating a partition for Ubuntu?

I saw three selections.  One was my 120GB HD, then it had a dark smily face that again showed my hard drive and said 120GB blah blah blah, and then below it was something that said EMPTY SPACE.  I know that's what I want, but it was only 8.2MB in size.  Can someone guide me through it or point me towards a website that'll explain to me what I want to do to make a 5GB system, 10GB home, and 1GB swap?[/QUOTE]

Is your whole drive (the 120GB internal) one Windows partition?

---

