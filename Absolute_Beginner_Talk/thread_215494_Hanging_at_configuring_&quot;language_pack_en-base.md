---
title: "Hanging at configuring &quot;language pack en-base&quot; (AMD64, software raid involved)"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Nescientist on 2006-07-14
So, I'm on a DFI Lanparty Nforce 4 chipset board with an existing installation of windows on one HD, an existing second HD formatted with NTFS (neither of which do I want to mess with). As a bid to bribe myself into switching to Linux, I've just now installed two 10k RPM SATA Raptors and a 400gb drive and spent the afternoon reading forums and HowTo's and trying to install Ubuntu.

I read that fakeRAIDs are a hassle for Linux systems, so that remains disabled in the BIOS. Instead I set up an MD with the Ubuntu partitioner (I'm using the alt-disc). I was unable to partition the resulting multidisk device through the graphical interface, so I let that be "/" and put swap on the other new drive. My current partitioning setup for ubuntu looks like this:

two 74gb in soft raid 0:
   148gb Ext3 / 

400gb:
   100mb Ext2 /boot
   4gb Swap
   396gb Ext3 /home

First, is there something inherently wrong with this arrangement? (I am a total neophyte after all; it would sort of surprise me if there weren't) Is there any way to coax my swap onto the Raid?

Second, after running through the core installation with no problems I'm now looking at a "select and install software" screen which has been hanging at 1% (Configuring language-pack-en-base) for ~25 mins. This is bad.


I seem to be having a run of bad luck, what with my first install disk being corrupt (I ran the checking utility on this one!) and not even getting through the core install.

any help is tremendously appreciated!

---

### Post by Nescientist on 2006-07-14
Just tried again with the exact same settings. No adjustments whatsoever. An error was thrown - something about wanting me to perform an FSCK. Tired and impatient, I ignored it. We'll see how that works out... I'm past where it hung up before, so I have my hopes up.

Update:

This time it got all the way through to "installing GRUB boot loader". Hanging at 0%. I'm just going to leave it like this and go to sleep, but I'm not very optimistic. ](*,)

---

### Post by Nescientist on 2006-07-14
Nope, nothing. So I've gone from hanging at apps to hanging at GRUB installation. I hope my MBR hasn't been wonked...

---

