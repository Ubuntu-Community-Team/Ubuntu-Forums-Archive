---
title: "[SOLVED] GParted recommendations"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Muad Dib on 2007-11-09
Hi,
I've tried to install Gutsy and got stumped during partitioning.  My entire drive is devoted to XP right now.  I want a dual system because my company uses some proprietary software that may not work with Linux.  If I take the plunge and go all out Linux only to find that I can't use the company website, I'm totally crippled until I reinstall XP.  So, I've read some many threads and guides and it sounds like GParted is the way to go.  I'm still nervous, so I would like some advice and reassurance before I move forward.

It is my understanding that these are the following steps I should follow:

[LIST=1]
[*]Disk Cleanup
[*]Disk Defrag (twice)
[*]3. Run GParted
[*]4. Create partitions XP(NTFS), Ubuntu(Ext3), FAT32 (or FS Drive) & home
[*]Run recover CD stemrescue
[*]Install Ubuntu
[*]After becomming familiar with Linux, trash Windows and have a happier life
[/LIST]

Am I missing anything or doing something unnecessary?  I'm nervous, but excited.  Please offer your wisdom and/or experiences to help me through this.  Thanks for any advice.

---

### Post by Dr Small on 2007-11-09
You don't have to setup partitions, Ubuntu automatically does that when installing. You can select Use Entire Disc, or Split the Drive, of which you will want in your case.

[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Dr Small

---

### Post by Pumalite on 2007-11-09
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by celticbhoy on 2007-11-09
Would I be right in saying that the FAT32 is for a shared data partition?

---

### Post by Muad Dib on 2007-11-09
Yes, the FAT32 or FS Drive is a shared partition.

---

### Post by celticbhoy on 2007-11-09
Is this something you need, or have you just seen in other postings

---

### Post by Muad Dib on 2007-11-09
In response to Dr. Small... I am unable to split the disk in the Ubuntu installation process.  Based on what I'm reading from how-to guides and other threads, because my XP partition is the entire disk, the installation will not allow for a guided resize or a manual one.  That's why I'm downloading GParted.  It's the only way I can see to accomplish what I'm after without reformatting XP.  Am I on the right track or should I be taking another path?  Thanks for your reply.

---

### Post by Muad Dib on 2007-11-09
In response to Celticbhoy... according to many how-tos and threads, it appears that a shared partition is desirable and beneficial for both OS's to share common files.  Thanks for your reply.

---

### Post by celticbhoy on 2007-11-09
Its just from what I have read, Gutsy is now adept at reading and writing windows drives, so the need for a shared drive is reduced. I am on a dual boot with Vista, and the installation should go fine. From what I have read in other posts it seems that the safest way is to re-size the windows drive using windows software (partition magic or similler) then let the Ubuntu installer set up how it wants with the extra partition created.

---

### Post by Pumalite on 2007-11-09
Defrag XP several times. erase all temp files. Boot from Gparted Live CD and right click on XP partition and resize it. Then install Ubuntu.

---

### Post by Muad Dib on 2007-11-09
Thank you all for the reassurance.  I think I'm on the right track.  Watch for future posts if I botch the install.  Wish me luck!!!

---

### Post by Dr Small on 2007-11-09
> **Muad Dib said:**
> Thank you all for the reassurance.  I think I'm on the right track.  Watch for future posts if I botch the install.  Wish me luck!!!
Good luck mac ;)

---

### Post by bliffle on 2007-11-09
It's always a good idea to have a GParted liveCD around: never know when you're going to need it. 

I think it's the best and most reliable partitioner to use when setting up dual boot HDDs. Also, one is advised to perform partitioning chores in steps. GParted doesn't apply changes until you tell it: it actually builds a script as you allocate, delete, resize, etc., then does things in sequence, and that sequence takes a long time and a mistake you made may take minutes or hours to manifest itself.

The way I usually do XP dual boots is to first buy a new clean HDD of the right size. All that I do on the old XP HDD is to run the XP HDD defrag and repair utilities several times until they run clean, then I shut it down and set it aside as backup and as a passive source to build the new HDD. Big HDDs are so cheap now that it is foolish to re-use them, and that goes for buying used HDDs from eBay, no matter what assurances are made.

---

