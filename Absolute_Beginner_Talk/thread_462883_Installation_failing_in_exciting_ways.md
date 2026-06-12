---
title: "Installation failing in exciting ways"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by gtsears on 2007-06-03
I downloaded the 7x live ISO and burned the CD at 8X yesterday. I tried it out in a locally built 1Ghz AMD clone. I tried it 3 or 4 times befor it booted successfully. I played with it a bit and decided to install it 'cause it was sooo ssslllllooowww running from the CD. The PC had a working install of Win2Kpro on it, when the first attempt failed at step 7 15% I thought it might be due to the NT file system. On the next Ubuntu boot I used the partitioner to manually clear all partitions and repartition. Because it had succeeeded in booting after 3 or 4 tries without me doing anything to fix it I decide to use that method with the install. After about 4 or 5 repeats and waiting 45 - 60 min. after the apparent hang, I switched to a trusty WinXP machine and came to the forum.

While getting registered and reviewing my profile etc. I noticed that the 15% dialog had faded and was unreadable, as I was walking over to get a closer look the dialog came back up, but then indicated 20% , and then the "ubuntu - File Browser" came up. The slider on the Install Dialog continues to advance (now about 52%). I don't think I did anything to fix anything, but the install seems to be OK for now. 

I'll post again when it finishes or croaks.

Gene 

First Edit at 21:27 GMT -5

It appeared to finish installing OK. When I clicked the RESTART button it went into lala land for long enough that I did a hard reset. On restart it hung at a black screen. After several tries at rebooting I have set it to reinstalling. On step 5 or 6 it did not find anything to import into the new install. Currently it says it is "Detecting file systems" the slider is at 15%.
I downloaded the 7x bootable ISO and burned the CD at 8X yesterday. I tried it out in a locally built 1Ghz AMD clone. I tried it 3 or 4 times befor it booted successfully. I played with it a bit and decided to install it 'cause it was sooo ssslllllooowww running from the CD. The PC had a working install of Win2Kpro on it, when the first attempt failed at step 7 15% I thought it might be due to the NT file system. On the next Ubuntu boot I used the partitioner to manually clear all partitions and repartition. Because it had succeeeded in booting after 3 or 4 tries without me doing anything to fix it I decide to use that method with the install. After about 4 or 5 repeats and waiting 45 - 60 min. after the apparent hang, I switched to a trusty WinXP machine and came to the forum.

While getting registered and reviewing my profile etc. I noticed that the 15% dialog had faded and was unreadable, as I was walking over to get a closer look the dialog came back up, but then indicated 20% , and then the "ubuntu - File Browser" came up. The slider on the Install Dialog continues to advance (now about 52%). I don't think I did anything to fix anything, but the install seems to be OK for now. 

I'll post again when it finishes or croaks.

Gene 

First Edit at 21:27 GMT -5

It appeared to finish installing OK. When I clicked the RESTART button it went into lala land for long enough that I did a hard reset. On restart it hung at a black screen. After several tries at rebooting I have set it to reinstalling. On step 5 or 6 it did not find anything to import into the new install. Currently it says it is "Detecting file systems" the slider is at 15%.

Second Edit at 06:18 GMT -5

It croaked saying a file's MD5 didn't match the one in the list.  I downloaded and burned the alternate ISO file.  On boot I ran the CD ROM checker, it failed saying the ./pool/main/g/gtk-sharp2/libgtk2.0-cil_2.10.0-0ubuntu4-i386.deb had an MD5 mismatch.  I downloaded it and burned a CD a second time.  Booted it and ran the CD ROM checker.  It failed saying that the ./pool/main/o/openoffice.org/openoffice.org-base_2.2.0-1ubuntu3_i386.deb file's MD% didn't match.  I took the CDs back to my WinXP machine and checked the MD5 values, they matched the list.  I rebooted the would be linux PC with the 2nd alternate ISO CD.  It got past the password entry screen and has stopped with the following error.  

[!!] Install the base system
Debootstrap warning
Warning:
file:///cdrom/pool/main/a/alsa-driver/alsi-base_1.0.13-ubuntu1_all.deb was corrupt.

I have choices of <Go Back> and <Continue>

When I chose <Continue> I got the following message:

[!!] Install the base system
Debootstrap warning
Warning: Couldn't download package alsa-base

Chose <Continue>

Well I fat fingered it and missed mabe 2 screens (when I tried to go back, it went elsewhere) on chooseing Continue again, several things flashed past and it stopped at :

[!!] Install the base system
Unable to install initramfs-tools
An error was returned while trying to install the initramfs-tools package onto the target system.

Check /var/log/syslog or see virtual console 4 for the details.

On Continue... it stopped at:

