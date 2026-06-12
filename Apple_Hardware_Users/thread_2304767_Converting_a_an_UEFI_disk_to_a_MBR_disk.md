---
title: "Converting a an UEFI disk to a MBR disk"
date: 2015-11-29
forum: Apple Hardware Users
---

### Post by Randymanme on 2015-11-29
I've recently been gifted with a Macbook Pro A1286.  My intentions are to wipe the disk and install Ubuntu.  I've been googling this topic and have read a lot about and around it --  most of which are rather too technical and convoluted for me.  I did, however, stumble upon some directions that seem a little bit too simple to true: ()please see screenshot)

Am I to understand that I can just use windows to convert the UEFI disk to a MBR disk, and then install Ubuntu without further ado?

---

### Post by oldfred on 2015-11-30
I do not know Mac.
But it is my understanding that all Mac with Intel chips use UEFI to boot.
And a Mac uses its own software to allow booting older versions of Windows in BIOS mode using a hybrid MBR/gpt configuration, which then must be kept in sync. Best to avoid hybrid partitioning at all cost.

       [URL="http://www.rodsbooks.com/gdisk/hybrid.html"]http://www.rodsbooks.com/gdisk/hybrid.html

[/URL]
 With 15.10
The amd64 (Intel x86 64bit) images specifically targeted at Apple hardware (amd64+mac) are no longer produced. 
[http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/](http://mattjanik.ca/blog/2015/10/01/refind-on-el-capitan/)
[http://ubuntuforums.org/showthread.php?t=2297148](http://ubuntuforums.org/showthread.php?t=2297148)

Some older info. Someone with a Mac should post newer data.

 [http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890](http://ubuntuforums.org/showthread.php?t=2289225&p=13355890#post13355890)
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx)
[http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac](http://askubuntu.com/questions/580202/refit-refind-grub2-what-is-the-right-way-for-ubuntu-14-10-on-a-mac)
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
Bugs Ubuntu fails to properly boot on Macbook Air 2013 6,1 & 6,2 - Use UEFI not CSM
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1197451)
Post #6 booting Kubuntu 12.10 in EFI mode on my Mac, by  trogdor1138
Boot Ubuntu from efi with Mac trogdor1138
[http://ubuntuforums.org/showthread.php?t=2091257](http://ubuntuforums.org/showthread.php?t=2091257)
 MacBook Pro 8,2: howto for dual boot Ubuntu/MacOS EFI with rEFInd
[http://ubuntuforums.org/showthread.php?t=2157775](http://ubuntuforums.org/showthread.php?t=2157775)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)




[URL="http://www.rodsbooks.com/gdisk/hybrid.html"]
[/URL]

---

### Post by luciano.x on 2015-12-01
What is the point?
You can install Ubuntu (64bits) in UEFI mode with GPT. No need to convert to MBR.
Just boot in UEFI mode, wipe the disk, have fun.

---

### Post by BobUgh on 2015-12-07
> **luciano.x said:**
> What is the point?
You can install Ubuntu (64bits) in UEFI mode with GPT. No need to convert to MBR.
Just boot in UEFI mode, wipe the disk, have fun.

Well, that might be the easiest way, but where are instructions for doing such a thing? I have looked in several places, and have only seen instructions (for single boot) to use MBR. [Many instructions also recommend a "CD" (over USB stick) but with the .iso being way over 700 MB, I assume the documentation should refer to DVD, not CD. But that's a different subject.]

Also, for the OP, "MacBookPro A1286" narrows it down to about 22 different models, [http://www.everymac.com/ultimate-mac-lookup/?search_keywords=A1286](http://www.everymac.com/ultimate-mac-lookup/?search_keywords=A1286)
And, AFAIK, if you do install Ubuntu only, somehow you will need to get a OSX system "bless" the disc or wait additional 30 seconds or something like that when booting.

For the past 4+ years, Apple hardware is usually specified by the model name (macbook pro), size of screen (15"), processor type and speed, and **when released** (mid 2012), and for the last couple years, one may need to add if retina or not. The full *model identifier* (MacBookPro7,1) may be unique enough for software purposes here. [http://www.everymac.com/mac-identification/where-to-find-apple-model-identifiers-model-id-machine-model-for-identification.html](http://www.everymac.com/mac-identification/where-to-find-apple-model-identifiers-model-id-machine-model-for-identification.html)
Model name and year released is usually what owners know their Mac by.

---

### Post by BobUgh on 2015-12-07
> **Randymanme said:**
> I've recently been gifted with a Macbook Pro A1286.  My intentions are to wipe the disk and install Ubuntu.  I've been googling this topic and have read a lot about and around it --  most of which are rather too technical and convoluted for me.  I did, however, stumble upon some directions that seem a little bit too simple to true: ()please see screenshot)

Am I to understand that I can just use windows to convert the UEFI disk to a MBR disk, and then install Ubuntu without further ado?

With the caveat I am trying to understand this myself, I think the answer is yes, because:
I installed a MBR disc in a MacBook Pro and without ado, it booted into Ubuntu. But it took a while.
Until you bless it using terminal in OSX, it will have a long boot time. And I think that will be whether you leave it as UEFI or convert it to MBR.

So you want the MacBook Pro to boot only to Ubuntu? I have also tried reading about Ubuntu on Apple hardware, and "convoluted" is a nice way of describing the help pages. Many of them are simply out of date. I know maintenance of documentation is difficult and costly, so I'm not complaining, just acknowledging. If I just understood better and had more time…

As luciano.x suggests, you might be able to reformat and install ubuntu and just ignore most of the documentation details and caveats regarding MBR and GPT. (?) If you have a recovery partition (often hidden), it will be to your advantage to keep it. I think the only advantage to MBR is if you are cloning (or just swapping the disk) from an older PC system to a Mac and may want to move it back again.

What year is your macbook? It could be one of 22 models, from a MacBook Pro "Core 2 Duo" 2.4 15" (Unibody) 2008 to a MacBook Pro "Core i7" 2.7 15" Mid-2012. I think they all will run 64 bit.

Unless it is old or will be used just for some dedicated purpose, I think you will want to make it dual boot, or at least have a way to boot OSX (e.g. from a USB memory stick, or the recovery disc/partition). I say this because after installing Ubuntu, you will probably want to boot into OSX on occasion. Or at least have access to an OSX system and be able to connect the disk to OSX (assuming the disk is your internal hard drive, that would mean removing it from your MacBook Pro and docking it in a usb (or other) adapter and connecting it to an OSX system as a external hard drive).

You might want to run OSX updates/upgrades mainly to get recent firmware. For example, some (many?) Macs will accept more ram than (originally) specified but only after some firmware update… You should do this from OSX before installing Ubuntu; if the machine is old, that may be sufficient as it is unlikely there will be future firmware updates.

But after installing Ubuntu, you will want to at least "bless" the disk or (partition?) from OSX, or your boot up times will be very slow. I haven't done this myself but that is my understanding. If your machine is recent, if you leave it as GPT and only overwrite the main partition and don't touch the recovery partition (and don't overwrite the EFI partition?), you might be able to boot into recovery and do the blessing. If your machine is very recent, you don't even need to worry about the recovery partition because you can  do "internet recovery" with no OSX on the hard drive. Within recovery you can launch a terminal app, it isn't obvious but it is one of several apps available. If you can't do either of those recoveries and/or if it is an older machine, you may eventually want the optical discs that originally came with the machine. So what year the machine is a factor in your decisions.

My experience:

I started using Ubuntu 7 years ago, then about 4 years ago 99% switched to OSX and 1% Ubuntu, and now just starting to try migrating my old Ubuntu system to newer hardware. I am considering using Apple hardware for Ubuntu, but have not really done the migration for good. (I may want to run a virtual machine in OSX but that would be the subject of another thread.)

Recently I (badly) cloned my old Ubuntu 12.? system disk (on a ~2005 Acer) to a SSD, installed the SSD into a ~2009 Dell, and Ubuntu worked. So that was with MBR, NTFS, EXTn, linux swap partition, and (an old?) GRUB; but I had not cloned the disk correctly (could only boot into Ubuntu) so I took it back out. Then days later I decided to put the SSD in a brother's 2012 MacBookPro. I installed the SSD and was about to boot into internet recovery when I decided "just for fun" to see what happened if I just powered on. I got a grey(?) screen for a LONG time (I assume because it wasn't blessed) but eventually Ubuntu came up and I was able to log in and it looked like my old Acer but bigger and faster! I was quite surprised, I had thought MBR didn't work in Apple hardware, but I had misunderstood the documentation. I didn't do much, I was logged in less than a minute before I shutdown and booted into recovery, where I reformatted the disk to Apple defaults: GPT, single apple partition and then installed OSX. (I want to put Ubuntu on my 2010 MacBook Pro, the 2012 wasn't mine to keep.) End of my experience.

The following discussion is worth reviewing if you have Apple hardware and don't know what to do with it: [http://ubuntuforums.org/showthread.php?t=2198619](http://ubuntuforums.org/showthread.php?t=2198619)

If your MacBookPro is still intact and you have questions, then would you please post more info on it? Year, OSX version, ram and hard drive sizes…
And what partitions are on your disk.
(There have been times various disk utilities don't show me some partitions.
I'm not sure if OSX disk utility shows grub but my memory is blurry.)

On OSX to see the hidden partitions with OSX Disk utility, first in terminal do:
```
defaults write com.apple.DiskUtility DUDebugMenuEnabled 1
```
Then startup the graphical disk utility, goto Debug, be sure "show all disks" is checked. The hidden partitions should be shown on the left but grey.

---

### Post by oldfred on 2015-12-07
Some slightly more up to date Mac UEFI info:
[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[http://www.rodsbooks.com/ubuntu-efi/index.html](http://www.rodsbooks.com/ubuntu-efi/index.html)

---

