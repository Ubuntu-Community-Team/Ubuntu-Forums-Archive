---
title: "Katapult at startup"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by amk221 on 2007-02-24
I've put a link to Katapult in /.kde/Autostart and now it loads at startup, which is what I want, but I'd prefer it to load 'in the background'. I don't need to see the Getting Started Katapult notification each time I log in.

So is there anyway to make applications (not just katapult) start minimized or even on a specific desktop so that they don't get seen at startup?

thanks

---

### Post by neko18 on 2008-02-24
I have the same issue. I placed Katapult in System>Preferences>Sessions (on Gnome), but the "Katapult Notification" is really annoying. Does anyone know how to fix this short of modifying the source code?

**Edit**
Fixed!
First, close Katapult (press Alt-Space, then Ctrl-Q)

Open a terminal and enter
```
nano ~/.kde/share/config/katapultrc
```

Now change both the "HideSessionNotification" and "HideUserNotification" lines to 2, so that section of the file should look like this:
```
...
HideSessionNotification=2
HideUserNotification=2
...
```

Press Ctrl-O, press Enter, then press Ctrl-X. Close the terminal

Now you can reopen Katapult by pressing Alt-F2, typing "katapult" then pressing Enter

---

