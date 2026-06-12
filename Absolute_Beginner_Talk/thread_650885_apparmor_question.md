---
title: "apparmor question"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by ptn107 on 2007-12-26
The apparmor security module is installed by default with Ubuntu 7.10. Is the package apparmor-profiles necessary for apparmor to function correcly? What additional functionality does apparmor-profiles provide? Is it preferred more towards a desktop and/or server platform?

---

### Post by PmDematagoda on 2007-12-26
You need the apparmor-profiles package since Apparmor provides protection by making programs follow the rules as stated in the profiles, without the profiles Apparmor will not know what to allow and restrict.

Apparmor controls permissions that are granted to applications and processes and defines what folders it can read and write to and what folders it can't read and write to. So it can be used to prevent a hacker who uses a vulnerability in an application or process from reading and accessing all the files in the PC since the hacker will be restricted to the folders that are allowed by Apparmor for that application or process, so it can be very useful for both Servers and Desktops.

More information can be found [here]("http://en.wikipedia.org/wiki/AppArmor").

---

### Post by ptn107 on 2007-12-27
Why are the profiles not installed by default?

---

