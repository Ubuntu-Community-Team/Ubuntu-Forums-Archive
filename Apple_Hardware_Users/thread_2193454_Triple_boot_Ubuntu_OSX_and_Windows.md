---
title: "Triple boot Ubuntu OSX and Windows"
date: 2013-12-12
forum: Apple Hardware Users
---

### Post by mattholl82 on 2013-12-12
After searching around for a while and a bunch of failed attempts I stumbled across this guide:

[http://www.davidlively.com/notes/macbook-pro-triple-boot](http://www.davidlively.com/notes/macbook-pro-triple-boot)

He doesn't have kind words about linux but that's ok because this is extremely helpful.  I have been using fedora and ubuntu for a couple years but only on PC's, this is the first mac I have owned so I have experience with multi booting a computer but this macbook retina had me pulling my hair out for a couple days hahaha.  This is really the best method I have come across because it doesn't involve deleting the OSX recovery partition or messing around with the EFI partition, MBR and GPT.  It just works, all you need to do is install rEFInd and your good to go.  Hope this helps someone.  Btw I have a retina macbook pro 10,1.

This is the real key to this, relocating OSX and it's recovery partition to a newly created partition at the end of the drive so you can install windows in the first slot.  Ubuntu and OSX boot from wherever the hell you want to put them.  This shouldn't have to be said, but I'll say it anyway.  Time machine is soooo easy to use, please back up your drive before messing around like this!!

[COLOR=#000000][FONT=Arial]"The key to this procedure is to relocate OSX and the recovery partition to the end of your drive (note that Disk Utility moves the Recovery partition for you to keep it next to the OSX partition). Since you can't move the partition you've booted from in *any* OS (to my knowledge), you'll need to boot from an external device that provides a good partitioning tool. 

Install the OSX Recovery Assistant to your external drive, and reboot. Hold down the left option/ALT key while rebooting until you're presented with a boot menu, which should provide options for (assuming you're starting from a 100% OSX drive) OSX, Recovery HD and the USB Recovery system (which will be the last Recovery item listed). Select the last recovery option listed.

Once it boots, you'll be presented with four menu options including "Reinstall OSX" and "Disk Utility." Select "Disk Utility."

Select the Apple SSD in the explorer (left pane).

You should only have one partition at this point. Divide it into a few parts. You'll need (based on my config, which has the 768GB SSD)

1. The existing OSX partition at the beginning of the drive (which we'll call **OSX1** in this article). This will eventually become your Bootcamp partition, so size it appropriately. I set it to 128GB. (I'm working on a 768GB SSD.)
2. A shared data partition, if desired. I set this to about 390GB.
3. A Linux partition. (80GB)
4. A Linux swap partition (I set mine to 16GB to match my RAM, which may or may not be a good reason).
5. The final home of OSX - I also set this to 128GB. (We'll call this **OSX2** from now on)

I found it easiest to add all the partitions before resizing them, and to keep everything as HFS+ (MacOS Journaled) until later. HFS+ partitions are easier to resize/move around than anything else. Also, Disk Utility does weird things to partition sizes when you create new partitions; save yourself a headache, create all the partitions, then set the sizes starting with the top-most partition and working your way down.

The important part is that you need an OSX HFS+ partition at the end of the drive. Resize the existing OSX partition to whatever size you want your Win7 partition to be. (This is really, really difficult to change later - give yourself plenty of space!)
Now, the fun part:

1. Your **OSX2** partition needs to be at least as large as the OSX1 partition (eventual home of Win7). In Disk Utility, select OSX1, and click the "Restore" tab.
2. Select **OSX1** as the source, and OSX2 as the destination.
3. Click Restore. You may have to right-click on the partitions and unmount them (context menu option). Just make sure OSX1 is the source, and not the other way around, or you're looking at a really, really slow (1+ hours) Internet recovery.
4. Wait awhile. This took me about 20 minutes to move apps, data and the OS.

At this point, you should have two functioning OSX installations. Not only that, Disk Utility was kind enough to clone the recovery partition, as well, freeing up valuable slots at the beginning of the drive.

Reboot, holding down the Option key (aka, ALT). You should see something like "OSX | Recovery | OSX | Recovery | Recovery". Select the SECOND OSX install. We'll do the rest of the disk utility work from there, and also need to make sure it really works before nuking the original.

Assuming this works (and if it didn't, YOU BETTER HAVE A BACKUP!!!!), open up Disk Utilty and delete the first OSX partition. Create a new FAT partition in its place of the same size. (You may be able to do this from the Win7 installer, but doing all the partitioning stuff from the OSX side makes it a little easier to keep the GPT and MBR in sync.)"[/FONT][/COLOR]

---

