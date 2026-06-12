---
title: "Blue &amp; White G3 in trouble"
date: 2008-02-13
forum: Apple PPC Users
---

### Post by Colinwlu on 2008-02-13
I decided to try Kubuntu 6.04 on my old B&W G3.  It has 3 hard drives, an 80gb with OSX Tiger a 20gb and it's original 6gb.  I loaded Kubuntu onto the 20gb drive and after a lot of trouble and searching on the web I eventually got Kubuntu to run.  Since then it has all gone down hill.  The screen size has changed to 640x480. Screen size cannot be changed as in System Settings>Display the slider no longer shows any other option and wont slide anyway.
I can not boot Mac OS, cannot boot from cd/dvd's, neither the Mac or Kubuntu dvd's. 
I'm not that well up with computers so only basic and easy to follow help please.
Thanks
Colin:confused:

---

### Post by stevejesus on 2008-02-13
First off, the B&W G3 if memory serves comes with an ATI Rage 128 Pro video card.

More than likely the reason you can't get above 640x480 is that Xorg is using the VESA driver, which sucks.

See if you can install fglrx.  I am not sure if it supports such an old card or not, but you can try,

Alternatively, you could do the following;
```
sudo dpkg-reconfigure xserver-xorg
```

This will run a program that will let you reconfigure the xserver.
First it will ask you to select which driver you would like to use.  Select the one that most matches your vid-card, and then answer all the rest of the questions.

Lastly, Kubuntu is TOO mach for that relic to handle with KDE and all that (IMHO).  It should struggle much the same way Tiger does.  Man, thats gotta be SO slow.  I would consider Xubuntu, or even a Command-line driven install.

---

### Post by stream303 on 2008-02-13
From what I've read, yabootconfig will work on older machines when it comes time to do things like triple-boot.  Yabootconfig won't work on a G5, but might be something to remember when you get your other original booting problems worked out.

How's your battery?

---

### Post by Colinwlu on 2008-02-15
Thanks guys but unfortunately my old faithful has failed me.  It has after 11 years, gone to the big Apple in the sky!!  SteveJesus called it a relic and said it was slow.  That is also a description of me so we went well together.  
Until I get another old relic I'll stick with OSX on my imac G5.
Colin:cry:

---

