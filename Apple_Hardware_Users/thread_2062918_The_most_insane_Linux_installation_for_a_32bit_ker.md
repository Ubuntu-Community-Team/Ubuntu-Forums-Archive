---
title: "The most insane Linux installation for a 32bit kernel on a 64bit EFI 2010 iMac"
date: 2012-09-26
forum: Apple Hardware Users
---

### Post by q64ceo on 2012-09-26
The insane way to install 32bit linux on a 64bit EFI iMac

Ok, after two weeks of trying, I finally was able to install a 32bit version of Ubuntu on my internal hard drive. You are probably asking yourself, “So? Easy. Burn a CD and put it in your optical drive.” Well, my optical drive is dead, and Apple has a terrible BIOS emulator on my 2010 27 inch iMac that cannot boot MBR disks connected via USB (and even FireWire). Then you will ask yourself, “Ok, cool; but why not go pure EFI route?” Well, I have an AMD card in my system, and AMD makes very terrible drivers. There are a few problems on a 32bit and 64bit MBR setup, but the driver does not offer acceleration on an EFI system, and it can even brick your linux installation.

This was the most frustrating thing I have ever done on a computer. I was on the hackintosh scene, and after this experience, I am going back. I cannot deal with Apple's extremely locked down system.

Supplies used:
Thumb drive
Parallels
Windows 7
iPartition (not really needed, but I preferred it over Microsofts partition tools)
Wubi
Wubi transfer script
12 cases of Mountain Dew

I started out playing with unetbootin for a few days. I was able to get a live disk image to run via its built in BCD entry in the Windows loader. Unfortunately, the installation always fails as it must dismount the internal hard drive in order to work with the partitions, and since I am running off an ISO on my internal hard drive, it cannot be dismounted. So, that was out. I tried putting it on my USB stick and using rEFInd and rEFIt to try to boot off of those USB ports. Still no luck. Tried the Windows 7 Parallels bootcamp installation trick and I still had no luck. I even installed Ubuntu using EFI and attempted to add the 32bit kernel after the fact. That did not work as well as GRUB2 only wanted to run EFI partitions.

Many, many, MANY reformats later and I finally got it.

The answer was in front of me for days, but I did not put two and two together. It is Wubi. 

Now, I installed Windows 8 (efi) version (as I said, bad bios implementation and dead optical drive so I had to install it via USB stick). Unfortunately, Windows 8 EFI boot uses UEFI secure boot, and Wubi couldnt work on that. So, I went back, threw on Windows 7 on my Internal HD via Parallels, and installed Wubi. 

Now, why I did not try this sooner, I do not know. But, how I ended up getting it to work was by running the Wubi transfer script to transfer the Wubi install to its own independent partition. This worked perfectly. Unfortunately, because of the way Apple has its hybrid MBR/GPT disks, running more than one partition in the hybrid MBR is simply idiotic and will eventually lead to hard drive corruption. So, in order to be able to have this perfect tripple boot install, I have my internal HD a pure MBR disk where I have Windows 7 and Lubuntu, and I have OS X on an external firewire hard drive.

Two weeks of frustration followed by euphoria, it still was a nightmare.

Basically, I guess I am writing this post as a help for those who were in my same situation, and for others to go yell at AMD for writing the worst drivers ever.

---

