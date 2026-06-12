---
title: "No mouse or keyboard input available"
date: 2008-12-05
forum: Arch and derivatives
---

### Post by benerivo on 2008-12-05
I've just tried to install arch with kde fron the default repositories, but i think because arch now uses a more recent version of xorg, it has caused a little problem on my machine (i installed arch the same way successfully last week).

From a fresh install, there is no keyboard or mouse response from either the login screen or the window manager. Even pressing Num Lock or Caps Lock, fails to light up the relevant lights on the keyboard. I have tried using both the nvidia driver and the nv driver. I haven't tried the following yet, but is this possibly a "downgrade" situation where i should reinstall an earlier version of xorg.

---

### Post by fwojciec on 2008-12-05
Are you sure you installed a driver for keyboard/mouse?  Like xf86-input-evdev package, for example?  It is not installed by default, I think.

Another thing to check out is this wiki page, which describes the new feature of xorg -- device autodetection and hotplugging using hal: [http://wiki.archlinux.org/index.php/Xorg_input_hotplugging]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging")

---

### Post by benerivo on 2008-12-05
Thanks fwojciec, those links were helpful, but i'm still having problems. My /etc/rc.conf is 'unreadable' from a live cd, which just sees the content as```
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
```I tried the extra package installations that you suggested, but they didn't fix it (even from a boot up straight to a console i had no keyboard), so i'm just going to reinstall linux on this machine.

---

### Post by fwojciec on 2008-12-06
rc.conf should *definitely* not look like this -- it looks like it's gotten corrupted somehow.  No idea what would cause it to look like this.  You can try reinstalling initscripts package and see if this will fix it.

---

