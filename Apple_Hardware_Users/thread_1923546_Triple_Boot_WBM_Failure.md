---
title: "Triple Boot WBM Failure"
date: 2012-02-10
forum: Apple Hardware Users
---

### Post by CedarHawk on 2012-02-10
Hey guys. 



First post, so please excuse me if this is wildly "off-kilter" in some way. I've done a lot of searching, but haven't been able to find a functioning fix yet. 
So, this is my first experience with a Linux-based system. I don't go into things in total stupidity, I've tried to get a good idea of where to go for a few days now. Installed the latest version of Ubuntu with no problems.


I installed it on my iMac from around 2008-2009, which already had Windows 7 Ultimate running on a 140gb bootcamp partition. From a few sites I read, it was still possible to install Ubuntu without any major problems. What I wound up doing was using Disk Utility to further divide the primary partition (OSX). 


Got onto the Windows OS, installed Ubuntu via dvd. Ran into no problems, Ubuntu works fine. I run into my issue when attempting to actually run the Windows OS. 
When I start up via rEFIt, I select Windows, and GNU Grub starts up. Selecting Windows then leads to this:



```

Windows Boot Manager

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:
1. Insert your Windows installation disc and restart your computer.
2. Choose your language settings, and then click "Next."
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: \Boot\BCD

Status: 0xc0000225

Info: An error occurred while attempting to read the boot configuration data.


(Enter to continue, ESC to exit)
```

This is totally unresponsive, only way to proceed is hard-restarting.
Now, I've tried booting from the install disc. The thing is, it still goes through GNU Grub, and when I attempt go fix anything via the recovery applications I'm told that a partition isn't selected. Even though I had to select, at rEFIt and GNU Grub. 


When I'm at the recovery section and open up the command prompt, I've tried listing all available partitions, but it only shows two. One of nearly 1TB (original HD, shown without partitions), and one that's empty. 






SO. I'm sorry for the extremely long-winded explanation, but if you need any more info please feel free to ask. I'm still extremely inexperienced with Ubuntu and Linux in general, so I apologize for any slowness on my part.
Any help would be greatly appreciated! :)

---

### Post by CedarHawk on 2012-02-13
Apologies for double post, needed to update.





Okay, so. It turns out I actually CAN boot up with the Windows disk. 
It goes to the installation menu for Windows 7, I select Repair, it shows "system recovery options", says to select an operating system. Thing is, the Windows system isn't showing. I hit load drivers, and the Windows OS is just gone.


Only things left are a C drive labeled EFI (with almost nothing on it), and X drive labeled Boot (which is what I'm currently accessing).


Any ideas?

---

### Post by varunendra on 2012-02-13
Hi CedarHawk, and Welcome to the forums!

The first thing I would have asked you to do is to download and run [boot info script]("http://bootinfoscript.sourceforge.net/") (from either the installed or a live ubuntu session), and post back its result here. But most probably I wouldn't know what to do afterwards, since _I have absolutely no idea about macs or their partitioning plans_.

Nonetheless, I would still recommend you to do so (follow the instructions on the download page I've linked to), and post back the results.

Also, when you say-
> **CedarHawk said:**
> ....Got onto the Windows OS, installed Ubuntu via dvd...
.. do you mean it is a WUBI install (Ubuntu installed "on top of windows" as an application)?

From a quick search through the "Apple Users" forum I found [this thread]("http://ubuntuforums.org/showthread.php?p=11228927&postcount=4") that seems to give some insight to your problem. You may post there a link to your thread asking for help. It looks like you need either the knowledge of *oldfred*, or the knowledge+expertise of *srs5694*. I'll try to consult *oldfred *and see if he is available and interested (although he has frankly admitted that 'macs' are not in his field of expertise).

---

### Post by oldfred on 2012-02-13
I do not know Macs either.

But you have to have a hybrid MBR/gpt partition scheme and have to be sure to keep them synchronized. Ubuntu will boot from standard gpt partitions with MBR or UEFI. Windows 64 bit normally uses MBR, but will boot with the newer UEFI. Apple's EFI is between version 1 & version 2 (I think) of UEFI, so Windows cannot use the efi to boot. 

So you have to have MBR for Windows and then gpt for the Mac. Not sure if Ubuntu is gpt or MBR or either.

[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

