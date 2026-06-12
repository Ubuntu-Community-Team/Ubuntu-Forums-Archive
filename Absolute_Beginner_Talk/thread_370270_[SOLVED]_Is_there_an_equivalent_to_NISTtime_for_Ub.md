---
title: "[SOLVED] Is there an equivalent to NISTtime for Ubuntu?"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by jrlii on 2007-02-25
Is there a Ubuntu utility equivalent to NISTtime, the clock setting utility from the (US) National Institute of Standards and Technology (NIST) ?

This little VB program uses the RFC-1305 protocol to get millisecond accurate time from NIST's (or some other) atomic clocks and adjusts the system time to synchronize. Unfortunately they only have versions for Windows and Mac.

Surely there is someone who has at least implemented a clock synchronizing program which gets its time from NIST, however, I haven't had any luck in finding one.

---

### Post by n8bounds on 2007-02-25
Use the gnome applet to alter your clock...you'll see an option in there regarding internet time.  say in a terminal
```

aptitude search nis

```
for more ideas

---

### Post by jrlii on 2007-02-25
Thanks. Now to figure out how to use it. 

something like:

ntpdate server nnn.nnn.nnn.

where nnn. nnn.nnn is the time server's IP address?

---

### Post by mcduck on 2007-02-25
Actually this feature is a built in. You just need to enable it in the time settings :D

Go to System/Administration/Time and Date and mark 'keep clock synchronized with Internet servers. If you want you can choose the server(s) you want to use from the list or add a new server.

---

