---
title: "X suddenly reboots"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Sliph on 2008-02-06
Hi guys, I'm pretty new to linux in general, and I appreciate you taking time answer our nubie questions:)

Now, to my problem:

My X just suddenly finds it appropriate to reboot itself for no reason at all.
I'm not sure what I have done to make it behave this way,


```
Feb  6 21:57:41 critical gdm[931]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Feb  6 21:57:46 critical gdmgreeter[4179]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Feb  6 21:57:46 critical gdmgreeter[4179]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Feb  6 21:57:46 critical gdmgreeter[4179]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Feb  6 21:57:46 critical gdmgreeter[4179]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Feb  6 21:57:51 critical hcid[5663]: Default passkey agent (:1.112, /org/bluez/passkey) registered
Feb  6 21:57:51 critical hcid[5663]: Default authorization agent (:1.112, /org/bluez/auth) registered
Feb  6 21:57:54 critical NetworkManager: <info>  Updating allowed wireless network lists. 
Feb  6 21:57:54 critical NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
```

I would really appreciate if anyone could shed some light on this!

Thanks in advance,
-Sliph

---

### Post by bwtranch on 2008-02-06
Hi, can't read it. Just paste what it says.

---

### Post by Sliph on 2008-02-09
Feb  6 21:57:41 critical gdm[931]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Feb  6 21:57:46 critical gdmgreeter[4179]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Feb  6 21:57:46 critical gdmgreeter[4179]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Feb  6 21:57:46 critical gdmgreeter[4179]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Feb  6 21:57:46 critical gdmgreeter[4179]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Feb  6 21:57:51 critical hcid[5663]: Default passkey agent (:1.112, /org/bluez/passkey) registered
Feb  6 21:57:51 critical hcid[5663]: Default authorization agent (:1.112, /org/bluez/auth) registered
Feb  6 21:57:54 critical NetworkManager: <info>  Updating allowed wireless network lists. 
Feb  6 21:57:54 critical NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by nidelius on 2008-02-26
I have the same problem this is what I get in the syslog:


Feb 26 10:05:09 ubuntu-nidelius gdmgreeter[7293]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Feb 26 10:05:09 ubuntu-nidelius gdmgreeter[7293]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Feb 26 10:05:09 ubuntu-nidelius gdmgreeter[7293]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Feb 26 10:05:09 ubuntu-nidelius gdmgreeter[7293]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 


I run 7.10 on a 6625WD zepto laptop.

---

### Post by RadiusXE on 2008-03-08
same problem :(

Mar  8 17:59:58 Radius-notebuk gdmgreeter[4788]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Mar  8 17:59:58 Radius-notebuk gdmgreeter[4788]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Mar  8 17:59:58 Radius-notebuk gdmgreeter[4788]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Mar  8 17:59:58 Radius-notebuk gdmgreeter[4788]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

Xubuntu 7.10 32b, lasp updates to the date of this post

I made It, my problem was moblock (maybe upgrade proces fail => bad conf). FULL Remove (with deleting conf) and then install resolves my problem with rebooting and shuting down...

---

### Post by gygabyte017 on 2008-03-09
I have the same problem..

Mar  8 11:51:13 gygabyte017-laptop gdmgreeter[5665]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Mar  8 11:51:13 gygabyte017-laptop gdmgreeter[5665]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Mar  8 11:51:13 gygabyte017-laptop gdmgreeter[5665]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Mar  8 11:51:13 gygabyte017-laptop gdmgreeter[5665]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
M

I'm a newbie, I don't know how to solve this issue... Please help, thank you!

---

