---
title: "Problem with Ubuntu Edgy"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by makinasvp on 2007-04-13
I have Ubuntu 6.10 with Nvidia drivers and Beryl installed.
Then I tried to install XGL/compiz going through this walkthrough:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28NVIDIA.29)

now my computer froze, and I get this in the command line...

```
(compiz-tray-icon:5997): GLib-GObject-WARNING **: invalid (NULL) pointer
instance

(compiz-tray-icon:5997): GLib-GObject-CRITICAL **:
g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)'
failed

(compiz-tray-icon:5997): GLib-GObject-WARNING **: invalid (NULL) pointer
instance

(compiz-tray-icon:5997): GLib-GObject-CRITICAL **:
g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)'
failed 
```

Any ideas? Am I going to have to reinstall everything all over again?

---

### Post by makinasvp on 2007-04-13
Im at work right now so I cant really do anything. But was wondering pehraps if I can simply go to the Add/Remove panel and remove XGL/compiz? Would that fix my problem?
Because now, Beryl isn't even working. I can see the icon on the top right, I can double click it to see the Beryl browser, but it just doesnt work...
Help!!!
Please dont tell me I have to reformat and reinstall everything... :(

---

### Post by rsambuca on 2007-04-13
Just copy your gdm.conf-custom-backup over the file you changed it to.  You can then just ```
sudo apt-get remove compiz compiz-extra compiz-plugins compiz-extra-plugins gnome-compiz-manager gnome-compiz-manager-extra xserver-xgl


```

---

### Post by makinasvp on 2007-04-13
how do I do the "copy your gdm.conf-custom-backup over the file you changed it to"? I am so sorry, I am a complete noob at this... lol

---

### Post by rsambuca on 2007-04-13
In a terminal, enter the following code:```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

This assumes that you followed the instructions exactly as per the link in your first post.  The 'cp" from the original instructions copied the xorg.conf file to xorg.conf_backup.  Thus, if the changes happened to mess things up, then you just copy the backup overtop of the changes you made.

Don't sweat it, if this doesn't get things back up and running, we should still be able to fix it!

---

