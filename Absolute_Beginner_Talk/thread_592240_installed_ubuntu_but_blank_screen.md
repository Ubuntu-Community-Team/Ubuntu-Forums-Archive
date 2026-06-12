---
title: "installed ubuntu but blank screen?"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-26
Ok for some reason when i try and load ubuntu after installation it will load grub and all the text portions of the loading stage but then all i get is a blank screen? i cant understand why this is as just recently i had the ubuntu beta release running with no problems at all and the live cd works fine so i tried booting into recovery mode and then i get text mode? so does this mean that ubuntu doesn't have the drivers for my ATI Mobility Radeon 9600?.

Any help would be appreciated,
thanx

---

### Post by Qwerty_ on 2007-10-26
When in recovery mode try and install the restricted drivers for your graphics card.

System>Administration>Restricted Drivers Manager.

---

### Post by kamitsukai on 2007-10-26
Ok ill post back if i cant (lol got to reboot as im using the live cd )

---

### Post by kamitsukai on 2007-10-26
i cant do that because i dontget to a graphical interface all i get is to text based command line thing lol

---

### Post by Qwerty_ on 2007-10-26
Hmm just to get it up an running try and configure some settings with this command.

```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by kamitsukai on 2007-10-26
no it came up with this screen and stuff and asked loads of questions and i selected my graphics card but it still doesent work :(|

---

