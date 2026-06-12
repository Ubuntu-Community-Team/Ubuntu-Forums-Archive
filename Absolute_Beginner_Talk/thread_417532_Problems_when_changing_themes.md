---
title: "Problems when changing themes"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2007-04-21
Okay, here's a low-level question for you.

I installed a Theme from gnome-look.org, can then changed to another one. But some of the old theme is still there. Any idea how to kick it to the curb? For instance, white lines round the Address bar and google/select-your-search thing in Firefox...

---

### Post by riven0 on 2007-04-21
Did you make sure that you changed everything in the Theme Details section? Like the windows borders, icons, etc.?

---

### Post by st33med on 2007-04-21
You might want to change the Firefox theme.  Ff doesn't depend on the system's theme.

Go [here]("https://addons.mozilla.org/en-US/firefox/browse/type:2") fo r the Themes. Unfortunately I'm not  entirely sure if it has the theme for you. Try getting a look-alike!

---

### Post by Taigrr on 2007-04-21
Ah, okay. Changing the firefox theme fixed that. I figured that the system would just override it.
Thank you much!

(Also, I don't know what happened with the title. "Hahaha!" was supposed to go into an IM window. Appologies, I do try and keep titles to the point.)

---

### Post by ComplexNumber on 2007-04-21
**Taigrr**
another thing to take not of when changing themes. sometimes the background of 1 or 2 of the applets on the panel can remain. for example, if you are changing from a dark to a light theme, 1 or 2 of the applets will still have a dark background (see screenshot). the way to refresh the panel is to open up a terminal and type in the following:
[B]killall gnome-panel

[/B]
also, some of the applets don't always refresh when changing icon themes, so the above command will rectify that.

---

### Post by Taigrr on 2007-04-21
Ahh, that helps a bunch! Thank you much, good sir!

Ubuntuforums always leave me feeling in-debt when people help, hehe...

---

