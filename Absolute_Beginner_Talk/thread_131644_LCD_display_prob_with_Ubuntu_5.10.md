---
title: "LCD display prob with Ubuntu 5.10"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by nubuntux on 2006-02-16
anyone please lend me some help, i have a dual-boot HP omnibook 500 notebook pc running WinXP and Ubuntu5.10. There's nothing wrong with installation and running apps in ubuntu, but ive have a problem with my display. the resolution is perfect, 1024x786 65Hz. it seems my vertical position of the display is missing a half of the menubar on the top, and exceeding a half on the bottom.

How do i adjust that display?

Thanks in advance!

---

### Post by frodon on 2006-02-17
You will find all the needed informations here : [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by nubuntux on 2006-02-17
ok ill try... Thanks!

---

### Post by nubuntux on 2006-02-17
ive run the xvidtune, but the button "Up" Down" doesn't response. how do i test that? any options?

---

### Post by keltong on 2006-08-12
I have the same notebook and tried xvidtune. When you click on the "shorter" to around 803 or 804, it will fit the screen perfectly. However, when I do a "show" and put the info as Modeline under the Monitor section of the xorg.conf file, it does no effect when I restart the system. Do I need to do anything else? When I 'Apply' under xvidtune it works perfectly. How do I make it permanent? Why does adding Modeline statement does not work? I'm running Dapper with Omnibook 500. Thanks.

---

