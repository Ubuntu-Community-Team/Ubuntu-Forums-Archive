---
title: "Updating Mac OS X to Leopard in a dual boot MBP"
date: 2008-09-22
forum: Apple Hardware Users
---

### Post by GeneralSunTzu on 2008-09-22
Hello,
I am aware this may look off-topic.
It isn't, but of course you will judge it.
I have a Mac Book Pro 2nd generation (2.33 GHz, 3GB RAM) with dual boot.
Ubuntu HH, and with help from many eminent posters here, perfectly fine tuned and working exceptionally well, and Mac OS X 10.4.11.
I decided to take the plunge and update to Leopard, for a number of reasons, immaterial here.
My corporate support provides me with a Leopard full retail DVD.
Upon booting from it, the only option it offers me, instead of the full set, is to wipe the HD and begin anew.
I have spent some time fine tuning Ubuntu, and I am afraid to have to begin again if I wipe the disk. Of course I have two Mac OS Backups and I may probably find out how to back up properly Ubuntu, but why am I unable to upgrade from Tiger to Leopard?
My suspects where:
1. rEFIt;
2. the DVD;
3. too many partitions, because of Ubuntu;
4. haven't got a clue.

Now - deleting rEFIt does not change anything. The DVD is perfect.
Why cannot I upgrade to Leopard?
Any gentlebeing has got a clue?

Thank you so much, as this is driving me literally up the wall, in spite of my Zen lessons...

---

### Post by cyberdork33 on 2008-09-22
> **GeneralSunTzu said:**
> Upon booting from it, the only option it offers me, instead of the full set, is to wipe the HD and begin anew.
If you look through the archived forum threads, you will see this is true for everyone that upgraded... including myself.
> **GeneralSunTzu said:**
> 3. too many partitions, because of Ubuntu;I think this is close. The general concensus was that there was an 'unrecognized' partition on the disk (not necessarily too many partitions).

Everyone that has upgraded had to wipe everything that I know of... sorry. You could maybe do a full install to an external disc, image that partition then restore it back onto your internal hard drive in place of Tiger...

---

### Post by GeneralSunTzu on 2008-09-23
> **cyberdork33 said:**
> If you look through the archived forum threads, you will see this is true for everyone that upgraded... including myself.
I think this is close. The general concensus was that there was an 'unrecognized' partition on the disk (not necessarily too many partitions).

Everyone that has upgraded had to wipe everything that I know of... sorry. You could maybe do a full install to an external disc, image that partition then restore it back onto your internal hard drive in place of Tiger...

Thank you very much cyberdork33. 
I think what I will do will be instead to preserve my Ubuntu partition as best as I can (I haven't found an appropriate tool, so far, you know one?), by backing it up to a FireWire disk [do hope Ubuntu has FireWire drivers], where I can create an additional image, then wiping my HD, installing blasted Leopard and then use BootCamp to bring back the Ubuntu partition. 
If anything in the Ubuntu low-level drivers uses absolute disk addresses then I am toast, however...

---

### Post by explorer59 on 2008-09-23
The Ubuntu installer modifies the boot track of the hard drive to accomodate the dual-boot feature. The Mac OS installer will no longer recognize the drive as valid.

I would like to suggest something purely speculative, but harmless, to try. If you have access to another Intel Mac, try putting your MBP into Target Disk Mode, then connect it to the other Mac using firewire, then boot and run the installer from the other Mac.

---

### Post by roost3r on 2008-09-27
Any Personal Computer I use, I typically always leave room for a Linux installation. Then I install the "manufacturer approved" OS, then Linux.

As someone already pointed out, try installing Leopard with your Mac in target disk mode. Failing that, clone your complete HD to another drive, then install Leopard fresh, leaving room for your Linux backup to be restored. You should be able to use the live CD to do a fresh install and then you can clone your backup over top of the fresh install. The reason I mention a fresh install is so that the boot loader can be installed correctly (I have no experience with IntelBasedMac's and Linux as of yet so I am unsure of how Linux boots them. I know for sure PowerPC Linux makes a special boot loader partition). Once the boot loader is installed and you have restored your Linux backup to the fresh install (I use dd typically for this), you should be able to restart the computer and boot into any OS you installed on it. At least that is the theory. :)

---

### Post by GeneralSunTzu on 2008-09-27
Thank you all!
Prepared to the worst, I backed up everything, used pybackpack (the only intelligible backup system I found) to back up my Ubuntu HH home directory and prepared for the worst.
Surprise! The Leopard installer left my other partitions alone, much as it had stated it was going to wipe the disk. In fact it wiped the partition, not the disk...
So, much to my surprise, after installing Leopard from scratch, patching it with the 10.5.5 elephant-sized combo installer (600+ MB) and moving everything back with the Migration Assistant (a couple of hours for 42 GB of aps and docs), I found I had lost nothing at all, as all other partitions had been left untouched, and so even rEFIt was working...
Amazing...

---

### Post by explorer59 on 2008-09-27
> **GeneralSunTzu said:**
> 
... Surprise! The Leopard installer left my other partitions alone, much as it had stated it was going to wipe the disk. In fact it wiped the partition, not the disk...

Glad to hear that! And a handy piece of info... I had not had the opportunity to put that nasty message to the test, but now we know... Which is not to say one should not backup one's data in such a situation...

---

