---
title: "No Sound"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2006-04-17
My machine has a C-Media audio chip and a Soundblaster Live PCI card.  Ubuntu has defaulted to using the C-Media chip and I need it to recognize the Creative Soundblaster card as the default audio device.  How can I change this?  Otherwise Ubuntu is working fine.  Thanks for any help you can give.

Don

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=mengd2002]My machine has a C-Media audio chip and a Soundblaster Live PCI card.  Ubuntu has defaulted to using the C-Media chip and I need it to recognize the Creative Soundblaster card as the default audio device.  How can I change this?  Otherwise Ubuntu is working fine.  Thanks for any help you can give.

Don[/QUOTE]
In termainl copy and paste the following:

> sudo alsamixer

Make sure _nothing_ is muted or turned down low.

---

### Post by mengd2002 on 2006-04-17
I found the answer System > Preferences > Sound.  Both sound cards were listed, I just had to change the default.

---

### Post by xXx 0wn3d xXx on 2006-04-17
[QUOTE=mengd2002]I found the answer System > Preferences > Sound.  Both sound cards were listed, I just had to change the default.[/QUOTE]
I'm glad that you could fix your problem :)

---

