---
title: "dual boot and shared data partition"
date: 2007-11-13
forum: Apple PPC Users
---

### Post by skj on 2007-11-13
noob alert!

new to OSX AND ubuntu.

I have an slot loading iMac 400mhz with 512mb ram and a 30 gb hard drive.  I have OS X 10.3 running already in one big partition. Tried the 7.04 live cd and got it working with a non-apple usb wireless adapter, so I'm happy. Just want to test it out, web surf, listen to music and let my niece bang on the keys when she comes over! 

Searched posts and think I have the non-destructive re-partitioning of the drive down... hopefully (use Gparted after turning journaling off to resize and create new partitions.) 

Question about this re-partitioning though. I thought I read that OSX was supposed to be installed on the second partition and Ubuntu on the first. Will I be able to do this with the way I have it set up now?

Also searched around for info on sharing files between osx and 7.04.  Still kind of up in the air on that.  Since I'm gonna re-partition the drive, could I just make a partition for the shared data (mostly mp3s)?  I thought I read something like a non-journaled hfs+ drive for this.  Is that correct? What would be some other ways or maybe more preferable ways to accomplish this? Could I just leave my mp3s where they are on my hard disc in OSX-land and access/add/delete them from there?

Thanks in advance for helping out a noob.

---

### Post by SycloneMedia on 2007-11-13
Welcome!

About the repartitioning: it's not that one has to be first (either can be) but the whole thing with your setup is that you want non-destructive and you already have OSX on it. So what you'd want to do is do your non-destructo partitioning and then have the liveCD install to the new partition or free space (if you choose to just open up the extra partition as free.) It 'should' automatically throw in 'yaboot' for you that way which will bring up a choice for you of which system to boot at startup. I did the same with a windows machine.

About the shared partitioning: make one. yes, keep it unjournaled hfs+. this way you can set your OSX system to "not manage" permissions on it and it just makes it a little easier from the linux end.
then when you've installed linux, you'll need to go and grab and install the hfs packages (theres one or two) which will install the necessary components to allow your linux system to read and mount the shared hfs part. then, you'll have to add the appropriate mount-point instruction line in your "fstab" file to allow the linux system to mount your shared part automatically at launch.

i can help you with this in more detailed instructions, but tomorrow... i'm about to head to bed, upset over the Niners loss... woe is me.

---

### Post by skj on 2007-11-13
Thanks, SM.  I'll try it later on when I get home.

Yeah that was a tough game to watch. But it's hard to grieve with you, I have the sadness of UCLA football down here.  I gonna ask the mayor to try to woo the Patriots out of New England down to sunny So cal! That way, Brady could meet his women on the beach.

---

### Post by skj on 2007-11-14
I've partitioned the hard drive but gparted doesn't have the option of formatting hfs+.  I rebooted into OSX and went to the disk utility but only had the 3 folder tabs on top (rescue, info and I can't remember the last one, sorry did this late last night.)

Can I do it this way or do I need to use the OSX discs for this? (which I thought I read somewhere).  Or can I use another type of formatting that will allow me to read and write from both OSX and Ubuntu 7.04?

Can I just fat32 it?  Pro and cons?

---

