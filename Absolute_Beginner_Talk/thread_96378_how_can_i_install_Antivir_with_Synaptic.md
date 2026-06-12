---
title: "how can i install Antivir with Synaptic?"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-11-28
hi, i'd really like to try Antivir. i did have clamav but i just uninstalled it. i know alot of people see no reason to use an AV but i move things (archives, music, video etc) from Ubuntu to XP and i'd like to have one. i like antivir and really want to use it. can you help me update my source list so i can install it with Synaptic? thanks

---

### Post by ecobuntu on 2005-11-28
have you tried to google for a repository?  the fact is that a .exe virus won't infected your linux partition...but there are still linux viruses out there so don't let anyone discourage from trying to keep your computer safe(r).

BTW...a quick googling from here looks like you could d/l the tarball and install it that way.

---

### Post by az on 2005-11-28
[QUOTE=ecobuntu]but there are still linux viruses out there .[/QUOTE]

Not really.  More like security vulnerabilities that have nothing to do with viruses.

---

### Post by Danielle on 2005-11-28
[QUOTE=ecobuntu]have you tried to google for a repository?  the fact is that a .exe virus won't infected your linux partition...but there are still linux viruses out there so don't let anyone discourage from trying to keep your computer safe(r).

BTW...a quick googling from here looks like you could d/l the tarball and install it that way.[/QUOTE]
hi, thanks. yes i definately want an AV.

i'm not able to install the tarball, i always  manage to get errors then spend hours trying to fix it.

---

### Post by arphe_el on 2005-11-28
I install the clamav antivirus and when i'm updating the database there is an interruption with my connection to the internet so it was cut off and when i'm trying to update it again using this command 

sudo freshclam

the out is like this
ClamAV update process started at Tue Nov 29 10:46:30 2005
WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Local version: 0.83 Recommended version: 0.87.1
main.cvd is up to date (version: 34, sigs: 39625, f-level: 5, builder: tkojm)
WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Current functionality level = 4, required = 5
daily.cvd is up to date (version: 1197, sigs: 1664, f-level: 6, builder: tomek)
WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Current functionality level = 4, required = 6

any suggestions to update this? 

also is there a GUI panel for this?

Thank you and GODspeed!

---

### Post by Danielle on 2005-11-28
how did you install calm? i installed from a tarball i think, i know it wasn't synaptic. when i uninstalled using synaptic i noticed there were alot of other clamav installs that i think still needed to be installed. have you looked in synaptic?

---

### Post by ertai on 2005-11-29
The only antivirusprogram for Linux I know is ClamAV. This you can install using synaptic. Just seach for "ClamAV" and you'll find it. I also recommend installing clamtk. This last package is a GUI for ClamAV (I don't know the frontend so can't help you with that).

arphe_el: You clamAV itself is outdated. So you'll need to update that before you'll be able to update your virusdefinitions.

---

