---
title: "Will a Kubuntu install over FC2 automatically update GRUB"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by New-In-Ohio on 2007-06-28
I've had Fedora Core 2 loaded on a dual boot x86 Celeron machine for several years.  GRUB is the OS loader and has worked great.  I want to completely over write the FC2 install with Kubuntu but I'm worried about GRUB getting the right information automatically from Kubuntu install.  I dont understand how the grub.conf file will be updated correctly since it lives in /boot/grub and this will in theory be erased along with the entire root.  I have the following:
hda1 is NTFS (GRUB MBR)
hda3 is root (ID 83)
hda4 is W95 ext'd (LBA)
hda5 is Linux LVM <-- this is where i had /home and /tmp and /usr and /var and swap

My plan is to delete partions hda4 & 5, repartition hda3 to include most of the free space, make new partion hda4 as a swap and then load Kubuntu on hda3.  I also plan to skip the boot loader portion of the install.  This is where I'm worried.  Any advice would be appreciated.

---

### Post by djchandler on 2007-06-29
> **New-In-Ohio said:**
> I've had Fedora Core 2 loaded on a dual boot x86 Celeron machine for several years.  GRUB is the OS loader and has worked great.  I want to completely over write the FC2 install with Kubuntu but I'm worried about GRUB getting the right information automatically from Kubuntu install.  I dont understand how the grub.conf file will be updated correctly since it lives in /boot/grub and this will in theory be erased along with the entire root.  I have the following:
hda1 is NTFS (GRUB MBR)
hda3 is root (ID 83)
hda4 is W95 ext'd (LBA)
hda5 is Linux LVM <-- this is where i had /home and /tmp and /usr and /var and swap

My plan is to delete partions hda4 & 5, repartition hda3 to include most of the free space, make Kuew partion hda4 as a swap and then load Kubuntu on hda3.  I also plan to skip the boot loader portion of the install.  This is where I'm worried.  Any advice would be appreciated.

New-in Ohio,

Are you not planning to use the OS residing on the NTFS partition? I don't think there is a way to skip that part of the installation using the Trial/Installer CD. There might be a way with the Alternate Installer CD, but that demands a great deal of command line know-how on your part.

The Ubuntu installer from the trial CD will not try to install itself over pre-existing Linux partitions. I've tried to do that with a corrupted installation of Ubuntu that got clobbered by an unwise choice of hitting the reset button, but had no personal data that needed to be recovered.

**---Warning---digression---**
BTW, power failures or deliberate power interruptions are better than ever hitting the reset button in an unresponsive Linux installation. No junk gets accidentally written to the HDD due to a power interruption. You still may get an un-bootable HDD, (which hasn't happened to me yet) but you should be able to mount it on another Linux installation, and then recover your data.
**---End digression---**

Use Dban to wipe everything but the primary partition, as that seems to be where the OS that uses NTFS is located. Was it the first OS installed on this HDD? I don't understand not wanting to run the OS in hda1, yet leave it apparently intact. I would let the Ubuntu Installer re-write the MBR with GRUB. It will recognize the NTFS partition as a separate OS and should leave it intact. Also, the Installer will let you make a custom configuration on unused parts of your HDD. Back to Dban, it does give you a choice of just wiping certain partitions, not the whole HDD. Darik Mihocka, the developer of Dban, may help you discern that for a minimum of $10.00, but there are many other resources available through [http://dban.sourceforge.net/](http://dban.sourceforge.net/).

Ubuntu has a unique way of dealing with the root account that may make your ideal installation impractical. Why are you worried about loosing the root partition? All of your personal settings are stored in your /home/yourusername folder. You may not be able to see some of the hidden folders. Your version of nautilus or whatever Fedora 2 was using as a file browser, should allow you to see those hidden folders for all your application settings, and you can copy them to some other medium. I've had success copying my .evolution and .mozilla folders back to my HDD before my first use of those programs in my new installation. I get all my old emails, address book  and calendar info in Evolution, and all my old bookmarks in Firefox. Other data didn't seem to matter so much to me, as the end product was what was important to me, not the program settings. It's probable that you'll want to use use different software in Kubuntu than you did in Fedora as well.

DJ

---

### Post by New-In-Ohio on 2007-06-29
Thanks for the reply.
I just re-read my post and realized I didn't state my objectives very clearly. Thanks for reading between the lines. I think I got the answer I needed. My objectives are to continue with a dual boot machine and use windows xp on the primary partition (still have autocad and a few other programs I dont want to give up). I'm not real concerned with loosing any of the FC2 data. I'm not trying to keep the root directory on hda3 or anything else. Although I did wish that i didnt have to lose the /home/*me *directory. I just thought it would be impossible to keep because of the LVM type of partition. BTW i am using the kubuntu-alternate install. Bottom line: I shouldnt worry about GRUB because the new install of GRUB and the MBR will automatically detect WinXP on the primary partition and use that to make a new /boot/grub.conf file. Right? I will explore dban to see if there is a way to pull one or two LVM partitions (/home and swap) out of a re-partition scheme and save them to be used with a new install.

---

### Post by Zzl1xndd on 2007-06-29
You shouldn't have any issues I did basicaly the same thing only I moved from Fedora core 5 to Ubuntu 6.06 but that was a little while ago.

---

