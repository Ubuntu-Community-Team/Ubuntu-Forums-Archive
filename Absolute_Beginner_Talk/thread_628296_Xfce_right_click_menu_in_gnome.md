---
title: "Xfce right click menu in gnome"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by apauloisdead on 2007-12-01
Is there anyway to put a right click menu in gnome similar to the one in xfce..?

---

### Post by felicity on 2007-12-01
Nautilus controls the desktop in GNOME so you'd need to either edit that menu or turn it off and use another. I believe there's a few choices for editing that menu, like nautilus-actions. 
Another option is to use another window manager. I'm using Openbox and made my middle-click-on-desktop open openbox's menu which is very similar to XFCE's. :KS

---

### Post by urukrama on 2007-12-01
This is a question that comes up regularly on these forums, and I'm afraid there is no simple answer. You could try another window manager, like Openbox, as has already been suggested. Or you could use a different desktop environment, such as Xfce, which does have a desktop menu.

There is a way to edit the menu that comes up now (the Nautilus menu). Compiz-Fusion might have a root menu also. I'm not sure, but it might be worth checking it out.

Check out the following threads:

[1. Right Click Menu?]("http://ubuntuforums.org/showthread.php?t=469043&highlight=xfce+menu+desktop")

[2. Is it possible to make the menu...]("http://ubuntuforums.org/showthread.php?t=452175&highlight=xfce+menu+desktop")

[3. Customise Gnome desktop popup menu -- how?]("http://ubuntuforums.org/showthread.php?t=228371")

[4. Is there a way to Fluxbox Menus Without Fluxbox?]("http://ubuntuforums.org/showthread.php?t=452462&highlight=xfce+menu+desktop")

Hope this helps.

---

### Post by XVII on 2007-12-01
You can replace Nautilus with Thundar.

---

### Post by apauloisdead on 2007-12-03
I don't really wanna replace my whole WM, how would i go about just replacing nautilus with thunar?

---

### Post by zvacet on 2007-12-03
[http://www.psychocats.net/ubuntu/nonautilusplease]("http://www.psychocats.net/ubuntu/nonautilusplease")

---

### Post by apauloisdead on 2007-12-03
Thanks!

Now that i have thunar up and running, how do i get the right click menu?

---

### Post by urukrama on 2007-12-03
Did you read the threads I linked to earlier? They contain the answer to your question.

---

### Post by mali2297 on 2007-12-03
> **apauloisdead said:**
> Thanks!

Now that i have thunar up and running, how do i get the right click menu?

One option is to use [DeskMenu]("http://packages.ubuntu.com/gutsy/x11/deskmenu"), it is configured from a .deskmenurc file in your home directory:

```

# Example .deskmenurc file
#
# Syntax
#
# menuitem=label:command
# submenu=label
# endmenu=
# divider=
# include=filename
# windowlist=label
# workspaces=label
# keycode=modifier+keyname
#   for example Control+Escape
#   this keycode is used as "hotkey"
#   to display the menu.
#

keycode=Control+Escape
menuitem=Terminal:x-terminal-emulator
menuitem=Run Program:gmrun

divider=

submenu=Graphics
menuitem=The Gimp:gimp
menuitem=Electric Eyes:ee
menuitem=Xv:xv
endmenu=

submenu=Multimedia
menuitem=GQmpeg:gqmpeg
menuitem=Audio Mixer:gmix
endmenu=

submenu=Games
menuitem=XBill:gnome-xbill
menuitem=FreeCell:freecell
endmenu=

divider=
include=/etc/deskmenurc.debian

divider=

windowlist=Window List
workspaces=Workspaces

```

---

