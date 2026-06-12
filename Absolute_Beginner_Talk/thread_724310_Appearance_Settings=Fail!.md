---
title: "Appearance Settings=Fail!"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Phin-Rott on 2008-03-14
Alright, I'm not sure what it was, but I installed something that was supposed to let me configure all aspects of my Gnome desktops appearance.
Well, now I cant find it, and nothing else works.  When I try to do something even as simple as changing the desktop background (by right-clicking the desktop and so on) a window pops up telling me
> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

Any ideas?

---

### Post by {BzF}~JOKesTER on 2008-03-14
Ok Try This:

Open A Terminal And Type:

apt-get remove gnome-settings-daemon

And Than:

apt-get update

apt-get install gnome-settings-daemon

:)

Tell Me How It Goes!!!!

If It Helps Please Hit "Thank" As Many Times As Possible!!!:):lolflag:

---

### Post by Phin-Rott on 2008-03-14
I got a little message telling me that gnome-settings-daemon couldnt be found...hmmm?

Thnks though!

---

