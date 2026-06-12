---
title: "Xserver / Graphics all messed up!!!"
date: 2007-05-09
forum: Apple Intel Users
---

### Post by The_Giver on 2007-05-09
After following this guide: [http://ubuntuforums.org/showthread.php?t=198453](http://ubuntuforums.org/showthread.php?t=198453)

to try to update my ATI drivers now xserver  no longer works =(      ( I get that same blue screen we all got when trying to installl ubuntu for the first time).

I get to the little Ubuntu bar and after that I get a command based login =(

Any ideas.. any way to just restore it with the live CD??? I heard ubuntu already came with a more recent driver anyways... damn it.

---

### Post by benanzo on 2007-05-09
while at prompt what happens if you type ```
startx
```            you can reconfigure x by doing ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by The_Giver on 2007-05-09
startx wouldnt happen ... no screens found etc etc.. I finally figured it out.. the problem was that when I was doing an  sudo apt-get install --reinstall xorg-driver-fglrx I kept on getting "not able to download.." even after doing apt-get update .. so I had to look for the package online.. it was a pain to figure out.. everythign seems to be back to normal now though.

One question though.. how do I check if I have dual monitor support at this moment?

---

### Post by benanzo on 2007-05-09
I am not exactly sure for the fglrx driver.  I would suggest you install displayconfig-gtk and see if it's able to setup up a dual monitor config for you.  It is beta right now, but they're really trying to get it going so it can be included in Gutsy.

```
sudo apt-get install displayconfig-gtk
```

then run ```
displayconfig-gtk
``` at a term to start it.

Report back the results, they need bug reports.

---

### Post by The_Giver on 2007-05-09
No luck.. but am I suposed to configure the "localpurge" file btw?

---

