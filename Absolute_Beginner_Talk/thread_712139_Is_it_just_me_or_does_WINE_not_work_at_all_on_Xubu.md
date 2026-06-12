---
title: "Is it just me or does WINE not work at all on Xubuntu compared to Ubuntu."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-01
Okay so on my laptop I have Ubuntu. I can run utorrent and Visual Boy Advanced no problem on it. However, my charger just went bad so I can't exactly check it for reference. I remember just right clicking on a .exe file and choosing to have it open with WINE. On Xubuntu I don't have the option of opening anything with WINE. WINE like isn't even an application for some reason. I can access the configuration utility, but that is it. What is going on here? How can I set .exe's to open with WINE on Xubuntu using the terminal?

---

### Post by Ptero-4 on 2008-03-01
Open a text file in your text editor and type this:
```

#!/bin/sh
wine <path/to/your/.exe>

```
Where you replace the text in the square parentesis with the path to the .exe you want to open.

---

