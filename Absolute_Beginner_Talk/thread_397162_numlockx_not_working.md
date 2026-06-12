---
title: "numlockx not working"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by sandman42 on 2007-03-30
Hi,

I've installed numlockx, but it does not work, i.e.:

- When I have user/password prompt is off
- Then it goes on for a little while
- When nautilus is loaded and run, it goes off and stays in this state.

I've tried to add 

[FONT="Courier New"]if [ -x /usr/bin/X11/numlockx ]; then
  /usr/bin/X11/numlockx on
fi[/FONT]

in /etc/X11/gdm/Init/Default but no luck

What's wrong?

Thanks

---

### Post by zvacet on 2007-03-30
After adding the lines and saving file press **ctrl+alt+backspace**

---

### Post by sandman42 on 2007-03-30
> **zvacet said:**
> After adding the lines and saving file press **ctrl+alt+backspace**

That's what I did. 

I've tried also on a different installation, but the behaviour is still the same: at the login prompt numlock is on. After password, when the panel that says nautilus, desktop and so on are loading, numlock goes off.

Any hint?

---

### Post by Patrick K on 2007-03-30
I don't know how but numlock stays on when I bootup. It didn't at first. I don't recall what I did but it seems to me there was a graphic applet that had a check box. I can't find it now, it's been a few months. I checked the "Default" file you mentioned and the lines are not in mine so that isn't how I did it (no mention at all of numlock in my Default file).  

This is really something that should be as easy as pie to set.

---

### Post by Patrick K on 2007-03-30
I found something that might help. It's in the Configuration Editor (it is in Add/Remove, if it isn't already installed). Open it and do a search for numlock (edit>find). There are three entries, two of which are "remember_numlock_state". The other is "numlock_on". That should fix you up.

---

### Post by sandman42 on 2007-04-01
> **Patrick K said:**
> I found something that might help. It's in the Configuration Editor (it is in Add/Remove, if it isn't already installed).

Good but....in which menu is it?

I have looked in the Add/remove, and it is checked, so it should be installed, but I haven't found it in any menu.

Thanks once again

---

### Post by Patrick K on 2007-04-01
I'm using Edgy (Gnome). It is in Applications > System Tools. You may need to edit the menus (right click on the menu) to make it appear. 

Command line is "gconf-editor" 

If you're using the KDE desktop I have no idea if it will work.

---

### Post by sandman42 on 2007-04-01
No, I'm using edgy too.

Everything is now ok (both numlock and gconf-edit)

Thank you very much for your help!!!!!

Ciao
:) :)

---

