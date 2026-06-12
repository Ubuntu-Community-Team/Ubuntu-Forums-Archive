---
title: "Gusty Sound Problems"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by championboxes on 2007-11-01
Ok I am having problems with sound in gusty... first I have a alienware m9700 laptop... I have had many problems with ubuntu and the x server... 

I have been able to resolve those problems by installing the drivers through the terminal...

well with gusty i did the same thing as i always do for fiesty by installing the video drivers through the terminal... it still didnt work... so i played around and ended up deleting the xorg.conf file... now there is a xorg.conf.failsafe and xorg.conf.failsafe.bak file...

well that fixed the problem now i can see the desktop and all that jazz... but now i do not have any sound... does anybody have any suggestions of what i can do? other than that i think everything is working fine... other than the feeling in the back of my mind that the x server may crash at startup...

---

### Post by rykel on 2007-11-01
I also deleted my xorg.conf file and now, no matter what I do, I do not have sound. I have also commented out the line referring to asoundrc.conf in ~/.asoundrc and still, no improvement.

btw, is sound affected by xorg.conf?? I thought that it isn't...

---

### Post by championboxes on 2007-11-01
Well my sound worked before i deleted the xorg file... but the screen wouldnt come on... idk what to do...

---

### Post by rykel on 2007-11-06
Hi all,

My sound is finally back!!!

[INDENT][LIST=1]
[*]Right-Click Volume Applet
[*]Open Volume Control
[*]Edit
[*]Preferences
[*]Headphone Jack Sense
[*]Close
[*]Switches
[*]UN-check Headphone Jack Sense
[/LIST][/INDENT]

My laptop soundcard is ICH6.

Hope that helps.     :guitar:

---

