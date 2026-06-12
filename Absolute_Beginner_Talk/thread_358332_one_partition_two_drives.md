---
title: "one partition two drives"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by TruckMonkey on 2007-02-10
Hey everybody, I am a brand new Linux user and have loved it so far:KS .  I've gotten this far from browsing the forums and the help here is excellent.  So the first thing is thanks!

I have added two 30 hard drives along with my main 40 gig (3 separate drives).  I want to partition the 2 30 gigs together to make one 60 gig.  Is this possible?  I found a post with a similar question, but the guy wanted to save his data.  I have no need for that.  I have two blank hd's I want to partition together.  Can anyone help me with that?

Thanks very much!

---

### Post by orb9220 on 2007-02-10
No I have never heard of this being done. And why would you want to?

What is great is that you have options.

1) have / root on one drive and /home on other. Advantage everytime you install new distro to / you still have /home nice and safe with all your installed applications.

2) one drive has your linux  and the other can be setup for data that xp and linux can share. Like Pics, Music, Movies and backing up your linux or xp system to.

Which is what I have done. I have a 120GB fat32 drive that both my linux and xp share.

---

### Post by old_geekster on 2007-02-10
> **TruckMonkey said:**
> Hey everybody, I am a brand new Linux user and have loved it so far:KS .  I've gotten this far from browsing the forums and the help here is excellent.  So the first thing is thanks!

I have added two 30 hard drives along with my main 40 gig (3 separate drives).  I want to partition the 2 30 gigs together to make one 60 gig.  Is this possible?  I found a post with a similar question, but the guy wanted to save his data.  I have no need for that.  I have two blank hd's I want to partition together.  Can anyone help me with that?

Thanks very much!
There is a way to do it, called RAID (Redundant Array of Independent (Inexpensive) Disks).  I could help you in Windows, but I am still too much a newbie in Ubuntu.

---

### Post by localzuk on 2007-02-10
There are a couple of options available to you. One is LVM and the other is RAID. LVM could be classed as software RAID.

I have never looked into LVM, but use hardware RAID extensively.

If you fancy buying a hardware IDE RAID controller you can use that. I would, however, say that you should just mount the 2 drives as separate directories eg /disks/1 and /disks/2. Why do you need it as a single partition?

---

### Post by TruckMonkey on 2007-02-10
> **orb9220 said:**
> No I have never heard of this being done. And why would you want to?

What is great is that you have options.

1) have / root on one drive and /home on other. Advantage everytime you install new distro to / you still have /home nice and safe with all your installed applications.

2) one drive has your linux  and the other can be setup for data that xp and linux can share. Like Pics, Music, Movies and backing up your linux or xp system to.

Which is what I have done. I have a 120GB fat32 drive that both my linux and xp share.

The reason is that I want to load a bunch of music to Linux.  I have 2 extra 30 gig drives I am doing nothing with.  I would like this machine to be Microsoft free so I am trying to span drives.  I have a 250 Gig in my XP machine, but I don't want to use that in this one.

---

### Post by meng on 2007-02-10
Well, although you can't have two drives on the same partition, you might have your music divided into two types; e.g. funky and non-funky. So you could mount one partition to /music/funky and one to /music/unfunky, and ultimately the effect is the same as if you had one big partition under /music.

This illustrates how much more flexible the partition/mounting scheme is in Linux compared to Windows.

---

### Post by TruckMonkey on 2007-02-10
> **localzuk said:**
> There are a couple of options available to you. One is LVM and the other is RAID. LVM could be classed as software RAID.

I have never looked into LVM, but use hardware RAID extensively.

If you fancy buying a hardware IDE RAID controller you can use that. I would, however, say that you should just mount the 2 drives as separate directories eg /disks/1 and /disks/2. Why do you need it as a single partition?

I would like to have one single 60 Gig partition for my music files to be stored in one spot (cheaply).  I have the extra drives and have more music than will fit onto one.  I am aware of RAID in regards to Windows, but would rather not put anything related to Microsoft on this particular box.

---

### Post by TruckMonkey on 2007-02-10
> **meng said:**
> Well, although you can't have two drives on the same partition, you might have your music divided into two types; e.g. funky and non-funky. So you could mount one partition to /music/funky and one to /music/unfunky, and ultimately the effect is the same as if you had one big partition under /music.

This illustrates how much more flexible the partition/mounting scheme is in Linux compared to Windows.

