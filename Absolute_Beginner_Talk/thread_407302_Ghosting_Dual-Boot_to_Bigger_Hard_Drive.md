---
title: "Ghosting Dual-Boot to Bigger Hard Drive"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by wsmoser2004 on 2007-04-12
Right now I have a dual-boot setup on my laptop where I dual-boot XP and Kubuntu.  The hard drive is only 40 GB, which is starting to get a little tight, so I'm considering getting a new (bigger!) one.  My question is: if I ghost the hard drive directly from the old one to the new one with Norton Ghost (or something similar), resizing the partitions and all, will it "just work"?  Will GRUB magically figure out the locations of the partitions, or will I need to re-install it?  

I'm probably overanalyzing the situation...but I really don't know that much about how partitions and such work out on the disk...

Thanks in advance for any advice!

---

### Post by mohjlir on 2007-04-12
Ghost has worked for me before in situations like this, except with w98. You may have to reactivate XP after you ghost it, but it should just work.

---

### Post by thefoolisme on 2007-04-12
Since I am in the middle of doing this, I thought I'd make a suggestion.  I ghosted my drive using the standard options from one drive to the other.  Switched the mast/slave configurations, tried to boot up, and got a blank screen with "GRUB" at the top that never went anywhere.  

I think I figured out my problem though.  I needed to go into the "Options" and make sure that I selected the option to copy the boot sector too.  I don't think the standard setup ghosts the boot drive.  I re-ghosted last night, but haven't tried it out yet.  With any luck I should be able to go home tonight, turn it on, and go.

---

### Post by wsmoser2004 on 2007-04-12
OK, sounds good.  I've done lots of ghosting of hard drives with just one partition (Windows), but I didn't know if dual-boot would affect it.

Thanks for the answers!

---

### Post by seshomaru samma on 2007-04-12
I dont know about dual boot but I ghosted Xubuntu many times and very often I would lose Grub
So better prepare a Live CD or SystemRescueCD with which to reinstall grub , if needed
like this:

1. Boot from a Live CD, like Ubuntu Live, Knoppix, SystemRescueCD, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0)"

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

### Post by wsmoser2004 on 2007-05-07
I just got a new hard drive (120 GB), ghosted it, and now magically it works!  I did select the "Image Boot" option in Norton Ghost to copy the boot sector as someone above suggested.  The only interesting part was that I managed to get lucky(?) and when I booted Kubuntu from the new hard drive I got the "/ has been mounted 30 times without being checked, check forced..." thing.  It scanned the whole drive and claimed that it found and corrected errors, and then rebooted.  Everything except my swap space worked after that, but that was a simple search on Ubuntu Forums to fix :).  So, yes, everything will "just work".

---

### Post by thefoolisme on 2007-05-07
Yes, as long as you select Image boot in the Norton options, it will copy the entire dual-boot drive without any issues.  :-)

---

