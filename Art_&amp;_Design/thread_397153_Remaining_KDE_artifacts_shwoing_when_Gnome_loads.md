---
title: "Remaining KDE artifacts shwoing when Gnome loads"
date: 2007-03-30
forum: Art &amp; Design
---

### Post by kwaanens on 2007-03-30
I recently played around, installing som KDE junk. Of course this left me with some blue artwork...
I have uninstalled all I could find, but I still have a blue screen after typing my user name and pw. What package do I need to reinstall to get back the default Ubuntu one?

- Ketil

<rant>there really should be a way to run both KDE and Gnome on a system without getting artifacts from the last installed in both.</rant>

---

### Post by montgoej on 2007-03-31
Hmm...that's weird cause I've installed/uninstalled KDE multiple times on my system and I've never had that happen.  Were you able to use both KDE and Gnome when you had KDE installed?  Do any messages pop up, any errors, etc.?  If you just install the KDE-Core package, you shouldn't have any artifacts from the other desktop showing up and you should be able to use Gnome and KDE by selecting "session type" at the login window.  If you can do that, try changing the session type to Gnome.
~Jordan Montgomery

---

### Post by kwaanens on 2007-03-31
No errors, nothing like that.
The artifacts being: KDE cursor, blue stuff here and there, and always that damned kubuntu-usplash.

I have no problems logging in to Gnome. The blue background I get is shown instantly after pw is entered, so it has nothing to do with my choice of session. (Default has always been Gnome anyway)

- Ketil

---

### Post by hikaricore on 2007-03-31
You could force reinstall the ubuntu-usplash and ubuntu-artwork and all the chite.  :)

---

### Post by kwaanens on 2007-03-31
I figured it out. Actually xubuntu-default-settings was the problem. Uninstalled that and reinstalled a couple of ubuntu-artwork related stuff, and I'm good.

Thanks though!

- Ketil

---

