---
title: "Superkaramba and beryl on startup"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by cawill on 2007-05-30
I have beryl and superkaramba installed on kubuntu and I added beryl-manager and superkaramba to ~/.kde/Autostart.
When the system loads up beryl sometimes uses the metacity window manager by default which can be easily changed later through beryl manager and as superkaramba opens before beryl, when beryl opens you cannot see the superkaramba themes.

How do I make beryl always use the beryl window manager and load up before superkaramba and have superkaramba themes only open not the theme manager load up as well?

Thanks, Chris

---

### Post by cferthorney on 2007-05-30
> **cawill said:**
> I have beryl and superkaramba installed on kubuntu and I added beryl-manager and superkaramba to ~/.kde/Autostart.
When the system loads up beryl sometimes uses the metacity window manager by default which can be easily changed later through beryl manager and as superkaramba opens before beryl, when beryl opens you cannot see the superkaramba themes.

How do I make beryl always use the beryl window manager and load up before superkaramba and have superkaramba themes only open not the theme manager load up as well?

Thanks, Chris

This happened a lot to me when I used FC6.  There should be an option in Beryl manager saying "If crashes fall back to X window engine" (Or words to that effect)  Change this option to KWin for KDEs option.  I found Beryl to be more stable after doing this for some reason...  It will load Emerald by default (Unless you choose KDEs Aquamarine) Beryl Manager -> CHoose window manager -> Emerald.

If you want Beryl to load before superkaramba, I personally would write a script as follows: (Use something like kedit, or kate to write the script)
```

#!/bin/bash
beryl-manager  &&  super-karamaba

```

Double check if Super Karamba is super-karamba or not - I am not on my home desktop here at work.  The && will load Superkaramba if beryl successfully loads.

Call the script what you like and put it in KDEs AutoStart directory with executable permissions (Right click in Konquorer and then select appropriate permissions)

I hope this helps.

---

### Post by cawill on 2007-06-03
k, sorry for the late reply.
Got it all sorted now, thanks for your help.

---

### Post by tenSe on 2007-08-06
I have exactly the same issue..
How did you get this to work ?

---

