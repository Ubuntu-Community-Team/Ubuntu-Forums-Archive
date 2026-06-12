---
title: "Resuming sessions in NX from the local host."
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by Baka no Kami on 2007-10-15
I installed NX on my system without any problems.  And I can attach, detach, and terminate the remote session at will from my Windows laptop.  Where I'm running into a wall is when I go back to the Ubuntu desktop.  

Say I start a program running in the remote session, set it up to do it's thing, and disconnect. Later I get back home and want to see if the program finished running. I log in and the program doesn't show up on the desktop.  I know that's supposed to happen because I'm not logging into the session I was using on the remote.  Is there a way to change that, or switch to the other session once I'm logged in.  I can relog into the NX session through the laptop with no problems. When I tried starting the NX client on the desktop and connect it to localhost, it sees the session I have running, but won't connect to it.  It lists it as unavailable even when no other computer is connected to it remotely.

This is with nomachines NX client/server.  Has anyone else run into that?

---

### Post by jnorth on 2007-10-16
Yep - took me a while to figure it out too.

This may or may not be the answer to your problem but it's worth looking at.

I actually ran into this accessing from 2 different machines.  It turned out that the color depth settings were different.  In other words, after opening a session from my laptop, and then disconnecting (leaving it running), when I attempt to connect from localhost, I see an available session running at 1260x740x32 but cannot connect.  Turned out my localhost X settings were set at only 16b depth settings.  I changed my xorg config to use 24(32) and viola.

I can duplicate the issue by opening a session on my laptop as normal, then changing my depth settings on the laptop to 16b, and reconnecting, it then shows the session but will not connect.

Works vice versa also, if you open a 16b session and try to connect from a guest running at 32/24 you cannot open.

Hope that helps, it took me a couple weeks to figure this out.

EDIT:  Just use vi or nano to edit the Screen section where it says  DefaultDepth    16 and change to 24.  Then, restart X or reboot.
If it is already at 24 then I guess that may not be your problem.  You'll also need to check your windows depth settings to make sure they are similar.
The file to edit is /etc/X11/xorg.conf

---

