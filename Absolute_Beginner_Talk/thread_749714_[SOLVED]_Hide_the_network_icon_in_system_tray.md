---
title: "[SOLVED] Hide the network icon in system tray?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-04-08
:KS

Thanks,
Tom

---

### Post by philinux on 2008-04-08
You'll have to explain that one. :)

---

### Post by Tom--d on 2008-04-08
Ok,

nm-applet shows an network Icon in the system tray. I do not want it there as I can access my network connection through System > Admin >Network

I would like it to not to show in my system tray, Is this possible?

---

### Post by sdennie on 2008-04-08
You could try disabling Network Manager via System->Preferences->Sessions.  That should prevent the applet from loading but, I don't know if you will have any other adverse effects.

---

### Post by Tom--d on 2008-04-08
> **vor said:**
> You could try disabling Network Manager via System->Preferences->Sessions.  That should prevent the applet from loading but, I don't know if you will have any other adverse effects.

but I need it to run so I can connect to the tinternet :)

---

### Post by DavidONE on 2008-06-14
I've been trying to find a solution for this as well - along with any other systray icon.  So far, no luck.

---

### Post by ad_267 on 2008-06-14
I've noticed if you do a "killall gnome-panel" or remove the system tray and add it again, the icon disappears, so it definitely isn't needed. But it always comes back when you log in. Sorry I can't be of more help.

---

### Post by DavidONE on 2008-06-14
If anyone wants it, vote it up at [http://brainstorm.ubuntu.com/idea/4060/](http://brainstorm.ubuntu.com/idea/4060/)

---

### Post by Tom--d on 2008-06-14
Its an easy one to solve. 

Just do not run nm-applet.

---

### Post by DavidONE on 2008-06-14
I want to hide it, not remove it (as per Windows).  Also:

> **DavidONE said:**
> ... along with any other systray icon.
:)

---

### Post by jhenager on 2008-06-14
> **DavidONE said:**
> I want to hide it, not remove it (as per Windows).  Also:


:)

Right click, and Remove from panel. Same as hiding it.

---

### Post by dje on 2008-06-14
If you don't want it to run every time you login go to System >> Preferences >> Sessions and untick 'Network Manager'

hope that helps,
dje

EDIT: oops this solution is already posted above, sorry

---

### Post by DavidONE on 2008-06-14
> **jhenager said:**
> Right click, and Remove from panel. Same as hiding it.

No, that is not an option in Ubuntu.

---

### Post by Tom--d on 2008-06-15
If you dont want it to be there, do not let nm-applet start up.

System > Pref > Sessions > Untick Network manager

---

### Post by DavidONE on 2008-06-15
Tom,

Thanks for the reply, but read the previous comments - that answer has already been given twice.  Removing it is not the same as hiding it and it doesn't address the second part of my question:

> **DavidONE said:**
> [SIZE="4"]I want to hide it, not remove it (as per Windows). ... along with any other systray icon.[/SIZE]

---

### Post by Tom--d on 2008-06-15
> **DavidONE said:**
> Tom,

Thanks for the reply, but read the previous comments - that answer has already been given twice.  Removing it is not the same as hiding it and it doesn't address the second part of my question:

There is no way of hiding it. 

All it does is manage your Network. 

You can just do it through,

System > Admin > Network

Easy :)

---

