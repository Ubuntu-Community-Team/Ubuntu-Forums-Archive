---
title: "Claws Mail crashing"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-04-21
v2.9.1 is crashing on first download of spam for the day on updated Ubuntu 6.10. Plug-ins are: Clam AntiVirus, Notification, and Trayicon.

Seems to crash during antivirus scan, after downloading new messages, but before displaying the messages in Inbox. The messages cannot be seen in Inbox on restart, but a check via webmail shows they've all been downloaded from the server.

Removing the Clam AntiVirus plug-in allows a new mail check to complete without crash, and all those first-load messages then appear in Inbox. 

AV plug-in can then be reinstalled and further mail-checks of the day download normally, including after shutting down and restarting Claws. Trouble appears to be just during the first big load of morning messages.

Possibly related: the previous Claws version did the same AV-check crash if Trayicon was set to 'Work Offline' during start-up. No problems when the Trayicon plug-in was at the default Online setting.

[We may not get any solutions on this thread, but the above may help a few people retrieve their mail.]

---

### Post by Kobalt on 2007-04-21
I do fear this is a Claws bug... have you tried launching it in a Terminal, checking the error messages and then searching the Claws forum/wiki for a bug track or workaround ?

---

### Post by ofb on 2007-04-22
> **Kobalt said:**
>  have you tried launching it in a Terminal, checking the error messages 

Good idea, and not yet: it didn't crash on this morning's start.

---

