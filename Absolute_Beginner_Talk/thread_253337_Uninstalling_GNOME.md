---
title: "Uninstalling GNOME"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by angelboy on 2006-09-08
I want to uninstall gnome from my system. For some reason gnome panels stopped to responding and i can do nothing to them. So I figured that 'cause reinstalling didn't do any good, I uninstall the whole gnome interface and then install it back. What packets I should remove by synaptic? I have heard that many programs uses gnome libraries and I don't want to mess those.

---

### Post by Druidor on 2006-09-08
I may be wrong on this but using the apt-get remove command at the command prompt would be your best bet

Sudo apt-get remove ubuntu-desktop


I believe that will remove the ubuntu gui from your machine & you can use the apt-get install ubuntu-desktop to put it back on.

---

### Post by vixinu on 2006-09-08
ubuntu automattically (I can't spell that word) comes with GNOME.  If you don't want it, try kubuntu or xubuntu

---

### Post by angelboy on 2006-09-08
If I remove ubuntu-desktop, does that affect to kde? Because I have both, gnome and kde in my ubuntu.

---

### Post by monktbd on 2006-09-08
delete the config files of gnome. maybe that helps.

easiest would be to add a new user and see if the problems is also with that user.

---

### Post by Lakefall on 2006-09-08
> **angelboy said:**
> I want to uninstall gnome from my system. For some reason gnome panels stopped to responding [...]
Reinstalling won't do you any good (unless you messed something up as root). All the applications store their settings and states in hidden configuration files and directories (folders) in your home directory (folder). Your problem probably shows itself because of something panel related somewhere inside either the directory .gnome2 or .gconf in your home directory. Note that these directories also contain many settings which have nothing to do with the panels. If you need to edit gconf, it may be best to use gconf-editor.

---

