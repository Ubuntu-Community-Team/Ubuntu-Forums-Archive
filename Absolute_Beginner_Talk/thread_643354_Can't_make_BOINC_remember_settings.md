---
title: "Can't make BOINC remember settings"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by Jim_S on 2007-12-17
Can't make BOINC remember settings with UBUNTU.
Any Ideas?:confused:

---

### Post by coolbrook on 2007-12-28
Any luck?  Which kind of settings do you mean?

---

### Post by jimbo2150 on 2008-01-03
I am having the same issue. When I go to Advanced -> Preferences... -> change any values then click OK. None of the settings are saved. When I go back into Preferences, everything is still default. Any ideas?

---

### Post by ticomse on 2008-01-05
It looks like the permissions on one of the config files needs to be changed.  Run the following command in a terminal to make your changes stick:

sudo chmod 660 /etc/boinc-client/global_prefs_override.xml

---

### Post by jimbo2150 on 2008-01-05
Thanks, turns out that changing the setting in your account online will change them as well.

---

