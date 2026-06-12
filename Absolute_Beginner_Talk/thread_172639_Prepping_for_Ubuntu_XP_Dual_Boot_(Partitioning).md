---
title: "Prepping for Ubuntu/ XP Dual Boot (Partitioning)"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by CarpKing on 2006-05-09
First of all, I'd like to say I'm glad to be here.  I've liked the idea of Linux ever since I first heard of it, but until a friend pointed me to Knoppix, I never concieved I'd actually use it.  After trying some other Live CDs I settled on Ubuntu because of its reputation for being noob-friendly and having a good community.  

I soon plan to reformat my hard drive and set it up as a dual boot with XP and Ubuntu.  I have read the HowTos and such, but I thought I'd check here with my anticipated partition scheme before taking the plunge.  

Here is my plan (total: 120 Gb):

5 Gb NTFS (for XP and some programs for it)
50 Gb ext3 (for Ubuntu and any files larger than 1 Gb)
1 Gb swap
the rest (about 56 Gb the way its currently formatted) FAT32

I have heard about having separate home and root partitions, but I'm not sure if I want to deal with that.  Is it worth it for a basic home desktop PC?

---

### Post by deadgobby on 2006-05-09
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p2)
[http://shots.osdir.com/slideshows/slideshow.php?release=475&slide=2](http://shots.osdir.com/slideshows/slideshow.php?release=475&slide=2)
How to at
[https://wiki.ubuntu.com//WindowsDualBootHowTo](https://wiki.ubuntu.com//WindowsDualBootHowTo)
For a good video on line
[http://video.google.com/videoplay?docid=-6104490811311898236&q=](http://video.google.com/videoplay?docid=-6104490811311898236&q=)
  ( the above link is a a good guide to watch  try this one 1st)

---

### Post by aysiu on 2006-05-09
[QUOTE=CarpKing]After trying some other Live CDs I settled on Ubuntu because of its reputation for being noob-friendly and having a good community.[/quote] The community is amazing, but I wouldn't call the software "noob-friendly." It's more like "intermediate" or "determined noob" friendly. A lot of command-line use, unlike Mepis or PCLinuxOS. If you don't mind copying and pasting a few commands into terminal every now and then, you should be fine. For example, in Knoppix, your Windows partition shows up on the desktop, you click it, and it automounts and opens. In Ubuntu, you need to do this...

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

...to get your Windows partition automounted.

> 
I have read the HowTos and such Did you read this one? [http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

> 
Here is my plan (total: 120 Gb):

5 Gb NTFS (for XP and some programs for it)
50 Gb ext3 (for Ubuntu and any files larger than 1 Gb)
1 Gb swap
the rest (about 56 Gb the way its currently formatted) FAT32

I have heard about having separate home and root partitions, but I'm not sure if I want to deal with that.  Is it worth it for a basic home desktop PC? I would set up a separate /home partition. When you're first learning, it's almost inevitable that you'll do a reinstall because you screwed something up. You may also want to do a clean install when Dapper comes out. So a separate /home partition will help you reinstall while keeping your data and settings intact. You may not need a separate FAT32 partition, though, as there are drivers that help you read/write Ext3 from Windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

I would do something like:

7 GB Windows (NTFS)
1 GB Swap
7 GB / (Ext3)
105 GB /home (Ext3)

---

### Post by nanotube on 2006-05-09
aysiu makes good suggestions. one point i would make though is that winxp is really more disk hungry than ubuntu - a fresh install with sp2, and some apps (like ms office, photoshop, etc), takes up about 5 gigs - at least it did for me. so if you want to have any playroom on your xp partition, give it more like 10 gigs, no reason to cut it too close with all that disk space you have. :)

---

### Post by aysiu on 2006-05-09
[QUOTE=nanotube]aysiu makes good suggestions. one point i would make though is that winxp is really more disk hungry than ubuntu - a fresh install with sp2, and some apps (like ms office, photoshop, etc), takes up about 5 gigs - at least it did for me. so if you want to have any playroom on your xp partition, give it more like 10 gigs, no reason to cut it too close with all that disk space you have. :)[/QUOTE] Agreed. I have something like 15 GB allocated to XP, even though I don't really use it any more. A few apps really clutters that thing up.

When I had Gnome, XFCE, and KDE on Dapper, it was 3.5 GB total for that and all the programs I had installed.

---

### Post by CarpKing on 2006-05-10
Thanks for all the help!  

> 
I wouldn't call the software "noob-friendly." It's more like "intermediate" or "determined noob" friendly. 

I would classify myself as "determined noob."  I don't have much experience with Linux, but I think I can learn.  I can handle command-line as long as I know what sort of commands to use, and I generally have good luck with computers owing to my intuition and elite googling skills.  

> there are drivers that help you read/write Ext3 from Windows

Sounds good.  I guess now my plans are:

10 Gb NTFS
1 Gb swap
7 Gb / ext3
102 Gb /home ext3

Barring any complications, I will give it a go as soon as I get all my data backed up.

---

