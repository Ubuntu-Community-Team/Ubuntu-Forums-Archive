---
title: "First Post - Dapper Success! on e1405"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by GreenMedallion on 2006-12-05
My new Dell e1405 arrived yesterday, and I had been preparing for its arrival by carefully studying these forums, the ubuntu site, and other related sites, so i could get Dapper on my machine. I am a complete noob. I have used a Mac since about 7th grade, some 17 years ago. Other than that I have faint recollections of DOS games and Texas Instruments, so using the programming language IS learning a new language.

The machine is Core 2 Duo, Intel T5600, and WXGA+, so I anticipated a few problems. There were some, of course, but overall, it was a clean install and a smooth partitioning so I can now dual boot.

Thanks to ubuntuforums.org for help. I actually followed the instructions on [this site.]("http://users.bigpond.net.au/hermanzone/p3.htm") for creating partitions for the dual boot. I thought I would note a few things I noticed as problematic, if only for archival sake.

Edit - I installed Dapper alternative for AMD64.

First, there is a moment during install when the screen goes black, except for 2 white squares. This has been noted on the boards as being related to the video monitor. However, the install runs clean in the background. I just patiently waited and pressed the enter key ever now and then, maybe 3 times total, and eventually the system ejected the install CD and rebooted.

I would highly recommend the Dapper alternative install CD. The text based install allowed me to adjust all the video settings before booting in to Ubuntu for the first time. Herman's [page 7]("http://users.bigpond.net.au/hermanzone/p3.htm") was a great walk through on this.

However with the WXGA+ screen you still need to install the 915resolution to get the widescreen running.

I installed Easy Ubuntu and this was very problematic. It messed with my sources list, and provided me with all types of errors, and just did not install everything it was supposed to - particularly the totem plugins seem problematic (this has been noted elsewhere). I then got Automatix and cleanly installed all the plug-ins necessary for web browsing, and alternate programs I wanted to run. Speaking of which - Swiftfox with its 32bit plugins runs well on my machine, and seemed the best solution to getting past the 64 Firefox plugin issues.

I noticed in partitioning that Dell already partitioned out a few sections as Fat32 and Fat16 - basically for restore and rescue operations. I left those be, though it is an annoyance to have the drives sitting on the desktop.


Now a couple questions-

Is there any way to hide those Dell partitions?

Is there a way to get fonts I use on my Mac over to Ubuntu?

Is there a particular program to set up a network with my Mac? I seem to be able to "find" my Mac (powerbook G4) but cannot see anything on it.

I seem to be having some trackpad issues. I've tried adjusting the settings, but it doesn't seem to solve the problems. Particularly, it doesn't seem to let me drag things out of my Firewire harddrive. (Maybe it is some other issue). Also, there is a delay between when I click my mouse, and the click is registered on screen. This delay leads to me mistakingly opening things, closing things, moving, not moving, etc, constantly. Is there any adjustment I need to make in the software/hardware to resolve these delays?

Lastly, some partitioning questions. I noticed the FAT32 can not accept files larger than 4GB. My only way around this is to make RAR out of files that large. Since my HD is now split 25/25/70 (Win/Ubu/FAT - basically, there are also the small Dell partitions and a swap partition), is there any way to re-partition and expand the Ubuntu partition in order to gain a little more room for holding the large files? Working with RAR is fine though, as it takes up less room anyway.


Well, hope to post more soon as my new brew of Ubuntu warms up.

---

### Post by Chinkostu on 2006-12-05
did you format the Ubuntu partition as FAT32? i would have made it EXT2 or 3 myself, did gparted not give you those options? or did you make the partitions in windows?

as for the small DELL partitions, find the drive locations (probably HDA3 and 4?) and remove them from /etc/fstab using whatever text editor you want (with sudo of course so you can save)

or you could change their locations. mounting them to /media brings them up in the computer window (like windows my computer) and on the desktop. mounting them elsewhere doesn't.

by the way, i'd get used to the way the installer works and suchlike, and the best ways of installing things. i've borked my system enough times now to understand whats happening and why. it may be time consuming, but its best off in the long run

---

### Post by GreenMedallion on 2006-12-05
> **Chinkostu said:**
> did you format the Ubuntu partition as FAT32? i would have made it EXT2 or 3 myself, did gparted not give you those options? or did you make the partitions in windows?

I made the partition prior to install - off the Dapper alternative install CD. Ubuntu is on EXT2. FAT32 is the big chunk of the drive where I can share things between Win and Ubu.

Thanks for the tips on the Dell partitions, I'll fool around with those later.

---

