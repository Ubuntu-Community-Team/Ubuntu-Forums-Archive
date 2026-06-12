---
title: "'bugs' with live cd"
date: 2005-05-08
forum: Apple PPC Users
---

### Post by dnix71 on 2005-05-08
I like the ppc live version on my G4 1.25 GHz eMac, but have a couple of requests for improvements.

  First, I'm still living on dialup, so I can't get on the net for support with the live disc since it doesn't support the Motorola SM56 modem that comes with my eMac. That modem is a very common WinModem also. Is there some way to add drivers to the live version to make dialup possible?

  Second, there is no native support for mp3 playback. I assume that is for legal/licensing reasons, since mp3 is a proprietary codec. Unencrypted dvds and vob files don't play either. XINE multimedia player from sourceforge.net is no longer available compiled for fear of legal challenges relating to software patents and propritary codecs, too.

  Maybe a script could be added to the live version so when someone tries to play an mp3 or mp1/mp2 movie Ubuntu would suggest transcoding them into ogg or mp4, and explain why non-proprietary, non-patented codecs help keep music and movies free for everyone.

  VLC (videolan.org) has warned they may be put out of business if the European Parliament fails to override it's own commission on software patents.

 And third, I could not get live Ubuntu to unmount or eject a dvd from an external LaCie firewire drive with a Pioneer 108 inside. The button on the front for opening and closing wouldn't work either and there is no drop down menu with control click and the one button usb mouse on the eMac. The eMac has a key in the upper right of the keyboard for disc eject for the internal drive.

---

### Post by Len on 2005-05-09
Well, the licencing reasons only exist in the USA now. I wonder why there is no europe only version of apps or so.

But, ejecting CDs can be done with a commandline. Syntax:

```
eject /dev/<devicename>
```

If I remember correctly it works also when the drive is empty.

---

