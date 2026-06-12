---
title: "Trackpad scrolling"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Jussi01 on 2007-02-24
Hei all, 

2 Quick things, probably no brainers but anyway... I have a vertical scroll and a horizontal scroll printed on my laptop trackpad. However only the vertical one works. How do I turn on the horizontal one?

Second question, I just checked out the new Feisty cd (herd 4) and they have a nice new blue theme called "glossy". anyone know if you can get this theme for edgy? if so where?

Cheers


Jussi

---

### Post by annda on 2007-02-24
is it made by synaptics? if so, install gsynaptics or ksynaptics (for Kubuntu) and configure using that tool.

---

### Post by RichPicker on 2007-03-01
I installed it, but get this message, and don't know what to do next. Can you help?

---

### Post by Jussi01 on 2007-03-02
> **RichPicker said:**
> I installed it, but get this message, and don't know what to do next. Can you help?

you need to edit your xorg.conf and add this line to the part that says synaptics touch pad

```

Option "SHMConfig" "true"
```

---

