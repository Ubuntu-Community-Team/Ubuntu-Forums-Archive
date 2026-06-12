---
title: "Dual boot xp and ubuntu issues."
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by tibetanpunk on 2007-04-28
I had xp installed on a 18gig partition on a 80gig drive divided into four partitions of roughly equal size (18gigs).
The remaining free partitions were used for data storage only. I cleared them out, backing all the files up onto an external hard drive and then set about installing Ubuntu which I am so far very impressed with. 
The installation went smoothly and I was able to boot into Ubuntu and everything was fine. I then restarted and tried to boot into my XP and I got a message saying that the windows system file 'hal.dll' was either corrupt or missing. 
I tried various things to solve this and nothing worked, so I ended up reformating and re-partitioning the entire drive and then re-installing windows.
I partitioned the drive as follows:

1st partition is 12 gigs and has the XP installation on it. 
2nd and 3rd are both 20 gigs each and will be used for data storage. 
4th is 10 gigs and will be used as either the FAT32 shared partition or the actual Ubuntu install.
5th is a 2 gig partition for the swap file.
6th is a 12 gig drive and will be used as either the FAT32 shared partition or the actual Ubuntu install.

I would like to be certain that this is set up properly, the partitions apart from the first two are still unformatted.
Is there a way that I can be certain that I will not encounter the same problem as before? I think the main reason for the corrupted xp installation was the device id was not the default one in the Ubuntu config on the MBR.
Any help would be greatly appreciated.
John

---

### Post by tibetanpunk on 2007-04-28
Ok, I seem to have resolved this issue by myself. I will explain how I was able to do it here and how to avoid the problems I had first time I tried (using my brand spanking new dual booting Ubuntu install!!!).
First, you need to make sure that your Windows XP installation is on Dev/Sda1, you can do this when you run the emulated Ubuntu that you can boot from the cd. 

When you boot from the Ubuntu cd, begin your install as normal, select your location, name etc. until you get to the partitioning tool within Ubuntu. 
From here, identify the partition (if you have more than one already) that contains your XP system files, it should be labeled 'Sda1' or as other people seem to see it 'Hda1'.  If you only have one partition you should be sweet, you can simply resize the one you have as long as you have compacted all the files so that they are all at the start of the drive (using windows defrag or equivalent).

This is IMPORTANT, if your XP system partition is not registered as 'Sda1' or 'Hda1' within the Ubuntu partition manager, quit the install for now and go and back up all of your XP related files because you will need to do a fresh install of XP in order for the dual boot to work correctly. 
That is unless you are very computer savvy and can work out how to resolve the issue when XP freaks out and refuses to load any more

If your XP system partition is Sda1 or Hda1 you are good to go, when you go to the next stage of the installation it will automatically recognize your windows XP installation and ask you if you want to import your profile from XP to the Ubuntu OS. I chose to let Ubuntu import my profile from windows XP. Then simply wait for the install to finish and restart, both XP and Ubuntu should be fully working and you now have a dual OS booting system! Congratulations! Give your self a nice pat of the back...And relax.

Ok, now for the people who were not so lucky... If your XP installation did not show up as Sda1 or Hda1 (like when I first tried to do this and it went horribly wrong when I installed Ubuntu, rendering XP useless) and you don't know much about command lines and such in order to fix the problem, well...Sorry, you are going to have to reinstall XP. So you are going to need a working copy of XP to reinstall from and probably back up the hard drive you are planning to re-install/reformat.

The way I did it was like this on an 80 gig hard drive:

1. Boot from the windows XP disk.

2. Follow the prompts to install XP until your get to the XP partition manager screen.
    
3. Create a 12 gig partition for your XP install (follow the prompts on screen that explain how to do this if you don't know).
    (delete previously made partitions if there were any. Follow the on screen prompts to do this)

4. Create 2x 20 gig partitions for data back up (my personal preference is to have most file types on separate partitions. One for games, one for videos, music etc, though you could just make your XP partition much bigger if you don't care)

5. Create a 10 gig partition for your Ubuntu (which you will install later).

6. Create a 2 gig partition for the Ubuntu Swap file.

7. Create a partition with the remaining space that you can later use as your FAT32 shared OS folder (there should be about 12 gigs left on the drive).

Still with me? Good.

Begin your XP installation as normal until XP is installed. Done. 
Boot into windows, right click 'My computer' and on the menu that appears click on 'Manage'.
Maximize this window and then click on 'Disk management' which is on the little program tree on the left hand side of the screen. The disk management utility should load.

From within disk management you should be able to format the partitions you have just created. Your XP installation should be the first partition and will be a primary partition, the others will appear as 'unformatted'. 
From here you can right click on the 2x 20 gig partitions and then select 'format' from the menu, make sure you have the right drive selected, procede past the warning message and then format the 2 20 gig drives, one at a time to NTFS file system (unless you have other plans for them).

After formatting has completed this you should be left with the 10 gig, 12 gig and 2 gig partitions. Now is the time to restart your computer and boot the Ubuntu cd.

My copy of Ubuntu had a slightly different menu system to the ones that I have seen tutorials on, so I was kind of in the dark as what to do. But actually it is pretty straight forward. I selected 'Install or run Ubuntu from the cd' option, the first option on the list and the emulated version of Ubuntu booted up to the OS.

I then selected the install icon off of the desktop and followed the steps to the partition manager. From here I selected 'manual' and continued.
On the next screen it said 'scanning drives' and showed all of the available partitions, my newly installed XP showed up as 'Sda1' (YAY!)

I selected the unformatted 10 gig partition, set it up as ext3 with the mount point '/'

I then selected the unformatted 2 gig partition and set it up as 'swap'

Then I selected the unformatted 12 gig partition and set it up as 'FAT32' with the mount point '/Data'

Then I simply hit next and the install had begun, I played guitar for a little while and chanted 'Om mani padme hung' in tune with the chords and in a little while the installation was done.
Then I restarted my system.

When I restarted I decided to check my XP installation was still good, XP booted as normal and everything was sweet. (YAY!)
I then rebooted again to make sure that Ubuntu was working fine, at first I did get an error message about the screen refresh rate being out of range and I had no picture. So I hit reset on my computer and started Ubuntu in recovery mode, then on the command prompt entered 'startx' and Ubuntu booted normally and here I am writing this for you, the poor confused nerds of the world...lol

Anyway, I am well pleased that I got this to work, I use XP primarily for audio recording, so now I can strip down XP (get rid of all the non-audio applications and services) so that it is nothing more than a hard disk recorder for audio and I can hopefully use Ubuntu for everything else while taking advantage of the stability and security that I hear Linux based systems offer.
I hope that this is useful, and good luck to you!
John

---

### Post by Austin_KW on 2007-04-29
Ok, I am no windows expert.
But I would not want people to go reinstalling windows just because it in not installed in the first partition. The ubuntu install should detect your windows on whatever partition and add the appropriate entry to your grub menu.

I assume the the problem here was that you resized and moved the windows partition. So that it now appears on a different partition number. I think that this can be fixed by editing your boot.ini and changing it to reflect the new partition number.

---

