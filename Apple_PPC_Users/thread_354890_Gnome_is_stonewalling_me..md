---
title: "Gnome is stonewalling me."
date: 2007-02-06
forum: Apple PPC Users
---

### Post by Banjaxala on 2007-02-06
I am getting an error when I try to start my Powerbook (G4 titanium, Dapper)--after I login, I get three errors in quick succession:

First from GNOME--

> Settings Daemon restarted too many times. [etc., etc.] Last message sent was IDL:omg.org/CORBA/COMM_FAILURE:1.0

Then the panel--

> There was a problem registering the panel with bonobo-activation server. Error code: 3. Panel will now exit.

Then Nautilus--

> Nautilus can't be used right now, there was an error from bonobo when attempting to register the file manager view server.

Some background to the error--I had no problems with the install (2 wks ago), and no problems afterward until I tried to install external codecs for multimedia, etc. I installed EasyUbuntu--which did not make media playable--followed by Xine player and its codecs package. DVD performance was choppy at best, so I tried a few other things--GXine, etc. Still no dice, and somewhere in there all sound ceased.

So, I think, I'll back up. I'll remove GXine, Xine, the codecs, all that. Deselected the packages, and lo, and behold, all administrative apps freeze upon opening (device manager, etc.)

It may or may not matter that I also installed IBM Java, but that was all completed well before the codec crisis.

Alls I want is to start over, have a clean slate, and I'll live without the codecs for a while. The funny thing is, it gave me the same errors just now when I booted from the LiveCD, and Gnome still wouldn't start (hence I type from the XP machine).

Any help is appreciated. Thanks,

j

---

### Post by grazie on 2007-02-06
Never encountered a problem similar to yours, but if you can no longer boot your machine with the Live CD, then something on your computer (and the not installed software) has changed. What's the machine? Maybe it's related to the famous Gnome date error (which personally I've not seen either)

---

### Post by Banjaxala on 2007-02-06
Well, as to the date error-- could well be. The date shown on the login screen was prior to the original install. I have continually had problems with the system clock under ubuntu, but once I'm logged in and the clock can sync to an online server, it keeps time just fine.

So, is there a history of problems with dates causing problems for Gnome?

---

### Post by Banjaxala on 2007-02-06
Right, so, searching the forum, I see the date bug is at fault here. So I've logged into failsafe terminal and fixed it for now.

In the future--would KDE stall at the same problem? If not, what's the package name to download?

Or is there a fix to my wayward system clock? It did not jump around at all (certainly not weeks into the past) in OS X.

---

