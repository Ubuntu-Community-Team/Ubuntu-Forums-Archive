---
title: "Setting up my new Dell XPS 420"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by EllsworthT on 2008-02-16
Hi all,

Just today, I received my brand spanking new XPS 420 (it's specs can be found in my signature).

My Goals:
1-To leave Vista alone on the factory installed 320GB hdd.
2-To install Ubuntu on an aftermarket, manually installed 320GB hdd.
3-A-To install a third 1TB neutral hdd that I can use to store files and be able to access these files from either OS.
4-To be able to select which OS to boot into at startup.

Can someone please run down in detailed instructions how to accomplish this. I've scoured the forum and have a few ideas of how this could be done (by piecing together bits from here and there). But this is my brand new computer and I want to get it right the first time.

Also, I am not interested in partitioning drives, so it may seem overkill to have a 320GB hdd dedicated to Ubuntu and Vista individually but it's what I want to do.

Thank you.

-Ellsworth

---

### Post by Presto123 on 2008-02-17
The thing you will have to realize is that if you wish to have it installed without partitioning the drive, you will need to stick with the live CD or run it off of Virtual Box.

But, in case you mean you don't want to have to deal with partitioning and allowing the program to do it, then that happens automatically when you install from the live CD.

Grub will be automatically installed which will allow you to boot either one with a selectable menu. With a second HD, you may have to go through an alternative way to install to that drive instead as it may only give you one selection for how to partition the drive.

Please post back what options it gives you when you decide to install.

Also, the external drive will work fine. I have one at 320gig that is recognized on everything in the typical FAT32 format.

---

### Post by Forrest Gumpp on 2008-02-17
EllsworthT,

There may be another way you can achieve what you say you want.  It is a hardware approach rather than a drive partitioning approach, and involves the use of relatively inexpensive pass-through adapters known as HDD caddies.

First some questions.

Do you have a spare (unoccupied) 5.25" drive bay (the ones the CD or DVD drives go in)?

Can two SATA HDDs be connected in your computer?  I should imagine they could, but as I do not have SATA drives myself, I can't be sure.

Presuming that two HDDs can be connected, the outline of this proposed arrangement is that the 1 TB HDD would be mounted internally in the standard 3.5" drive bay space, while the othe SATA cable would connect to the docking receiver part of the SATA HDD caddy installed in the spare 5.25" drive bay.  (This may involve the replacement of a SATA cable with one of different length to reach the optical drive bays.)  You would actually have to buy two SATA drive caddies (around $15 AUD each here), but you would only use one of the docking receiver components.

The two caddies proper would contain your 320 GB Vista HDD in one case, and your proposed 320 GB Ubuntu Linux HDD in the other.  Obviously this means your 3.5" Vista HDD must be taken out of its internal bay and mounted in a caddy.

When your Vista caddy is inserted and switched on, you can boot into Vista as you normally would.  Upon shutting down, you would then switch off the caddy power and physically remove your Vista from the computer.

You could then insert the empty 320 GB HDD you had acquired, and proceed to install Ubuntu upon it with absolutely no prospect of interfering with your Vista.  If you are inexperienced or unconfident with installation of Ubuntu, you are free to choose the guided partitioning option on the live CD, in which case the installation is all but fully automated.

You can put off formatting the 1 TB HDD until you have become familiar with the partitioning tools, and more importantly, aysiu's and Herman's guides and the mine of information and links in ubuntu_demon's sticky.  You can't screw up your Vista, and if you screw up Ubuntu before you have significant data or setting up done, its as simple as re-installing from the live CD.

To go back into Vista, shut down Ubuntu, switch off the caddy, swap caddies, switch back on, and boot up.

If you do go this way, be sure to place a label on each of the HDDs themselves as to what OS is on them.  Labelling on the lids of the caddies is all very well and should be done, but lids can get changed around.  Be sure, especially if you are about to re-install or format another HDD, that you do not blow away an OS you want to keep!  Check the actual disk labels!

---

