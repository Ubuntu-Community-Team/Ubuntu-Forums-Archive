---
title: "shutting down x server"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by pug_205 on 2006-04-24
I'm running a webserver, and I want to totally shut down the GUI. When, I'm in x server, and I press cntrl + alt + bs it shuts down, but then pops right back up again telling me to log in. How do I shut it down for good?

---

### Post by tseliot on 2006-04-24
[QUOTE=pug_205]I'm running a webserver, and I want to totally shut down the GUI. When, I'm in x server, and I press cntrl + alt + bs it shuts down, but then pops right back up again telling me to log in. How do I shut it down for good?[/QUOTE]
CTRL+ALT+F1
then log in (if required)
sudo /etc/init.d/gdm stop
(or sudo /etc/init.d/kdm stop if you use KDM)

---

### Post by pug_205 on 2006-04-24
Wow, that certainly was a prompt response.  :o 

Thanks alot. :-D

---

### Post by steve.horsley on 2006-04-24
[QUOTE=pug_205]Wow, that certainly was a prompt response.  :o 

Thanks alot. :-D[/QUOTE]
Actually, by this forum's standards, it was positively tardy.;)

That only disables GDM once of course, so it'll still be there after a reboot. If you want to disable it permanently, it's probably easiest if you install bum (boot up manager) from synaptic, then use that to disable gdm. 
1) use **startx** to get the gui working again temporarily
2) enable multiverse and universe repositories in synatic
3) install bum
4) do **killall gnome-panel** to update bum into the menus
5) do System->Administration->Boot Up Manager and disable gdm there
6) logout to bring X down again

---

