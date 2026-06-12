---
title: "How to get madwifi working with acer 5520"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by Mightygringo on 2008-03-12
how do ii get madwifi 0.9.4 to work on my laptop,can u please help me through this command ata time

---

### Post by wormser on 2008-03-12
It has been a while since I have installed madwifi.  I believe you just need to install madwifi-tools.

```
sudo apt-get install madwifi-tools
```

---

### Post by Arkenzor on 2008-03-12
Isn't madwifi included in the Ubuntu restricted drivers package? If that's the case, then it should have been activated by default. If not, go to System -> Administration -> Restricted drivers manager and activate the driver (whatever it's called, if the name doesn't contain "madwifi" then it'll at least have a reference to your wireless chip model).

If the madwifi driver isn't available in the Restricted Drivers Manager's list then it probably means it's not the right driver for your wireless card.

---

### Post by Mightygringo on 2008-03-12
nah it shows up on the restricted drivers it just  i dont know how to get my wifi card to show up in my network manager

---

### Post by linux1time on 2008-03-12
are you sure that ubuntu is identifying your wireless card as the real one you have?i ask you this cause there are several cards that ubuntu doesnt recognise well

---

### Post by Mightygringo on 2008-03-12
nah its the main brand used with madwifi,i had it working,i guess i pulled off a fluke now i cant get it to work,

---

### Post by Mightygringo on 2008-03-12
athreo or something

---

### Post by jonnywombat on 2008-03-12
athros support can be a bit flakey with mad wifi drivers.. it kinda depends on exactly which chipset you are using..

However ndiswrapper can be used and works well (i use it myself)

There is a good how to at [http://ubuntuforums.org/showthread.php?p=4295874&posted=1#post4295874](http://ubuntuforums.org/showthread.php?p=4295874&posted=1#post4295874) (You may need to scroll up a few posts)...

If you have a different atheros chipset than the one mentioned here then visit [http://www.atheros.cz/](http://www.atheros.cz/) to get your drivers... but the process remains the same

---

