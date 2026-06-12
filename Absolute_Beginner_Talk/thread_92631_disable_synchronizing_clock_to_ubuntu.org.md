---
title: "disable synchronizing clock to ubuntu.org"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by wakatobi on 2005-11-20
Can I disable syncrhronizing clock to ntp.ubuntulinus.org.

thank's for your helphttp://ubuntuforums.org/images/smilies/confused.gif

---

### Post by PokerFacePenguin on 2005-11-20
[QUOTE=wakatobi]Can I disable syncrhronizing clock to ntp.ubuntulinus.org.

thank's for your helphttp://ubuntuforums.org/images/smilies/confused.gif[/QUOTE]

better to change the server it connects to if you are worried about the failing

---

### Post by bunced on 2005-11-20
Open a terminal (Applications -> Accessories -> Terminal )

Type the following:

cd /etc/init.d
sudo nano  ntpdate

[COLOR="DarkOrange"]right after the line[/COLOR] #! /bin/sh

[COLOR="DarkOrange"]add a line[/COLOR]
exit 0
# exit zero not o

That should fix it! Let me know if you have more problems :)

Blessings,
David

---

### Post by wakatobi on 2005-11-20
thank's for help

best regards,

wakatobi (small Island at south-east celebes)

---

