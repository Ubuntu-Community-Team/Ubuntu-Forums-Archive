---
title: "&quot;No Bootable Disk -- insert boot disk and press any key&quot;"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by chris24 on 2007-11-24
Hi,

I have an Intel Mac, and wanted to boot up gOS (thinkgos.com), which is apparently based on Ubuntu (which is why I came to this great community for support!). In OS X (Leopard), I selected the linux boot DVD from the Startup Disk preference. I booted, and it booted into the gOS installer. There was some sort of install error. gOS ejected the disc after it got an error. I tried booting back into OS X, and it didn't work (All the different Mac OS X Boot keys didn't work, such as C, etc). I then inserted the Mac OS X Leopard Install Disc to change my startup disk, and that didn't boot either (using C, etc). Now, I have my Leopard Disc in my Mac (iMac Core Duo, 2.0Ghz), and the eject boot keys aren't working now. I also have an external hard drive, with a bootable Mac OS X Tiger partiiton - that wouldn't boot either. I'm getting the error "No bootable device -- insert boot disk and press any key". Of course, I can't enter my physical disc, so I decided to use a USB Flash (key) drive to boot up Ubuntu, in order to change my startup disc. I am having a little difficulty of installing ubuntu on it. 

Here's what I've tried: Format the USB Flash Drive as an HFS+ volume (using a Windows PC... I am clueless, I don't know if this is the correct format?), then moved the files from my ubuntu live dvd onto the drive. I now get "missing operating system" when I plug the Flash drive (with ubuntu) into my Mac. How can I install Ubuntu onto a USB Flash Drive (Which format like HFS+, FAT32?), for an Intel-based Mac, in order to change my startup disc? 

Thanks for all your help! :-)

---

### Post by anewguy on 2007-11-24
First, I'm not sure if formatting the USB flash drive in NFS would work or not.  Also, I'm not sure that just copying the files to it would work - remember we burn a CD as an image for this LiveCd, not by a file-by-file copy.  People who do the normal burn instead of an image burn run into these same type of problems as you are having with your USB flash drive. It sounds like it is also missing any boot loader information, and I'm not sure how you get those onto a USB flash drive.

I think I would start by searching this forum for running Ubuntu off a flash device - I have seen postings on this.  Perhaps they can help you get to where you want.

---

