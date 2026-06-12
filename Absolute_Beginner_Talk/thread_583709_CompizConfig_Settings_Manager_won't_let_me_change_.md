---
title: "CompizConfig Settings Manager won't let me change any of the settings"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Ulfursson on 2007-10-20
I installed the CompizConfig settings mannager as intructed in another thread (through Applications -> Add/Remove). Once I open it, it won't let me enable any of the effects - the check boxes next to them are greyed out and I can't check them. What am I doing wrong?

---

### Post by Ulfursson on 2007-10-20
Um, help?

---

### Post by Haise on 2007-11-03
I believe this is a bug where the user doesn't have permissions to edit their compiz settings.  I tried doing this:

```

sudo chmod 777 csm

```

With the hopes that maybe it would magically let me have control over compiz without jumping to root every time, but no luck.  The only solution I've been able to come up with was to run it as root, which you can do via:

```

sudo ccsm

```

Unfortunately, for this workaround to have any effect on your desktop settings, you have to run your entire userspace in root, which is completely unacceptable for me.  This is the main reason that I switched over to Sabayon, which is a gentoo-based distro available at [http://www.sabayonlinux.org/](http://www.sabayonlinux.org/).  Their integration of compiz is much more complete and comprehensive, and includes compizconfig-settings-manager by default, as well as an easily accessible icon in the notification area where you can change your settings/windowmanager.

---

### Post by rickycodie on 2007-11-03
try reinstalling it and if that doeswn't work then try installing gnome-settings-manager

---

### Post by Haise on 2007-11-03
No dice for me.  I ran remove --purge on compiz, it's libraries, and compizconfig-settings-manager, reinstalled it.

Still can't change my compiz settings.  I wish I knew more about how compiz handled permissions so I could hunt down whatever file governs it and change that...

---

### Post by Haise on 2007-11-03
Found my problem; the configuration files (located in ~/.config/compiz/compizconfig/) weren't owned by me; they were owned by root for some reason.  Changing the attributes let me change my settings.

---

### Post by 5oak on 2007-12-06
I have the exact same problem. Changing attributes to the config file (I see just one config file) didn't help. Options are still 'greyed out'.

Edit: make sure the box saying 'automatically sort plugins' is checked and everything works again, at least here it does.

---

### Post by khendar on 2008-04-02
> **5oak said:**
> 
Edit: make sure the box saying 'automatically sort plugins' is checked and everything works again, at least here it does.

Thankyou! That's been bugging me for hours!

---

