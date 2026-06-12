---
title: "[SOLVED] Cannot shrink volume in Vista for Ubuntu install on separate partition"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by TheNorthWaves on 2007-12-14
First of all, I searched for a while on this. I am determined to install 7.10 on its own partition - on my lenovo thinkpad loaded with vista home premium + a recovery partition (I made the recovery disk already, and if I have to wipe the system, so be it. Thats the last resort).

Anyway, I wanted to avoid using gparted to partition with vista installed due to what I read about errors. I go to use vista disk shrink, and naturally I get the problem with having 114700 MB but being able to only shrink 28MB. Pathetic. I read that turning off page file is a bad idea in vista, so I defragged, deleted shadow copies, ran disk cleanup, etc... have 30something gigabytes free, but every time I run disk shrink, it says 28MB available to shrink... this is regardless of having 9 gigs free or 37 gigs free on my HDD. Anyone know a way around this problem, or perhaps a good freeware partitioner that won't screw up my current vista install?

I looked around for a solid hour or so, and still I am not sure what the solution is.

Thanks

---

### Post by DeLaNooch on 2007-12-14
I don't know a lot about Vista and don't personally like it very much.  Regardless, I had a friend who was trying to do something similar to what you are trying.  He eventually just gave up and wiped the whole disk and started fresh.  That is what I would do in your situation, but that's not really answering your question at all.  As far as partitioners go, I would recommend PartitionMagic.  However you might have a hard time finding a usable trial version.

As far as recovery partitions go... I hate those damn things.  I burned DVD's of the factory image like you said you did, and when I installed Feisty I just got rid of everything.  I have a fairly small disk in my notebook, and I set up the partition very easily with the Ubuntu install partitioner.  I set up a root partition, a swap partition, a Fat32 partition for file storage, and left ~30GB free in case I need to put XP back on it for school next semester.  ...Hopefully I won't need to.

Sorry for that little tangent.  I didn't really help much. :lol:

---

### Post by TheNorthWaves on 2007-12-14
I'm starting to feel like that's what I'll end up doing. Either that or just not do it at all. I think I would have to erase my restore partition but i'm not sure how the reinstall would go

---

### Post by DeLaNooch on 2007-12-14
> **TheNorthWaves said:**
> i'm not sure how the reinstall would go

If you are referring to the Vista reinstall I may be able to offer insight.

In my case, I have an HP notebook that came with an install of XP MCE.  I have rebuilt the notebook once with the recovery DVD's.  In my case, the DVD's just ran Ghost and reinstalled the factory image of my drive.  When I was finished, EVERYTHING was back to factory state, including the recovery partition.

Don't be discouraged from trying.  As long as you have any important data backed up, worst case scenario is that you go back to Vista and get a fresh factory install.

Hope that helps you in making a decision!

---

### Post by dstew on 2007-12-14
Usually, it is an immovable file that blocks your attempt to shrink the partition. In Vista, there are immovable files set aside for paging (same function as Linux swap) and hibernation. You need to disable paging and hibernation, then defragment, then try to shrink.

To disable paging, you can use the Vista system manager Start -> Control Panel -> System and Maintanence -> System. Under the Advanced tab, Performance section choose Settings. Go to the Advanced tab, Virtual Memory settings, click Change, uncheck Automatically manage paging file sizes for all drives, select the primary partition (the one you are trying to shrink), click No Paging File, then Set. [Here]("http://www.maximumpcguides.com/move-and-optimize-windows-vistas-paging-file/") is a link that gives more good information about paging in Vista.

To disable hibernation, you need to enter a command on the system console. [Here ]("http://www.vistajuice.com/2007/04/enabledisable_hibernation_in_v.php")is a link that tells how to turn hibernation on and off.

Once you have turned these off, reboot Vista, defragment, then try to shrink again.

EDIT: You may have to delete the hibernation file after you disable hibernation. See [here]("http://vistahelp.blogspot.com/2007/01/disable-hibernation-and-free-up-space.html"). You use Hibernation File Cleaner under the Disk Cleanup system tool.

---

### Post by DeLaNooch on 2007-12-14
You can't disable hibernation in Vista via the GUI like you can in XP?  Hm... that's weird.

---

### Post by plinydogg on 2007-12-14
I had the same issue as you (discussed in this thread: [http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425) ). I was able to get it to work by running the Vista partitioning utility from a command prompt. Here's what I said about it in the post linked to in the parenthetical:

