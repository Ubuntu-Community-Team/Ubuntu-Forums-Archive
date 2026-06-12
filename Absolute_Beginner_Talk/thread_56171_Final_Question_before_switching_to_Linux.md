---
title: "Final Question before switching to Linux"
date: 2005-08-11
forum: Absolute Beginner Talk
---

### Post by bvilches on 2005-08-11
Well, first let me say that I'm new to Linux, in fact, I haven't even installed Ubuntu yet.

I want to do it but first I have some questions ... I know you guys can help me.

1) I have 2 HD. In one of them i have Xp installed and on the other only files. Both of them are NTFS. I will install Ubuntu on the first one, and the second one should stay the same. I know Linux doesn't get along very well with NTFS, so I'd like to make this second HD ext3 and not lose any info on it (I imagine I'll have to transfer the files to another place). Which is the the best way to do it??

2) On this second HD, many of the files has non english names and uses letters like á, é, ü ... will this be a problem? how can I solve it?


3) I have many (MANY) windows fonts ... will they be good for linux?


Well, I think that's it ... thank you guys in advance!

---

### Post by KingBahamut on 2005-08-11
Simple answers 

1. Let installler take care of it, but yes, youll have to move the data first of course.
2. no, be sure you follow the uby guide [http://ubuntuguide.org](http://ubuntuguide.org) for all the localization stuffs
3. Some may some may not.

---

### Post by aysiu on 2005-08-11
[QUOTE=bvilches]Well, first let me say that I'm new to Linux, in fact, I haven't even installed Ubuntu yet.[/quote] Welcome to Linux. It's a fun place.

> 
1) I have 2 HD. In one of them i have Xp installed and on the other only files. Both of them are NTFS. I will install Ubuntu on the first one, and the second one should stay the same. So, I'm confused as to what you actually want. Are you trying to set up a dual-boot? Or do you want Ubuntu to be on one drive, and your files on another drive?

> 
I know Linux doesn't get along very well with NTFS, so I'd like to make this second HD ext3 and not lose any info on it (I imagine I'll have to transfer the files to another place). Which is the the best way to do it?? It kind of depends on whether you want a dual-boot or not. If you do want a dual-boot, not only can Linux not write to NTFS (it can read NTFS just fine, though), but XP cannot read from or write to ext3.

> 
2) On this second HD, many of the files has non english names and uses letters like á, é, ü ... will this be a problem? how can I solve it? I don't know.

> 
3) I have many (MANY) windows fonts ... will they be good for linux? If you [enable extra repositories](http://ubuntuguide.org/#extrarepositories), you can get Microsoft TT Core Fonts through Synaptic Package Manager.

---

### Post by varunus on 2005-08-11
Here's a step by step guide with pictures on how to partition using the Ubuntu installer:
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

---

### Post by bvilches on 2005-08-11
> So, I'm confused as to what you actually want. Are you trying to set up a dual-boot? Or do you want Ubuntu to be on one drive, and your files on another drive? 

The second one, Ubuntu on one drive, and your files on another drive.


Thanks for replying so fast!!

---

### Post by aysiu on 2005-08-11
[QUOTE=bvilches]The second one, Ubuntu on one drive, and your files on another drive.


Thanks for replying so fast!![/QUOTE] So no XP. Okay. I have some advice, but please wait for others to weigh on in those before taking it (I'm an almost four-month newbie myself).

Before doing anything, back up your files. Do whatever you can to back up all your files--use an MP3 player, burn them to CD or DVD, copy them to floppies, upload them to the internet, borrow a friend's extra hard drive. You may want to back up your settings as well (email/internet--if you use Internet Explorer, Firefox can import your IE settings in Windows; you can then transport those settings to Linux quite easily).

Then, install Ubuntu. Pick the first hard drive for / (root) and swap partitions (swap should be twice your RAM. Then, pick the second hard drive as the /home partition.

That's it.

But are you absolutely sure you want to just go ahead and install Ubuntu. Have you tried the live CD first to see if you like it?

---

### Post by bvilches on 2005-08-11
Thank you for your answer ...

I've seen (and used) ubuntu on a friend's computer, so I know what it's like.

I'm tired of Windows so I want a change.


What I couldn't figure out yet is th files with non english character. I want to install Ubuntu in english and use this files with characters like the ones I mentioned before (á, é, ü, etc ..). I can't find it on the Starter Guide.

---

### Post by varunus on 2005-08-11
Ubuntu uses UTF-8 by default, so you should be able to see all of those characters even if you're using English as the main language.  I just tried making a file called é.txt in my home folder, and had no problems; everything worked and correctly displayed the file that I tried.

---

### Post by bvilches on 2005-08-11
Thank you ...

One last thing: I was thinking on how to move the data in the HD with all the files. I have a little network at my house. So I imagine I could move all this data to the other PC (Win Xp) and once I have Ubuntu installed on mine's I can get my data back using Samba ... is this a good option?

---

### Post by az on 2005-08-11
You chose your keyboard map when you install.  So you can have a french, canadian-french, or english keymap all with the same physical keyboard.  It is your choice.

Yes, you could do that with samba.

---

### Post by bvilches on 2005-08-11
OK, Many, many thanks to all of you guys.

You've anwered all my questions ... now the Linux community can welcome a new member.


Thanks again

---

