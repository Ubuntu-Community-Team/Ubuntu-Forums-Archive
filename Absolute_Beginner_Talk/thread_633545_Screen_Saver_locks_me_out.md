---
title: "Screen Saver locks me out"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by paskins on 2007-12-06
Hi! I am new to this whole Ubuntu "thing". I bought the computer from a guy at work, and I love it! For some reason, my screen saver locks me out sometimes, I do not want to type in my password every time. The lock is turned off, and I have the power management setting on "never". When the guy at work looks at it, the screen saver does not lock (of course!) but it locks for me! What is going on? He said it was a bug, not a virus and I should check with you guys. Any help you can give???:confused:

---

### Post by CatKiller on 2007-12-06
The screen locks some time after the screensaver kicks in. I think the default is 5 minutes. So you might need to leave it a while when showing your colleague.

You could try setting/clearing the "Lock screen when screensaver is active" checkbox in the **System -> Preferences -> Screensaver** dialogue to see if that helps. Otherwise, if you press **Alt-F2** and run **gconf-editor** you'll get a configuration tool. Navigate to **/apps/gnome-screensaver** and change the **lock_delay** key to some larger value so that you don't need to type your password in so often.

---

### Post by paskins on 2007-12-06
> **CatKiller said:**
> The screen locks some time after the screensaver kicks in. I think the default is 5 minutes. So you might need to leave it a while when showing your colleague.

You could try setting/clearing the "Lock screen when screensaver is active" checkbox in the **System -> Preferences -> Screensaver** dialogue to see if that helps. Otherwise, if you press **Alt-F2** and run **gconf-editor** you'll get a configuration tool. Navigate to **/apps/gnome-screensaver** and change the **lock_delay** key to some larger value so that you don't need to type your password in so often.

Thank you, the lock delay is set to 0, I set it to 100, what does that mean?

---

### Post by CatKiller on 2007-12-06
**Key Documentation**
> Short description: Time before locking

Long description:The number of minutes after screensaver activation before locking the screen.

---