interesting, thanks for the point.  I'll look into that.

does anyone have any advice on a music player/organizer?  I use Media Monkey on my XP box, but they don't offer a Linux version...

---

### Post by meng on 2007-02-10
Rhythmbox (GNOME) and Amarok (KDE) are the defaults. You can run Amarok in GNOME, by the way. Neither is perfect of course.

---

### Post by orb9220 on 2007-02-13
Amarok in gnome on mine.
Which organized 1000 cd's at over 65GB's on a fat32 drive so my xp and ubuntu can share it.

It is in synaptic and run's great on gnome or kde.

---

### Post by lamego on 2007-02-13
You can do this with LVM, you can create a single volume group composed of your 2 disks, then just create a single logical volume on it.
Anyway it is always a good practire to have /home on a specific partition .
LVM is not software RAID has someone mentioned, LVM is a storage management system which may be used to achieve software like RAID., but that no it's primary purpose.

---

### Post by TruckMonkey on 2007-02-13
> **orb9220 said:**
> Amarok in gnome on mine.
Which organized 1000 cd's at over 65GB's on a fat32 drive so my xp and ubuntu can share it.

It is in synaptic and run's great on gnome or kde.

Wow, Amarok looks pretty cool.  I'll have to give that a shot.  Thanks for the tip.

I have an external USB2 fat32 drive that I have quite a bit of music on.  How difficult is it to add that HD to my Linux box?  Is it just plug and play, or will I have to confogure or format first?  I use it as a portable music file to share between my PCs and laptop.

---

### Post by TruckMonkey on 2007-02-13
> **lamego said:**
> You can do this with LVM, you can create a single volume group composed of your 2 disks, then just create a single logical volume on it.
Anyway it is always a good practire to have /home on a specific partition .
LVM is not software RAID has someone mentioned, LVM is a storage management system which may be used to achieve software like RAID., but that no it's primary purpose.

I've been messing around with LVM and it seems pretty cool (if I could get it to work).  I keep running into an error stating there is no physical name for the drive HDC1, even though there does seem to be a name on it when I check the drives... weird.  Still working on it.

---

### Post by localzuk on 2007-02-13
RAID is not windows based. Take a look at [http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID).

---

### Post by localzuk on 2007-02-13
I stated that LVM 'could be' classed as software RAID - as it does a bunch of similar things. It is normally best not to overly complicate a situation with excessive information when it is un-needed.

---

### Post by mixmaster on 2007-02-13
LVM is definitely the way to go for this.  You can add extra harddrives and simply expand the logical volume to encompass them at a later stage if your collection grows too much and it has other nice features.

The easiest time to set up LVM is at or immediately after install.  There are guides around on doing this.  I believe you can actually do it during install if you use the alternate install CD, although I've never tried this.  I don't think you can do it with the normal live-CD installer but in that case install into the smallest partition you can and then use LVM to access the remaining space.

---

### Post by hyper_ch on 2007-02-13
For more infos about LVM check here:  [http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

---

### Post by TruckMonkey on 2007-02-13
> **mixmaster said:**
> LVM is definitely the way to go for this.  You can add extra harddrives and simply expand the logical volume to encompass them at a later stage if your collection grows too much and it has other nice features.
This is exactly why I want to try it...:KS 

> **mixmaster said:**
> The easiest time to set up LVM is at or immediately after install.  There are guides around on doing this.  I believe you can actually do it during install if you use the alternate install CD, although I've never tried this.  I don't think you can do it with the normal live-CD installer but in that case install into the smallest partition you can and then use LVM to access the remaining space.
Cool, I just installed recently, so I may reinstall with the alternate CD.

Thanks!=;

---

### Post by lamego on 2007-02-13
> I stated that LVM 'could be' classed as software RAID - as it does a bunch of similar things. It is normally best not to overly complicate a situation with excessive information when it is un-needed.
Describing LVM as a storage management system should be far more easy compared to the definition of RAID, also it's not misleading...

---

### Post by localzuk on 2007-02-13
Not really. What is a storage management system? I haven't heard this term before. Many other people will be in the same boat. However, most people who are looking at linux will have heard of RAID - so saying that LVM could be described as software RAID indicates their simularity but doesn't blanket label it as that.

As I can't find an English definition of an SMS, all I can go on is the name and that provides very little to go by.

Anyway... Back on topic...

---

