---
title: "A few questions about Xubuntu"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by pi_ar on 2006-06-05
Hi,
I'm quite new to Linux and I liked Ubuntu a lot. The reason for me to use Ubuntu was - I had to install some modern OS on very old computers (PII 350 MHz, PIII 450 MHz with 128-256 MB RAM) to replace Windows 98 in one office.
But then I discovered that since 6.06 Xubuntu will be a supported member of Ubuntu falimly and that it fits such computers best. Still, there are some questions that I got when testing Xubuntu within a vitrual PC software:

1) As the documentation suggests, Thunar does not support browsing networked PCs (in a LAN), so how can I access network PCs?

2) In Ubuntu I was able to setup networked HP LaserJet 1020 printer quite easily, simply installed foo2zjs, went to printer setup front-end and added the printer telling that it is a printer networked via Samba. How about Xubuntu? Does the web-based front-end support same funcionality?

3) Keyboard layouts: a) is there any way to set up a keyboard shortcut for switching keyboard layouts in Xubuntu (like alt+tab or ctrl+tab in Windows)? Because in the environment I work with there is a need for many keyboard layouts (Lithuanian, English, Polish, Russian and German) and they have to be swithed quite often. b) there is a minor bug with layouts - if you define many layouts (like "us,lt,de,pl,ru") the keyboard layout switcher does not recognize the last layout ("ru" in our case).

Thank you for helping me in advance.

---

### Post by Tortanick on 2006-06-05
1) if you install nautilus, open a terminal, and type nautilus you will be a able to use the standard file manager from Ubuntu with your Xubuntu desktop.

2) if its a seprate program it *should*be the same for both. I can't say for sure.

3) probobly but I don't know how

---

### Post by pi_ar on 2006-06-05
Thank you for the Nautilus trick.
Now I have another problem - when Nautilus is installed all the files I delet are simply deleted from the disk. There is no confirmation dialog and there is no trash bin in Xubuntu :) Any suggestions?

---

### Post by pi_ar on 2006-06-05
Well, I found a way to acces the trash bin via Nautilus. Still, now Xfce Appfinder won't start... I should probably stick wint Ubuntu untill next release :)

---

### Post by Lou Quillio on 2006-06-09
1) [Browsing shares]  Yeah, that's why you keep Nautilus around, for now.  Note that Nautilus may take control of the desktop from `xfdesktop`, so you'll want to kill this behavior in gconf:

  [http://forum.xfce.org/index.php?topic=2417.msg10952]("http://forum.xfce.org/index.php?topic=2417.msg10952")

Another reason to keep Nautilus around is that while Thunar will display thumbnails if another app has created them, it can't yet create them itself.

  [http://xfce-diary.blogspot.com/2005/09/thumbnails.html]("http://xfce-diary.blogspot.com/2005/09/thumbnails.html")

If you have a directory full of, say, photos, view it once in Nautilus to generate the thumbnails, then go back to using Thunar the rest of the time (for speed).  Nautilus' thumbnailers will fail sometimes.  To have them re-try generating any failed thumbnails, delete the contents of

  ~/.thumbnails/fail/gnome-thumbnail-factory/

The upshot is that while Thunar is excellent and fast, [Benedikt's]("http://xfce-diary.blogspot.com/") being very careful not to bloat it, and to conform to [FreeDesktop.org standards]("http://freedesktop.org/wiki/Standards").  Some things will be implemented via plugins, so that there will always be a lean-and-mean Thunar for those who need that.

2) [CUPS]  Yep.  XFCE4 has no GUI tool for printer management, and I don't think one's planned, so you either use the browser-based CUPS interface for that, or `gnome-cups-manager`.  Or do it longhand, if you're a masochist.

3) [Keyboard layouts]  I switch between `us` and `us_intl` keyboard layouts (for the dead keys).  XFCE4 leaves this up to X.  Here's the relevant stanza from my /etc/X11/xorg.conf:

> Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "logiaccess"
    Option         "XkbLayout" "us,us_intl"
    Option         "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
EndSection 
You can see I'm listing the two keyboard layouts I want to use in the `XkbLayout` option.  `XkbOptions` then allows me to toggle between them by pressing Alt+Shift, and additionally toggles the ScrollLock LED to let me know when I'm using `us_intl`.  If you use the xfce4-panel keyboard layout switcher plugin, its display will toggle, too (flag or text abbreviation).  Or you can click the plugin indicator (flag, etc.) to toggle, instead of using Alt+Shift.  This works well, and isn't limited to two layouts.

4) [Trash]  It's not apparent, but "trash" systems are owned by the file manager.  It seems like something that's system-wide, or at least desktop environment-wide (Gnome, KDE), but it's not.  (Not exactly, anyway.  If you exclusively use Naultilus with Gnome, it'll seem like there's a "Gnome" trash system.)

Nautilus implements trash one way; another file manager may do it differently.  Thunar doesn't yet have a trash system, again because of a desire for Freedesktop-compliance and a commitment to doing it right the first time.

[http://thunar.xfce.org/wiki/design:overview#trash_system]("http://thunar.xfce.org/wiki/design:overview#trash_system")

At the moment, then, "deleting" with Thunar is just that:  deleting.  There is no trash recovery, and `recover` or `e2undel` are of no use on ext3 filesystems.  **Important:**  You should provide Nautilus for users who expect a trash system, until Thunar implements one.

# # #

Unfortunately there hasn't been a lot of XFCE-specific documentation for (X)ubuntu users, and most of the Ubuntu resources presume Gnome.  Keep your eye on the ones linked above, and also here:

[http://help.ubuntu.com/6.06/xubuntu/desktopguide/C/index.html]("http://help.ubuntu.com/6.06/xubuntu/desktopguide/C/index.html")

LQ

---

