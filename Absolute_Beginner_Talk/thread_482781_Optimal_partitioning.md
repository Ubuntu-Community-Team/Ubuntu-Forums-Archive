---
title: "Optimal partitioning"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by Delirious on 2007-06-24
So far I'm loving my Ubuntu experience on my little p3 800mhz 384mb of memory and some other old stuff :D

I'm getting ready to install Ubuntu on my main rig in the coming days though and would like to know what the best way to setup the partitions are.

For example since I'm a long time windows user (and admin by trade) and i have my machine setup like such:

drive 1: windows (cause it gets re imaged alot :p )

raid 5 array split into multiple partitions:
  partition 1: installed programs  (so i don't have to reinstall them when windows is re imaged)
  partition 2: my virtual machines
  partition 3: storage for everything (music, movies, files, etc)

I want to run Ubuntu and windows on drive 1 and have separate partitions (ntfs and ext3) on the raid array for the windows and Ubuntu programs. And then the rest of the space is going to be for Ubuntu as it will be my primary os and windows will be only for games and maybe a few other small programs.

How or what would my partition setup look like to achieve this? Is it possible to setup Linux so that it installs programs on a partition on the raid array and not on drive1 where Ubuntu will be? Id like it setup like this so that if i had to reinstall Ubuntu i would only have to reconfigure and re install a minimal amount of stuff.

---

### Post by maddot on 2007-06-24
You could use a little cheat i used. First, resize the partitions accordingly to your preference. Here, i'm talking about your windows partitions. Use either linux's gparted or a windows 3rd party app. I used the latter... paragon ;). Anyway, make space for ubuntu....depending on how much you want to give it as a whole. If say you have a 180 gig hdd... allocate bout 10 if yer still gona play around with it. Allocate as much as you think you'll use. Take note that ubuntu doesn't need alot of disk space. I have ubuntu installed for 2 months and it's still only eating about 7.5gb og my 58gb partition...lol

Then, once you have resized and have free space on the hard disk, boot up ubuntu, click on largest empty space or something along that lines. And it should install snugly in it. 

I still not clear about setting up individual partitions for linux distros. I know that linus by default will create 3 partitions. 2 ext3 partitions and a swap. anyways, that's another story. After you've complete the above, it should work nicely.

---

