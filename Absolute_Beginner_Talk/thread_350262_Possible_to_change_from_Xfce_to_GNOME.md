---
title: "Possible to change from Xfce to GNOME?"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by Genotrius on 2007-01-31
Is it possible to change from Xubuntu to Ubuntu without reformatting and loosing all of your data?

---

### Post by meng on 2007-01-31
Sure, drop to terminal:
sudo apt-get install ubuntu-desktop

---

### Post by Genotrius on 2007-01-31
Seriously? That's it?

---

### Post by mcduck on 2007-01-31
> **Genotrius said:**
> Seriously? That's it?
Yes, that's it. After doing that you can click the 'session' button in the login screen and Gnome will be there :)

Of course you don't have to use terminal, you can install the package with Synaptic too.

Same thing goes for kubuntu-desktop (KDE).

---

### Post by Brunellus on 2007-01-31
> **Genotrius said:**
> Seriously? That's it?
yup.  if you're a glutton for punishment, try doing it in slackware without package management.

---

### Post by Genotrius on 2007-01-31
> **Brunellus said:**
> yup.  if you're a glutton for punishment, try doing it in slackware without package management.

No thanks, I'll use apt-get! I think I'll install KDE too, while I'm at all of this...
Hey, I'm using Edgy, but so I don't have to ask later, what should I do about all this when it comes time to update?

---

### Post by IYY on 2007-01-31
I'd suggest to use aptitude instead of apt-get. It's the exact same thing, but if you later want to remove the package (due to cluttered menus, for instance) it'll be easier.

---

### Post by Genotrius on 2007-01-31
Uh oh... It didn't give me the option to start a GNOME session. Just 
Last Session, 
Xfce session, 
System Default Session, 
Failsafe GNOME, 
and Failsafe Terminal,
like usual. Why could that be?

---

### Post by mcduck on 2007-01-31
> **Genotrius said:**
> Uh oh... It didn't give me the option to start a GNOME session. Just 
Last Session, 
Xfce session, 
System Default Session, 
Failsafe GNOME, 
and Failsafe Terminal,
like usual. Why could that be?

Hit ctrl-alt-f1 to get to console, log in and run 'sudo /etc/init.d/gdm restart'. That should reload GDM that handles the graphical log-in.

(or just reboot. But that wouldn't be as fun as reloading GDM, would it? ;) )

---

### Post by Genotrius on 2007-01-31
It seems it was a problem in the installation. I did it using Synaptic, and everything was fine.
I'm in GNOME right now! Sure looks interesting. Very orange...

---

