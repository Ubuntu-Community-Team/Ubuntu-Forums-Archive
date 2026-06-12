---
title: "Quake 2 Key Board and mouse"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by Nolander on 2007-07-13
I installed quake 2 but when i run it i get
```

QuakeIIForge 0.3
using /home/nolander/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx

```

?????

How do i set it up with the key board and mouse? i think thts my problem

Ta,
Nolander

---

### Post by phr0ze on 2007-07-13
I would look for this file and see if there is a problem with it. pics/colormap.pcx
For keyboard and mouse settings (although I don't think this is the issue) I'd check the config.cfg it talks about. All of this should be in the quake2 path.

---

