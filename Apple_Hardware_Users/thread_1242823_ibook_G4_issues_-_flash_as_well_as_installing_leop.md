---
title: "ibook G4 issues - flash as well as installing leopard"
date: 2009-08-17
forum: Apple Hardware Users
---

### Post by MrRedPants on 2009-08-17
At my wits end.

I have an ibook G4 "gifted" to me. It has a powerpc g4 (1.2) processor at 1.33Mhz.  It had OS X 10.5.7 (leopard) on it and one day, it froze became unbootable. No tips or tricks will work (keyboard combinations etc)

The friend has leopard install DVD (retail) but not original discs that came with ibook. The ibook has a CD drive, not a DVD drive which makes the DVD useless. She says the guys at the apple store installed it. Great. Anyone want to go pay the 'genius' bar a couple hundred bucks to install the operating system? Not me.

So, after hours of trying to figure something out. I installed ubuntu 9 (the most recent version) - quite easily I might add and intended to just use this OS. The problem is that Adobe Flash 10 is not supported on PPC which is a big deal breaker. No youtube, no hulu, no flash. It just wont work. I cant find a solution there.

So, I'm back to my original problem. How to get OS X leopard onto this machine with no CD drive. I have googled and googled, and more googling. I have not binged, however. No binging. 

Most tutorials reference doing things to the mac hard drive, mounting iso images etc from WITHIN the mac. This presumes the MAC is working which this is not. Then there is target disk mode. I have been unable to get a powerbook G4 to see the ibook in target disk mode so that is no good. I even got desparate and 'aquired' cd's to install tiger and that gives a plethora of error messages.

So, what I do have. A working ubuntu installation and a 7.5GB iso image on the desktop of ubuntu that is the leopard install CD. There must be a way to go from there to get the thing loaded. Oh, and yes, you can use an external hard drive but it must be firewire. Good luck locating one of those to borrow from your neighbor. Apple, apple, apple. How do I hate thee.

Anyway, the bottom line question - other than any someone might get from reading the above. Is there a way to partition and format the drive within ubuntu, load/mount/extract/copy the leopard dvd iso onto that partition and allow the ibook to start from that partition / drive? 

Thanks in advance and for reading.

---

### Post by tiresia on 2009-08-17
Flash and Java can be a real problem on a powerpc running GNU/Linux. 
A couple of questions, before giving you my suggestions
1. Do you have another Mac?
2. Do you want to keep Ubuntu on your iBook?

---

### Post by MrRedPants on 2009-08-17
1. I do have another mac (borrowed from a neighbor) - it is a powerbook G4. When I put the ibook in target disk mode, the powerbook just wont see it. Interestingly it sees the cd drive (if I have a cd in there), just not the HD. The powerbook has an old os on it (10.2 i believe)

2. I just want it to work well. I'd keep ubuntu if I could get the flash to predictably work. I'd use other linux version. or I will put an apple os back on it if I could ever get that to work!

I'm just [not gonna pay a lot for this muffler]("http://www.youtube.com/watch?v=4lk3o-JvfTw"). (dated myself)

---

### Post by tiresia on 2009-08-17
If you mount the Leopard .iso image, can you see all the files to install OSX?

---

### Post by MrRedPants on 2009-08-17
I'm not sure where you're thinking I would mount it, but, in Windows using isobuster, yes, I can see all the install files.

Not sure where you're going, but, I have the iso both on the powerbook G4 as well as the ibook with ubuntu.

Not sure how to mount the iso on either but I assume you're leading in that direction.

---

### Post by MrRedPants on 2009-08-17
I mounted in ubuntu as described [here]("http://hacktivision.com/index.php/2008/02/24/how-to-mount-iso-images-in-ubuntu-the-ea?blog=2")

It mounted the bootcamp install portion of the DVD but not he MAC OS X install. When I look at the iso in IsoBuster in windows, it may be because it's in HFS format. I can screenshot if needed but basically the iso image contains a bootloader install (iso) and the os x install (hfs)

---

