---
title: "GNOME Settings Daemon - Themes"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by Own3d on 2008-04-20
Hello , Once again I require some help from someone a bit more knowledgeable than myself at Ubuntu 7.10. I have used a lot of themes and customized the graphical settings of Ubuntu a lot to make it look pretty :) But my problem is every so often upon start up I get presented with this error message...
 


There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-Up1ran9EYj: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in.

Upon Restart its fine until around another 20 start ups and i'll get the message again . After logging in after receiving that error the theme doesn't work and upon trying to open the Appearance settings I get this message: 

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

Any help would be appreciated, Only been running Ubuntu for 2 weeks by the way.

--Chris--

---

### Post by Own3d on 2008-04-20
Bump

---

### Post by erginemr on 2008-04-20
This is a known bug in Gnome in Gutsy:
[http://ubuntuforums.org/showthread.php?t=608767&highlight=OAFIID](http://ubuntuforums.org/showthread.php?t=608767&highlight=OAFIID)

I have also been experiencing this from time to time. deleting what is inside the /tmp (temporary) folder may help: Open nautilus (file manager), browse to your /tmp folder and delete what is inside all. Restart your computer to see if the problem is gone.

---

