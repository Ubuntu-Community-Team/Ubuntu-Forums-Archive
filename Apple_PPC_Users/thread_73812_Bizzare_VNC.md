---
title: "Bizzare VNC"
date: 2005-10-10
forum: Apple PPC Users
---

### Post by DaveHartburn on 2005-10-10
Anyone got any ideas about solving a very strange VNC problem?

I've just setup a PC for a few people to run remote linux desktops off, using VNC. It is just the basic 5.04 desktop (not server) install version.

The X server on the PC itself works fine, however if I start up a vncserver (just with the vncserver command), the X session does start, allows you to connect, but the keyboard settings are really screwed up. For example, 5 seems to map to delete, L maps to 0, G to j etc.

Although this sounds like I've got incorrect X settings somewhere, what is very strange, is starting another vnc session under any other user, works fine, all keyboard settings normal. If I then kill the first vnc session, then the second one suddenly gets very screwy keyboard settings.

Basically the lowest vncserver process running, at any time, has a broken keyboard setup, all others are fine.

One clue is that the first session does seem to have slightly different font configuration, and you see the fonts change on server :2 if you kill :1. Basically it looks like the one session picks up a completely different X configuration from somewhere.

I've checked the logs VNC creates for two VNC sessions, one working and one not. Apart from the server and port number, the logs are identical.

Is there any logs or config scripts I can provide that may be useful?

---

### Post by DaveHartburn on 2005-10-10
Sorry, I've accidently posted this to the wrong forum, please ignore.

---

