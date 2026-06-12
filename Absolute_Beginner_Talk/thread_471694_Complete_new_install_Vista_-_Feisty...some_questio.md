---
title: "Complete new install Vista - Feisty...some questions"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by Peverel on 2007-06-12
Hi everyone,

Great forum, maybe you can help me with my new set up.

I'm using a Dell Inspiron E1505 laptop and have currently Vista and Edgy on a dual boot.
I installed Edgy after Vista and I'm running a bit out of space in Edgy. So I wanna make a fresh install with Vista and Feisty Fawn.

I'm actually running linux most of the time, but I wanna set up Vista for gaming and some Office and Adobe work...

So, I have a 60GB internal HD and a 250GB external HD. I want to install both systems internally, but here are some questions which I am not sure about, so please let me know if you know... :)

Would it make any sense to install games on the external HD to free up internal HD space? Maybe format a partition in NTFS, would it make it faster?

I thought about allocating 40GB to Vista and 20GB to linux, any critics?

Would it make sense to install a linux partition on the external HD and copy and install files and programs on this one?

I'm using an ATI X1400 graphics card. I experienced and read about Feisty's problems with this card, so what should I do during install so that it works?

I guess anything else that works in Edgy (Bluetooth etc.) works in Feisty as well?

When is a new Ubuntu version due to come out that would make me wait with the fresh install?

Anything else to be aware of before the fresh install?

Thanks in advance!!!

Ubuntu rocks :)

---

### Post by cotcot on 2007-06-12
No need to reinstall. 
Your external hhd is large enough to backup first. You have to defragment vista first (at least this was the case with XP, maybe vista is different). Then I suggest to reduced the edgy partition as much as you can (with GpartedLiveCD). Then reduced vista with  for instance 1GB more than the new size of your edgy partition (with GParted as well). Then you can move the edgy partition to the vista partition and extend the edgy partition to the size you want. (again with Gparted LiveCD). 
Why this 1GB ? Could be more or less. The important thing is that the space you create by reducing vista must be large than the new edgy partition. This is mandatory for moving the edgy. (parted does not allow moving when there is overlap from the old to the new location. Maybe you do not need to reduce edgy. You have to defragment vista first.

An example with figures. Suppose your vista is 48 GB and your edgy 12 GB of which 5 GB is used. Make backups (for instance with 'tar' or with 'partimage'). Reduce vista to 40 GB. Reduce Edgy to 6 GB. Move edgy so that it is between 40 and 46 GB. Extend Edgy to 60 GB. Now you have 40 Vista and 20 Edgy. (I have this kind of operations several times)

Putting partitions on the external hdd depends whether you carry the hhd all the time with you or not and of your backup strategy. 

Ubuntu has a 6 months release cycle. It is in april and october, hence the name ending on .04 or .10. With the year in front it is 7.04 or 7.10. So in october 2007 you can expect the next release.

---

### Post by Peverel on 2007-06-12
cotcot, thanks, this sounds actually pretty easy...

The thing is, I wanna make a fresh Vista install anyways because it's a bit messed up (I guess I played with it too much :) ) and there are always internet pop ups coming up which I couldn't get rid of (I'm a noob in linux, not in windows :) ).

Furthermore, I think a fresh Feisty install is better than updating Edgy? (I also played a bit with Edgy, so I guess it is a bit messed up as well, installed programs to weird locations etc.). 

The downside is that my Edgy is now actually in the state of which I like it (Desktop environment, programs, plugins, scripts etc.) so this would mean a bit of work with a fresh install...

What would you say about a fresh Feisty install over updating Edgy to Feisty?

And thanks for clearing up the update cycle... :)

---

### Post by starcraft.man on 2007-06-12
My personal opinion is I always prefer a fresh install of things over an upgrade to a new version. That said, Ubuntu upgrades seem a lot better than the few Windows upgrades I've seen happen *gets painful memory*. If you do want to give upgrading a try, it couldn't hurt. First make sure you have a CD of Feisty just in case it goes bad and becomes unbootable, things can always go wrong....

To ensure a smooth upgrade path I'd do a few things first. If you have Beryl/Compiz installed I'd remove them for now. I would then proceed to uninstall the 3d drivers for your card and switch back to the 2d nv/vesa drivers. A lot of people it seemed to me ran into trouble when they left the drivers installed and on. Then I'd remove any third party proprietary apps that you installed after that really aren't supported by Ubuntu: VMware, Parallels, Automatix, Google Earth... you sometimes get problems from these. Then I'd pop in the CD and upgrade from it, that way you don't have to redownload.

Hope it goes well, if not ya always go CD for clean install. Do make sure you back up your data before doing any of this please.

---

### Post by plinydogg on 2007-06-12
One word of caution, if it hasn't been mentioned already: if you're going to be changing the size of your Vista partition (or otherwise messing with it), make sure you do so from within Vista itself!

---

### Post by cotcot on 2007-06-12
> **Peverel said:**
> 

The downside is that my Edgy is now actually in the state of which I like it (Desktop environment, programs, plugins, scripts etc.) so this would mean a bit of work with a fresh install...

What would you say about a fresh Feisty install over updating Edgy to Feisty?

And thanks for clearing up the update cycle... :)

I fresh install is generally better. However you might keep your edgy along with vista and a new feisty install (triple boot). You can install feisty with the alternate install CD telling the installer not to install a boor loader and add feisty manually to the menu.list of your edgy install. You could remove edgy as soon as you are as happy with feisty as with the edgy.

---

### Post by Peverel on 2007-06-12
That sounds good... after the Edgy delete I can allocate the available space to Feisty...

Thanks so far for your suggestions, I will keep you posted when I finally do the fresh install... :)

---

