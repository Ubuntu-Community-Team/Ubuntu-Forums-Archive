---
title: "Rhythmbox 0.9.1 bug (crashes)"
date: 2005-12-12
forum: Bug Reports / Support
---

### Post by acornejo on 2005-12-12
When used in remote control mode, rhythmbox uses dbus to communicate to an existing rhythmbox process.

After upgrading Rhythmbox from the ubuntubackports project it now fails to work in remote control mode, and it crashes.

To reproduce this error just do the following:

Open a rhythmbox instance as you usually do, and hit the play button to start playing the playlist of your choice. Now open a console and try the following:

[FONT="monospace"]
acornejo@casiopea:~ $ rhythmbox --play-pause

(rhythmbox:22447): Rhythmbox-CRITICAL **: couldn't connect to session bus: Unable to determine the address of the message bus

** (rhythmbox:22447): CRITICAL **: dbus_g_proxy_new_for_name_owner: assertion `connection != NULL' failed[/FONT]

Also a popup box appears that reads the following:
[B]
The Application "rhythmbox" has quit unexpectedly.

You can inform the developers of what happened to help them fix it.  Or you can restart the application right now.[/B]

Well, I guess thats all, i hope it gets fixed soon, this is one of the really cool features of rhythmbox, so it WILL be missed while its broken.

---

