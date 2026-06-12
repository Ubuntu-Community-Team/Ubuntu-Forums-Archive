---
title: "SlicknesS-black"
date: 2012-04-14
forum: Art &amp; Design
---

### Post by smd0665 on 2012-04-14
Hi. I'm using SlicknesS-black, which I love. A while ago, I had to re-install Ubuntu (and SlicknesS-black), but now the theme doesn't apply to everything. Refer to my picture of VLC. It's no longer dark. I did sudo chmod -R 755 /usr/share/themes/SlicknesS-black. Did I miss something? Thank you.

---

### Post by mcduck on 2012-04-16
As far as I know the theme shouldn't even apply to VLC, as VLC is a QT4 application, while SlicknesS is a GTK2 theme...

---

### Post by earlycj5 on 2012-04-18
> **mcduck said:**
> As far as I know the theme shouldn't even apply to VLC, as VLC is a QT4 application, while SlicknesS is a GTK2 theme...

Yes, it can.

QT4 Settings > Appearance > Select GUI Style: GTK+

---

### Post by emma157 on 2012-04-19
it looks great. i dont think there should be a problem.

---

### Post by al111 on 2012-04-19
It does look good-

---

### Post by smd0665 on 2012-11-22
Thanks to Julius Machinebacon
[https://plus.google.com/106299844117311287434/posts]("https://plus.google.com/106299844117311287434/posts")

slumslayer and kaira
[https://bbs.archlinux.org/viewtopic.php?id=99175]("https://bbs.archlinux.org/viewtopic.php?id=99175")

for solving this issue for me. Installing qt4-qtconfig and choosing the gtk-theme in .xinitrc (I don't use a dm) worked :)

---

