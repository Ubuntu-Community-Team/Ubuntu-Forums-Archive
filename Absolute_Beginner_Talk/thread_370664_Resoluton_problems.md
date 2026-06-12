---
title: "Resoluton problems"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-02-26
hello, i'm having a huge problem with my resolution and i tried messing with the xorg file and taht did not work. wait it gave me option to change resolution but it was 800x600 so it was a downgrade. i have a intel graphics card. and i was wondering if anyone can help me.

---

### Post by Kateikyoushi on 2007-02-26
I would try to reconfigure it first. Copy the following to the terminal.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tcebak on 2007-02-26
alrighty i'd tried it and still i have no progress. i have selected 3 settings for my resolution in the xorgconfig. (should i only select one?)

---

### Post by Darklighter137 on 2007-02-26
Have you considered upgrading your graphics card drivers?   That gave me the correct screen resolution.

---

### Post by tcebak on 2007-02-26
well, i'm on a laptop. and i'm saving up for an IBM laptop.  i use my custon desktop for windows (backup)

---

### Post by tcebak on 2007-02-26
Holy crap i did it another time only selecting one resolution and it worked!!! THANKS!!!!

---

