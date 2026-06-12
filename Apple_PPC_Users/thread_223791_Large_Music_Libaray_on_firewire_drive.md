---
title: "Large Music Libaray on firewire drive ?"
date: 2006-07-26
forum: Apple PPC Users
---

### Post by linmu on 2006-07-26
Lin Mu here:
I am swicthing from Mac OS 10.3.9 to "Dapper"
And have a large Firewire drive, that I use to keep my Mac OS on.
While testing Dapper on the internal drive. This works fine.

But I also keep a large (50 gig) music colection on anouther partion of this firewire drive. I do not have room on the internal drive, for this.

So... How do I access this music? 
I have tryed "banshee" and set the location of libaray to the firewire drive. But it only found a few wave files?
I have tryed "amaroK" and got confused?

No I do not want to import all, or even some of this libaray to the internal drive.


All my music is in MP3 by "lame"
System:
iMac DV SE 400mhz, 385 ram

---

### Post by silex on 2006-07-27
Do you have the mp3 decoder installed?  Ubuntu doesn't come with it installed by default because of a "freeness" issue.  If you haven't, install the "ugly" codec package like so```
sudo apt-get install gstreamer0.10-plugins-ugly
``` to enable mp3 playback.  For a variety of other multimedia and restricted software issuses, check out this wiki page:

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by linmu on 2006-07-27
Thank you, 
Yes that was it. I used "easu ubuntu" to load codex's
Odd that I never caught that Ubuntu does not load these.

---

