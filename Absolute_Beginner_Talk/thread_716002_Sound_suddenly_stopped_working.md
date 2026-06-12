---
title: "Sound suddenly stopped working"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by modernsapien on 2008-03-05
I turned my computer on and my sound doesn't work. I restarted a couple times with no effect. When  I double click on the volume control it says there is no Gstreamer plugins installed. Checked Package manager and they are installed. Tried reinstalling them with no effect as well. No special sound card just on board. Could anyone help me out with how to fix this?

---

### Post by herbster on 2008-03-05
Paste output of:

```
cat /proc/asound/cards
```

and Right-click the volume control, hit properties and check all the volume levels and/or whether they are muted.

---

