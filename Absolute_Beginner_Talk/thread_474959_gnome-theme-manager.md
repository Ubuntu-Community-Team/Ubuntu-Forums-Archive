---
title: "gnome-theme-manager"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Fakircho on 2007-06-15
when i run
sudo gnome-theme-manager

i get the following error

(gnome-theme-manager:11320): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

How can i fix this ?

---

### Post by dbbolton on 2007-06-15
> **Fakircho said:**
> when i run
sudo gnome-theme-manager

i get the following error

(gnome-theme-manager:11320): GLib-CRITICAL **: g_hash_table_foreach: assertion `hash_table != NULL' failed

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

How can i fix this ?
why are you running that app as root in the first place?

anyhow, it's a graphical app. you would have to run it as 'gksudo gnome-theme-manager'. and that would just change the theme for root's account, since root uses its own config files. sudo uses your config files, so running it as sudo wouldn't really do anything.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Fakircho on 2007-06-16
I am very new to this stuff so i have a lot to learn 
but thanks i managed to resolve my issue :)

---

### Post by dbbolton on 2007-06-16
> **Fakircho said:**
> I am very new to this stuff so i have a lot to learn 
but thanks i managed to resolve my issue :)
well, you can easily launch gnome-theme-manager by going to System > Preferences > Theme.

---

### Post by forestpixie on 2007-06-16
:)

---