> Wait! Wait! As a last ditch effort I looked at the help files for diskmgmt.msc (where you access Vista's volume shrinking abilities). There were instructions about how you use the utility from a command prompt. I figured, why not try it so I did. And I was able to shrink the partition by 14 GB! Enough for Ubuntu install right (at least a basic install?).

---

### Post by TheNorthWaves on 2007-12-14
I would like to try the command prompt thing - however, I looked at your provided link as well and I'm not actually sure how to do what you're talking about

---

### Post by stchman on 2007-12-14
> **TheNorthWaves said:**
> First of all, I searched for a while on this. I am determined to install 7.10 on its own partition - on my lenovo thinkpad loaded with vista home premium + a recovery partition (I made the recovery disk already, and if I have to wipe the system, so be it. Thats the last resort).

Anyway, I wanted to avoid using gparted to partition with vista installed due to what I read about errors. I go to use vista disk shrink, and naturally I get the problem with having 114700 MB but being able to only shrink 28MB. Pathetic. I read that turning off page file is a bad idea in vista, so I defragged, deleted shadow copies, ran disk cleanup, etc... have 30something gigabytes free, but every time I run disk shrink, it says 28MB available to shrink... this is regardless of having 9 gigs free or 37 gigs free on my HDD. Anyone know a way around this problem, or perhaps a good freeware partitioner that won't screw up my current vista install?

I looked around for a solid hour or so, and still I am not sure what the solution is.

Thanks

I am going to assume that you bought this laptop with Vista pre-installed.  If yes then from my experience most images that manufacturers install are BLOATED terribly.  If you can see if you can get your hands on a Vista OEM DVD.  Completely wipe the hdd and start from scratch.  Use your Vista key on the bottom of your laptop so you are legal.

During the Vista install re-partition the hdd as you see fit.  Leave some free space for Ubuntu.

MAKE SURE you backup any personal data.

Once you are done go to [www.blackviper.com](www.blackviper.com) and he will show you how to turn off the un-necessary services Vista has that bloats it terribly.

After you are done install Ubuntu and be in dual boot bliss.

---

### Post by TheNorthWaves on 2007-12-14
that sounds like an excellent idea, since I happen to have an exact copy of this OS on a disk from another  system I built - the problem is that my lenovo came with vista preinstalled WITH MS office... how would I manage to "get that back" using some other dvd with only vista on it?

---

### Post by TheNorthWaves on 2007-12-14
I figured out how to work the shrink feature via the command prompt but it's still stuck telling me there's 28MB.... agh. Will try some more things and update later.

---

### Post by TheNorthWaves on 2007-12-15
well i disabled paging and also hibernation, defragged, etc... still 28MB. Am I out of options? Remember I have vista installed with office suite, with recovery discs and a partition.

---

### Post by TheNorthWaves on 2007-12-16
bump - anyone?

---

### Post by BLTicklemonster on 2007-12-16
Upgrade from Vista to XP first, then do it.

---

### Post by Paqman on 2007-12-16
Maybe ask the same question on a Vista forum?

---

### Post by TheNorthWaves on 2007-12-16
> **Paqman said:**
> Maybe ask the same question on a Vista forum?

Fair enough - and to the previous person, I don't have XP

---

### Post by dstew on 2007-12-16
Did you try the things I suggested in my previous post? That is, disable hibernation, remove the hibernation file(s), disable paging, defragment, then shrink. After you shrink the partition, you can of course re-enable those Vista features.

EDIT OK, I see you did it. But did you remove the hibernation file(s)?

---

### Post by plinydogg on 2007-12-17
Sorry nothing seems to be working for you. I suggest that you follow a previous poster's suggestion and search Vista forums. That's how I learned about using the Vista partition utility in command line mode (which didn't work for you unfortunately). I'll post back here if I find anything else.

---

### Post by cmo220 on 2007-12-17
What worked for me was to defragment 3 times.  For some reason it didn't work after the first 2 times but did after the 3rd.

---

### Post by Irihapeti on 2007-12-17
I know some people say not to use Gparted on a Vista partition. However, I did it successfully, and I gather others have as well. When I booted into Vista after the resizing, it wanted to run chkdsk and reboot a couple of times, which I did. After that it was fine. As you have the disks to reinstall if something does go wrong, I don't see that you have anything to lose by trying it.

---

### Post by TheNorthWaves on 2007-12-24
I ended up using a full version of vista and foregoing the factory installed vista on my computer...
Ran gparted, installed vista, installed ubuntu, it works!

---

