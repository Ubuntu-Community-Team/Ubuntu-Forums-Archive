---
title: "setting up mounting and partitions"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by nbv4 on 2007-06-14
I just installed feisty. During the installation, I couldn't get it to install right (something to do with boot drives which resulted in a grub error), so my only option was to just open my computer, unplug all my hard drives except for the one I want to use as root.

I did just that and it installed fine. Here is how my drives are:

80GB SATA - Ubuntu is installed here. Both root (ext) and swap.
200GB IDE - One big FAT32 partition for storage of files. I want this mounted to /windows or something.
400GB SATA - Half this drive is NTFS with stuff I need, and the other half is an empty ext partition. I want to move all the stuff from the NTFS part over to the ext part, then merge the two into one big ext partition which is mounted to /home

I just plugged them back in, and they show up under the gnome file explorer thing, but I can't figure out how to access them via command line.

How do I go about doing this?

---

### Post by eljalill on 2007-06-14
All your hard drives are mounted to somewhere. Generally this is /media . So if you navigate to /media in the command line, they should all be there, and you can access them :) .
Btw a good way to find things, if you know their name is the "locate" command .

---