[!!] Install the base system
Installation step failed
An installation step failed.  You can try to run the failing item again from the menu, or skip it and choose something else.  The failing step is: Install the base system

On Continue... I got the Menu to try again... trying again

Will update on outcome.

---

### Post by AtrejuT on 2007-06-03
To me all this sounds very much like a problem burning the CD's:
Did you try burning it at _minimum_ speed? Then check the MD5. If they don't match it's not worth trying.
Do you burn on the XP-machine? Because if they match there it might just be that the error correction of the cd drive in that machine is better than on the machine you're trying to install to.

---

### Post by gtsears on 2007-06-03
> **AtrejuT said:**
> To me all this sounds very much like a problem burning the CD's:
Did you try burning it at _minimum_ speed? Then check the MD5. If they don't match it's not worth trying.
Do you burn on the XP-machine? Because if they match there it might just be that the error correction of the cd drive in that machine is better than on the machine you're trying to install to.

I think it is the second scenario, the MD5 on the CD files match, at least all of the ones I have checked.  It occurs to me that I can check the MD5 of all the files on the CD.  Assuming that they all match, is there anyway to turn off the checking on the INSTALL machine?

Gene

---

### Post by lazyart on 2007-06-03
how much memory is in this computer, and have you tried the alternate CD?

---

### Post by ramjet_1953 on 2007-06-03
Two things to remember when burning ANY iso.

1. A MAXIMUM burn speed of 4 X

2. Use quality media. Cheap media is OK for music and most data CD's but it doesn't cut the mustard for iso's.

Regards,
Roger:cool:

---

### Post by gtsears on 2007-06-04
> **lazyart said:**
> how much memory is in this computer, and have you tried the alternate CD?

Both PCs have 256Mb RAM.  Yes I discussed downloading it twice in an earlier post in this thread.

Gene

---

### Post by pappapump on 2007-06-04
GTsears, can you list what hardware you have installed in your box please?
I have a feeling It may be something I've run into b4 with older amd's.

---

### Post by gtsears on 2007-06-04
> **ramjet_1953 said:**
> Two things to remember when burning ANY iso.

1. A MAXIMUM burn speed of 4 X

2. Use quality media. Cheap media is OK for music and most data CD's but it doesn't cut the mustard for iso's.

Regards,
Roger:cool:

Of the three ISOs downloaded and burned, the first a "Live CD" was burned at 8X and the two subsequent downloads and burns of the "Alternate CD" were burned at 4X.

I think **AtrejuT** has the right of it since ALL the burned CDs pass MD5 checks on the files failed on the target PC with the idea that the target CD Drive is a little outof spec, it was Mfg'd in 2001.  Unfortunately I only have one bootable CD Drive other than the CD/DVD burner in my Win XP machine.

I forgot that the XP PC has not FAT space on any drive before I tried installing from the "Live CD" to the XP machine.  Except that the options presented for where to put the Linux install were a bit anemic and I had to choose manual partitioning, the install went fine until it found nowhere to put the GRUB dual boot chooser, then it failed.

Any suggestions on how to fix that WITHOUT risking the C:\ WinXP boot partition?

The original target PC is crippled, but it will boot to a command line.  I tried the install to the XP machine thinking maybe I could copy the CD files to the TARGET PC and run the install from a 2GB slave drive in that PC.

Any confirmation on the workability of that idea?

I tried Red Hat about 3 years ago and I still haven't had anywhere near the problems with Ubuntu as I did with Red Hat.  There is the one issue in that it is still a failure story.  :)

Gene

---

### Post by gtsears on 2007-06-04
> **pappapump said:**
> GTsears, can you list what hardware you have installed in your box please?
I have a feeling It may be something I've run into b4 with older amd's.

Thanks for the response. 

H'mmmn, It has a KSOM7 motherboard 256MB RAM, a 6.4GB drive and a 2GB drive (both are Western Digital), the CD drive is an AOpen.  The CPU is a 1400+ AMD Duron.  I don't remember what kind of RAM it has.

Gene

---

### Post by frozenjim on 2007-10-07
I was able to duplicate the problem on an AMD 1133 Athlon.  Installation seemed fine up to the "**Install the base system**" part.  Then it just stopped with the error at 30%.  I rebooted and started again after repartitioning the drive and it stopped at 1%.  After half a dozen attempts where it crapped out during Base Installation, I realized that I had a problem.

Fortunately, I have used the CD disk to install many times - so I know that it is a good CD.  So even though the system was perfectly fine before, I wondered if this might be a CD-ROM issue.  I replaced the 32X Creative CD with a newer LG DVD/CD unit.

It worked just fine.

So, the identical problem on a very siimilar box - solution was to [COLOR="Red"]replace the CD drive with a better one[/COLOR].  (Now get that XP off of your perfectly good machine!)

---

