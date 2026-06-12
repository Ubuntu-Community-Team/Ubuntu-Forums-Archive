---
title: "Complete noob question."
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by johanhartman on 2006-05-11
You might class me as less than a complete beginner, coz i haven't even installed ubuntu yet. The reason for this might well be rather stupid but also rather important. I want to install ubuntu but onto a computer used by other members of my family who wants to keep windows. My questions are: When I first boot from the iso cd and i install the ubuntu, will a partition be created automatically so that I can boot to windows when I want, and.. If it does create the partition how do i reboot to windows when the need arise.:-k 

I do reealise that to many of you this may sound like a stupid question and I myself feel ashamed asking it but any help will be greatly appreciated:)

---

### Post by shurguywutt on 2006-05-11
about how much free space is left on your hard drive?

---

### Post by bigred on 2006-05-11
If you don't have anymore free space u will have to delete the windows partition which would erase everything.  Google for dual boot with windows and ubuntu as they have a nice video on how to install it and that would give you the info you need.

---

### Post by johanhartman on 2006-05-11
[QUOTE=shurguywutt]about how much free space is left on your hard drive?[/QUOTE]

20.7 gb left of 37.2gb

---

### Post by Fredde on 2006-05-11
Boot a livecd and let them play around with it.

---

### Post by confused57 on 2006-05-11
If you have a fast internet connection, I'd recommend downloading both the LiveCD and the install .iso.  Make sure to burn the .iso "as an image", don't burn directly as a data cd.  Check your cd burner software & look for the word "image".  Burn the cd 4x-8x, lower speed, the less chance of corruption.

Try booting up with the LiveCD first, make sure your bios is set to boot from the CD drive first.  There could be hardware incompatibility problems, so it's a good idea to run the LiveCD on your system first; it doesn't install, just runs from ram memory(if you have enough ram).  If the LiveCD works OK, then go ahead and install Ubuntu.  

Here's the best guide for dual-booting:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

If you don't understand anything, don't hesitate to ask questions before you begin installing.

---

### Post by shurguywutt on 2006-05-11
alright well just download the newest ubuntu iso. correctly burn it to a cd.  insert the cd, restart your computer, follow some of the instructions.  when u get to the partition part, choose manually set up partition then select automatically configure free space. or some variation of that.  i cant remember the exact messages.

---

### Post by Rinzwind on 2006-05-11
[QUOTE=shurguywutt]alright well just download the newest ubuntu iso. correctly burn it to a cd.  insert the cd, restart your computer, follow some of the instructions.  when u get to the partition part, choose manually set up partition then select automatically configure free space. or some variation of that.  i cant remember the exact messages.[/QUOTE]

That's an advice I'd not give to a newbie. 

I'd advice to download a trial of Power Magic (IF your country allows you to download software) and do this from within Windows. PM is excellent for partitioning and it's more intuitive than a partitioning by hand.

---

### Post by Kvark on 2006-05-11
[QUOTE=Rinzwind]I'd advice to download a trial of Power Magic (IF your country allows you to download software) and do this from within Windows. PM is excellent for partitioning and it's more intuitive than a partitioning by hand.[/QUOTE]
Yeah or the free trial version of [Partition Magic]("http://www.soft32.com/download_151.html"). Shrink your windows partition. Make a FAT32 partition that is big enough for any files you want to use from both Windows and Ubuntu. And leave 10 GB or so unpartitioned for Ubuntu's installer to partition. Then tell the installer to use all the free space on the disk (don't tell it to wipe and use the whole disk!).

---

### Post by aysiu on 2006-05-11
[QUOTE=confused57]
Here's the best guide for dual-booting:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)[/QUOTE] I agree. This link will tell you everything you need to know, and it walks you through the process (with screenshots).

---

### Post by K.Mandla on 2006-05-11
[QUOTE=Kvark]Yeah or the free trial version of [Partition Magic]("http://www.soft32.com/download_151.html"). [/QUOTE]
I thought the trial version didn't allow you to make changes to the disk? I might be wrong. It's been a while since I used PM. :-?

---

### Post by catlett on 2006-05-11
Confused57's link is the best I have seen so far. But just to make a quick suggestion. The install can do the dual boot very easily.
First make sure your computer can boot from a cd. This setting is in the computer bios. Try and restart your computer with the cd in and see if it boots. If not when your computer first starts look for the quick image of your computer company's logo. This screen will have an option listed (something like press F12 for setup. Not all computers are the same).
This will take you to a menu. Look for a title of "boot" or "boot options". This allows you to list the order the computer starts. Mine is floppy, cdrom,hard drive. The main thing is to have the cd drive listed before the hard drive.
When the cd boots you will come to a screen...press enter.
The install will detect a few things and then it will come to the important part, partitioning.
Choose the option "resize your current partition". Sorry I don't know the exact wording but it does say resize and there is only 1 resize option. Confused57's link has a screen shot.
Once you select the resize option THAT's IT! The installer will automatically resize your windows partition and make the partitions for Ubuntu. You have plenty of free space. The installer takes around 10 to 12 gb (sorry again I don't know ther exact number)
After that follow all prompts. Most of the time you can just accept the defaults by hitting enter.
The install will install a bootloader. Say yes to everything. What it will do is overwrite the windows boot manager with a bootloader called grub (grand unified bootloader).
Grub will be the screen you see when your computer starts. It will have a menu with an option for windows and ubuntu. You pick one and grub starts it. You will have to restart your computer to switch between systems.
It is relatively simple and safe BUT accidents can happen. You should make a backup of your windows system before you start just to be safe. Good luck.

---

### Post by Rinzwind on 2006-05-11
[QUOTE=K.Mandla]I thought the trial version didn't allow you to make changes to the disk? I might be wrong. It's been a while since I used PM. :-?[/QUOTE]
I didn't use them but when I say trial you should be reading it in between quotes ;)

edit:
In my opinion windows should have a native program that allows for partitioning. I consider it ABSURD windows doesn't have one.
If I have any beef with Windows it's that. Someone pays them money and they skip a feature that's truly needed for a good computer administration.

That windows can only delete a partition where it's obvious that that is totally not needed validates for me the usage of a one-time copyright infringement.

---

### Post by steve.horsley on 2006-05-11
[QUOTE=johanhartman]20.7 gb left of 37.2gb[/QUOTE]

I assume Windows is already there on a 10 Gig partition.
If that is genuine free space then you are all set. If it's an unused partition, delate that partition to leave unused space. Just run the installer and when it gets to the partitioning, tell it to use the unused space. It will use all of it, creating two partitions - a system partition and a swap partition. It will also set up the bootloader to give you a choice of windows or Ubuntu.

Back up your data first. Just in case.

---

### Post by johanhartman on 2006-05-12
I have followed [this]("http://users.bigpond.net.au/hermanzone/") link and read through it, but it talks about a logic swap partition, what is this for and how many space do you recomend I allocate to it?

---

### Post by RRS on 2006-05-12
Swap is normally recommended to be twice the size of your computers RAM. The system uses it like additional ram space.

I seem to recall the swap partition being sized and created automatically but it does ask permission first.

Herman's site helped me a great deal and you'll find it recommended thruout these forums.

One other thing, in addition to backing up your Windows data it's also a good idea to defrag the drive before installing too.

Welcome to Ubuntu :)

---

