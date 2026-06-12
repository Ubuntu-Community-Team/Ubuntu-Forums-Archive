---
title: "Selecting partition on Apple PPC G5 system"
date: 2014-11-12
forum: Apple Hardware Users
---

### Post by mlevin77 on 2014-11-12
I am installing Ubuntu 12.04 LTS onto an Apple PPC G5 system. I've got it  booted off the live CD and am trying to install it. Partitions I have, according to "sudo blkld", are sda3 and sda5, which are on  one drive, and sdb2 which is on another drive. What I want is to leave sdb2 untouched (it has OS X 10.5.8 on it), and to install  Ubuntu onto sda. I selected New Partition Table, and set up a partition for swap, and a partition of type "newworld" which it automatically set as / mount point. But now when I hit "Install now", it says "No root file system is defined. Please correct this from the partitioning menu." even though I have the / set for a sda3 partition (340 Gb). What am I doing wrong?

---

### Post by rican-linux on 2014-11-12
Check out this tutorial over at the PPC Luddite blog [here]("http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-ii.html"). Also check the Ubuntu's PowerPC FAQ wiki [here]("https://wiki.ubuntu.com/PowerPCFAQ#What_do_I_need_to_know_for_dual-booting.3F").

---

### Post by este.el.paz on 2014-11-12
> **mlevin77 said:**
> I am installing Ubuntu 12.04 LTS onto an Apple PPC G5 system. I've got it  booted off the live CD and am trying to install it. Partitions I have, according to "sudo blkld", are sda3 and sda5, which are on  one drive, and sdb2 which is on another drive. What I want is to leave sdb2 untouched (it has OS X 10.5.8 on it), and to install  Ubuntu onto sda. I selected New Partition Table, and set up a partition for swap, and a partition of type "newworld" which it automatically set as / mount point. But now when I hit "Install now", it says "No root file system is defined. Please correct this from the partitioning menu." even though I have the / set for a sda3 partition (340 Gb). What am I doing wrong?

@melvin:

You might be confusing the installer by splitting the install on two drives.  If this is your first install process in linux, first try it the easy way.  Using Disk Utility in OSX (hopefully you are doing "dual boot"?), cut out 50 GB or so, set it as "free space" and erase, or format it as "FAT" . . . then boot the install disk . . . when the choice for "install along side OSX" or "install into largest free space" . . . pick that one . . . and let the installer cut the partitions as it will.  It should install Yaboot, which will let you pick which system you want to load . . . .

Then you can look at the GParted table and see what it selected for each partition.  Later, if you need 340GB for the system you can do the install again . . . but, general wisdom is to keep a partition for oSX alive . . . .

e.e.p.

---

### Post by mlevin77 on 2014-11-13
>  You might be confusing the installer by splitting the install on two drives.  

   sorry, what do you mean splitting the install? I just want to install Ubuntu onto one drive (wipe the whole thing), and leave the other drive alone (leave the OSX on it). Do you mean I need to remove one of the drives so that the machine has only 1 during the install process?

> If this is your first install process in linux, first try it the easy way.  Using Disk Utility in OSX (hopefully you are doing "dual boot"?), cut out 50 GB or so, set it as "free space" and erase, or format it as "FAT" . . . 

   ok, so I go to OSX, and use Disk Utility to format the 2nd disk (the one I want to be all Linux) as FAT, right?

> then boot the install disk . . . when the choice for "install along side OSX" or "install into largest free space" . . . pick that one . . . 

   I never saw this option. When I booted off the Live CD and ran the Installer that was on the desktop, I didn't see anything like that option. Am I running the wrong installer perhaps?

---

### Post by mlevin77 on 2014-11-13
Aha. Now I see that I actually need 3 partitions: an Ext4, a swap area, and a NewWorld. What's weird is that those instructions say to name the partitions (and this installer's partition editor doesn't give me a field for naming them) and it also says to tick various bootable and mount options flags, which also don't appear here at all. Which one should be "/" - the NewWorld boot partition or the Ext4? If I give Ext4 the / mount point, then it automatically assigns NewWorld to /home - is that right?

---

### Post by este.el.paz on 2014-11-13
> **mlevin77 said:**
> Aha. Now I see that I actually need 3 partitions: an Ext4, a swap area, and a NewWorld. What's weird is that those instructions say to name the partitions (and this installer's partition editor doesn't give me a field for naming them) and it also says to tick various bootable and mount options flags, which also don't appear here at all. Which one should be "/" - the NewWorld boot partition or the Ext4? If I give Ext4 the / mount point, then it automatically assigns NewWorld to /home - is that right?

@mlevin:

My apologies, I was reading your post too fast to see what you actually said about the two drives . . . and it is something I've been thinking about for future ventures in linux . . . OSX on one and linux(s) on another.  So, right, you can set up 3 partitions, or 4 for some people who have a separate "/" & "home."  But, again, you should be able to use "automatic" to install the system . . . the installer should find the drive you want and install into it.  If it isn't "finding" it, perhaps you can try what I said about erasing and formatting it.  But, if you are just wanting to use the entire drive there shouldn't be a problem.

