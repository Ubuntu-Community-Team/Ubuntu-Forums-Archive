---
title: "Load spanish keymap in kubuntu 7.04?"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-08-29
Hi! I remember doing on a Linux computer on my university the command:

```
loadkeys es
```

 and the Spanish keymap was loaded, but kubuntu 7.04 seems that doesn't' recognize this command, which command should I use instead?

Thanks!

---

### Post by hyper_ch on 2007-08-29
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by fredscripts on 2007-08-29
Thanks for answering,

The command you put does the same that the command "loadkeys es" or is something to enable to use that command?

---

### Post by Mornedhel on 2007-08-29
I use 'setxkbmap us' to switch to a US layout, then 'setxkbmap fr' to switch back to the French AZERTY layout. (I run Ubuntu Feisty Fawn with GNOME.)

The above command (dkpg-reconfigure) would attempt to rewrite your X preferences so as to use Spanish all the time, which may or may not be what you want to do.

---

### Post by fredscripts on 2007-08-29
Oh what I was looking for was that setxkbmap command. Thanks! One curious question, why it's not available the "loadkeys" command?

---

### Post by Songwind on 2007-08-29
You can make it a permanent option from the Settings applet.  You can have multiple keyboard maps available and a Notification Area icon for changing between them.

---

