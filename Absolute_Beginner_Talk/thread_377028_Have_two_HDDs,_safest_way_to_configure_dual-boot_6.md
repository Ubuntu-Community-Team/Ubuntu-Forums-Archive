---
title: "Have two HDDs, safest way to configure dual-boot 6.10 with Vista?+many other nOOb q's"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by TheNorthWaves on 2007-03-05
Hey everyone - I'm glad this forum exists!

the description of both of my computers is in the signature...
I have old Windows copies laying around to attempt setting up a dual boot situation on the mess-around PC before I get the confidence to mess around with my main PC...
first of all, I hear that from XP --> Vista, they changed the boot.ini file to something that's a pain in the butt to work with. I'm not sure of the relevance though.
A friend built my "main" computer and installed vista home premium on it. Nothing is branded and I have all the discs. I have been barely playing around with 6.10 yet on my mess-around PC and would like to at some point run a dual-boot setup on the main machine.
[B]
I have two SATA HDDs, one 160gb (with vista installed on it), and one HDD with 250gb that I merely fill with music and Top Gear videos - IE: If necessary, I can wipe the 250gig hdd and install Ubuntu on it, if that's "safer" than putting it on the Vista HDD.[/B]
This brings me to another question, I recall that 6.10 uses FAT32 and Vista uses NTFS. If I reformat the 250gb hdd as FAT32 and throw 6.10 on there, will I theoretically have any problems with windows also recognizing all the Top Gear and Food Network episodes that I plan to toss back on that giant hdd, when I boot up into Vista?
The main goal is to have full functionality of both Vista and Ubuntu, an easy way to boot into either of them at startup, and to arrange this setup in the most "stable" configuration. IE: How can I do this so one OS doesn't screw up the other OS's boot record, etc? I am going for the "camry" of dual boot setups here - least likely to fail.

I might sound like I know some things, but honestly I'm almost clueless. I have done a lot of reading but it doesn't mean I can practically apply it.
Thank you all so much for reading all of this- Does anyone have suggestions? I read the dual-boot articles but I want to run the right setup for my particular system and frankly I don't know what is the best.

---

### Post by mikewhatever on 2007-03-05
Since you have more then one HDD, the safest way is to install Ubuntu on second one. You do not need  to wipe it out, just resize and create Ubuntu partitions. [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)
Please note that neither version of Ubuntu uses FAT32, although it can read and write to it. That means you might need to create a FAT32 exchange partition.
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

Grub bootloader allows you to choose an OS at boot. You can install GRUB to the MBR of the non Vista HDD along with Ubuntu.
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by Phantom784 on 2007-03-05
Ubuntu doesn't use Fat32, it uses ext(2/3).  Windows can't natively read ext.  There is a program you can install in windows that lets it read ext, but then if you get a windows virus, your linux partition is also at risk.  I'd suggest only using a portion of your second drive for linux, leaving enough space for any software you might want to install later.  Make the rest Fat32, which can be read by both Windows and Linux.  That way, you can see your media from either operating system.

---

