---
title: "DVD playback error"
date: 2006-06-15
forum: Absolute Beginner Talk
---

### Post by hyimted on 2006-06-15
hi all -

i'm trying to run my totem movie player, but when i pop in a dvd, i get the following error:

[B]Totem could not play 'dvd://'.

Error invoking "dvdnav_get_next_block": Error reading NAV packet..[/B]

afaik, i have the libdvdread package already installed.  any ideas?

thanks,

ted

---

### Post by rai4shu2 on 2006-06-15
Sounds like you still need libdvdcss2. See this for more details:

[https://wiki.ubuntu.com/RestrictedFormats#head-38863fbbf26f3d29d557d0f754e7d83ce3220cda](https://wiki.ubuntu.com/RestrictedFormats#head-38863fbbf26f3d29d557d0f754e7d83ce3220cda)

---

### Post by hyimted on 2006-06-15
thanks ... i installed the file, but no luck.  i'm not getting the error anymore, but the dvd just spins.  i also installed the regionset thing just to be sure ... that seems fine.

any other ideas?

totem shows "play CORPSE_BRIDE" as an option, i can see the dvd on my desktop, etc.  it's like ubuntu recognizes it as a valid dvd, it just won't play.  oh yeah, are there other "preferred" dvd playback applications or linux or does everyone just use totem?

---

### Post by rai4shu2 on 2006-06-15
Did you install "totem-xine"? (The default Totem won't work with DVDs.)

---

### Post by hyimted on 2006-06-15
[QUOTE=rai4shu2]Did you install "totem-xine"? (The default Totem won't work with DVDs.)[/QUOTE]that works rai ... thanks!  i had no idea what totem-xine even was.  :-$ 

the picture quality is pretty good, but it's a little jerky.  i'll work on that part later.  thanks again!

---

