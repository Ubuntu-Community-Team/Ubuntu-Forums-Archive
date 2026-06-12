---
title: "iTunes and iPhone under VirtualBox"
date: 2011-05-10
forum: Apple Hardware Users
---

### Post by boomcat on 2011-05-10
I run iTunes (10.2.2) under Windows 7 inside Oracle VirtualBox and use this to sync my AT&T iPhone 4. This works fine and I have been able to sync my iPhone apps and music successfully.

Today I synced my iPhone and then started to upgrade the iPhone software to 4.3.3. Halfway through the process, the iPhone crashed, with the scary "Connect to iTunes" message locked on the screen. I restarted the computer and restarted VB, Win 7 and iTunes and tried to restore the iPhone, but it crashed again and again, with error message "8000065". This indicates a USB connectivity problem. I disconnected all unused USB devices and removed all of the VB USB filters except the iPhone, but it still kept crashing halfway through the "restore" process.

On my third or fourth attempt, I decided to check the VB Devices/USB list whenever the iTunes progress indicators had been still for more than 15 seconds. When I did, I found that the iPhone had been unchecked, so I checked it. Immediately, in the lower right corner of Win 7, a small window opened saying, "Windows is searching for device drivers", then "Windows is installing Apple iPhone driver." At that point the restore process continued, and the progress indicators on iTunes and the iPhone began to move again. I had to do this twice more during the restore process. But ultimately the iPhone restore process finished successfully. Of course, I still had to sync my phone to restore all of my music and apps, but that process finished by itself in about 30 minutes with no intervention on my part.

I am using Ubuntu 10.10 as the host OS, Win 7 was fully updated before I started this, and iTunes was 10.2.2.

It is interesting that this loss of USB connectivity never occurs during routine syncing of music and apps, only during iPhone op system upgrades!

Any comments or suggestions?

---

