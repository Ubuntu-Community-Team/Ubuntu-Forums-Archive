---
title: "Is this how Gaim is supposed to work?"
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by hotstovejer on 2006-06-14
So I opened up Gaim today, after my power went out and I restarted my machine, and all of a sudden, I couldn't use the letter t! Here is why!

When I would type t, and not T, it would pop up with an option for a new instant message. Then I clicked on the conversation tab in the window, and it literally would say "New instant message      T"

Am I just not seeing something where I can change that? That shouldn't be that way.

Thanks for the help!

Jeremy

---

### Post by atomicSpatule on 2006-06-14
Go to the keyboard options [System -> Preferences -> Keyboard], second tab, and click add, then select your country and everything. It should now work

---

### Post by hotstovejer on 2006-06-15
That didn't work. Didn't change the option in Gaim.

WTF could be causing that?

---

### Post by vruum on 2006-06-15
I have no idea how it happened, but if you don't have any settings that you can't recreate, try going to the folder .gaim in your home folder (the .gaim folder is hidden, so you need to tick the show hidden files box in the view menu in nautilus.) and delete the file prefs.xml see if that changes anything

---

### Post by hotstovejer on 2006-06-15
Aha! It was in the accels.xml! Found it, and put a control in there! Thanks guys!

Jeremy

---

