---
title: "Cannot Create Desktop Launcher"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by kmclar on 2007-05-28
I have Ubuntu 7.04 AMD64 running gnome.  Suddenly, the icons have dissappeared from my desktop launchers, and when I doubleclickthem, instead of the action, I get what looks like the definition of the launcher opened in gedit.  This now happens with new ones I create by asking the menu to "add desktop launcher" as well.

What has happened?

---

### Post by greybirds on 2007-05-28
Has anything (power failure, ungraceful shutdown, etc.) happened around the time you noticed the problem, or have you installed or uninstalled any software?

---

### Post by kmclar on 2007-05-28
I had installed then uninstalled beryl, then re-booted.

---

### Post by init1 on 2007-05-28
This must be a nautilus issue. Maybe you could reinstall it.

---

### Post by kmclar on 2007-05-28
No,

I reinstalled nautilus using synaptic, and I still get the same behavior.

---

### Post by greybirds on 2007-05-28
Nautilus and Gnome in general create a whole series of configuration files that are stored in various hidden folders and files in your home directory. They don't get changed or removed when you uninstall or reinstall the software itself. If Beryl fiddled with those settings, they wouldn't be reset necessarily later on.

You might get a better response if you post in the desktop effects forum. The users who read that are a lot more familiar with what changes Beryl makes to the system. Here's the link: [http://ubuntuforums.org/forumdisplay.php?f=223]("http://ubuntuforums.org/forumdisplay.php?f=223")

---

### Post by kmclar on 2007-05-28
Thanks!

I'll try there.

---

