---
title: "Jumping off the Cliff"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by swoskow on 2007-03-09
OK - I have done my homework, spent many hours reading HOWTO's, The Ubuntu Book, the forums etc etc and now I am ready to take the plunge and set up Ubuntu on my system.  

I have a specific purpose for doing this so I thought I would post to the forum and get some opinions from Newbies and experienced users to see if I am doing this correctly.  First my computer is new and I bought it specifically to set it up as a Linux box (cheapest I could find but it is a Gateway and so far it has been very good to use).  The main purpose for the computer is to be a home network running under Linux.  I read an article on Tom's Hardware (DIY NAS Smackdown Aug 8, 2006 by Bill Meade) on setting up a Raid 5 or NAS using Ubuntu and Samba which I am following.  

The main use of this computer is to download music and video files (lossless- flac or shn - I am the ever dangerous Dead Head so of course I have every show the Grateful Dead ever played auds and SBD all in lossless format - approx 1 Tb of music all free and legal thanks to the foresight and generosity of the GD).  I will use this computer to download and store the files and hopefully be able to access the files from various other Home computers (all running Windows XP).  

In the computer I am using for Ubuntu I have 4 hard drives - 1X 200 GB internal HD (this is the drive that came with the comp and has XP) I will call this drive C since I still think in Windows (hopefully that will change), 1X 500 GB internal (both internal are IDE) call this drive B formatted as NTFS, 1 external Maxtor 1 Tb drive (formatted as NTFS), call this drive E and and an extra WD 400 gb drive (formatted as NTFS), call this drive F.  The computer also has numerous USB and firewire ports.  I would like to be able to dual boot (I need XP for a few tasks such as playing flac, shn or DVD files though I probably could set up Foobar and Media Player Classic on a USB stick).  

I would like to set up Ubuntu (using the alternate CD) on a separate partition on drive C along with Windows and partition the extra space in a way that Windows and Ubuntu can share (Fat 32 seems to be the best way to do this).  The drive B and E I would like to set up as a RAID 5 (3X 500 gb partitions) with drive F as a spare (I am not sure but I think I need a 500 gb for this).  After reading through numerous forums it looks like the best way to do this is set the Raid up under LVM (I planned to keep the boot HD out of LVM).  From my reading it looks to me that I need to avoid Grub and set up Lilo in the root (not the boot section).  OK so far I think I am OK.  

Then I need to set up Samba which looks to be pretty straightforward and my wireless network (supposedly much easier in the recent release (Efty Edge - still can't get used to the funny names).  Now I have one more problem.  I want to be able to access the files from other computers running Windows XP on the Network.  I have read that with the discs formatted as Fat 32 you can read and write from both XP and Ubuntu.  Can you set up Fat 32 on Raid?  I found the Ext 2 Installable File System for Windows that looks like it will allow XP to access the Ext 2 volumes.  But, I am not sure Ext 2 is the best file system for my use?  Thats it ( I hope) - am I asking too much?  Am I getting in over my head?  Is there better ways to do what I want?  

Any comments, help and advice from the community would be very much appreciated.  I am really looking forward to using Ubuntu (I am tired of fighting with Windows) but I want it to work and I do not want to spend every waking hour trying to figure out problems - this is a hobby not my full time job.

---

### Post by tonyr1988 on 2007-03-09
-First, congrats on reading up on things ahead of time! I hope that you'll find these forums are a great resource when you have any problems nd questions (and you're never asking too much).

-Not to complain, but for future reference, you may want to space out lengthy posts a tad. It makes it a tad easier to keep track of where you're reading / responding. :)

I can only answer a few of your questions (I don't use RAID, and I use GRUB instead of LILO), but I hope it at least helps a tad:

-If you're accessing your files from *another* computer on your network, it doesn't matter what the file system is (FAT32, ext3, or anything else). Your other computers will see it as a "smbfs" (Samba FS) and it'll work no matter what the original FS is.

-However, you ARE limited if you're accessing the files from teh *same* computer. There are drivers for ext file systems under Windows (experimental, of course) and drivers for NTFS file systems under Linux (even more experimental, since NTFS is closed-source). FAT32 is not the best file system, but you shouldn't have any problems with Ubuntu + Windows reading/writing it. Note, however, that FAT32 does have limitations (like a 4GB max file size).

-So...if you're using Ubuntu primarily (and Windows occassionally), I'd say go with ext2 or ext3. If you're going to be rarely using Ubuntu (hopefully that'll change ;)), then NTFS or FAT32.

