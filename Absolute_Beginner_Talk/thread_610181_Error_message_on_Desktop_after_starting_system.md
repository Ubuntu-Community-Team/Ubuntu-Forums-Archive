---
title: "Error message on Desktop after starting system"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by explorer716 on 2007-11-11
When I start up Ubuntu Studio 7.10, I get a message on my Desktop  telling that there was a
 
failure during start-up.  Below is a copy of the message:

                                 "There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-djOjqrNd2e: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in."


I can delete the message and everything seems to work OK, but I would like to understand what the problem is and how to correct it.

Thank you in advance for your assistance.

---

### Post by Shinbu-Otaku on 2007-11-13
in my experience, this is where Daemon/Beryl etc is installed on a pc which doesnt have a 3d capable graphics card (or a 3d graphics card which is not enabled competly). To resolve this, either enable the 3D setting on the graphics card (system>Restricted driver manager), or uninstall Beryl/Compiz/Daemon whichever is causing the problem.

If that doesnt solve it, im not sure what else to do lol

---

