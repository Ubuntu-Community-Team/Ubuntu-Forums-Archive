---
title: "Is someone else logged into my computer?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by chameleon_789 on 2006-06-03
I just set up the uptime panel of gDesklets, and it tells me that 3 users are logged in.. Is that normal (I'm running a few programs in the background, mldonkey rythmbox and a few others)? How can I check which users are logged in?

---

### Post by hw-tph on 2006-06-03
Every login shell you are running will show up as a logged in user - this includes terminals if running them as login shells. Open a pair or three new tabs in the Gnome terminal and you will most likely see even more users "logged in".

Try the **w** and **who** commands to see what consoles the "users" are attached to.


Håkan

---

### Post by CompShrink on 2006-06-03
Linux uses different users to give different permissions to programs, so the gDesklet probably just got confused. To check who is logged in right now, the most basic way is to open a terminal and type in:

**users**

Nice simple obvious command, isn't it? Now, this is assuming it's not a smart hacker hiding himself. Not vary likely, but possible.


If you want a little example showing who is running what, open a terminal and type in:

**gnome-system-monitor**

and go to Edit > Preferences, check the "user" box hit ok,
and then View > All Processes

You can scroll through the list and see all the various processes being run under different user names. Most should be under root and your own user name.

---

### Post by chameleon_789 on 2006-06-03
Thanks for the tips.. luckily I just had some terminal windows open, but those commands ease my paranoia a little bit :)

---

