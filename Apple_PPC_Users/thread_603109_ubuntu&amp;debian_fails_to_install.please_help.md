---
title: "ubuntu&amp;debian fails to install.please help"
date: 2007-11-04
forum: Apple PPC Users
---

### Post by feardotcom on 2007-11-04
Power Mac G4 400mhz
256mb ram
ati rage pro 128 16mb video card
40gb maxtor hard drive


debian and ubuntu both fail to install at 33% at "Partition Formating" i have tried it multiple times and still nothing, anyone any ideas?



this is what debian says at 33%   "fixing recurisve fault reboot is needed!"

---

### Post by iAtari on 2007-11-05
Hmm.. perhaps look at the program you used to write the .iso, i'm assuming its a live CD? 

Try the slowest write speed available, and/or re-download the .iso file from a different mirror.

How far in the partition formatting can you get? How are you formatting your drive? (Clean install, Wipe everything, partition, ect.)


iAtari

---

### Post by feardotcom on 2007-11-05
with debian i actually was able to get option f4 to come up and it was giving errors about the hard drive.
kernel denied access because of bad sector or something, so i am assuming the hard drive is finally going out?

---

### Post by feardotcom on 2007-11-05
after replacing the hard drive and just letting it sit for about 4-50 mins at 33% it goes to a blank screen and starts printing out this:


(process: 17838): info:  kbd-mode: setting console mode to unicode (utf-8)

killed
killed



and just keeping repeating that over and over, except the process numbers are different each time

---

### Post by iAtari on 2007-11-05
Sounds like a bad hard disk on this one.

---

### Post by feardotcom on 2007-11-06
yeah i think it is, and after alittle bit it just me like  train i feel so stupid, i burned a cd at 40x for a 32x cd rom, it didn;t even dawn on me when you said that in your previous reply, so i reburned at 8x and it installed fine, no problems.....but the 120gb hard drive is dead, but my 40gb is fine my only problem now is when i boot up the mac, everything goes through saying initializing this and that etc etc and then it seems like its going to x windows and then the monitor pops up saying in a moving box "sync. out of range" the video card is a ati rage pro 128 16mb or 8mb video card pci, but it says on the agp, which i dont understand, if it says agp but its in a pci slot...wtf?

---

