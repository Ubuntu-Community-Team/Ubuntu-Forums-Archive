---
title: "Icon theme creation"
date: 2010-05-07
forum: Art &amp; Design
---

### Post by cipherboy_loc on 2010-05-07
How do you create an icon package? I have a bunch of icons that I created, but 

[LIST=1]
[*]Sadly, they do not cover every program/button. So I would need to find a way to use my icons for the applications that I have designed icons for and then default to the GNOME theme, if I don't have an icon for that application/button/menu icon.
[*]How do I package it? I would like to share it with my friends (that use Ubuntu/Linux), but for now it would take a lot of work to set them up with my icons. Something along the lines of manually changing all of their icons to what I have.
[/LIST]

Side question: Is there a way to create an icon (lets say for the WiFi applet) that senses its background and changes color? AKA if the user is using a dark panel, it would use a light version of the wifi applet monitor, and if the user is using a light panel, it would use a dark version of the wifi applet monitor?


Thanks in advanced

---

### Post by morgengenuss on 2010-05-07
ad1) usually this is done via inheriting other themes, in your index.theme put the line "Inherits=$name_of_the_icon_themes(comma_separated)_you_want_to_inherit"

side answer: this is a planned feature in gnome, see read [here]("http://jimmac.musichall.cz/log/?p=974").

---

### Post by koostudios on 2010-05-09
I can't answer the first question as I've never packaged my icon sets myself (I normally just change each icon one by one) but I know they're compressed into a tar.gz normally and placed into /share/icons folder but for the second question - i suggest releasing -dark and -light versions so that people can simply choose between them when they set their theme.

---