-You mention that you need Windows to "play FLAC, SHN, or DVD files". Just to let you know, Ubuntu can play FLAC files perfectly (from my experience), and from a quick search (you may want to look into it more), it can do SHN files as well. You also shouldn't have a problem playing video codecs either - you may have to install a few things to get those working, but you should be up and running without too much effort. Not to say you definitely shouldn't have Windows anymore, but if that's all you need to do, you may want to consider Ubuntu full-time (just a thought :D).

-You're certainly not in over your head. To be honest, you may have a few problems getting everything up and running - I'm not sure how easy it is, for example, to set up RAIDs. But once you get it all going, it's tough to look back. ;)

---

### Post by Crooksey on 2007-03-09
I think you think the task is bigger than it actually is...

Basically you need to dual boot ubuntu and XP, on ubuntu just use the standard EXT3 filesystem.

Then setup samba and the folders that are made public on ubuntu, need to have read and write acsess enabled (basic samba configuration).

Is your media going to be stored on the Ubuntu partitions or the NTFS partitions, why not just setup a FTP server for your LAN ?

---

### Post by swoskow on 2007-03-09
Thank you so much for the quick reply - one of the best features of Ubuntu is the community.  I can ask questions and not have people make me feel like I am an idiot.  I will space the post.  

tonyr1988 - glad to hear that I can play flac and shn's - I have spent so much time reading about installing that I have not read much about using it.  I may never need Windows again, wouldn't that be nice!  

Crooksey - thank you for the advice.  Can you point me somewhere to read about setting up ftp on LAN?  If not I can search - no problem.

Again thank you both for the help and advice.

---

### Post by swoskow on 2007-03-09
> **Crooksey said:**
> I think you think the task is bigger than it actually is...

Is your media going to be stored on the Ubuntu partitions or the NTFS partitions, why not just setup a FTP server for your LAN ?

I was plannig on storing it on the Ubuntu partitions (in the Raid).

It looks like setting up FTP server is simple (I love simple :) ) ([http://www.ubuntuforums.org/showthread.php?t=378476&highlight=FTP+server](http://www.ubuntuforums.org/showthread.php?t=378476&highlight=FTP+server))  I'll try that.

Thanks again

---

### Post by Kateikyoushi on 2007-03-09
After seeing your post I also thought about doing what the title suggests, please format your posts to make them readable especially longer ones.

I wouldn't recommend fat for raid, rather use ext and the ext windows driver.

---

### Post by nik on 2007-03-09
Welcome :)

Seems like you're getting your answers. Noce to see someone doing some research instead of posting "It no work!!! Help!!!" (hope nobody gets offended :)

I just have one advice. Forget about windows. Unless you play games, or have a very specific win only program you just have to use, you're better of with linux only. There will be a few problems (mainly do to lack of hardware manufacturers ignoring linux) but you'll solve them quickly, especially if you have no choise... (i.e. no windows) :)

Good luck :)

---

### Post by swoskow on 2007-03-09
> **Kateikyoushi said:**
> After seeing your post I also thought about doing what the title suggests, please format your posts to make them readable especially longer ones.



I hope that helps - I could not find how you change the line spacing.

---

### Post by swoskow on 2007-03-09
> **nik said:**
> Welcome :)

Seems like you're getting your answers. Noce to see someone doing some research instead of posting "It no work!!! Help!!!" (hope nobody gets offended :)

I just have one advice. Forget about windows. Unless you play games, or have a very specific win only program you just have to use, you're better of with linux only. There will be a few problems (mainly do to lack of hardware manufacturers ignoring linux) but you'll solve them quickly, especially if you have no choise... (i.e. no windows) :)

Good luck :)

So far the posts have been very helpful - the fact that I have not received many reply s tells me I must be on the right track.

Now that I know I can play my music files and videos on Ubuntu, you may be right and I can say bye bye to Mr Gates.

---

