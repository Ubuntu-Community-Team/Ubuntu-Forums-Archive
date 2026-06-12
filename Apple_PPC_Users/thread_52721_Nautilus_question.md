---
title: "Nautilus question"
date: 2005-07-28
forum: Apple PPC Users
---

### Post by Ptero-4 on 2005-07-28
Hi. I wanted to know just one more thing. Is there any proyect to port the gnome 2.10 nautilus file manager (along with it's built-in cdburner, imageviewer and archiver) to work nativelly in OSX, or is any patch available to compile it and it's addons in OSX nativelly.

P.d: by native I mean. running straight under quartz without needing X11, being packaged as a OSX .app packaged application and using the OSX appearance manager (aqua controls drawn by the OS, not a custom gtk2 theme and menubar handled by OSX).

P.d2: I know that OSX have a file manager called the Finder. But it's (since OSX public beta) as slow, complex and crappy as the KDE file manager (which I don't quite like) and I wanted to replace it with the spatial nautilus 'cause nautilus is what the OSX Finder should have been in the first place.

---

### Post by codejunkie on 2005-07-29
[QUOTE=Ptero-4]Hi. I wanted to know just one more thing. Is there any proyect to port the gnome 2.10 nautilus file manager (along with it's built-in cdburner, imageviewer and archiver) to work nativelly in OSX, or is any patch available to compile it and it's addons in OSX nativelly.

P.d: by native I mean. running straight under quartz without needing X11, being packaged as a OSX .app packaged application and using the OSX appearance manager (aqua controls drawn by the OS, not a custom gtk2 theme and menubar handled by OSX).

P.d2: I know that OSX have a file manager called the Finder. But it's (since OSX public beta) as slow, complex and crappy as the KDE file manager (which I don't quite like) and I wanted to replace it with the spatial nautilus 'cause nautilus is what the OSX Finder should have been in the first place.[/QUOTE]

i don't exactly know if this is what your looking for, but fink is great if you have a mac i cant remember exactly but i believe that you have to use a special version of X11 from apple that interfaces gnome with aqua/quartz but it doesn't have the polish that the aqua GUI has if that's what your wanting, it's still basically gnome but on the plus side you can still have gnome KDE and tons of other open-source apps on your mac and aqua for the eye-candy.

---

### Post by Ptero-4 on 2005-07-29
[QUOTE=codejunkie]i don't exactly know if this is what your looking for, but fink is great if you have a mac i cant remember exactly but i believe that you have to use a special version of X11 from apple that interfaces gnome with aqua/quartz but it doesn't have the polish that the aqua GUI has if that's what your wanting, it's still basically gnome but on the plus side you can still have gnome KDE and tons of other open-source apps on your mac and aqua for the eye-candy.[/QUOTE]
 I have fink but I don't want to use X11 (the special version of X11 from apple doesn't interface the clipboards correctly) besides I don't want the bulk of just another GUI system specially one that loads like hundreds of widget toolkits with no apparent reason,  I don't have a gtk2 theme to match my current OSX theme (yes Aqua can be themed), And I don't want to load a full DE just to replace the file browser that comes with OSX. I know there are some Finder replacements but all of them are navigational mode file browsers (I don't like the navigational file managers) only one is spatial but it's expensive demoware and it's crap (no built-in archiving, built-in cd burner can only burn at 1x and if you try setting it at 2x or higher all you get are coasters, etc). And there's konqueror under Qt/Mac but it's well it's the fat, and Krappy KDE file browser and to install it you have to install half KDE with it).

---

### Post by Akoluth of Nandus on 2005-07-29
AFAIK there is no port of GTK2 to OS X that doesn't need a X server.

---