To answer the "flagging" question if you are doing the partitioning manually . . . try to double click on the line item in GParted, it should open a drop down window that lets you select "yaboot" for New World, "/" for home/root . . . and "swap" . . . but, should be easier to let the installer run the whole show from automatic.

e.e.p.

---

### Post by mlevin77 on 2014-11-13
Hmmm. Now it seems to have completed the install, but when I said "ok to reboot", the screen filled with multi-colored stripes of dots, and nothing would happen. Then I rebooted the machine with the button on the front, and it came up with the OS X.  How do I get it to actually boot into the Linux, assuming it did really install it?

---

### Post by este.el.paz on 2014-11-14
> **mlevin77 said:**
> Hmmm. Now it seems to have completed the install, but when I said "ok to reboot", the screen filled with multi-colored stripes of dots, and nothing would happen. Then I rebooted the machine with the button on the front, and it came up with the OS X.  How do I get it to actually boot into the Linux, assuming it did really install it?

@mlevin:

This might be where the actual work begins . . . is this a G5 iMac or PowerMac?  You might have to read through the forum posts on topics like "Testers wanted for 12.04" . . . and try to piece together the issues involved with getting linux to run . . . most likely you will have to either make or find an xorg.conf file that lists the proper video driver and/or screen resolution . . . .  It's fairly simple . . . either find the website with name like "linuxjemac.be" . . . and find your machine . . . or recently Boris Richard posted instructions on how to use the Terminal to set up an xorg.conf file in the recent "Fixing sound in 14.04" . . . something like that.

But, usually if the video card isn't selected then at least you get to the Yaboot windows . . . .  But, another thing is to use the option key on reboot, and that should load the OSX boot manager window, should show the OSX disk and the linux disk . . . use the arrow keys or mouse to click on the disk you want to boot from.  Other option, did you check the md5sum number for the iso?  Lastly, if you can't seem to boot the system, try to get the "SuperGrub2" app, burn it to CD and see if it will find the systems and boot them.  It could be that you need to find the right boot parameters to get the system into a clean GUI, it could be simple . . . or a bit more complicated . . . .  Back in 12.04 I had to work pretty hard to get the right driver set up on my iMac . . . and there is some stuff about G5 that takes some knowledge . . . don't have a G5 so I don't know what that might be.

e.e.p.

---

### Post by rican-linux on 2014-11-14
What are your screen dimensions? for my PowerBook G4 when I upgraded to Xubuntu 14.04 I need add set this yaboot parameter:

```
Welcome to yaboot version 1.3.16
Enter "help" to get some basic usage information
boot: Linux video=radeonfb:1280x854-32@60
```

You will need to match with your screen settings. More info can be found in this thread [here]("http://ubuntuforums.org/showthread.php?t=2218037")

---

### Post by mlevin77 on 2014-11-15
I'm not sure I'm even to the screen problem yet: when I reboot my machine, it goes to Apple OS not to the Linux: how do I tell a G5 PPC to boot off the Linux that was supposedly installed?

---

### Post by rican-linux on 2014-11-15
When you boot do you hit the alt key and even get the option to boot into linux?

---

### Post by mlevin77 on 2014-11-15
> **rican-linux said:**
> When you boot do you hit the alt key and even get the option to boot into linux?

   what's the Alt key on an Apple keyboard?

---

### Post by mlevin77 on 2014-11-15
> try to get the "SuperGrub2" app, burn it to CD and see if it will find the systems and boot them.

  I see it but is there a version for PPC G5 CPU?

---

### Post by este.el.paz on 2014-11-15
> **mlevin77 said:**
> > try to get the "SuperGrub2" app, burn it to CD and see if it will find the systems and boot them.

  I see it but is there a version for PPC G5 CPU?

@mlevin:

The SG2 app should work for any system . . . burn it to CD and boot with c key . . . if/when the linux kernel shows up . . . select it.  If it boots it may mean that Yaboot did not get installed . . . if nothing linux shows up the install did not work . . . try again.

e.e.p.

---

### Post by rsavage on 2014-11-16
Powerpc grub2 stuff is named ieee1275.

Have you installed 12.04 using the live ISO?

---

### Post by rsavage on 2014-11-16
> **rsavage said:**
> 
Have you installed 12.04 using the live ISO?

The reason I ask this is because I don't see how you've ended up in this situation with the 12.04 live ISO.  Normally, if the system doesn't automatically boot into linux, then something has gone wrong with the install, and in which case you wouldn't have got the reboot message (it would just crash before then).

Post 12.04, the installer was patched to prevent the crash, but you'll have to follow these instructions:

[https://wiki.ubuntu.com/PowerPCFAQ#I.27ve_lost_yaboot.2C_what_can_I_do.3F](https://wiki.ubuntu.com/PowerPCFAQ#I.27ve_lost_yaboot.2C_what_can_I_do.3F)

---

