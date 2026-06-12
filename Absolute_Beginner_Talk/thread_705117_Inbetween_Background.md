---
title: "Inbetween Background"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by gyf on 2008-02-23
Hi this isnt really an important question but  when i log in to my ubuntu desktop for about 6 seconds between the login screen and when my desktop loads my screen is filled with a cream colour. I was just wondering is there anyway to change this colour.

Thanks!

---

### Post by wolfen69 on 2008-02-23
i have my desktop and theme set for dark. 6 seconds of brown is ok. no biggie.

---

### Post by gyf on 2008-02-23
yeah im not really worried about it just wondering if there was anything i could do to change it

---

### Post by yabbadabbadont on 2008-02-23
Yep.











Oh, you want to know *how* to change it, not just confirmation that it can be changed...  :D

System->Administration->Login ...  (not sure of the exact name)

The background color can be changed there.

---

### Post by ShodanjoDM on 2008-02-23
Seems like gutsy gdm "bug".

Try this:

```
sudo cp /etc/gdm/PreSession/Default /etc/gdm/PreSession/Default.bak
```

To make a backup of the gdm configuration, then:

```
sudo gedit /etc/gdm/PreSession/Default
```

Find these lines near the end of the file:

```
# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#dab082"
```

Then change the BACKCOLOR="#dab082" to  BACKCOLOR="#000000". This will change the login background color to black.
Someone suggested to change the "#000000" to "x" but I haven't tried it myself.

Anyway, the line should be like this now:

```
# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#000000"
```

Save it, log out and re-login again.

---

### Post by gyf on 2008-02-23
cheers thanks for that ShodanjoDM

---

