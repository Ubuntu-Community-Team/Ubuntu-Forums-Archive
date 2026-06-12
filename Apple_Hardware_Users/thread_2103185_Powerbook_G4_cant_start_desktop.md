---
title: "Powerbook G4 cant start desktop"
date: 2013-01-09
forum: Apple Hardware Users
---

### Post by vinibali on 2013-01-09
Hi all!
Im a happy owner of an Powerbook G4 12"(1,33+nv fx5200), just almost...
I tried to fix the issues by the FAQ, the first was the snd-powermac.blacklist=yes thing, that was easy to fix at the yaboot.conf
but i cant get on the desktop, even if i have 8 bits of colordept if set the bootparameter: Linux nomodeset.
Also cant make the xorg.conf, with the Xorg -configure, it says: "Number of created screens does not match number of detected devices".
and the var/log/Xorg sad the same: "Number of..."(at nomodeset) and "no screens found" at normal boot.
I found an xorg.conf.new at the main user's home and tried to wget an other from [http://mac.linux.be/content/xorgconf-file-powerbook-g415-12-lucid-lynx]("http://mac.linux.be/content/xorgconf-file-powerbook-g415-12-lucid-lynx")
but nothing works...
whit G4 has an internal and capality for external digital monitor.
i think the default is the external, but cos there's not device connected, maybe thats why it cant start.
so pls help me :)
help me guys, thanks :)

---

### Post by abtabt on 2013-01-10
you can try this if that works Lubuntu CD is good for this old mac 

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

can you post 

dmesg

and 

/var/log/Xorg.O.log

---

