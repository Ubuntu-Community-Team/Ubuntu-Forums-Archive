---
title: "Just a quick question."
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by Sp00ne on 2006-10-01
Whenever i close my laptop screen, it goes to hibernate, where is the option to change this?

I feel stupid as hell.

---

### Post by reldruH on 2006-10-01
In KDE it's in K Menu > System Settings > Laptops and Power > Laptop Battery > Button Actions. Kind of difficult to find, but that whole section is really great. I hear even better support for hibernation and suspending is coming in Edgy Eft. I don't know where the same things would be in Gnome, though.

---

### Post by Sp00ne on 2006-10-01
Thanks for that.

---

### Post by Sp00ne on 2006-10-01
Sorry for the double post, but for some reason when i do "alt-ctrl-del" i only get 4 choices: lock screen, hibernate, switch user and log out.

There is no "shutdown" choice for some random reason.

If anyone has any ideas on how to fix it, that'd be tits.

---

### Post by aysiu on 2006-10-01
Are you using GDM as your default display manager? If you're not sure if it's GDM or KDM, paste this command into the terminal: ```
cat /etc/X11/default-display-manager
```

---

### Post by Sp00ne on 2006-10-01
It came out with "/usr/sbin/gdm"

---

### Post by aysiu on 2006-10-01
That's the problem. If you're using GDM as your default display manager, you won't be able to shut down directly from KDE.

You should change it to KDM. ```
sudo aptitude update
sudo aptitude install kdm
```

---

### Post by devils_casper on 2006-10-01
Hi !

is it Kubuntu ??? 
if yes, then no need to install KDM. its already there. you have to make it default.

sudo dpkg-reconfigure kdm

select kdm from gdm/kdm option.




casper

---

