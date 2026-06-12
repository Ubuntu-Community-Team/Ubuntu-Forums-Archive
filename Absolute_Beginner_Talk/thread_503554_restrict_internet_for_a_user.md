---
title: "restrict internet for a user"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by gizmoarena on 2007-07-18
how to restrict a user to use internet?
can it be done by creating groups and add a new user on it?
I want to create users, who cannot use anythinh rather that office and multimedia stuffs.

please let me know in details.

---

### Post by Amplidude on 2007-07-18
Probably the easiest way of doing it is through Firestarter. Go System>Administration>firestarter. on the fireststarter dialog box select the policy tab. Immediately below the policy tab is an option box. Select  Outbound traffic policy. Left click then Right click in the bottom of the three boxes (Deny Service) and click on Add Rule in the popup. Select the name of the service from the drop down box (HTTP) and then fill in the When The Source Is section with the name of the computer you want to block from the internet. Good luck

---

### Post by KIAaze on 2007-07-18
DansGuardian might also be a solution:
[http://dansguardian.org/?page=smoothwall]("http://dansguardian.org/?page=smoothwall")
[http://ubuntuforums.org/showthread.php?t=237355]("http://ubuntuforums.org/showthread.php?t=237355")

---

### Post by gizmoarena on 2007-07-20
thanks both of you. 

but can't I just do it without using a firewall?

---

### Post by KIAaze on 2007-07-20
If you have a DHCP connection, one possibility would be to disable the automatic IP detection at startup.
I don't know exactly how yet, but I could look into it later. (maybe it's doable in the "services" window in system->administration)

Renewing the IP address after startup usually requires root permissions as far as I know.
At least when using the "dhclient" command. (That's what I usually do to get an automatic IP without rebooting)

---

### Post by gizmoarena on 2007-07-23
I have done it in some other way :p

I disabled network from sessions then removed the internet and session options from main menu ;)
and thats doing the job so far :D

---

