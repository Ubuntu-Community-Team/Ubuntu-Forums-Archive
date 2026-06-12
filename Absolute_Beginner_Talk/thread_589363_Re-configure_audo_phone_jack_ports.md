---
title: "Re-configure audo phone jack ports"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by stfury on 2007-10-24
HI guys , 
sorry for the nuubosity
on my mobo the green output sound jack does not work - however through windows (control panel - sound effects) i was able to reconfigure the 3 audio jacks so that blue was back speaker out and pink was still microphone so everything worked fine - i plugged my hifi into the blue one.

please could someone tell me how to do this on ubuntu 7.10 im sorry for the trouble.

cheers,
stfury

---

### Post by startherepodcast on 2007-10-24
You might want to try typing "alsamixer" into your Terminal. You get a control panel with all your channels of your sound card (at least you should). Just play around with the settings a bit (m key to mute and unmute, the rest is pretty self explanatory), the channels on the far right end of the interface, I cant remember their name,  might also be worth a try.

Hope that helped, PM me if it doesnt work

Leon

---

### Post by stfury on 2007-10-24
pls wil someone help me with this it is still giving me a load of trouble thanks the alsomixer didnt work at all i pm'd u leon

---

### Post by stfury on 2007-10-25
im sorry to reply to my own post but pls wil someone help me sort out this problem

---

### Post by Qwerty_ on 2007-10-25
Alright I once had this issue and I was unable to solve the problem it was suggested to me to try these commands

```
sudo dpkg-reconfigure alsa-base
```
```
sudo dpkg-reconfigure alsa-utils
```

Perhaps they will work for you.

The original topic was [http://ubuntuforums.org/showthread.php?t=512263](http://ubuntuforums.org/showthread.php?t=512263)

---

### Post by stfury on 2007-10-25
no thanks for the help but they didnt work. look at this pm this is what i mean
------------------------------------------------------------------------------
u see the way i did on windows wat that i just set it to surround sound so it automatically made the blue phonejack (center speaker out) instead of (line in) like its default.then i just plugged my hifi into that so i didnt have to plug it into the green broken port surely there must be a way to do this in linux aswell?

cheeers stfury thanks for the help man

---

