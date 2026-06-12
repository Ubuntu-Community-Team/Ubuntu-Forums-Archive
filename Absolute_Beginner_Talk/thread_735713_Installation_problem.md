---
title: "Installation problem"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by rltw on 2008-03-25
I need to manually set up a partition on the disk on which v7.10 will be installed from the CD. Evidently this means I need to define a root file system on the Linux partition, but I see no option for doing so in the GUI.

This disk has 2 Win2k installations on the first 2 primary partitions. I was hoping to install Ubuntu on the first to avoid having to reinstall the Windows apps which are on a logical drive.

---

### Post by MeTylerDurden on 2008-03-25
there must be something for that in the menu.. i am just glad i didnt have todo any of that .. try searching forums for help ..   find some install links
[http://ubuntuforums.org/showthread.php?t=613462](http://ubuntuforums.org/showthread.php?t=613462)

---

### Post by knightcoder on 2008-03-25
Can you see two separate partitions on windows ??
If so, you can use the one which doesn't have windows to install ubuntu.

---

### Post by knightcoder on 2008-03-25
Sorry, I didn't read your message properly.
I think you may face problems when installing on the first one ..... I'm not entirely sure. But you should have no problems installing on the second one, if its a primary partition.

---

### Post by rltw on 2008-03-30
So far what I've gotten out of this is a greater appreciation for Windows.

I finally figured out that the way to define a root file system was to type "/" in the field where you specify how the partition will be used. The option only appeared in the pulldown menu after I had formatted the partition as ext3.

But that turned out to be moot. Despite reading here that this version needed at least a 10gb partition, the installer called for a minimum of 2gb, which was about 100 mb less than I had, so I tried it. The installer sat there "detecting file systems" for several minutes before I aborted to format the partition with gparted. After I restarted the installer, it finally proceeded to start copying files. At about 80% completion, I was notified that the target drive was full, but the installation proceeded anyway. Finally it tried to install grub, which produced a fatal error, and evidently corrupted the MBR as well, so I ended up deleting the Windows partition and reinstalling.

Having said all that, I have to add that I ran the check of the live CD, which said 1 file was bad; but of course it didn't say which file, so for all I know it  could have been insignificant. The MD5's of the .iso and the CD were both correct.

So anyway, I think there's some room for improvement on the installer.

ETA: Before I did any of this, I did move the Windows OS to the first partition on the drive.

---

### Post by rltw on 2008-03-30
Switched to Xubuntu 7.1. CD self-check says no errors. Deleted and recreated the ext3 and swap partitions. Went through all 7 installation steps - this time canceling the grub installation - and again it hung at 15%, "detecting file systems", with the disk showing a spike of activity about every 2 seconds. Aborted the install again, and can't restart it without rebooting. No error messages.

Anybody?

---

### Post by Tatty on 2008-03-30
You really shouldnt attempt to install Ubuntu to a 2Gb partition, its just not going to work.
Remember that on any file system you should always keep at least 20% free, because it will cause fragmentation problems if it gets fuller than that.

It sounds like you are making this install harder than it needs to be...

Which installer are you using?  Live CD or Alternative?  You should use the live CD if you can because it is much more user friendly.

1. Check the Md5 hash of your .iso file, then burn it again really slowly.
2. Before installing, use the "check cd for errors" option on the menu that pops up on boot.
3. boot to a live CD, reduce your windows partition (if you still have it) to a sensible size and leave at the very least 10Gb free for Ubuntu.
4. Dont create any new partitions manually, ubuntu can do that for you. simply leave all the space for ubuntu as unallocated.
5. start the installer, when the partition section comes up, select the option which is something along the lines of "use free space on the disk", and that should grab all that unallocated space that you left free, and it will automatically partition it for ubuntu.

You will be left with three partitions:

1 - for your windows install
2 - for your Ubuntu root and home
3 - for your Ubuntu Swap

---

### Post by rltw on 2008-03-31
> **Tatty said:**
> You really shouldnt attempt to install [X]Ubuntu to a 2Gb partition,According to Xubuntu.org, the minimum partition size is 1.5 gb. IF that's wrong, what is the minimum? Or, what kind of Ubuntu derivative can I fit in 2gb?

---

