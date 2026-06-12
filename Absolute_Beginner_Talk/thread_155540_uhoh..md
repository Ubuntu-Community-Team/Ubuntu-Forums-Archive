---
title: "uhoh."
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by nerdman on 2006-04-05
Not sure where to post this horrible helpme post.

First of all, thank god for Knoppix. Because its the only thing I have running right now, my computer is falling apart.

Here WAS my system, as of last night.

Primary Master: 80GB hdd, FAT32 (Windows XP), FAT32 (Shared storage) NTFS (Windows only storage).
Primary Slave: 21GB gdd, with whatever format Ubuntu makes its partitions. I have Ubuntu this whole drive.

ONE of these harddrives has gone bad- GRUB gives me "Error 21" on boot.
I take out the secondary. GRUB gives the same error.
I take out the primary and replace the secondary. Either I need to play with my BIOS, or there is no boot record on the secondary.

Windows had been locking up and crashing and whatnot, so I have to assume the 80GB has gone bad. (Also, windows doesn't even acknowledge any partitions on the secondary-- why would its failure cause problems with Windows?)

so... >< What do I do?

How can I possibly recover some of the data on my big storage partitions?

Do I have to format my Ubuntu drive, or is there some way I'll be able to save my settings, etc. Also, if I make the Ubuntu drive the new primary, won't my fstab be fubar'd?

I have a Knoppix live CD (Which I'm running now). Are there any data recovery utilities somewhere on here?

I have a DVD burner on a computer in the living room, connected via ethernet. Am I going to have to surgically install the harddrive and attempt data recovery, or is there a way to maybe configure samba on Knoppix?

bleh. I gotta go to school, I'm east coast and an hour late. Hope you guys can help.

---

### Post by towsonu2003 on 2006-04-05
[QUOTE=nerdman]
ONE of these harddrives has gone bad- GRUB gives me "Error 21" on boot.
I take out the secondary. GRUB gives the same error.
I take out the primary and replace the secondary. Either I need to play with my BIOS, or there is no boot record on the secondary.
[/quote]
There is some info on this 21 thing here and in its replies: [http://lists.debian.org/debian-user/2005/02/msg00415.html](http://lists.debian.org/debian-user/2005/02/msg00415.html) maybe helpful? a good advice it gives is to check the cables. 
[QUOTE=nerdman]
windows doesn't even acknowledge any partitions on the secondary[/quote] windows won't see ubuntu's partitions, that's normal... 
[QUOTE=nerdman]
so... >< What do I do?[/quote]
I would try to change the places of the secondary and primary and try to restore the grub using ubuntu's live cd or similar: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows) and yes, this will bork your fstab. but you can always adjust the partition names in fstab -just a text file- (bf booting to your ubuntu) using a live cd. Check out how knoppix mounts your primary and secondary (/dev/hda? /dev/hdb? /dev/hdd? etc) after you swapped them. you'll be editing fstab so anything that pointed to the primary (/dev/blabla) will now point to the secondary and so on... mount points (/media/blabla) and everything else will stay the same. back a file up before editing it of course... 

[QUOTE=nerdman]
I have a DVD burner on a computer in the living room, connected via ethernet. Am I going to have to surgically install the harddrive and attempt data recovery, or is there a way to maybe configure samba on Knoppix?[/quote]
that sounds like a good and easy idea, if recovering grub doesn't work. you could attach the drive and boot the pc with knoppix/ubuntu livecd and back up to dvd. I doubt knoppix can see your hard drive if it's gone bad though... 
[QUOTE=nerdman]
bleh. I gotta go to school[/QUOTE]school sucks.

---

### Post by nerdman on 2006-04-05
Okay, been working with it...

Ironically, I find I like KDE much better than Gnome. Haven't played with the terminal any yet, but if its the same then I think I'll be a switcher. I can't see why it wouldn't be.

its weird, Knoppix is picking up all three partitions on the master harddrive... The cables being checked and cleared,  I really have no idea what's wrong with it.

Did you guys know Knoppix comes with XMMS already running?
Yeah, all my MP3s are playing fine. With only my primary harddrive in... it seems to be fine.

Now I just gotta figure out how to burn CDs / DVDs in Knoppix... I have like 30Gb of Anime and random movies on here that needs backed up. Heh.

What I'd love to have is a network share tutorial in KDE or just terminal. because I'm not exactly allowed to do surgery on the comp with the DVD burner unless its broken. Selfish punks won't share in my downtime =P

and if I could get WINE to run WoW, I'd drop windows in a heartbeat. (This is cue for a link to information on the subject) ^^;

---

### Post by towsonu2003 on 2006-04-05
did you try swapping primary with secondary and recovering grub (and tweaking fstab accordingly)?

---

### Post by nerdman on 2006-04-05
I was wrong... Error 21 is comming up because my Ubuntu drive is dead. checked cables, Knoppix supports my conclusion- the drive with my GRUB setup is now bad. GRUB can't load, so windows can't. Now, how do I revert GRUB, since my intention is no longer to maintain my Ubuntu partition? Also, I cannot reinstall windows, I lack a disc.


EDIT: Yeah, all this stuff pertains to reconfiguring GRUB. How can I get a working windows-only MBR put on, just until I can get new harddrives (This 80 is too full as it is)

---

