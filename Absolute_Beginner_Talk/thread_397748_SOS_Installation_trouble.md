---
title: "SOS Installation trouble"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by deez on 2007-03-31
SOS

Hello all.  I'm pretty new to Linux.  Before I had Mandriva and decided to try another distribution, Ubuntu.  After some initial trouble I got Ubuntu up and running.  I was doing well, but then I decided to re-load windows and set up a dual boot system.  I write to you now from the Ubuntu live CD.  I can't get either windows or Ubuntu to work.  Here's what happened.  After re-installing windows, the OS wouldn't come up, I got a GRUB error.  This, I believe, is the boot-loader trying to find Linux and missing it b/c it ain't there anymore.  Fine, I thought.  I'll reload Ubuntu, partition the drives like I wanted and everything should be dandy.  I manually partitioned the drives, one for Windows, a SWAP of 1 Gig, and then 31 Gigs of ext 3 for root.  The install process got to 15% and stopped.  I tried again.  Same, same.  I tried again, this time opting to format the entire drive as I had originally had success with.  Same, same, 15% and it stops.  I reloaded windows, hoping to take the system back to square one, but I end up with the same GRUB error.  

Any help would be great.  I had UBUNTU for a day and it was great.  I'm a bit gutted I tried to have my cake and eat it too. 

I'm running, or trying to run it on an ACER travelmate 250 laptop.  I have checked the CD and I get checksums failed 0, so I reckon it's alright. 

I had success with Ubuntu 6.06 LTS (what does the LTS mean?), but before I attempted and failed with UBUNTU 6.10.  I have since tried UBUNTU 6.10, but still get the same halting at 15%. 

When it freezes, it is 'writing file system for / to ext 3' or other such computer lingo.  

S.0.C.

---

### Post by zvacet on 2007-03-31
[http://ubuntuforums.org/showthread.php?t=358183&highlight=windows]("http://ubuntuforums.org/showthread.php?t=358183&highlight=windows")

If this not good enough search in **Tutorials&Tips**.it is subforum wich you will find on the front page of this forum.

---

### Post by Austin_KW on 2007-03-31
In gereral you want to install windows first and then linux because the windows install will overwrite the MBR with its own loader and you wont have grub (you can do it the other way 'round and then fix it from the live cd with chroot & update-grub but it is more complicated). 
In this case I am not sure why the windows installation did not do this. Sound like your partitions are messed up. You may want to delete all partions and start again (installing windows first).

---

### Post by deez on 2007-03-31
So...I got it working.  I turned the computer off for 3 hours, came back and did the exact same thing and it worked.  Ubuntu installed itself.  I did't bother with dual boot.  How does one go about adding a dual boot with Linux installed?  Is it possible?  I want the option, but I don't want to deal with it at the moment.  I'm happy to just let it be and learn some Linux.  Thanks.

---

### Post by Woody@N87 on 2007-03-31
I'm new at this myself, but I think Austin's on the money here.  I installed 6.10 with windows running on the machine already and the dual boot works fine, (Although I'm thinking it was a waste, I NEVER boot into windows anymore).

  In your case I think you might have to go back to square one and format the drive, re-install windows then install ubuntu off of the CD.  Not being near as good at this as a lot of the other posters that is the way I would do it.  Somebody else might be able to give you a short cut.

---

### Post by Austin_KW on 2007-03-31
You will need to install grub back to the MBR as windows will overwrite it. I have done it with LILO another linux bootloader so I presume that grub should work.
After you install windows boot from the ubuntu cd
Mount your linux partition somewhere like /mnt (if its not auto mounted)
chroot /mnt (or where you mounted your linux install)
Then I think it is grub-install and update-grub to install grub and generate the menu

---

### Post by deez on 2007-03-31
Uhhhhh...I'll think I'll let it rest for the moment and worry about it later.  There's really only one or two programs that make me even want to use Windows so maybe I can find them on Linux.  Thanks for the help. 

Is it bad for the hardware to change systems so often?

If I install Windows again, how can I be sure that GRUB will not try to boot?  That's what happened last time.  I loaded windows only to have it not be bootable b/c GRUB was looking for Ubuntu.

---

### Post by Austin_KW on 2007-03-31
No problem running different systems.

Not sure why windows did not install its boot loader last time. But you can always boot the CD and fix the boot loader, then update-grub will find you windows install and add it to the menu.

---

