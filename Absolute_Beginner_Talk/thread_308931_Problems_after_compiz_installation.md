---
title: "Problems after compiz installation"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by Arkitekt on 2006-11-28
Ok so earlier i installed compiz, after i had installed and restarted i didnt like it as much as i thought, so i copied back the backups i had made, and removed the compiz packages.

however, now after everything is gone and the regular GDM loads, every window i open seems to be missing its border. liek in firefox the top bar is gone (the one that allows you to click and move, and also holds the minimize/maximize and exit buttons) 

how can i get this back?? as well it looks like the one panel that shows the open windows, doesnt list any of the windows i have open. doesnt show firefox or terminal or anything.

also the desktop switching on the panels is gone, i dont see any desktop boxes i can switch to like before. I had two before, how can i get that back? 

as well. when i load up, i always have my panels at the top, i like to have the one with the menus at the very top (applications, places, system) and have the other panel (the one with show desktop button and trash, and lists open windows, below it. now when i restart my machine the always change places. how can i make what i like permanent?

thanx in advance for any help, i would love to get this problem solved, if not i guess ill just reinstall.

---

### Post by redDEADresolve on 2006-11-29
did you edit your /etc/gdm/gdm.conf or /etc/gdm/gdm.conf-custom settings?

go through the guide/howto you used and undo all the changes you made.

---

### Post by Arkitekt on 2006-11-29
i already have :( is there anything i can edit to get these things back?

---

### Post by 454redhawk on 2007-01-02
I also have this problem. It did not happen untill today. I have reboot several times since installing compiz 2 days ago and everything appeared ok. But now I am missing borders and any window I open covers the top main panel. I have to use file quit to exit an app.

---

### Post by 454redhawk on 2007-01-03
Bump

---

### Post by 454redhawk on 2007-01-05
?

---

### Post by Famicommie on 2007-01-05
> **454redhawk said:**
> I also have this problem. It did not happen untill today. I have reboot several times since installing compiz 2 days ago and everything appeared ok. But now I am missing borders and any window I open covers the top main panel. I have to use file quit to exit an app.

Do you mean that you have no borders while using Compiz, or that after you uninstalled Compiz you lost your borders?

---

### Post by 454redhawk on 2007-01-05
> **Famicommie said:**
> Do you mean that you have no borders while using Compiz, or that after you uninstalled Compiz you lost your borders?

Actually, I have bordes while using the XGL session login. I no longer have borders when using the standard Gnome session.

---

### Post by Bigbluecat on 2007-01-05
I have something similar although I'm using Beryl and after working well for a while it eventually will not log in (just get a plain brown screen).

With a plain Gnome session I lost the window borders. Have not found a permanent solution to this yet but there is a temporary fix.

In you gnome session (the one with no borders) open a terminal and run the the following:

> metacity --replace

Hopefully your window manager will come back.

---

### Post by M_the_C on 2007-01-05
> **454redhawk said:**
> Actually, I have bordes while using the XGL session login. I no longer have borders when using the standard Gnome session.
You have to choose a theme using System>Preferences>Emerald Theme Manager.

---

### Post by 454redhawk on 2007-01-05
> **Bigbluecat said:**
> I have something similar although I'm using Beryl and after working well for a while it eventually will not log in (just get a plain brown screen).

With a plain Gnome session I lost the window borders. Have not found a permanent solution to this yet but there is a temporary fix.

In you gnome session (the one with no borders) open a terminal and run the the following:



Hopefully your window manager will come back.

That seems to have done it. I have rebooted after using your suggestion and did not have to use that command again to login.
I will post if something reverts back.

Much thanks

---

