---
title: "Preparing for a full installation"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by RKCole on 2007-05-29
Hello, everyone.

I am finally in the process of preparing for a full Ubuntu installation.  The main thing holding me back was the fact that my Lexmark X2470 did not work in Ubuntu (not the fault of Linux, however); unfortunately, I would not be able to afford a new printer for awhile.  Luckily, though, I learned how to utilize VirtualBox and install Windows XP as a virtual machine.  Through this I can use my printer while still running Ubuntu as my primary OS; it's still bad that I have to use Windows, though.  

Anyhow, I have a few questions before I get things backed up and ready for the full installation.  First, here are my specs:

Dell Dimension 4600i
Pentium 4 (2.80GHz), 1GB PC2700 DDR SDRAM
nVidia GeForce FX 5500 AGP card with 256MB onboard video RAM
Primary HDD:  250GB Western Digital IDE HDD (Currently holds Windows XP)
Secondary HDD:  80GB Seagate ST380011A (Holds my current Ubuntu installation)
Samsung CR-R/W Drive
LG DVD-ROM Drive (Currently not working)
Standard 3 1/2 Floppy Drive

Everything works just great in Ubuntu under these specs; my reason for posting the specs relates to the following questions.

1.  I know that there are many different ways for partitioning for a Linux installation.  What would be a good way to partition for this installation?  I typically partition in this manner, but I am not sure if it is optimal:

**(/)** (usually I size this around 6GB+)--formatted as ext3
**(/home)** (usually sized using the majority of available space)--formatted as ext3
**(/windows)** (usually 7GB+)--formatted as FAT32--I am not sure if I will keep this partition or not in a full installation.  Any suggestions on this one?
**swap area** (this should be twice the RAM, but no more than 512MB, right?)

As far as the partitioning is concerned, what should be primary and what should be logical?

2.  I was testing VirtualBox last night to see how things worked with having Windows XP running as a virtual machine.  Needless to say that things worked pretty well (except for a problem with full-screen which I do not know how to solve yet).  Anyhow...is it possible to back up my Windows XP virtual machine so that I do not have to re-create one?

3.  Is there any way to "copy" my current installation to the new drive, or would I just need to do a fresh installation?

4.  Are there any type of open source cloning programs for Linux (like Acronis TrueImage or Ghost) that I can use to take a snapshot of my new installation in case something goes wrong?

5.  I would like to use Gutsy when it comes out, but I'm still somewhat leery of doing a dist-upgrade.  Wou8ld this be a problem?

Well, I guess that's about it.  Thanks for any and all responses/suggestions.  I'm looking forward to going through with this. :)

Take care.

---

### Post by starcraft.man on 2007-05-29
1) Setup seems fine. I personally prefer 1 GB at the max, more can never hurt and you have plenty of GB left over :p.  As for the window partition, I would give it more than 7, probably closer to 12. A lot of things can collect in the C drive of a window install even if you install everything to another shared drive (especially updates, they are pesky). And its easier to have more than run out of space later. I would also make it NTFS (the ntfs-3g drivers for Ubuntu work very well, I don't really see a reason to lower yourself to using fat32).

2) Long as i know, like any other VM, all you do is back up the virtual hard drive and config file and you can then put them on your drive again after you install. Just burn them to a DVD or offload them somewhere else. You can easily find where the files are at by going into File > Global Settings and checking where the VDI and machine folders are. Then when you reinstall, point vbox back at the old files.

3) I'm not sure what you mean by current installation... if you mean how Ubuntu is configured, you have to reinstall things far as I know if you do a clean install. If you mean put back your windows partition, use the image programs I suggest in 4. Please clarify.

4) All you need is an imaging program to do that. There are a few like [here.]("http://linuxappfinder.com/backupandrecovery/driveimaging") I can't really recommend any one in particular, I still use (sadly) acronis true image, mostly because I have far too many backup (TIB files) with it and it would be a pain to reimage. 

5) You can do a clean install over Feisty when gutsy comes out (in october I think). You can also install it and add it as an extra boot option if you want to try it out. You don't have to do a dist-upgrade to get to it though. Or you can even just continue using Feisty. There are many happy Dapper users for instance.

Hope that answers your questions. :)

---

### Post by RKCole on 2007-05-29
starcraft.man,

Thanks for the response.  As far as the /windows partition goes, I wasn't sure if I should keep one as there will no longer be a Windows installation on the computer, unless the VM would be considered as one.  :)  This is why I was so unsure of whether or not I should still have a /windows partition, or if I should just have a backup/storage partition instead.  See...I will still be working on Windows computers for others (as I am kind of a freelance tech to some extent), and so I have a lot of free software that I keep (OpenOffice.org, GIMP, and many more) to install on client PCs at their request.

As far as upgrading to Gutsy when it comes out...I would just use the installation CD and opt for an upgrade install, right?  That should keep any personal data (such as pictures and documents) intact, correct?  Regardless, there will be backups.

I'm really looking forward to this.  The thing that makes me feel even better about it is that my wife has finally been messing around on Ubuntu, and she seems to like it.  Before this she had an anti-Linux type of attitude.

Thanks again for the response, starcraft.man.

---

### Post by RKCole on 2007-05-29
Sorry, starcraft.man, I missed your request for clarification in #3 in your answers.

I currently dual boot Windows XP and Ubuntu; I want to replace Windows XP completely.  XP is on my 250GB drive at this time; this is where I intend to install UBuntu.  I was basically curious as to whether or not I could carry over the settings of my current installation (on the 80GB drive) to the 250GB drive after installation.

I apologize for not explaining that better.  Thanks again.

---

