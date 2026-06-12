---
title: "Can't boot from CD"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Sk8Save on 2008-02-08
Tried booting from CD.  Changed the BIOS so that the CD-ROM drive was the first in the list (actually, disabled all other in list, so it was the only).  I have 2 CD-ROM drives...the first would do nothing, just spin for a bit and then stop (oddly, that's the RW drive with which I made the CD-ROM).  The second, when the CD-ROM is placed in there and booted, spins for a while, I get the copyright notice (in text) and then it stops.  Any ideas?

Ubuntu 7.10
IBM NetVista P4 2.6
640MB RAM
"normal" o/s is XP

(anything else I need to list to help diagnose?)

TIA!

---

### Post by taurus on 2008-02-08
Have you tried to boot with the same CD on another computer to make sure the CD is bootable?

How did you burn the ISO image?

---

### Post by bumanie on 2008-02-08
Sounds very much like a burning error of some kind, possibly have burned the iso incorrectly or may be burned at a higher speed than the burner is meant to burn at. I once did that by mistake, had a 52x cd, but burner would only burn at 48x max. Got the very early part of the disc before getting unreadable squiggles and colours.

---

### Post by tad1073 on 2008-02-08
[quote=sk8save](actually, disabled all other in list, so it was the only)[/quote]
You didn't disable your hard drive from booting did you?

---

### Post by Sidewinder1 on 2008-02-08
Did you do the md5sum check on the iso file? Did you, then, burn the iso file as an "image"?, at the above mentioned maximum speed of 4X. If the answers to all of the above are yes, do as suggested above, try to boot it in another computer. If it boots in the other computer try using a can of air to blow-out and clean your DVD/CD drive.

---

### Post by Sk8Save on 2008-02-08
Thanks for all the replies.  I used Infrarecorder to burn the CD.  I didn't so anything with respect to limiting or controlling the speed of burning (not sure how to do that).  Also did not do the md5sum or whatever to check the burning.  I do know that there are several files on the CD, not just one.

---

### Post by Sk8Save on 2008-02-08
Okay...it's obviously the CD.  I booted on another computer (HP laptop) and it got just a touch further before giving me a boot error).  Guess I'll have to figure out how to slow the burn down...

---

### Post by taurus on 2008-02-08
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Sk8Save on 2008-02-08
I have downloaded using bitstream torrent.  Can't seem to get WinMD5sum because the website is down.  However, while they work on it, I notice with infrarecorder that there is only 1 speed I can choose:  maximum.  In that drop down box that listed in the document at [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso) (which in the screen shot it lists all sorts of speeds), there is only the one choice.  How do I slow it down?

---

### Post by taurus on 2008-02-08
You can also use CDBurner XP, [http://www.cdburnerxp.se/download.php](http://www.cdburnerxp.se/download.php).  There is an option to set the speed of a burn.  Remember, burn it as an _ISO image_, not as a data file or it won't boot.

---

### Post by sneeks on 2008-02-08
or image burn is also another good one.

---

