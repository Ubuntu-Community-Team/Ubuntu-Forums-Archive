---
title: "Linux media center"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by tompie on 2007-02-27
Hi, 
I've following idea:
I want to continue to use the PC upstairs with WinXP, install another PC in the living room as a Linux media center and put a Network Attached HD in the garage, so that I have access to all data (also e-mail) from both systems-PC's. Does this seem a good idea?
Other questions related to this topic:
1.should I use FAT32 on the NAS?
2. does there exist a linux audio player that can deal with a soundcard with more than one output? (I'm quite an audio fan and want to continue to use my mixer). Is this possible with Amarok?
3. I use Google Sketchup now on the winXP. Is there an alternative for (k)ubuntu?

Thanks for the help!

---

### Post by justifier on 2007-02-27
as far as a media centre goes, MythTv as a media centre program, HDD anything but NFTS not sure bout the audio player, just try it, as for google sketchup you CAN get otehr CAD programs for linux, just google linux CAD

---

### Post by igknighted on 2007-02-27
For a media drive, I would strongly recommend you avoid FAT32.  There are file size limitations that in a media setting you may run up against.  I would recommend using ext3 and installing the proper windows driver to read that file system.  Alternatively (though not ideally) you could use ntfs with the recent ntfs-3g driver.  A samba setup might also be an option (now that I think about it, probably the best option).

---

