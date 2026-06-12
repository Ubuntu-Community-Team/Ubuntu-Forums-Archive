---
title: "Incredibly insensitive touch pad on G4 PB"
date: 2006-06-15
forum: Apple PPC Users
---

### Post by rshd301 on 2006-06-15
I have Dapper running fine on my G4 Powerbook (including the wireless network) with very few issues. One which bugs me is the lack of response from the touch pad for mouse work. It is seriously slow and unresponsive. Can anyone advise of a config option for this to speed things up a bit.

Many thanks

---

### Post by BoneKracker on 2006-06-20
Look into Xorg configuration and modules that have to do with that device.

I would start by going to the command line and typing "man xorg.conf", and visiting the Xorg website.
You might also do a general internet search for "xorg touchpad" and so on.

---

### Post by goessmann on 2006-06-20
i got mine to work decently with these descriptions:

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

cheers
florian

[QUOTE=rshd301]I have Dapper running fine on my G4 Powerbook (including the wireless network) with very few issues. One which bugs me is the lack of response from the touch pad for mouse work. It is seriously slow and unresponsive. Can anyone advise of a config option for this to speed things up a bit.

Many thanks[/QUOTE]

---

### Post by goessmann on 2006-06-20
i got mine to work decently with these descriptions:

[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

cheers
florian

[QUOTE=rshd301]I have Dapper running fine on my G4 Powerbook (including the wireless network) with very few issues. One which bugs me is the lack of response from the touch pad for mouse work. It is seriously slow and unresponsive. Can anyone advise of a config option for this to speed things up a bit.

Many thanks[/QUOTE]

---

