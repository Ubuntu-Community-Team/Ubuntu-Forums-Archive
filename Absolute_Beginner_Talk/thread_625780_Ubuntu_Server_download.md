---
title: "Ubuntu Server download"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by happyharry on 2007-11-28
Just downloaded Ubuntu Server - it has the same iso file name as the normal 7-10. Is this supposed to be correct? Further questions:
Does the server come with a gui or is it purley command line?
Do I have set php + mysql?

Thanks

---

### Post by nc_jed on 2007-11-28
> **happyharry said:**
> Just downloaded Ubuntu Server - it has the same iso file name as the normal 7-10. Is this supposed to be correct? Further questions:
Does the server come with a gui or is it purley command line?
Do I have set php + mysql?

Thanks

 - Install is text based (not command line).  No GUI after install.  If this is a need, try to sudo apt-get install gnome-desktop to install a gui on top or set the config up for xdm / x11 forwarding.
 - Yes.  All that stuff is available (I think installed by default).  if not, sudo apt-get install mysql-server mysql-client apache2 php
 - Alternately, you can add these tools to a standard desktop install (use Xubuntu if you need to lighten things up).
I am running a 700 Mhz laptop as a "server" with a full on LAMP stack, so it can be done on what some consider to be light hardware requirements.

---

