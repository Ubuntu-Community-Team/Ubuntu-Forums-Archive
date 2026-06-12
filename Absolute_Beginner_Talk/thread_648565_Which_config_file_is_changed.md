---
title: "Which config file is changed?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by mikeserv on 2007-12-23
When I change the Login settings from "Automatic Login" to regular login screen, what file is physically changed to reflect that?

-Mike

---

### Post by Gwasanaethau on 2007-12-23
I think it's:

/etc/gdm/gdm.conf-custom

Though be wary of editing this file directly - it's easy to mash things up!

---

### Post by mikeserv on 2007-12-23
I don't think I will be.  But I'll have two different versions, which will each be edited through the "Login Settings" app, and they'll be copied over each other via a bash script.

-Mike

---

