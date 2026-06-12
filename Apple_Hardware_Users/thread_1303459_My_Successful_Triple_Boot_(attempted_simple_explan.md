---
title: "My Successful Triple Boot (attempted simple explanation)"
date: 2009-10-28
forum: Apple Hardware Users
---

### Post by sebovzeoueb on 2009-10-28
Hello there all,
This is my first post, in which I am going to explain how I managed to Triple Boot my MacBook Pro 17" unibody (version 5.2) with OS X Leopard, Ubuntu Jaunty and Windows XP Pro. I am a complete noob to the process, and would therefore like to share my experience in case anyone else is struggling. It seems to me that some of the explanations out there are unnecessarily complicated or include unnecessary steps. However this is more an explanation of what I did, rather than a guide on the best way to do it. See summary at the bottom for rapid explanation.

**[COLOR=Red]DISCLAIMER: I don't really know much about all this, and I arrived at my results through trial and error. I am therefore not responsible if this damages your setup in any way!! Back up your files! [/COLOR]**[COLOR=Red](I didn't, but it doesn't matter too much to me if I wipe everything)[/COLOR]

[COLOR=Black]-I started with my whole hard drive as OS X (after a few failed installations I managed to remove the Linux Swap partition by booting from the Ubuntu CD (using Ubuntu **without** installing it) and using the partition tool, as Disk Utility seemed unable to remove it, more about this later[/COLOR].

-It seems to me that you **do NOT need Bootcamp Assistant or rEFIt!** I originally did all this using rEFIt, but then realised it was unnecessary, so removed it. It is however possible that the gtpsync utility included with rEFIt may come in handy if your partition tables end up being out of sync (don't know much about this), but I was OK and I think you may be able to use this without having rEFIt installed, not sure though. You will need the Bootcamp drivers for Windows though, but not the partitioning assistant from OS X.

-It seems that the system used to boot Windows **can only deal with 4 partitions**, and Windows has to be the last one. There will already be 2 partitions on your hard drive: a small one called EFI, and your main OS X one. This means **you will need Linux as your 3rd partition and Windows as your 4th. **

-The best way I found to acheive this was to boot from the Ubuntu CD **[COLOR=Black]without installing Ubuntu[/COLOR]**, as mentioned above, as the partition editor included with Ubuntu, called GParted, seems to be the best (**hold down [C] at startup to boot from CD**). It is in System / Administration / Partition Editor in the menu at the top of the Ubuntu desktop (No mention of "GParted" until in the program itself). We need to resize the OS X partition and create 2 partitions **after** the OS X one. The 3rd one needs to be in some Linux format, I used ext4, and the 4th one in NTFS for Windows. I did this in a roundabout way using OS X Disk Utility to make the partitions, then realising I couldn't format them to the right format (Couldn't seem to install Windows without the NTFS partition, i.e. it didn't recognise other formats correctly, and wouldn't install on FAT for some reason) used GParted, so I would say to simplify things, just go with GParted form the start. Bear in mind that at a later point we will take a couple of GB off the windows partition (more about that later, I believe it may be possible to avoid this)

-At this point I installed Windows on the NTFS partition (insert Windows disk, press [C] at startup, follow instructions on screen, select partition 4 etc.). **To access windows you must hold down [alt] when starting/restarting**. This brings up a choice of boot disk. Once you have Windows up and running at this point you may install the Boot Camp drivers, then proceed to Ubuntu installation, or just go straight to Ubuntu installation and sort the drivers out later. That way you know everything works first.

- So, at this point I installed Ubuntu on my 3rd partition. To do this I chose to **manually edit partition table** when choosing the install partition, and select my ext4 partition as mount point **root**, which may just be called **/**. At this point I **shrank my Windows partition by 2 GB and made a Swap partition** (create a new partition with Swap format, right at the end of the hard drive, I think 2GB is more than enough, but not an expert on this). Then I proceeded with install.

-I think it may be possible to dispense with the swap partition altogether by creating a swap file in Ubuntu, but I do not know how to do this, and my setup works just fine with the swap partition.

-And voila, everything is installed and working, to accesss Windows or Ubuntu I just hold down [alt] and select Windows, which then loads GRUB (the dual boot selector for Linux) which lets you choose between Ubuntu or Windows. For OS X I just let my computer start normally.

-N.B. Windows first did some kind of CHKDSK thing after having it's partition resized, but once it had verified the disk it was fine.
[SIZE=3]
[/SIZE][COLOR=Green][B][SIZE=3]SUMMARY[/SIZE]

-No Bootcamp, no rEFIt, normal OS X installation.

-Make 2 new partitions using Ubuntu from CD boot. Partition 3 for Linux (ext3 or ext4), partition 4 for Windows (NTFS).

-Install Windows on Partition 4.

-Install Ubuntu on Partition 3, and shrink Partition 4 to put the swap partition at the end of the hard drive.

-Done![/B][/COLOR]

[COLOR=Black]Hope this may be of help to anyone struggling to acheive a triple boot. This worked for me, but as I say, there is no guarantee it will work for anyone else, seeing as some people seem to do this in a more complicated manner.

edit: Oh yeah, and for some reason, if I have my USB mouse plugged in it takes a painfully long time (maybe 5min) for GRUB to appear. I looked for a fix for so long before realizing that unplugging the mouse does the job!
[/COLOR]

---

### Post by PhoHammer on 2009-10-28
Haha! So funny that I found this post so soon after you put it up. I just got my MacBook today
and I want to put Ubuntu (or another Linux) on it. With all the talk of bootcamp and odd refit 
or whatever it's called it seems like it's harder to do on a Mac than on a PC...

So I wonder if I can use gparted to resize my mac os x partition then just install ubuntu from the 
live cd in a newly made ext4 partition. Does GRUB not override OS X's bootloader? 

And I wonder if there is any danger in resizing OS X partitions with gparted. I know Vista can have 
a heart attack if you don't use it's volume shrinker to resize its partition. Hopefully OS X isn't the
same?

---

### Post by sebovzeoueb on 2009-10-29
To be fair, I made my partitions using OS X Disk Utility, then formatted using GParted, but I think it should work doing it directly from there, Windows XP didn't seem to mind having its partition resized apart from doing some kind of verification at startup. Probably just Vista being difficult. If in doubt, check with someone who actually knows.

GRUB only appears when I select the Windows partition in the OS X bootloader (Which only comes up with Macintosh HD and Windows, no mention of Ubuntu), so no, it doesn't override it. 

If you are just dual booting, I think things shouldn't be too difficult, it seems to be the triple boot that is slightly harder to acheive.

---

### Post by PhoHammer on 2009-10-29
> **sebovzeoueb said:**
> .

GRUB only appears when I select the Windows partition in the OS X bootloader (Which only comes up with Macintosh HD and Windows, no mention of Ubuntu), so no, it doesn't override it. 


So it looks like when you do the alt boot, it comes up with a "Windows" option and if I only had 
ubuntu installed it would be the windows option that would take me to GRUB. I guess boot camp 
assumes you are using windows and just labels the option that way..

---

### Post by besweeet on 2009-10-30
I can't seem to get into Windows 7. After I installed Ubuntu 9.10 x64 yesterday, Windows 7 showed up in the list of boot entries in GRUB 2. If I try and select that, it will just kick me back to GRUB 2...
 
I want to reinstall GRUB 2 but have no idea how to do that.

---

### Post by pelle.k on 2009-10-30
sebovzeoueb, super nice guide. I particularly like the summary. Too bad i didn't have this guide back when i setup my triple boot. I learned everything the hard way. Just like you did, i imagine! :D

> After I installed Ubuntu 9.10 x64 yesterday, Windows 7 showed up in the list of boot entries in GRUB 2.
I did respond to you in that other triple boot thread, but anyway, this got me thinking. Did you install ubuntu on a new partition. If so, that partition must have newly created, and also at a position before the windows partition (well provided you have read the first post in this thread and understood it). **Meaning**, windows own bootloader is probably having problems locating the original position since you changed the structure of the disk.

Do you follow me here? If i'm wrong, stop reading here, otherwise, grub is not the problem here, but windows own BCD (like the C:\boot.ini file in XP). To edit the windows 7 BCD, boot the windows install disc to get a recovery command prompt, and follow these instructions; [http://ubuntuforums.org/showpost.php?p=7432521&postcount=5](http://ubuntuforums.org/showpost.php?p=7432521&postcount=5)

---

