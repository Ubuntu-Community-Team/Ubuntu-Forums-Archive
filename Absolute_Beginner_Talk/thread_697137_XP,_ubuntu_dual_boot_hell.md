---
title: "XP, ubuntu dual boot hell"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Eagle70ss on 2008-02-14
Here Goes...

I have a single hard disk with about 40G...I have 30G partition(C:) and a 10 Gig(D:) partition...MY XP OS is on the larger partition and the 10 gig is free...I just want to install ubuntu on the small partition without wrecking my WORKING XP....:) I know I don't want to use the guided partition manager because that will screw with my XP partition...I've tried creating ext3 partition under "/" mount point..and a 512 MG swap space//.but it won't format it...It always comes up with format error and won't do anything...

I'm completely new to any linux stuff except live CD's...Is this as simple as it gets?? LOL...Using 7.10 OS....This is a far cry in complexity from the windows "pick C drive and hit install and walk away(unattended style)...

Thanks in advance...

---

### Post by Presto123 on 2008-02-14
Try formatting that 10 gig bit as a FAT32 in XP. That seems like you are having an issue with it being locked. It's been a while since I've used XP in my own personal usage, but I know there is a way to do so.

Otherwise, you might get a Gparted Live CD that MIGHT get you to this point.

You are doing everything else correctly from what I can see, though.

---

### Post by phil66 on 2008-02-14
[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

Try the method outline in this article

---

### Post by spacefreak86 on 2008-02-14
Actually I got mine to work quite easily. I have two physical drives in my system, a 80 GB that is partitioned 50/50 with windows XP on one part and an empty logical drive on the other. My other drive is a 320 GB hard drive that I split into three 102 GB hard drives. I had plenty of extra space, so from windows I deleted out one of the partitions, causing it to go to free space. From there, I shut down windows, put in the live CD. When I installed Ubuntu 7.10, I simply selected the drive that was not partitioned or written on, and let Ubuntu install on that. I think I took that space and first created a swap drive with 512 MB of space on it, then created another drive for the file system under etc3 (or whatever its called) and under the mounted entered in "/" for the root (No linux experience at all, got these instructions off this site while in Windows)

 It should work with XP, I just started with Ubuntu a few days ago and if I could get Halo and LaTeX running, I could all but ditch windows since my of my activities reside on internet programs.

---

### Post by Presto123 on 2008-02-14
> **spacefreak86 said:**
> Actually I got mine to work quite easily. I have two physical drives in my system, a 80 GB that is partitioned 50/50 with windows XP on one part and an empty logical drive on the other. My other drive is a 320 GB hard drive that I split into three 102 GB hard drives. I had plenty of extra space, so from windows I deleted out one of the partitions, causing it to go to free space. From there, I shut down windows, put in the live CD. When I installed Ubuntu 7.10, I simply selected the drive that was not partitioned or written on, and let Ubuntu install on that. I think I took that space and first created a swap drive with 512 MB of space on it, then created another drive for the file system under etc3 (or whatever its called) and under the mounted entered in "/" for the root (No linux experience at all, got these instructions off this site while in Windows)

 It should work with XP, I just started with Ubuntu a few days ago and if I could get Halo and LaTeX running, I could all but ditch windows since my of my activities reside on internet programs.

Unfortunately, he cannot get TO installing Ubuntu yet...but otherwise, nice tip. :)

---

### Post by Eagle70ss on 2008-02-14
Update...

I used Partition magic in Windows to delete my smaller partition and I left it unallocated...so when I went to install ubuntu again..It then had a third guided option to just use biggest free space and it was virtually automatic from there, but now the Grub boot loader doesn't recognize my XP installation at boot up...any ideas...I previously had a Vista OS on the smaller partition and that shows up on the boot menu instead of XP...any ideas..?

---

### Post by Eagle70ss on 2008-02-15
Problem resolved with Grub editor that come in debian package...easy to install and to edit the boot loader and now I can boot into XP and Linux at will...Thanks for all the help from everyone who posted...

---

### Post by mkoehler on 2008-02-15
Congratulations!

@ SpaceFreak.....LaTeX works perfectly under linux, I use it on a standard basis to make formal reports - you can find it packaged in synaptic.

---

### Post by spacefreak86 on 2008-02-15
Yeah, I finally got it work in both Kile and TexMaker. So now the only thing preventing me from ditching windows is getting my Halo fix ... and finding a video downloader to download videos from YouTube.

---

### Post by cybertron3000 on 2008-02-16
I entered the Kingdom of Ubuntu from XP about 2 months ago, and I eliminated my XP forever.  Welcome aboard.

---

