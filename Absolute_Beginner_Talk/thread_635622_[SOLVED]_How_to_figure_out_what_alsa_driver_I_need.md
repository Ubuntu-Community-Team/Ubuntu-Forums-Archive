---
title: "[SOLVED] How to figure out what alsa driver I need"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by jonward690 on 2007-12-08
Ok I am trying to recompile and install my alsa drivers,but I don't no which driver to choose for my sound card how would I go about finding this out?

---

### Post by nikoPSK on 2007-12-08
maybe you don't need a driver...? Try this:

```
asoundconf list

```

that'll give you all audio output sources on your pc. Then do this:

```
asoundconf set-default-card XXX
```

where xxx is you card. In my case it was "Audigy"

---

### Post by jonward690 on 2007-12-09
Yea well is there just a way to find the name of the driver I need I am compiling the sound card myself

---

### Post by nikoPSK on 2007-12-09
as I said possibly the driver is already there. Give me the output of asoundconf list please.

---

### Post by jonward690 on 2007-12-09
Well I arealdy fixed it,I didn't want to use the alsa drivers that came with my system cause they were messing up I needed complile the thing myself and the driver I needed was hda-intel.

---

### Post by nikoPSK on 2007-12-09
okay, glad you resolved your issue.

---

