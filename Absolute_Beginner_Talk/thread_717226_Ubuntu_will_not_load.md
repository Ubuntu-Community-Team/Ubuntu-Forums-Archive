---
title: "Ubuntu will not load"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Crash90 on 2008-03-06
I have been using Ubuntu for about a week. 

Today after work, I came home and booted up my computer. Upon coming to the desktop, I noticed some of my icons were different. For example, the shutdown button, now looked like a small runner. My wired network connection looked like a cat 5 plugin instead of 2 computer screens.

Also, my menu's had some different icons/coloring. Everything was loading incredibly slow and my volume recorder crashed.  A bit mystified by all of this, I shut the computer down properly and restarted after about 3 minutes. Now I cannot even access Ubuntu at all. it goes to load up but my screen stays blank after the Dell screen. 

During so my caps lock button and the button next to it (looks like a box w/ a downward arrow in it) will continually flash.


The last thinig I did last night before shutting down was to update my dvdcss and to install the mp3 codecs. I also ripped two cd's.

What gives? Where do I even start?

---

### Post by justin whitaker on 2008-03-06
> **Crash90 said:**
> What gives? Where do I even start?

Do you have a LiveCD around?

 I am thinking hardware, as there should have been nothing software related (assuming you did not upgrade anything else) that would have caused those sorts of issues. 

There is a rescue mode on both the Alternative and LiveCDs....I would check to see where your hardware is failing.

---

### Post by Crash90 on 2008-03-06
> **justin whitaker said:**
> Do you have a LiveCD around?

 I am thinking hardware, as there should have been nothing software related (assuming you did not upgrade anything else) that would have caused those sorts of issues. 

There is a rescue mode on both the Alternative and LiveCDs....I would check to see where your hardware is failing.

I am actual using the live cd right now to post! Let me see if the rescue mode helps!

---

### Post by Crafty Kisses on 2008-03-06
This sounds like your Video card, do you have anyone else in the house with you, it doesn't make since that the icons just changed out of the blue.

---

### Post by justin whitaker on 2008-03-06
> **Codename said:**
> This sounds like your Video card, do you have anyone else in the house with you, it doesn't make since that the icons just changed out of the blue.

I was thinking something like that too. A power spike that fried the GPU?

---

### Post by Crash90 on 2008-03-06
Booted into the Rescue mode through GRUB - my install disk downloaded off ubuntu.com had no rescue mode option....weird.

Here is the error return - I am thinking it's a corrupted HD (This would be the 3rd in this laptop) Or maybe just a reinstall

```


Unrecovered read error - auto reallocate failed
I/O error dev sda sector

Ex3-fs error (device sda-1)
ext3_get_inode_loc: unable to read inode block  indoe =2113537 block=422707

run-init: /sbin/init:permission denied

Kernel panic attempted to kill init

```

At this point the two lights start flashing and all stops, just like a normal boot up. Here's hoping it just needs a new install. If not, I am sure Dell will be thrilled to hear I have linux installed and I need a new HD. Glad I have that 5 year warranty!


EDIT:

I tried to do a fresh install. Unfortunately it failed. Upon trying to format/create a new partition the install fails. The error it gives is:

The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed

Stuck again.

---

### Post by Crash90 on 2008-03-07
Bump! I hope to have this computer back up and running this weekend:D

---

### Post by dwanders on 2008-03-07
I have seen this exact thing where the little button turns into a runner, and some of the Icons are different than before. And normally, as I am booting into Ubuntu (Just after the login screen, as the desktop is loading) there is an error message about the window manager having a problem loading, so it fell back to something else. 

Usually I just reboot and it clear up.

---

### Post by Crash90 on 2008-03-07
> **dwanders said:**
> I have seen this exact thing where the little button turns into a runner, and some of the Icons are different than before. And normally, as I am booting into Ubuntu (Just after the login screen, as the desktop is loading) there is an error message about the window manager having a problem loading, so it fell back to something else. 

Usually I just reboot and it clear up.

Unfortunately that route did not work. I am into some hardware/hard drive problems. Trying to reinstall fails - I can't set up new partitions.

---

### Post by dwanders on 2008-03-07
Oddly enough, I have also had problems re-installing Ubuntu over old Ubuntu / other distros. Many time I like to hop around testing distros. My Last jaunt was to test out Mint, I ended up back with Pro+ech, it seems to run pretty good my old PIII with 256Ram. Anyway, when I have problems: 
1) I boot into the Live distro of choice (somethingsmall and fast with qparted)
2) make sure no partitions are mounted
      a) df should tell you whats mounted
      b) umount any /dev/... hard drives
3) make sure the swap is off   
      a) swapoff -a
4) run Qtparted
5) delete everything
6) then boot the distro you want and try installing it again

before doing that, may want to check the drvie # badblocks -n /dev/... I have headr this should tell you if the drive has any badblocks. 

Hope it helps - goodluck

---

