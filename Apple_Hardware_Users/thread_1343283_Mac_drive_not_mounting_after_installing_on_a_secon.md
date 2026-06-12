---
title: "Mac drive not mounting after installing on a secondary drive"
date: 2009-12-01
forum: Apple Hardware Users
---

### Post by Bluke on 2009-12-01
I have searched the forums and didn't find anything, so I hope this is not a duplicate post.

I recently installed (after following all installation steps closely) Ubuntu on an external drive hooked up via USB.  Upon attempting to reboot into Mac OS I found that my internal drive (not the one used to install) would not mount. 

I ran tests on the drive, all came back that the drive was fine.  I was able to repair permissions, reset PRAM, and archive and install on that volume.  However the drive was still not mounting; but it can be seen and can be read and written to when booted from another volume.

In order to get it working again I had to do a clean install of the entire Mac OS on that drive and restore my backup.

My question is more of "why did this happen and what can I do to prevent this from happening again?".  I would really like to get this system running.

Any help will be appreciated.  I am a new member, so please understand if I make any obvious no-no's.

Cheers,

-Luke

Config: Macbookpro3,1 / 64bit intel core 2 duo (TY500) / OS X 10.6.2 / NVIDIA GeForce 8600M GT

---

### Post by linuxopjemac on 2009-12-02
Maybe you touched the partition of that drive during installation with gparted, making it unreadable for MacOS?

---

### Post by Bluke on 2009-12-02
Not quite sure, I'm new to the multiple boot volumes scene.  I might try it again to see if it succeeds, the only problem is that it's a pain to take out the internal drives on my model macbook pro.  Is there a way to unmount my internal while installing to make sure that this won't happen again?

**I found [this]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") site for install on a mac that has a [supporting post]("http://ubuntuforums.org/showthread.php?t=1297229").  I'm going to try this sometime after finals next week and update this thread with the progress.**

---

