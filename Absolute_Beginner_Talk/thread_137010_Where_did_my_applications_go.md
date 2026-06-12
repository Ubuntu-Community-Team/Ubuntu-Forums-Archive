---
title: "Where did my applications go?"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by hovmod on 2006-02-27
More newbie-stuff here: 

I used the Synaptic Package Manager to download and apparently install some programs (some Java stuff, for instance ), and when it was done downloading and installing I was told everything was OK and closed the dialog.

But now, where are the apps? Not under 'applications', that's for sure. Also not in 'add applications' - I think I'll have to edit and add something to some desktop or conf file somewhere (like the guide for installing GNU-CASH), but don't even know what I'm looking for. 

What actually happens with the programs when I am told they're installed and I can't find them? Where do they go?

---

### Post by Madpilot on 2006-02-27
Not everything automatically adds itself to the menus.

If you use the "Add Applications" tool to add stuff, everything there will be in your menus, and Add Apps even tells you where in the menus. Synaptic is bigger and not as organized.

Press Alt+F2 and type the name of your package, that usually launches it.

You can edit the menus by right-clicking on the title of the menu & selecting "Edit Menus". Pick the category you want your app to appear in, and hit the "New Entry" button.

Add the package name (usually) to the Command box in the New Entry window, and whatever you want in the other boxes.

---

### Post by newuser111 on 2006-02-27
or install the 'debian menu' which shows all apps

sudo apt-get install menu

---

### Post by hovmod on 2006-02-27
Thanks. 

What a delightfully friendly forum!
I was expecting everyone to tell me to rtfm... :hihi:

---

### Post by Jucato on 2006-02-27
Unfortunately, there are so many "manuals" out there (almost one for each distribution, plus a myriad for linux itself), that "rtfm" is almost useless... :D

(That, and it's actually against forum rules to say rtfm to someone. :D )

---

### Post by LordBug on 2006-02-27
In Ubuntu, close GAIM (it has issues with this I've read), and issue a "killall gnome-panel" from a terminal (this may require sudo, I can't remember).  It'll stop and start the gnome-panel, and it should find any new apps.

---

