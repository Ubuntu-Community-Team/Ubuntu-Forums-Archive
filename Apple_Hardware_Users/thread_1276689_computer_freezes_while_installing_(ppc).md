---
title: "computer freezes while installing (ppc)"
date: 2009-09-27
forum: Apple Hardware Users
---

### Post by megabenman on 2009-09-27
Hey, I have a 2nd generation 20" iMac G5 with 512MB of RAM.  Originally I had a 170 GB partition with Mac OS X 10.4.11 and a 61.5 GB  partition with Kubuntu Feisty.  I posted a thread a while ago here asking for help upgrading kubuntu to 9.04 but the most common suggestion was just a clean install.  I ran the kubuntu 9.04 live CD and tried to install it.  However it consistently freezes after picking my keyboard layout.  It says "scanning disks" and then freezes at 52%.  Then, I put in the ubuntu disk and ran the install.  It got to the prepare disk space screen (step 4) without freezing, but I noticed it would not let me isntall over the 7.04 partition.  So, I closed the installer and opened up gparted.  I deleted the 7.04 partition giving me 61.5 GB of free space.  I went back to the installer and once I got to step 4 I selected "use the largest continuous free space".  The bar at the bottom showed exactly what I wanted, a 170 GB OS X partition and a 61.5 ubuntu partition.  I pressed forward and this box came up with a loading bar.  It reached 100% and went away, but then my mouse froze.  I can't press any keys on the keyboard or move my mouse.  The fans are not maxxed out which is good since I know the computer isn't totally frozen but it still sits there forever until I hold power.

How cna I fix this?  Thanks

---

### Post by megabenman on 2009-09-27
An update.. I managed to install ubuntu throught the alternative CD.  It appeared to install successfully.  But, when I try to boot into through yaboot it never gets past the black screen with the white cursorline in the top left.  Any help? Thanks.

---

### Post by megabenman on 2009-09-29
Another update...
I tried many different boot options like nosplash, video=ofonly, and nosplash video=ofonly but they did not work either.  I then deleted my partition and  tried this page:
[http://usablelinux.wordpress.com/2009/05/21/ubuntu-9-04-on-an-imac-g5/](http://usablelinux.wordpress.com/2009/05/21/ubuntu-9-04-on-an-imac-g5/)
and, like it said, installed using "video=ofonly."  That yieled the same results.

Any help :(

---

### Post by rjcalifornia on 2009-09-29
Hey! the freezing part with Kubuntu Live CD 9.04 happened to me. What I did was burning the disk at a lower speed (24x) (which it worked) and typing 

live nosplash powerpc

---

### Post by megabenman on 2009-09-30
ehh im a powerpc64 :P

---

