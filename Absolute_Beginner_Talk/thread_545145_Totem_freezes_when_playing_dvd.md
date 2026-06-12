---
title: "Totem freezes when playing dvd"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by hiikeeba on 2007-09-07
I just purchased a Dell Inspiron 1420 with Ubuntu 7.04 preinstalled.  The first night I played a DVD with no problem. While on a business trip, I attempted to play a DVD and kept getting an error saying the file could not be opened, and Totem would stop working.  I tried to install Ubuntu Restricted Packages from Add/Remove, but that package is not listed.  Does anyone have any ideas?

---

### Post by AusIV4 on 2007-09-07
Commercial DVDs require a package called libdvdcss to play. It's legality is questioned in some areas, though there is no case law to say definitively that it is illegal. It is not in the Ubuntu repositories, but can be found in some third party repositories with a quick google search.

Additionally, I found that Totem with GStreamer (the default) is incredibly unreliable. I would recommend installing the package totem-xine, as the xine engine tends to run more smoothly.

---

### Post by Seisen on 2007-09-07
This might help you.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvds%29]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs?highlight=%28dvds%29")

---

### Post by Hospadar on 2007-09-07
As for finding the restricted drivers, make sure you have "all available applications" selected in the upper right corner of add/remove

---

### Post by hiikeeba on 2007-09-08
> **AusIV4 said:**
> Commercial DVDs require a package called libdvdcss to play. It's legality is questioned in some areas, though there is no case law to say definitively that it is illegal. It is not in the Ubuntu repositories, but can be found in some third party repositories with a quick google search.

Additionally, I found that Totem with GStreamer (the default) is incredibly unreliable. I would recommend installing the package totem-xine, as the xine engine tends to run more smoothly.
Well, I Googled libdvdcss, installed totem-xine and can get the FBI and Interpol warnings to play.  Nothing else.  Same using gxine.  I can honestly say I know the penalties for copying a DVD.  But still no DVD love.   I appreciate your help.

---

### Post by hiikeeba on 2007-09-15
I finally found a program that would play DVDs, VLC media player.

Thanks for all your help!

---

