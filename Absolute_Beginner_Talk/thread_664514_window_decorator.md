---
title: "window decorator"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by skymera on 2008-01-11
when i start up emerald is my windows decorator.
i want it to be GTK.

i change it with ALT+F2 sand save the session but when i restart Emerald takes over.

how do i make it permanent?

im using Compiz

---

### Post by forestpixie on 2008-01-11
you could add it to compiz config I assume - start the settings manager

go to the window decoration in effects adn put it in the command line - I have emerald in there so I guess you could put it there

I thought the standard decorator was metacity

---

### Post by geirha on 2008-01-11
compiz starts emerald by default if it finds it, and falls back to gtk-window-decorator or kde-window-decorator if it doesn't find it. So, you can either uninstall emerald, or edit /usr/bin/compiz (as root/with sudo) and change ```
USE_EMERALD="yes"
```
to ... yes, you guessed it! ```
USE_EMERALD="no"
``` :)

---

### Post by Keith Hedger on 2008-01-11
try:
```

gedit .config/compiz/compiz-manager

```
and adding the line USE_EMERALD="no"

---

