---
title: "Can't create HFS+ Partition"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by mph66 on 2006-10-11
Howdy,

This is my first post, please be nice.  :D

I've backed up all my data and installed Ubuntu.  After going through some initial cartwheels to get the config file altered to the refresh rate required by my eMac, I was up and running.  I've formatted the entire drive.  Linux is great, but I still need some Mac progs in my life.  So I reboot from the Ubuntu Live cd and, lo and behold, when I go to manually edit partitions, I can't create an HFS+ partition.  I need to create an HFS+ partition so that I can:

1) reboot from a Mac OS X cd.
2) Reformat/partition the drive for Mac/Ubuntu
3) Re-install OS X
4) Re-install Ubuntu
5) Re-install progs.

This is a PPC eMac 1Ghz, 512 revB(?)

Any clues for this Ubuntu nooblet would be greatly appreciated.  This forum has already been a great help in getting started with Ubuntu, a much more user-friendly distro than Fedora, IMHO.

Best,

Marc

---

### Post by PriceChild on 2006-10-11
You could try using the gparted livecd: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I'm not sure why you're unable to do it in ubuntu's live cd... but i suppose i've never found it too stable either.

---

### Post by mph66 on 2006-10-11
...sez that the Gparted cd will run on x86 machines.  The eMac is a PPC chip.  I do thank you for the suggestion, though.  Perhaps there are other open source boot disks out there for the Mac.  I just don't know of any.  Or at least not yet.

Thanks,

-Marc

---

### Post by randiroo76073 on 2006-10-11
Do you have the live cd for MAC, or are you possibly trying this from I86 cd[don't know if it would even boot]?  See if these links help:
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)
Here's a google for yaboot:
[http://www.google.com/search?q=Yaboot&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official](http://www.google.com/search?q=Yaboot&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)
Here's another that might help:
[http://www.google.com/search?q=Mac-on-Linux&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official](http://www.google.com/search?q=Mac-on-Linux&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)

HTH

---

### Post by PriceChild on 2006-10-11
> **mph66 said:**
> ...sez that the Gparted cd will run on x86 machines.  The eMac is a PPC chip.  I do thank you for the suggestion, though.Sorry about that... maybe there's a Knoppix livecd... seems not... latest posts about its betas are in 2003 :S

---

### Post by Najand on 2006-10-11
Best way is to use Mac's CDs and partition. 

1. Insert your Mac OS X installer CD into the drive. Restart your Mac while holding down the 'c' key on your keyboard to boot from the installer CD.

2. When the OS CD installer dialog box launches double click on the 'Install Mac OS X' icon. At this point you do not want to install so do not click on 'continue'.

3. From the menu bar at the top of the screen click on Installer, slide down to Disk Utility. This will open the Disk Utility program. Click on the Partition tab and select the drive that you want to partition.
And follow the partition process to make a fs+ and an emty space for your linux. 

It is better to reinstall your Mac at this moment

After installation finished try installing ubuntu using the live cd.
(sometimes it fails to install yaboot when you select partition manually in Ubuntu Installation Process, so it would be nice to selece "install ubuntu on the biggest free partition" and continue.)

---

### Post by mph66 on 2006-10-11
Yes, I've tried to re-install from the Mac OS X cd.  I musn't have explained myself clearly.  Sorry.  Because I've reformatted the whole drive for Linux, when I insert my Mac OS X cd, it won't boot.  I instead get a menu that says:
l to boot Linux
c to boot cd

So, naturally, I hit "c" to boot from cd.  I get "..." and then it reverts back to the menu.  No boot from the OS X cd.

So now I'm trying to get a toehold on my hd with an HFS+ partition so that MAYBE I can boot from the Mac OSX cd and reformat the drive.  Mac's Disk Utils tools are much better for formatting partitions, and I can get a reinstall of the Mac system and make space for the Linux system.  

At the moment, I can't do that.  I'm trying to figure out how to get my Mac OS X cd to boot so that I can get the job done.  Hopefully, this clears up any confusion.  Sorry for any confusion my description might have caused.  A

Most of all, thanks to all who are responding to the query.  I really appreciate your efforts!

-Marc

---

### Post by mph66 on 2006-10-11
Yes Randiroo, I'm 100% sure I'm booting from the PPC Live cd.  Otherwise, I couldn't have gotten Linux installed on a PPC disk because you're right, an X86 Live cd wouldn't boot a PPC Mac. :)

-Marc

---

### Post by mph66 on 2006-10-11
BTW, It's a G4 PPC processor, to be precise.

-Marc

---

