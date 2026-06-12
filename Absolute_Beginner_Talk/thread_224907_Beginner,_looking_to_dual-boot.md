---
title: "Beginner, looking to dual-boot"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by goossenm on 2006-07-28
Hello,

I plan on using Ubuntu as my primary OS but, for work-related reasons, I also need to use Windows XP. I've explored the options available to me and plan on dual-booting.

I've read enough tutorials that I feel comfortable attempting a dual-boot. I have a 60 GB hard disk I plan on using. I understand I'll have a Windows partition, an Ubuntu partition, and (depending on what tutorial I read) a swap/etc partition. Ideally, I'd also like a partition I can use to keep personal files that, hopefully, can be accessibly by both Windows and Ubuntu. Is this possible?

Does anyone have any advice and/or links for me? If someone knows a tutorial that meets all my needs I'd be forever greatful.

Thanks in advance,
goossenm

---

### Post by OffHand on 2006-07-28
[http://www.pcmech.com/show/os/903/](http://www.pcmech.com/show/os/903/)

This is a nice visualguide (screenshots) and this is how I would set up my partions too. 

One partition for the system, one for the swap and one for home. You can use a FAT 32 partion to exchange files between xp and ubuntu.

---

### Post by Smandola on 2006-07-28
Goossenm,

I just took a desktop that I purchased (Xp pre-installed), and loaded Ubuntu 6.06.  I used the following link.

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

It was very helpful set of instructions.  He was very detailed and for the most part it was pretty simple to understand.

My only problem was that I realized that the back-up copy of Xp wasn't what it should have been.  I was able to take a 200Gb drive and divided it up with 60 for Xp, 15 for Ubuntu, 2 for Swap and the remainder for share between O/S's.  And Yes, I can share the files.  Give it a try, and you may want to ensure that your back-up copy is golden first.

Good Luck.
s.

---

### Post by djsroknrol on 2006-07-28
this is the most popular link on the fourms for dual booting

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by deadgobby on 2006-07-28
If you like a visual one.
video.google.com/videoplay?docid=-6104490811311898236
very good online vid.
Gobby

---

### Post by PaulFXH on 2006-07-28
Hi
I did exactly what you are planning 4 days ago and it went just fine.
Although I did a lot of reading, googling, posting and ruminating beforehand I found this video to be exactly what I needed.

[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

Note that you need to watch it carefully a number of times before you start the install.

Good luck
Paul

---

### Post by goossenm on 2006-07-28
Hello,

Thank you for all your help so far!

I'm about to begin the dual boot process. I plan on following the [guide](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/) linked by Smandola. I'm currently trying to figure out my partitions and how large each will be. I'm quoting a portion of the article (#6, under step #1):

[quote="Matthew J. Miller's HOWTO's"]For my 80 GB hard drive, I used:

* Windows XP: 60 GB
* Ubuntu Linux: 14 GB
* Linux Swap: 1 GB (the rule of thumb is twice as large as your RAM)
* FAT32: 5 GB[/quote]

I'm using a 60 GB hard disk, as previously stated, and since I plan on using Ubuntu as my primary OS assigning the majority of my disk space to XP seems counter-productive. I've seen throughout my readings that the "FAT32" partition can be used for sharing files so I'd probably like a nicely sized partition for that (the majority, if not all, of my personal files should be housed here). I've also read conflicting information about what size a "Linux Swap" partition should be.

I assume everyone has their own personal preferences for what size each partition should be, but as I'm a beginner, I'm hoping I could be given some suggestions as to how big each partition should (probably) be.

Any help is always (and still) appreciated,
goossenm

*Apologies for the long post. I wanted to give as much information as I could but I still feel like I left something out!*

---

### Post by OffHand on 2006-07-29
Actually the best size for swap is 1.5 * amount of physical ram.
Goodluck and let us know if you managed to install it properly.

---

### Post by alan yeates on 2006-07-29
I have some files in Windows which would take many hours to replace, so I bought a second hard drive and backed everything up before starting. However I have now installed Ubuntu several times without problem, and thought that Ubuntu could cope with everything except desktop publishing, but now think of moving that over to Scribus, which is better than it first appears! What I am getting at is that there is no need to worry too much about your split, the only people who are going to use XP after the switch appear to be gamers, though my son gets around even that! So I would always say 50/50, if not more for Ubuntu. XP still haunts me however, had to do a 40 mile round trip to find that there is a bug with printing WMF's in XP SP2, which would be funny if not so tragic. Msoft recommend editing your BIOS, which is not for most users.

---

### Post by kilis on 2006-07-29
the video [http://video.google.com/videoplay?docid=-6104490811311898236&q=Ubuntu](http://video.google.com/videoplay?docid=-6104490811311898236&q=Ubuntu)

---

### Post by Smandola on 2006-07-29
Hi goossenm,

I've seen posts/threads that recommend anywhere from 1.5 to 2 times the size of your RAM be available for swap.  On the installs that I've done, I've never seen more than 100mb of swap used (according to system monitors).  The install that I just completed, I did a 6.06 Desktop install.   I had a partion size of 15Gb for my / (root), where ubuntu resides, and 2Gb swap (I have 1Gb RAM on this box).  I'm not finished loading some of the packages that I want, however, I think that I've used less than 25% of the partion.  Linux code typically isn't a space hog, unlike M$ code.  I had plenty of space to play with, so I made the Win partition larger than it needed to be.  I'm not an expert on what size partion M$ needs.  For my purposes, its likely that this space and code will never be accessed.  Which brings up a really good question... why have dual boot.

Just fyi...I also have a very old 486 with a 4GB drive, and can easily fit 6.06 Dapper on it.  

djsroknrol, thanks for the link, I didn't see that one when I was doing my install.  Looks like a great resource too.

If you haven't watched the video, its worth watching.  Some good humour there too.

Good Luck, and post back if you have additional questions, or to let us know how you made out.
s.

---

### Post by geovino on 2006-07-29
Thanks for the link; [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) 
It looks very good.

I have Win XP on the hda (80gb) and PCLinuxOS on hdb (40gb). I want to partition the hda drive and give Ubuntu 40gb. PCLinuxOS uses Lilo, how can I add Ubuntu to that Lilo bootloader or can I use GRUB to bootload all three?

---

