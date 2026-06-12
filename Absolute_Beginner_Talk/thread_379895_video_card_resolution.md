---
title: "video card resolution"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by nichanson on 2007-03-09
Hi
My Ubuntu is basically home worthy now but I have one more thing to find out. At the moment my max resolution is   1024x768, with 60 refresh as the only option. I know my card can handle a faster refresh and bigger resolution but don:t know where to start to make this possible in linux.
thx

---

### Post by halitech on 2007-03-09
open a terminal and run 

```

sudo dpkg-reconfigure xserver-xorg

```

and select the higher resolutions. if still not available, you may need to install the correct closed drivers for your card

---

### Post by nichanson on 2007-03-09
My Graphics card is as follows:
Leadtek WinFast A180 DDR TH :: GeForce4 MX 440 AGP8X
([http://www.bjorn3d.com/read.php?cID=67](http://www.bjorn3d.com/read.php?cID=67))
but I can't find it in the config
sry for the trouble
Nick

---

### Post by halitech on 2007-03-09
have you tried running the reconfig yet? it may be all you need

---

### Post by nichanson on 2007-03-09
Sry
It may sound silly but can I chose or try any of those names (or cards) in the drop down list as they haven't got NVidia or GeForce in the list. I tried one of them (nv), gave it a name and closed it, but the resolution setting was still the same.

---

