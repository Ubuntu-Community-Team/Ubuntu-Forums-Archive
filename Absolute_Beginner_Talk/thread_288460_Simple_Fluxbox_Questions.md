---
title: "Simple Fluxbox Questions"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by NavmaN on 2006-10-29
Hello,

I was just wondering what the default file browser was for fluxbox, for example, in gnome it's nautilus, in fluxbox what is it, and what's the command for it to run in the terminal.

Also, when I install styles/themes, do they autmatically get added to the menu under the sub-menu styles, or do I have to manually add them?

Thanks Very Much,
NavmaN

---

### Post by 23meg on 2006-10-29
Fluxbox is a window manager, not a desktop environment with its own apps, so it doesn't have a file manager.

---

### Post by kerry_s on 2006-10-29
You can use any one you want. Are you using a fluxbox on gnome install? If so you should be able to still use nautilus. If your using a server+fluxbox you can install which ever one you want, rox is very popular, you might also want to go lighter. What are your spec's?

---

### Post by NavmaN on 2006-10-29
I have fluxbox on gnome install, but when I use nautilus it changes the desktop background of fluxbox, and makes it so that if you click at all (i.e. on the first click) it removes the taskbar and you can't get it back.

---

### Post by NavmaN on 2006-10-29
Where can I get rox?
Thanks

---

### Post by kerry_s on 2006-10-29
I beleave you have to launch nautilus with -> nautilus --nodesktop

You can get rox in the repos->
Use synaptic
or
sudo apt-get install rox-filer

---

### Post by yabbadabbadont on 2006-10-29
When you run Nautilus, you need to pass the "--no-desktop" parameter so that it won't do what it did.  (did that make sense?)

Personally, I like Thunar, but Rox can be configured to provide desktop icons for fluxbox as well as act as a filemanager.

Edit: You beat me with your post, but you gave the wrong option... so there. :p :D

---

### Post by NavmaN on 2006-10-29
Oh thanks very much!
NavmaN

---

### Post by songo on 2006-10-29
if you want just a file-manager you will want thunar rather rox.
the style, add the downloaded theme to /usr/share/fluxbox/styles and it will apear on the menu.

---

### Post by Ptero-4 on 2007-05-17
Since the OP is running fluxbox within gnome, he can´t pass options to nautilus, but he can set nautilus to not show the desktop using gconf-editor (/>apps>nautilus>desktop, the key is ¨show_desktop¨).

---

### Post by RedSquirrel on 2007-05-17
> **Ptero-4 said:**
> Since the OP is running fluxbox within gnome, he can´t pass options to nautilus, but he can set nautilus to not show the desktop using gconf-editor (/>apps>nautilus>desktop, the key is ¨show_desktop¨).


It looks to me that the OP is running Fluxbox on top of  GNOME, that is, the OP has GNOME and Fluxbox installed, and can choose Fluxbox at the login screen. 

This means the OP still has access to all the GNOME apps while they are running Fluxbox.

In the specific case of Nautilus, it must be run with the --no-desktop option to prevent it from managing the desktop (so that Fluxbox will do that). The automatic menu generators for Fluxbox setup the command for nautilus as:

```
nautilus --browser --no-desktop
```

or similar. (Check the manpage for nautilus to verify the exact names of the options.)

---

