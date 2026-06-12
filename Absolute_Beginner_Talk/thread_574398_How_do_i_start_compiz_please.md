---
title: "How do i start compiz please"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by tonym53 on 2007-10-12
hi i would like to know how to run compiz can i do it from terminal?

i tried this

tony@tony-desktop:~$ compiz-tray-icon

(compiz-tray-icon:7484): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:7484): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:7484): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:7484): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

---

### Post by RomeReactor on 2007-10-12
Hi. I suggest you instead install **gnome-compiz-manager**; look for it in Synaptic, or:
```
sudo apt-get install gnome-compiz-manager
```
Once it's installed, you'll find it in "System->Preferences->GL Desktop".

---

### Post by overlord.gaurav on 2007-10-12
Isn't GL Desktop the old version of Compiz??

---

### Post by tonym53 on 2007-10-12
I have gl dsk top now what can i do??

---

### Post by RomeReactor on 2007-10-12
> **overlord.gaurav said:**
> Isn't GL Desktop the old version of Compiz??
Yes, that's used for Compiz; for Fusion, I think you use **compizconfig-settings-manager**.

> **tonym53 said:**
> I have gl dsk top now what can i do??
tonym53, which version of Ubuntu are you running? if you're on Feisty, and haven't installed Fusion, then go to "System->Preferences->GL Desktop", enable desktop effects there, and check the option to have the tray icon.

---

