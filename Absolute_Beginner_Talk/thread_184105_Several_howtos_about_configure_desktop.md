---
title: "Several howtos about configure desktop"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by mellibra on 2006-05-29
1. How to hide disks like ha1, I choose to disable its accessibilities, but next time I start, it shows again.
2. How to show "My computer"?

---

### Post by Jagot on 2006-05-29
If you mean what I think you do, then this is how to do it:

Hit Alt+F2 and type gconf-editor.

Now within gconf-editor go to apps -> nautilus -> desktop.

Tick the 'computer_icon_visible' box to have essentially the My Computer icon, and  untick 'volumes_visible' to hide any volumes.

---

### Post by Googler on 2006-05-29
from **Applications** menu select **system tools>configuration editor**
from the configuration editor left pane select** apps>nautilus>desktop**
then from the right pane uncheck the **volume_visible** and check other things that you want it to appear on the desktop

---

### Post by mellibra on 2006-05-29
Thanks, it works.

---

