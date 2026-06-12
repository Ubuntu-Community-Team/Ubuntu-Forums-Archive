---
title: "[SOLVED] Why won't it let me just partition?"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by jeff4760 on 2007-10-12
I am getting so tired of trying to install Ubuntu (Feisty that is).  I installed Kubuntu 64 bit the other day ( installed fine) but decided to go with Ubuntu.  On the Live CD, I get stuck under the partition page.  The crappy partitioner won't let me partition it the way I would like to.  I go to manual and there are two partitions already there.  One is My XP OS and the other is the XP programs.  They are listed as /dev/sda1 and /dev/sda5.  I know that means that the first is primary and the second is logical.  I want to create a primary /boot drive, and then a logical /, /tmp, /home, /shared_data.  I will most likely put the swap partition on my second HD.  I have two gigs of RAM so I am not worried about it.  When i get halfway through the process, the extra space all of a sudden says "unusable"--wtf!  I start off making the /boot partition as 100 MB and primary.  It lists it as /dev/sda3.  After that, any other partition I make the partitioner automatically makes primary, without me having a say, and makes that one /dev/sda4.  For some reason, I think the Live CD partitioner also thinks that I have two existing primaries (not one) at startup, because that only makes two that the Live CD just created, and I only had one ( Windows to start with).  After that I cannot make any more partitions.  I have rebooted the cd multiple times and it just won't work.  I have done the checksum on it and it is a perfect match, and checked the cd finding no errors.

I tried fdisk under the terminal, but I don't think I am using it right- or actually know how to.  I read on a post to start it up by " sudo fdisk /dev/sda ".  I do that and it says the number of cylinders is set to 18241, and that there is nothing wrong it but it is larger than 1024.

Fdisk seems to do the same damn thing.  I first create the 100 MB primary /boot partition, and then I try to create a new logical partition and nothing happens.

I just don't know the process and what to type to get the partition sizes I want.  I want a 100 MB /boot, a 10 gig /, 10 gig /tmp, 15 gig /home, 50 gig /shared_data, and 1 gig /swap ( which I can put on the same drive and not the second one if it is easier).

That's the order I want them in, unless swap goes on the first HD, then I want it before (or after if that's better) /home.

I have a 150 gig 7200 RPM that I want to dual boot with XP, and want to do a little entry level video-audio editing with Linuxes programs, so that is why I want this setup (my selection is based off of my current research from the past few days).  I am not afraid of any "wasted space", no please no comments on that.  I also have 500 gigs to play with on the second drive, so again, I am not afraid of wasted space.

I also tried using Acronis disk director and made the partitions that way.  Then I boot the Live CD and no partitions show up, not even the XP ones.

Any expertise/ suggestions on fdisk and how to finally get Ubuntu on my system?

---

### Post by j.bunce on 2007-10-12
Try downloading the "alternate" ISO. It's text based and you might find you get along with it a bit better.

---

### Post by rsambuca on 2007-10-12
I like to set things up before hand using the [gParted liveCD]("http://gparted.sourceforge.net/").

Also (and this has nothing to do with "wasted space"), don't bother with the separate /tmp file if you are using ubuntu or derivatives.  I can't remember the exact details offhand, but basically ubuntu uses some slightly different filesystems than other distros and it makes a separate /tmp partition completely unnecessary.

---

### Post by mc4man on 2007-10-12
i think you first should get a clear idea of how you want to use both hdd's with the 2 os's. then go back into xp and set it up as needed before installing ubuntu. The extended partition you now have on your 1st hdd  (programs) has to go, it should be a primary. (or not at all)

---

### Post by jeff4760 on 2007-10-13
Well I finally got it working.  I uninstalled all the programs under the windows XP D drive, and deleted that drive.  For some reason every time I tried to make it again, it would default to a a primary drive under an extended partition.  Well I just decided to make the XP OS partition bigger, and keep everything on it.    Another odd feature was that the unallocated space was defaulted to a primary label also, and there was no freaking way to change it.  No program would do it: gparted, fdisk, partition magic, etc.  What I did was continue making logical partitions from it for all the Linux partitions and made the last remaining space (which would default as a primary, unless formatted) to a Fat32.  Partition magic (what I finally used to get this headache working) wrapped that Fat32 partition along with all the linux partitions into one nice extended partition.  So that ended up making 3 primary partitions.  One for XP OS, one boot, and one extended.

To reiterate:  the partitioner on the Live CD never could make this work.  It defaulted primary partitions all over the place.  I'm not sure if that is a bug or just a feature that was overlooked.  I don't think all new users will have this this much nitpicking, as I did, for the partitions,  but it might be something to tell the developers of the next release of the Live CD download.

Another thing I should mention for anyone new to installing Linux.  If you are making your partitions under Windows (which I recommend), then DO NOT use Acronis disk director.  The partitions never showed up under the Live CD, therefore I could never install Linux using Acronis.

Partions magic did the job; rather oddly I should add, but I am up and running ubuntustudio with no problem.  Oh, and the audio file after you log in is simply beautiful under ubuntustudio.

Thanks for all the suggestions.

---

### Post by LowSky on 2007-10-13
if kubuntu installs just fine, all you have to do is unistall the kubuntu desktop and install the ubuntu desktop.... should work fine.

---

