---
title: "Sound Setup"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Armaniboy on 2007-07-08
I have gone to Systems>Preferences>Sounds on Ubuntu Feisty Fawn 7.04 and can NOT setup sound on my computer...well laptop to be more specific. The card is identifiable on the drop down windows. Its the Intel 82801DB-ICH 4 or at least I believe its that. There are like 3 options on the drop down all Intel and then Auto Detect. I put autodetect and then click on the "Test" button but it seems like it just stalls.  There is also ALSA, ESD and OSS as options, but I couldn't tell u the difference between them if I tried. I can play media like Videos, but there is no sound. This problem is on Amarok, Totem Player, and ANY media player I have. Even VLC which surprised me. There was a post about inserting a command line in the Terminal that automatically checks the upgradeness of the card to see if it just needs an update. Did that and it installed nothing because I guess I'm set. 

IF ***** I have to go in threw the terminal to fix this, please make the posting really cllear because I"M REALLY REALLY REALLY new at using the terminal. I SORT of understand how to use it and the synatpic system manager as well I'm IFFY about using. However the ADD/REMOVE options...I guess you could say I'm a PRO :lolflag: Thank you for helping me :)

-Armaniboy-

---

### Post by Sean K on 2007-07-08
You won't get much help here with your sound. You'll only get replies telling you to search for the "Comprehensive Sound Guide" which I have never found usefull, though you may find it so. Ubuntu and sound don't seem to go together, especially in Feisty. Maybe they'll one day release a fix for it, but for now...

---

### Post by forrestcupp on 2007-07-08
I hate to ask simple questions, but are the volumes turned up in the system audio mixer?  Either right click on the audio icon in your system tray and choose to open the mixer window, or in a terminal, type:
```
alsamixer
```
alsamixer brings up a command line GUI for setting your volumes.  Make sure the master volume, and any other applicable selections are turned up.

That's just a starting point.

---

### Post by reset3x on 2007-07-08
> **Sean K said:**
> You won't get much help here with your sound. You'll only get replies telling you to search for the "Comprehensive Sound Guide" which I have never found usefull, though you may find it so. Ubuntu and sound don't seem to go together, especially in Feisty. Maybe they'll one day release a fix for it, but for now...

:-({|=

---

### Post by Armaniboy on 2007-07-09
I tried right clicking on the volume icon and was able to open up the panel and adjusted it so I could get sound. HOWEVER..I ONLY get sound through the headphone jack. When I take the jack out I can't get sound. I have speakers setup to the headphone jack and the sound seems very soft even when I have them up all the way. The setting on the control panel for the volume control as well are up all the way and NOT muted. I'm stumped on this one. 

-Armaniboy-

---

### Post by Kingskid on 2007-07-09
Try here:

[http://ubuntuforums.org/showthread.php?t=491007&highlight=no+sound+acer](http://ubuntuforums.org/showthread.php?t=491007&highlight=no+sound+acer)

---

### Post by Armaniboy on 2007-07-09
I tried that but I don't have an ACER computer or anything ACER in my comp. Is there an alternative solution to this?

-Armaniboy-

---

