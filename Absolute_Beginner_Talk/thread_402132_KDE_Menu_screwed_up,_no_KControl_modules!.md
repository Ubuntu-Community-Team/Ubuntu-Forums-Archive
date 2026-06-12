---
title: "KDE Menu screwed up, no KControl modules!"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by DizzyTech on 2007-04-05
All of my KMenu is screwed up.  All of my KControl and KSysinfo modules are listed in the Lost and Found menu.  There are also things missing, like Icons and Widgets menus (they can still be run via kcmshell).  It also shows there some Sim City 3000 Unlimited entries installed by Wine, long after its removal.

KControl only shows OBEX Devices.  Also, there are two "Settings" menus in KMenu, one being the contents of the menu in GNOME (I'll get to that in a second), and the other leading to the OBEX Devices object.

I've cleared out the caches and menu fies in /tmp, /var/tmp, and ~/.config.

Note that I am running Ubuntu Edgy Eft, with Kubuntu-Desktop installed.  The first time this came up,  I completely purged everything related to KDE via Synaptic, and cleared out my config.

Later, I installed Amarok and its dependencies, and later the rest of kubuntu-desktop.  I've even run reinstall on all my KDE Apps, but that only works for applications, like K3B and Amarok.

I ran system-settings via command line, and it still has everything, though I believe my kcontrol paranoia is from an underlying problem, and my KMenu is screwed.

Note:  here's what system-settings gives in the Terminal window:
```
adding Font Installer /usr/share/applications/kde/kcmfontinst.desktop
adding Icons /usr/share/applications/kde/icons.desktop
adding Style /usr/share/applications/kde/style.desktop
adding Window Decorations /usr/share/applications/kde/kwindecoration.desktop
```

How do I rebuild this [KMenu] from scratch?  

Regards,
DizzyTech

---

### Post by DizzyTech on 2007-04-05
Bump...
Bump...
Bump it up!

---

### Post by Jucato on 2007-04-05
If you want to revert back to an original unmodified K Menu, go to ~/.config/menus directory and move or remove the applications-kmenuedit.menu file that would be in there.

Hope that fixes it.

---

### Post by DizzyTech on 2007-04-06
I never got to try it; I completely uninstalled KDE (unlike before:  I just realized I didn't totally remove everything), and did a low level delete of all KDE items.

---

### Post by mayhemt on 2007-04-09
I had the same problem &&&  here's a work around.
Bring up Kmenu editor. (Right click on K menu on left corner & select Menu editor)

You should see two settings things on left side. The second one with (strange) folder icon. expand it (click the + sign)

Scroll a little down and expand lost & found. I dragged all those icons  from lost & found into that folder shaped settings menu & now kcontrol works good. Only problem is they are cluttered on left side. Now i have to figure out putting them in their default groups. 

Of course I still see this error when run from konsole.

```

kcontrol: WARNING: No K menu group with X-KDE-BaseGroup=settings found ! Defaulting to Settings/


```

Till we figure out a permanent workaround.... chill out!!!

---

