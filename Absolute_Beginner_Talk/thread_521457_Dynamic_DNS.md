---
title: "Dynamic DNS"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by ben22 on 2007-08-09
Hi,

I am a newbie to Ubuntu, but installation of OS went fine. Now I installed inadyn with synaptic package manager.

When I run the terminal gksudo "gedit /etc/inadyn.conf" the terminal prompts:

"While connecting to session manager>
Authentication Rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed."

The editor opnes but the inadyn.conf is empty...

What does that mean? Can anyone help?

Thx
Ben

---

### Post by splintercellguy on 2007-08-09
The message should be ignored. It is a known bug, and is perfectly harmless. As for gedit being empty, perhaps the file doesn't exist?

---

### Post by Nythain on 2007-08-09
try it without the quotes... or try just putting the quotes around teh file path part
gksudo gedit /etc/inadyn.conf
gksudo gedit "/etc/inadyn.conf"

---

### Post by ben22 on 2007-08-09
> **Nythain said:**
> try it without the quotes... or try just putting the quotes around teh file path part
gksudo gedit /etc/inadyn.conf
gksudo gedit "/etc/inadyn.conf"

I entered it as described in the help:

[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)


without "
gksudo gedit /etc/inadyn.conf

---

### Post by ben22 on 2007-08-09
wehn i go to the file browser > /etc/ there is no file like inadyn ...

---

