---
title: "Losing the Gnome Saved Session"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2007-10-23
This is a simple question that's probably easy enough to answer that I'll never figure it out myself.

I made the mistake of saving my gnome session in System > Preferences > Sessions

It's not overriding all of my startup preferences, even after a logout / reboot.

How can I get rid of this saved session?

---

### Post by pteri498 on 2007-10-23
*bump*

Any ideas? I really need to change my startup, but I can't lose this saved session.

---

### Post by pteri498 on 2007-10-23
*sigh* hours of searching and guess-and-checking and still nothing.

This is making me want to return to the ease of XP's msconfig and Startup folder.

---

### Post by pteri498 on 2007-10-24
Ok, I think I've got it.

Startup files in ~/.config/autostart/ and the configuration file for ~/.gnome2/session

I renamed the session file to session.bak and now I can start anew.

---

