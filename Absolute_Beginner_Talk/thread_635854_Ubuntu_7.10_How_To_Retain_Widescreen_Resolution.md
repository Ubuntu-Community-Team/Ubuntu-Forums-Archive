---
title: "Ubuntu 7.10 How To Retain Widescreen Resolution"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by wackoyacky on 2007-12-09
A newbie here, recently just upgraded Ubuntu from 7.04 to 7.10 on my Fujitsu P7120 laptop.  Everything went smoothly but after restarting my screen resolution was not detected automatically.

After some research and playin around I found out that I can make it wide by going to Screen & Graphics and select "LCD Panel 1280 x 800" and checked the widescreen option.  After logging out and logging in finally widescreen resolution was detected and “1280 x 768” are already included in the resolution selector in “Screen Resolution” menu.  But after restarting, the resolution keeps on resetting back to “1024 x 768”.  When I check the “Screen Resolution” menu, “1280 x 768” resolution is nowhere to be found.  When I check back the “Screen & Graphics” menu, the model was set to “LCD Panel 1280 x 1024” :(

As for the previous version, I thought there's something that needs to be done in xorg.conf file to make Ubuntu remember the screen resolution set, but everything looks different what is written on the xorg.conf file(well atleast for a newbie like me).  But even still, I can see “1280 x 768” in several sections of the file, so may be this issue is not related to xorg.conf.

Please advice or do you have any links where I can read on and fix this problem?  Honestly this has keeping me awake late at night for the past few days.

Thanks a lot in advance.

---

### Post by short3000y on 2007-12-09
im having the same problem!!!!!!!!!!!

---

### Post by wackoyacky on 2007-12-09
Any inputs anyone?  Is this a clear bug or what?

Thanks!

---

### Post by Hobo Joe on 2007-12-09
What graphics card and drivers are you using?

---

### Post by wackoyacky on 2007-12-10
I don't have my laptop with me right now, but my laptop is Fujitsu P7120

---

### Post by wackoyacky on 2007-12-10
Good news guys!  I was able to find my solution here
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

And the exact fix was this
[http://clipmarks.com/clipmark/3B6BC490-11CD-4CF0-8044-106699A16F48/](http://clipmarks.com/clipmark/3B6BC490-11CD-4CF0-8044-106699A16F48/)

:)

---

