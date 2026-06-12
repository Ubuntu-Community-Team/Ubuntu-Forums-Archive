---
title: "Two problems:  Internet seems slow &amp; CastPodder install"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2006-03-29
I'm quite new to Ubuntu & Linux but enjoying the learning though it can be frustrating at times.  Dual booting XP and Ubuntu.
#1  Firefox seems to be slow getting pages under Ubuntu compared to my XP boot.     Is there something different in how it would be working?  My connection is via D-Link router (DI-524) and hi speed access.  The router is connected directly (wired) to this machine, one of three in house.
#2  Tried to install CastPodder with no luck.  Downloaded tarball (CastPodder-4.0.tar.bz2) and 'extracted' files to desktop folder.  Now what?!  (the instructions at castpodder site are minimal and assume a lot of base knowledge I don't yet have!)
Thanks from a newb!

---

### Post by tkiesel on 2006-03-29
#1: One immediate help is this.  Type about:config into the Firefox address bar. In the "Filter:" field at the top, type in ipv6 . That will filter out everything but one entry titled network.dns.disableIPv6 which by default is set to false.  Double click that entry to make it true.

Other tweaks can be found [various places]("http://www.testingreflections.com/node/view/1549") online, and are common to Firefox on any platform. 

#2: I haven't tried installing CastPodder yet. (Probably will soon though.)  I'm of limited help there.  Most programs will come with instructions inside the extracted folder.  Check there to see if there are any better install instructions.

Good luck and happy computing!
-T

---

