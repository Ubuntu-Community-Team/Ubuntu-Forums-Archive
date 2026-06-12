---
title: "Adding user- no sound"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by sankarv on 2006-09-23
In ubuntu 6.06 I added new user using

adduser usrname

and gave password,etc.


Now i logged in as new user and i cannot hear sound.

The volume control is disabled. Its giving error on clicking as GSstreamer not installed. But i can hear sound with the user i created initially duriong installation.

pls help

---

### Post by kidders on 2006-09-23
Did you remember to add your new user to the "audio" group?

**Edit: ** In case you're interested, access to audio devices *can* give a malicious user scope to crash your PC, or at least eat up all its CPU time, so it's standard practice in Linux not to grant access to them by default. (See **ls -l /dev/audio**)

---

### Post by bulldog on 2006-09-23
Go to users and groups in your administration menu.

Open it and select the new user.
Choose preferences and see what rights you gave the new user [use audio etc]and alter if necessary.

---

