---
title: "Setting static IP in Xfce"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by AsYouWish on 2006-07-19
Is there a graphical interface? How is it done from the command line?

I could also load Gnome, I know theres a graphical whatnot there, although Im still not entirely sure which IP to put where.

Im behind a router, just looking for a static IP over the internal network (so I dont have to keep re-maping the samba share from my xp box).

Thanks

---

### Post by 5-HT on 2006-07-19
[quote=AsYouWish]Is there a graphical interface? [/quote]
You can install xubuntu-system-tools.
 [quote=AsYouWish]How is it done from the command line? [/quote]
You can edit /etc/network/interfaces.
To view the syntax and options for the configuration file, please refer to the manual page: ```
 man interfaces 
``` 
[quote=AsYouWish]
I could also load Gnome, I know theres a graphical whatnot there, although Im still not entirely sure which IP to put where.

Im behind a router, just looking for a static IP over the internal network (so I dont have to keep re-maping the samba share from my xp box). [/quote]

You could configure a static IP for Ubuntu and have the router assign it to the pc, but that may not be necessary. What about just configuring the router to bind a specific IP to your MAC (should be an option in the router's config if available) and keep Ubuntu configured for DHCP? 

For both methods you'll need to get the router to assign a specific IP to your box, but so long as that is occurring there shouldn't be a need to set Ubuntu up for a static address as it'll only use the one it's assigned.

Hope that helps.

---

### Post by AsYouWish on 2006-07-19
Got it. Thanks a bunch.

---

