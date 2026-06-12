---
title: "Problems with numlockx"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2007-06-25
I recently installed Ubuntu on a laptop, and I'm used to having a keypad that doesn't have num lock on by default, so I automatically installed numlockx per the instructions on ubuntuguide.org. But then I realized that that was a mistake, since...I don't have a num pad, so it's right in the middle of my keyboard. So I deleted the changes I made to /etc/X11/gdm/Init/Default, and sudo apt-get remove numlockx, and then used Synaptic to fully remove it. But still I get num lock when I start GNOME! How can I stop this?

---

### Post by chimerical_brio on 2007-06-26
...bump...

---

### Post by chimerical_brio on 2007-06-26
Sorry to be obnoxious but...help!

---

### Post by Seisen on 2007-06-26
I don't know if this will work but we can give it a try.

```
 gksuodo gedit /etc/X11/gdm/Init/Default
``` and remove these lines and save the file

```
if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
```

---

