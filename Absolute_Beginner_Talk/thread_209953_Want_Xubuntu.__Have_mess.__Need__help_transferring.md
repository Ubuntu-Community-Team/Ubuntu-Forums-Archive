---
title: "Want: Xubuntu.  Have: mess.  Need:  help transferring data."
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by SoloSalsa on 2006-07-05
Alright, alright, my story:
I had Win98.  I tried ReactOS;  lost my master boot record.  Can't boot anything.  No room to re-install 98, don't want to reformat with 98.  Decided to go with Xubuntu (I 'ent scared!).  But I need some help first...
My HDD, and documents, are intact.  But I need to get them off before I can format for Xu.
   1)  What can I boot with, that supports Dot4 USB, just to transfer my files?  I think Xubuntu can access my disk on livecd, but I recon it will be slo-ooo-ow.  Should I try Damn Small?  Or is there something simpler?
   2)  When I install Xubuntu, what file system should I use?  When looking through the messy HDD, one tab allows me to format it with a nice selection of formats.  Which one is best/fastest/safest/best! for Xubuntu?
   I know this can be done, please give me your suggestions as to how.
Thanks!

---

### Post by briguy on 2006-07-05
Your Xubuntu disk as a live CD will (or should) work as well as any to transfer your files from the HDD to a USB drive.  Give it a try, if it's really slow you can try something else!

I tend to use ext3 filesystems, which seems to work well.  Here's a link to a FS benchmark if you're interested to learn a bit more about the different ones available: [http://linuxgazette.net/122/piszcz.html](http://linuxgazette.net/122/piszcz.html)

---

### Post by metaltailz on 2006-07-05
Well I had a situation sort of like yours, but not really. Ok for your documents I'm not sure that you would be able to get them off using a 0.4 USB port, I suggest that you use the Xubuntu liveCD and email them to your self or upload them to a websever.
Damn Small Linux is actually quite good for hoping on to a broken computer and looking at the HDD and its files.

As for the file system when you install Xubuntu, I had a little trouble with this so I will tell you what you should do.

I am assuming that you are using 1 HDD, create a primary partition for / that is over 2 Gigs and format that to ext3, then create a partition for 'swap' which has to be atleast 256 Megs. That should work out, I suggest that you plan out your HDD partitions on paper before you actually decide to install Xubuntu.

Good luck!

---

### Post by catlett on 2006-07-05
Did you try fixing you mbr? In case you don't already know, put in a windows install disc. Boot to ir. Enter the recovery mode. After a few prompts etc you will get a command prompt C:\ 
At the prompt enter ```
fixmbr
``` That rewrites the master boot record. If the boot sector is messed up and fixmbr doesn't work, run ```
fixboot
``` This repairs the boot sector. Then rerun fixmbr to rewrite the mbr.

If you can download a linux live distro I assume you have internet access? If you don't have a windows install disk just download an XP install disk from a bittorent site like The Pirates Bay and use that to get into the recovery console.

If you still can't get into windows, I would recommend Knoppix because it will auto mount your windows partition and put an icon on your desktop. If you want to keep it small, I prefer "Puppy Linux". Silly name great minimalist live distro

---

