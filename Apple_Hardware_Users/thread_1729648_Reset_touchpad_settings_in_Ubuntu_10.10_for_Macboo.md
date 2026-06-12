---
title: "Reset touchpad settings in Ubuntu 10.10 for Macbook 5.1"
date: 2011-04-15
forum: Apple Hardware Users
---

### Post by trentgillham on 2011-04-15
I followed the instructions at.

[https://help.ubuntu.com/community/MacBook5-1/Maverick](https://help.ubuntu.com/community/MacBook5-1/Maverick)

It told me to disable the mouse plugin in gnome-settings-daemon.
so I did

gconftool-2 --type boolean --set /apps/gnome_settings_daemon/plugins/mouse/active false

Then told me to edit the xorg.conf.

Pretty much it screwed the touchpad up and when I try to change the settings manually it doesn't take affect.

So does anyone know how to reset everything so I can use the standard mouse plugin?:confused:
UPDATE: I figured out how to do it, but for anyone else you simply put.

gconftool-2 --type boolean --set /apps/gnome_settings_daemon/plugins/mouse/active true

Just replace false with true. I'm an idiot.

UPDATE 2: I rebooted and it reverted back...is there a way to make that change permanent?

UPDATE 3: The command line where I just replaced false with true does not work now. It worked once, but once I rebooted the command does not work. I am back to square one. Please help this it annoying.
I want to control the mouse settings with the regular mouse plugin.

---