### Post by tiresia on 2009-08-17
If you would have an OSX running on your iBook, it would be quite ease.
1. Start from Ubuntu LiveCD and repartition your HD leaving 8GB free.
2. Restart in MacOSX and partition the free Partition with HFS+ with Apple Disk Utility
3. 'Restore' with the Apple Disk Utility on the new Partition the MacOSX Installer Image
4. Choose from the System Preferences as StartUp Disk the 8GB Partition contaning the 'restored' MacOSX Installer
Therefore, if you can get Tiger running on your iBook it woud be quite easier.
Why can't you do that in Ubuntu? Because Parted can't generate HFS+ File System (and MacOSX runs only on HFS+)

The second way, would be to REDUCE the number of Files in the MacOSX Installer, so that it can be contained in a Single Layer DVD. How to do this? Even if it is possible to do it in Ubuntu, it should be easier to do it in MacOSX (on the borrowed PowerBook).
Apple Disk Utility
1. Generate a New Image 8GB (DVD+R DL), HFS+, sparse disk image (.sparseimage), name 'Leopard' - Mount it
2. Restore your .iso Installer on the 8GB .sparseimage 
3. Open Terminal to show all hidden files in Finder
```
defaults write com.apple.finder AppleShowAllFiles ON; killall Finder
```
4. Move to the trash all optional files that you don't need - Printer Drivers, Languages .pkg, additional fonts, X11
Here is the list (it can be a bit different)
  BrotherPrinterDrivers.pkg
  CanonPrinterDrivers.pkg
  EpsonPrinterDrivers.pkg
  FujiXerorPrinterDrivers.pkg
  GutenprintPrinterDrivers.pkg
  HewlettPackardPrinterDrivers.pkg
  LexmarkPrinterDrivers.pkg
  RicohPrinterDrivers.pkg
  SamsungPrinterDrivers.pkg
  XeroxPrinterDrivers.pkg
  
  BrizilianPortuguese.pkg
  Danish.pkg
  Dutch.pkg
  Finnish.pkg
  French.pkg
  Italian.pkg
  Japanese.pkg
  Korean.pkg
  Norwegian.pkg
  Polish.pkg
  Portuguese.pkg
  Russian.pkg
  SimplifiedChinese.pkg
  Spanish.pkg
  Swedish.pkg
  TraditionalChinese.pkg
                                         
  AddictionalFonts.pkg
  X11User.pkg

5. Empty the Trash
6. Terminal - make files again hidden
```
defaults write com.apple.finder AppleShowAllFiles OFF; killall Finder
```
7. Apple Disk Utility - Create a New Image 4.7GB (DVD-R), HFS+, read/write disk image (.dmg) - name 'Mac OS X Install DVD' - Mount it
8. Restore now your 8GB 'Leopard.sparseimage' on 'Mac OS X Install DVD.dmg'
9. Burn the Mac OS X Install DVD.dmg with the Apple Disk Utility on a Single Layer DVD
10. Restart the iBook from the Installer pressing C

---

### Post by MrRedPants on 2009-08-17
First off, THANK YOU.
 
First option - agreed, would be easy. I dont know why I can't get Tiger on. I get kernal debug errors which ends in panic: we're giving up here or something like that. I put the same cd into the powerbook and it started up fine (booted holding 'c' key). It would seem a hardware issue with the ibook but not supported by fact that ubuntu installs and runs fine. I am trying another copy of tiger tomorrow. I know there are issues with installing versions earlier than the one the machine shipped with (which is uknown to me).
 
Second option - according to the system summary I ran before the machine died, it only has a CD drive, not a DVD drive.
 
I am inquiring about a friends external hard drive that has firewire so that may be an option.

---

### Post by MrRedPants on 2009-08-18
UPDATE:

I was able to get a Tiger install running (as I type). It took some work, to say the least. Once I get that done, I will go with option 1 or I may  just leave Tiger on there. With disk utility on the tiger install disk, I was able to do the partitioning with no problem. I did not test it, but, in the disk utility, an iso image can be restored. What I would have tried was to boot the Powerbook into target disk mode and see if it was seen in the disk utility running from install CD. If so, I would just mount the leopard DVD to the partition I created, set as startup disk and violoa. If that is possible (again, not tested), it would have saved me hours of headache.

The bottom line, if the apple disk utility was available as a stand alone download (amongst any other utility), but that one in particular - if that could be downloaded and run on a bootable CD - it would have saved me a lot of trouble.

As a Windows user and I'd go as far as to say expert - there are so many tools to fix Windows PCs. When this ibook broke, forget it.

Anyway, thanks. I'll post any more updates as appropriate.

---

