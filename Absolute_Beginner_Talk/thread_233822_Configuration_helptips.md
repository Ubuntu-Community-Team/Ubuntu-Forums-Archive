---
title: "Configuration help/tips"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by bearglenn on 2006-08-10
I installed Ubuntu a little over a week ago, so I've been using linux for about a week now.  I have it configured and know enough to do my day to day stuff, but I there are a few outstanding iussues I just can't seem to work out.

Let me give you a history of my machine. It was originally built to be a gaming machine.  It has 2 nvidia 7800 256 xfx cards in it.
4 sata drives in it (I used to have a raid 0 configuration, but I broke the raid to install linux) and 1 ide 300 gig drive, 4 gigs of ram etc, etc, etc

so currently my system is dual booting.  Windows XP on sda1 and Ubuntu on sda2 this works fine.
----------------------------------------------------------
Brings me to question one:
I would like to set up a media drive for music and movies.  I would like to use my 300g drive (hda1) for that, and I would like both XP and linux to share the drive.  I know linux can read ntfs drives but everything I read says it has issues writing to the ntfs drive? Which is a problem because I would like to use my linux install for optaining the media, ripping dvd downloading music etc.  Is there a way to do this?  is there a file system format that plays nice with both XP and Linux maybe a fat32 or something?  I have 2 sata hard drives maybe I can format one to be fat32 or whatever save the media to it then go into windows and move it to the 300 gig drive?  

----------------------------------------------------------
 Question 2 video:
SLI, multi monitors, and HDTV

I have 2 7800 cards which in windows supports 4 monitors in normal mode and 1 monitor in SLI world.

I have 2 monitors hooked up to the machine and a HDTV via DVI to HDMI cable.  All intergrated into my entertainment center. (Its pointless but I get a lot of comments on it when people frist come into the house) I can do without the 2nd monitor now that I'm used to the multi-desktop feature in linux, but I can't seem to get a picture on my TV, which I use for watching movies and music videos and such on a larger screen. What is the secret to having multi monitors working in linux.  I used to automatix to install the nvidia driver and I think its working properly.

and further does sli work in linux?  If not no big deal I can always go back to windows to play games.

Any help out there?

---

### Post by stevanbt on 2006-08-10
Hi bearglenn,
In answer to question 1, I would have thought that it would be best to have a fat32 partition that you use as a shared partition between XP in Ubuntu.  I use this setup on my laptop and it works ok.

Another way would be to use another computer as a file server and share data on it's drives between XP and ubuntu.  I haven't used Network Attached Storage, but this might also be worth considering.

I've read NTFS drives in linux before, but I've only ever read from them.  FAT32 is way easier.

Hope this helps.

---

