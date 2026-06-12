---
title: "Splash screen changed without asking me if it was allowed"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Mimsy on 2006-09-24
I just booted up my laptop to play around some more with the desktop themes in Ubuntu, and to my great surprise I was greeted by the blue Xubuntu log in screen.

The initial boot sequence was all brown Ubuntu, while it listed all the proceses that were starting up, but the login screen was Xubuntu. I clicked on "session" to select GNOMe, since I want that desktop, and was asked if I wanted to make that my new default. I said "yes" and logged in.

Here's the kicker though: I uninstalled the Xubuntu desktop packages about a week ago. Why is the login screen suddenly back?

As soon as I have posted this I'm going to reboot and see if it's still there. This fascinates me.

After reboot: Yep, still there. Still Xubuntu blue.

/Mimsy

---

### Post by orb9220 on 2006-09-24
To change logon go to system>prefs or admin and select logon manger change back to ubuntu.

For boot splash run this in a term.

sudo update-alternatives --config usplash-artwork.so

and select which one you want.

---

### Post by Mimsy on 2006-09-25
Back to the Ubuntu screen again. Thank you! :)

/Mimsy

---

