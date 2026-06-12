---
title: "Now it doesn't boot :("
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by monk3yboy on 2007-05-28
So this weekend I decided to give Ubuntu (Feisty of course) a try.  So far it hasn't gone so well.  I finally figured out how to get the proper screen resolution (darn those proprietary nvidia drivers that didn't recognize my monitor right!)  I tried listening to some music via my installed xmms and that worked but for whatever reason it only saw very little of my collection.  So I tried Amarok, this is where the real problems started.  It would always freeze when i tried to play anything, it had generating play list at the bottom of the screen and it just stayed there.  I've tried rebooting multiple times but it still does that every time.  Well on the last try I was installing the updates to the most recent kernel while trying to run amarok.  I went to restart the machine after the updates where done and the whole thing froze.  Keyboard, screen, I could move the mouse but I couldn't' click on anything and nothing showed that my pointer was over a button or anything.  So i hit my reset button (actually been having to hit it several times since install) and then the screen errored out and froze.  Here's what it said:

Kernel 2.6.20-16 (the -15 works though)
1.086484 RAMDISK:ran out of compressed data
1.0865151 invalid compressed format (err=1)
1.087130 Kernel panic - not syncing:VFS:Unable to mount root fs on unknown - block (0,0)

When installing Ubuntu i didn't have a spare drive to install a swap partition to so just fyi I don't have one
here's my comp specs
e6400 OC'd to 2.8 ghz
2 gig DRR2 800 g.skill
Gigabyte P965-DS3 V3.3
2x 500 gig Samsung sata

Any suggestions?  DO i need to reformat and try again?  Should I try creating a small 5 gig partition via Partition Magic (running XP pro right now) and then format that as my linux swap partition and then reinstall ubuntu?  Should I remove the new kernel via synaptic package manager and then run the update manager again?

---

### Post by Happy_Man on 2007-05-28
And, your RAM went out of space, everything piled up, BAM! Deadness. What you need to do, is MAKE A SWAP PARTITION NOW. Just like a Windows pagefile, a swap partition provides HDD space in case of ram overflows. Absolutely essential. If you haven't done very much, I would suggest making a swap partition using the Ubuntu LiveCD, and then reinstalling. Boot up the LiveCD, and go to System --> Administration --> GNOME Partition Editor. Delete your Linux partition, make an extended partition, and then stick a 512 mb swap in there (formatted swap, over 512 mb is overkill). Use the rest for /, and reinstall using those partitions.

---

### Post by monk3yboy on 2007-05-29
If I can boot up into the previous kernel can i just go in there and use the gnome partition manager to create the swap partition out of the main partition I have setup for my windows media storage?  If possible I would prefer to not reformat my current Ubuntu partition.

---

### Post by monk3yboy on 2007-05-29
Now that I am booted back into ubuntu I can't find a way to partition off a section to create a swap file.  Is there a way I tried unmounting but it wouldn't let me.  In what program can I fix this?

---

### Post by Happy_Man on 2007-05-29
You need to boot from a LiveCD. 

If you boot from HDD, then the partition must be mounted for it to read and work, right? So you have to boot from the LiveCD, so that the partition isn't mounted and you can change it. Sorry..... :(

---

