---
title: "FTP/HTTP network install via floppy."
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by Martin_C on 2005-09-27
Hi there. I wasn't sure where to post this...but anyway... The only other linux distribution I ever used was Suse (back when it was free), because it had a full floppy network install. You just download and write the floppy image to a disk, boot it up, and it detects your network card, and starts a full network install...you didn't even have to pre-partition anything...it did everything for you. I have an old Thinkpad 240 with an orinoco I wanted to turn into a wardriving ubuntu rig, but it is unable to boot from a CD-ROM, it can only boot from floppy. I've read the wiki's, other posts, etc...and the explanations were numerous, confusing, and a bit too complicated for me. Is there any way that a full floppy network install image be available for breezy? That would make my life and other's lives so much easier. For those of you who remember how easy this was with Suse, you'll know what I'm talking about. All you needed was a floppy disk and a network connection, and you were ready to do a full install on any machine. The only way I've been able to get ubuntu on this laptop was to use one of those hdd to laptop hdd adapters and install it on my desktop and transfer it to my laptop...unfortunately, all the networking stuff is detected during the first part of the installation, so I'm unable to get networking stuff to be detected and I'm not experienced enough to configure this stuff on my own. I hope a develper reads this, considers it, and the option is available soon. Thanks.

---

### Post by philipacamaniac on 2005-09-27
You can't do it with 1 floppy these days - the Linux kernel is too large. Apparently, it takes 5 floppies. Here is a thread that provides the floppy images. I'm actually about to try this myself for a laptop sans a working CDROM.

[http://www.ubuntuforums.org/showthread.php?t=29555](http://www.ubuntuforums.org/showthread.php?t=29555)

---

### Post by Martin_C on 2005-09-27
Thanks for the reply. That post addresses the exact same issue I was having. I'm going to try it tonight. As far as I remember, the suse network boot disk didn't have a full kernel. It just detected your network card and harddrive and you type in the ftp or http source and it downloads the appropriate files to start the installation...it did it all on-the-fly. This was only a few years ago??? Suse 8.0 with KDE if i remember correctly...man that was nice. But thanks again for the link.

---

### Post by Martin_C on 2005-09-27
Worked flawlessly! Thanks for the link! Everything installed perfecty via wireless connection...funny thing is...i don't have a wireless network...I have no idea who's wireless I was leeching off of...but it's a fast one! LMAO :D

---

### Post by n0manarmy on 2006-02-10
I've just started messing with this entire setup provided by this thread and I've got a couple questions.

First off, my laptop. I've got an external floppy and no CD-Rom so i have to use a floppy option, no other choice.

When i use the current floppy setup i can only get 5.04, i can't get breezy (5.10)

Is there a way to redirect the mirror selection to download the latest version of ubuntu instead of 5.04? 

Follow up question, how would i redirect the mirror if i wanted to install Kubuntu instead of ubuntu, kde would be better than gnome (for my preference.)

---

