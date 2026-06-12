---
title: "Just installed Ubuntu on a iMac G3"
date: 2009-03-06
forum: Apple Hardware Users
---

### Post by slammed87d21 on 2009-03-06
Well, this is the first Apple I've installed Ubuntu on, so I'm probably just making a noob mistake. The problem I have is the screen resolution and refresh rate seem off. I have Ubuntu 6.10 installed from the alternate install cd.

---

### Post by avtolle on 2009-03-06
Did you mean 8.10? If you really did install 6.10, it hit end of life April, 2008, and there aren't any repositories up for it, although the old releases site might have the packages still (don't know).

For most of us, installation of newer releases (since 7.10 in my case) has required manual editing of the /etc/X11/xorg.conf file. You should do a search, as I recall seeing some working xorg.conf files posted for g3s here on the Forum.

---

### Post by slammed87d21 on 2009-03-06
I did, and when I brought up the file, it was empty. I've yet to find a post that explains what to do when the file is empty. I may have looked over a post, but I've not found anything yet.

---

### Post by avtolle on 2009-03-06
On 8.10, /etc/X11/xorg.conf is indeed empty. See [http://ubuntuforums.org/showthread.php?t=1058232](http://ubuntuforums.org/showthread.php?t=1058232) and in particular the attached text file containing the OPs xorg.conf file created for his/her 8.04 installation on a similar computer.

BTW, if memory serves, in /etc/X11 there is a file named something to the effect of xorg.conf.failsafe; what I did was copy it to xorg.conf, open it in a text editor, and determine the changes I needed to make to it via manually editing to get something usable for my G4 Cube. Still isn't "perfect", but I'm able to get the 1024x768 resolution for my display. Interestingly, when I reboot, I get the warnings about being in low graphics mode, select run in low graphics mode for this session, etc., but once signed in I'm not in low graphics mode any longer. 

Anyway, the linked tutorial is very good, and will hopefully give you some clues as to how to proceed. Good luck.

---

### Post by slammed87d21 on 2009-03-06
Thanks. I'll try that in a little while. I'll post the results.

---

