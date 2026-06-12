---
title: "edgy and flash"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by murmsk on 2006-10-23
I am having trouble installing macromedia's flash addon for foxfire onto edgy.

I installs fine but whenever there is a flash call from a webpage foxfire shuts down.

any ideas?

thanks  steve

---

### Post by Greguti on 2006-10-23
Open your xorg.conf file in root mode:

```

sudo gedit /etc/X11/xorg.conf

```

Find the line *DefaultDepth	16* in the "screen" section. Change it to *DefaultDepth	24*. Save your file. Restart X (Ctrl+Alt+Backspace).

Worked for me, on 2 differents computers.

---

### Post by Aberrix on 2006-10-23
good info to know ;)

thanks.

---

