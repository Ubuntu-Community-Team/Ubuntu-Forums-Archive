---
title: "Powerbook G4 Hangs on Install"
date: 2010-03-23
forum: Apple Hardware Users
---

### Post by sargenme on 2010-03-23
I foolishly bought a powerbook g4 without the startup disks. One day kernel panic set in. I have no disk utilities with which to check/repair the disk. 

I tried to save the machine by installing Linux, first Debian, then various Ubuntu releases. Every time I try to install the installation goes fine until it hangs when it writes the ext3 or ext4 file system. I've let it hang for hours, nothing. It hangs at different %-completed points depending on the release (Ubuntu 5.1, PPC hangs at 34%, if I remember correctly). 

I tried booting and running Ubuntu from a Ubuntu 5.1 Live for PPC, but when it loads it gets stuck at a blank brown screen with a mouse pointer. 

Any suggestions?

BTW, I'm a newbie.

---

### Post by DougieFresh4U on 2010-03-23
Hello and Welcome to the Forums 
Don't know if you have disk issues but,try the Karmic 9.10 Desktop PowerPC
Was the only cd to boot with out having to mess with X to get some sort of desktop

---

### Post by sargenme on 2010-03-24
Thanks, this version got to the authentication screen. Unfortunately, it keeps failing automatic login. I haven't set a username or password for this machine, nor do I know how.

---

### Post by linuxopjemac on 2010-03-24
Debian Lenny should work just fine.

---

### Post by sargenme on 2010-03-24
Debian Lenny hangs creating ext3 file system, just like the all the others.  I wonder if there is something wrong with some of the hardware. 

I'm guessing I'm gonna have to just bite the bullet and call Apple and hope they'll send me the installation disks whereby I might test the hardware, and just reinstall OS X. Unfortunately, my wife has forbade my spending any money on fixing this computer :P.

---

### Post by penguirl on 2010-03-24
It sounds like you've got a disk problem, have you tried booting into Single User mode to run fsck? Or even better would be if you can boot into Target Disk Mode and use someone else's Mac to write zeros to disk to find out if there are any bad sectors.

---

### Post by sargenme on 2010-03-25
> **penguirl said:**
> It sounds like you've got a disk problem, have you tried booting into Single User mode to run fsck? Or even better would be if you can boot into Target Disk Mode and use someone else's Mac to write zeros to disk to find out if there are any bad sectors.

I wish I could boot into single user mode; doesn't that require having linux already? The computer has no operating system. 

If I can borrow a firewire from someone I'll try the Target Disk Mode.

---

### Post by penguirl on 2010-03-25
> **sargenme said:**
> I wish I could boot into single user mode; doesn't that require having linux already? The computer has no operating system.

I think single user mode is part of the firmware, try holding down the "&#8984;  S" keys after the startup tone, at the prompt type "fsck" and enter. You may have to run it more than once.

---

