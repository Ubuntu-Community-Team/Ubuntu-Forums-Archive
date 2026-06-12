---
title: "How do I make Ubuntu the startup OS?"
date: 2010-05-30
forum: Apple Hardware Users
---

### Post by ilazria on 2010-05-30
I just got a Mac Pro 1,1 as a hand-me-down.

 [COLOR="SeaGreen"]Model Name:	Mac Pro
  Model Identifier:	MacPro1,1
  Processor Name:	Dual-Core Intel Xeon
  Processor Speed:	2.66 GHz
  Number Of Processors:	2
  Total Number Of Cores:	4
  L2 Cache (per processor):	4 MB
  Memory:	2 GB
  Bus Speed:	1.33 GHz
  Boot ROM Version:	MP11.005C.B08
  SMC Version (system):	1.7f10
[/COLOR]

I'm very new to linux, and this is my first time trying it on a Mac. I've installed Snow Leopard on the second HD, and Ubuntu 10.04 on the first. I have 3 250G HDs and 1 160G HD I trandferred from my G5. I can't figure out how to make Ubuntu the startup OS. I can access it by holding the option key and accessing the drive labeled windows. Everything seems to work fine, I just can't set it up as the startup.

If I go to disk utility on Snow Leopard, I can see the first drive, but everything is gray. It shows up like this-

**250.06GB ST3250824AS P Media**
   [COLOR="SlateGray"]disk0s1
   disk0s2
   Linux Swap[/COLOR]

Only when I highlight disk0s2 can I run verify disk and repair disk. This is what I get when I try that.

[COLOR="Blue"]Verifying volume “disk0s2”
** /dev/disk0s2
Invalid BS_jmpBoot in boot block: 000000
Error: This disk needs to be repaired. Click Repair Disk.
Verify and Repair volume “disk0s2”
** /dev/disk0s2
Invalid BS_jmpBoot in boot block: 000000
Volume repair complete.Updating boot support partitions for the volume as required.Error: Disk Utility can’t repair this disk. Back up as many of your files as possible, reformat the disk, and restore your backed-up files.[/COLOR]

Again, nothing seems wrong with the Ubuntu HD when I access it after holding the option key.

I've looked up tons of different forum posts, but I'm finding the information confusing. The advice about rEFIt seems to involve partitions, which I don't think applies to my situation, since each OS is it's own entity on separate drives. Bootcamp and Parallels seem to involve starting up in Snow Leopard and accessing Ubuntu from there, but I'm finding that process to be a bit confusing as well. Plus, while Bootcamp or Parallels might be the way to go, I'm feeling stubborn now. If there is a way to make Ubuntu the startup OS, I want to do it, just because I've had so much trouble with it. 

I'm not a complete novice when it comes to computers, but Linux is a whole new language for me. I started using it on our Windows laptop after I managed to get some massive virus that crapped the whole thing out. Don't know how I did it, didn't open any strange emails or visit any websites I hadn't visited just fine on the Mac. But I did, and so the husband put Ubuntu on the laptop for me. I've enjoyed the challenge and the versatility, so I want to keep playing with it on the Mac Pro. Can anyone help?

---

### Post by jamesixgun on 2010-05-30
I don't remember the exact location, but somewhere in System Preferences, there's an option to choose the startup disk. (It may be in accounts? Perhaps someone will correct me.) You might be successful choosing the Linux disk in that dialog, if you can find it.

I'll swap over to my mac install in a minute and see if I can find the right dialog and edit it in shortly.

Edit: :facepalm: the System Preferences is at System Preferences --> Startup Disk.


But others might have a better option, and you might have tried this before, so sorry if I've wasted your time.

---

### Post by ilazria on 2010-05-30
I don't mind at all! Anyone willing to help is appreciated. 

I have tried going to startup disk through the Mac OS, but the drive with Ubuntu on it doesn't even show up. I can only see the Snow Leopard drive and the old drive from the G5 with Leopard on it. The 3rd drive, with no os on it, doesn't show up either.


> **jamesixgun said:**
> I don't remember the exact location, but somewhere in System Preferences, there's an option to choose the startup disk. (It may be in accounts? Perhaps someone will correct me.) You might be successful choosing the Linux disk in that dialog, if you can find it.

I'll swap over to my mac install in a minute and see if I can find the right dialog and edit it in shortly.

Edit: :facepalm: the System Preferences is at System Preferences --> Startup Disk.


But others might have a better option, and you might have tried this before, so sorry if I've wasted your time.

---

