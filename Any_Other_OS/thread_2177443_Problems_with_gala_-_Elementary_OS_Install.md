---
title: "Problems with gala? - Elementary OS Install"
date: 2013-09-28
forum: Any Other OS
---

### Post by rgutierrez on 2013-09-28
P4 1.8GHz, 1GB RAM, 40GB HDD, Nvidia GeForce FX 5600

Looking for direction. Elementary OS live CD loads fine with noapic, nomodeset, and free software only. I select these options for the actual install, and everything seems to install fine. Login and all I get is wallpaper and a cursor. The window manager never fully loads. I've reinstalled twice, after playing with nvidia drivers, lightdm/gdm swapping and configuration changes. Here are some errors from xsession-errors:

```
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 55
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 56
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 59
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 58
nvfx_screen_get_param:95 -  Warning: unknown PIPE_CAP 30
Window manager warning: Log level 128: Preferences.vala:328: Loading preferences from file '/home/user1/.config/plank/dock1/settings'
Window manager warning: Log level 16: Preferences.vala:184: '/usr/share/plank/themes/Pantheon/dock.theme' is read-only!
Window manager warning: Log level 128: Preferences.vala:328: Loading preferences from file '/usr/share/plank/themes/Pantheon/dock.theme'
Window manager warning: Log level 128: Settings.vala:158: Loading settings from schema 'org.pantheon.desktop.gala.keybindings'
Window manager warning: Log level 128: Settings.vala:158: Loading settings from schema 'org.pantheon.desktop.gala.shadows'
Window manager warning: Log level 128: Settings.vala:158: Loading settings from schema 'org.pantheon.desktop.gala.behavior'
** Message: applet now removed from the notification area
Window manager warning: Log level 128: Settings.vala:158: Loading settings from schema 'org.pantheon.desktop.gala.animations'

(gala:1562): Cogl-WARNING **: Skipping layer 1 of your material since you have supplied texture coords outside the range [0,1] but the texture doesn't support hardware repeat (e.g. because of waste or use of GL_TEXTURE_RECTANGLE_ARB). This isn't supported with multi-texturing.
gnome-session[1479]: WARNING: Could not launch application 'gdu-notification-daemon-pantheon.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-disk-utility/gdu-notification-daemon" (No such file or directory)

** (zeitgeist-datahub:1747): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!

(applet.py:1754): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:1754): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:1754): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:1754): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(applet.py:1754): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-settings-daemon:1522): GLib-CRITICAL **: g_variant_get_int32: assertion `g_variant_is_of_type (value, G_VARIANT_TYPE_INT32)' failed
WARNING:root:timeout reached, exiting
Cannot connect to backend, is it busy?


```

---

### Post by rgutierrez on 2013-09-28
Found that plank works when run separately on display :0. so, I don't think it's my video drivers or anything like that. That is, unless gala doesn't like my video card for some reason. I have no idea. Anyone else?

---

