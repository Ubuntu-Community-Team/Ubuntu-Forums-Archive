---
title: "I stuffed my DansGuardian......."
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by troos on 2007-07-30
'lo

As an uninstall option, I decided in my "wisdom" to remove all references on my Ubuntu to DansGuardian by deleting related files and directories. (example "rm -rf /etc/danguardian", "rm -f /etc/init.d/dansguardian", etc).

I did this after I did the "apt-get remove dansguardian", thinking to myself I will be able to make a clean, brand new installation after these manual actions.

To my "amazement", I find that after the re-install of dansguardian (apt-get install dansguardian), all files removed manually are not restored. 

I'm now stumped and I have no idea how to recreate all the manually removed files and directories.

How do I correct this problem? Where do I go from here? 

Any help will be appreciated

---

### Post by FleetAdmiral74 on 2007-07-30
if you kept track of the stuff you deleted, you can make the folders from the terminal with the mkdir command

edit: it seems you already know about the command line though, unless you didn't know what you were doing above, just copy pasting the text into the terminal

---

