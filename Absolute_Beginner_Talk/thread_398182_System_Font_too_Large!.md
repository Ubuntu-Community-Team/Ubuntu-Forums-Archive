---
title: "System Font too Large!"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by gastro54 on 2007-03-31
I recently installed XGL-Beryl and am having trouble with my system fonts - they are too large. How can i reduct their size?

attached is a screenshot.
[IMG]http://img384.imageshack.us/img384/848/screenshot1oc6.png[/IMG]

---

### Post by benerivo on 2007-03-31
Have you tried changing the font sizes in System>Preferences>Fonts (at least i think that's the route to modify them - i'm on kde and not gnome).

---

### Post by jordanmthomas on 2007-03-31
Try running gnome-settings-daemon and see if your themes come back (including your fonts)

---

### Post by gastro54 on 2007-03-31
> **jordanmthomas said:**
> Try running gnome-settings-daemon and see if your themes come back (including your fonts)
OK, when I enter this command in terminal, everything changes back to normal like how I want it.  However, once I exit out of the terminal, the large font returns.  This looks promising, though - thanks.

---

### Post by gastro54 on 2007-03-31
OK I added gnome-settings-daemon to "Startup Program" under "Sessions" and everything looks good now.  Is this the best way to make the change?

---

### Post by jordanmthomas on 2007-03-31
I'm not sure exactly how you have everything set up, so I don't know what *would* technically be the best, but what you've done shouldn't pose any problems.

---

### Post by gastro54 on 2007-03-31
OK, I just looked at the System Monitor and it lists 2 gnome-settings-daemon as running. Can I end the first one before starting the 2nd one in "Startup Programs"?

---

### Post by jordanmthomas on 2007-03-31
The only harm that will come from ending gnome-settings-daemon is your themes and fonts will look bad untili you start another one.

gnome-settings-daemon should run all by itself, so I'm not sure why it's not in your case.  You only need one to be running, so feel free to kill the first one.

```
killall gnome-settings-daemon && gnome-settings-daemon
```

---

