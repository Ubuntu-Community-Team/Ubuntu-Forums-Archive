---
title: "Fluxbox questions"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by Goemon4 on 2007-12-16
Hey all, i just installed Fluxbox 1.0.0 over Kubuntu and im just wondering how to clear up, and or organize Fluxbox's menus. Most of the similar threads the forums listed were just about enabling menus, which i have down, their just very un-organized, any tips on how to organize them are appreciated. 

Thanks

(also how to clear out all the kde config apps, and options, cause i dont want to mess up my kde settings in anyway, which i fear i might do since everything is mixed up, and im used to going straight to Kcontrol and what not for configuring my system, removing things like that would really help, so yeah any tips?)

---

### Post by LaRoza on 2007-12-16
The menu is in ~/.fluxbox/menu, you can edit it as much as you want.

---

### Post by Goemon4 on 2007-12-16
Ok, but all i see in that file is this 

[begin] (fluxbox)
[include] (/etc/X11/fluxbox/fluxbox-menu)
[end]


Would i need to open /etc/X11/fluxbox/fluxbox-menu for menu editing instead? If so then i guess i answered my own question, lol. 

ty for the quick response

---

### Post by LaRoza on 2007-12-16
Oh, here is mine:

```

#[begin] (fluxbox)
#[include] (/etc/X11/fluxbox/fluxbox-menu)


[begin] (Fluxbox)
#[exec] (Dolphin) {/usr/bin/dolphin}
[exec] (Thunar) {/usr/bin/thunar}

[separator]

[exec] (Terminal) {/usr/bin/gnome-terminal}

[separator]

[submenu] (Applications 0)
    [exec] (Abiword) {/usr/bin/abiword}
    [exec] (Firefox) {/usr/bin/firefox}
    [exec] (GEdit) {/usr/bin/gedit}
    [exec] (KWrite) {/usr/bin/kwrite}
    [exec] (OpenOffice) {/usr/bin/soffice}
    [exec] (Opera) {/usr/bin/opera}
[end]

[separator]

[submenu] (Applications 1)
    [exec] (Synatpic) {gksudo /usr/sbin/synaptic}
    [exec] (VirtualBox) {/usr/lib/virtualbox/VirtualBox}
[end]
 

[separator]

[submenu] (Applications 2)
    [exec] (Gnometris) {/usr/games/gnometris}
    [exec] (Mines) {/usr/games/gnomine}
    [exec] (SuperTux) {/usr/games/supertux}
    [exec] (DosBox) {/usr/bin/dosbox}
[end]

[separator]

[submenu] (Settings)
   [config] (Configuration)
   [submenu] (Styles) {}
      #[stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
   [reconfig] (Reconfigure)
[end]
   #[workspaces] (Workspaces)
[separator]
   [exec] (Poweroff) {gksudo poweroff}
   [exec] (Reboot) {gksudo reboot}
   [restart] (Restart)
   [exit] (Exit)

[end]


```
(Some are commented out, because I use the same menu for all my installations, and not all have the same apps)

The includes make it easier to handle.

---

### Post by Goemon4 on 2007-12-16
Ohhhhh i see what you mean now. That seems pretty easy to do, thanks. 

One more quick question, is it possible to change the default apps in Fluxbox without changing them in KDE? Eg, instead of using Konqueror as my default filebrowser in Fluxbox, could i use ROX Filer, but still use Konqueror as the default in KDE, or is that impossible? 


and again, thanks for the quick response

---

### Post by RedSquirrel on 2007-12-16
See the link in my signature for help with the menu.

There are no "default applications" in Fluxbox. You can use whatever you want.


Edit: Just to clarify -- Fluxbox is a window manager, not a desktop environment, so it has no default applications. ;)

---

### Post by Goemon4 on 2007-12-16
ahh, i see then, ok i guess ill just take things out of the menu and go from there. Thanks for all the help

---

