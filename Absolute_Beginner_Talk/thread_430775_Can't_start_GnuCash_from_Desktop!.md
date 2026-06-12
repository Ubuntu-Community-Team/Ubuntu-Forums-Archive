---
title: "Can't start GnuCash from Desktop!"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-05-02
I've managed to load GnuCash into Daper and it works - but only if I start it from Terminal with the command sudo gnucash.

If I make a launcher on the desktop with the command gnucash - nothing happens.  Also nothing happens if I use sudo gnucash in the launcher unless I've previously launched it in Terminal.

Can anyone guide me as to what I should do so that a launcher will start the program and also not use sudo.

Thanks

David

---

### Post by Seisen on 2007-05-02
How did you install gnucash, when I installed it I ended up with a menu icon that i could click on.

---

### Post by David Floyd on 2007-05-02
I installed following the instructions here: [http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Accounting_Application_.28GnuCash.29](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_Accounting_Application_.28GnuCash.29)

So there is a menu item, which when clicked, nothing happens.

When I enter gnucash in Terminal I get an error message:
```

~$ gnucash

Gnome-ERROR **: Could not set mode 0700 on private per-user Gnome directory </home/david/.gnome_private> - aborting

aborting...
Aborted
~$

```

I changed the Launcher to sudo gnucash - but still nothing happened.

When I enter sudo gnucash in a terminal the GnuCash runs - after I've entered my password in the terminal (which is a bit of a pain).  I would much prefer to click a launcher or a menu item as with other programs.  Any help appreciated.

Thanks,
David

---

