---
title: "Update Hardware and Drivers info"
date: 2006-11-27
forum: Apple PPC Users
---

### Post by Hawkeye05 on 2006-11-27
I just swapped a Hard Drive out of an IBook and put it in a Powerbook, Different Graphics cards Resolutions etc. anyway i cant get anything to display, i have vital files on the HDD that i need to get and id prefer to use KDE instead of Terminal, im looking for a command that can update all my hardware dirvers etc. also i need the command to refresh my ethernet interfaces (to find the network connection) Any help is GREATLY APPRECIATED!!!:mrgreen:

---

### Post by Zarephath on 2006-11-27
Why would you not backup your critical data first then you could just format the drive, reinstall, and be done with it...As for your problem I would have assumed that when it booted it would re-detect your system hardware and re-align the setup...since this is not the case there is more than likely a piece of hardware that won't allow this to happen. My suggestion would be put it back in the original computer, backup the data...then format and reinstall after putting it back in the other computer...then restore your data backup...far easier and less time wasted trying to make it work the way it is currently...

---

### Post by stmiller on 2006-11-27
> **Hawkeye05 said:**
> I just swapped a Hard Drive out of an IBook and put it in a Powerbook, Different Graphics cards Resolutions etc. anyway i cant get anything to display, i have vital files on the HDD that i need to get and id prefer to use KDE instead of Terminal, im looking for a command that can update all my hardware dirvers etc. also i need the command to refresh my ethernet interfaces (to find the network connection) Any help is GREATLY APPRECIATED!!!:mrgreen:

Yeah. Backup first! Good grief, man. This is a lesson learned, I suppose.

You could try booting the PPC live install disc, then mounting your home directory from the internal disc and get files off that way onto your home network. Backup before doing anything crazy like changing a hard drive. The powerbook uses an nvidia graphics chip, while the iBook is ATI. Very different; I'm not surprised X would not start. I suppose the network interface is different also.

If the live CD doesn't boot into the live desktop, you can choose the 'rescue' option at boot (hit tab at the boot prompt) and get files off that way, from the command line.

When you have everything backed up, I'd try an Ubuntu 'update' from the install disc. See if that works. Good luck.

---

