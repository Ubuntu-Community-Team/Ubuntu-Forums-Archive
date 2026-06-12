---
title: "How do i tell if desktop or server version installed?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by cavecanum on 2007-11-01
Someone  just handed me an ubuntu machine.  Looks cool.  But I'm now trying to figure out if the desktop or server version 7.10 has been installed.  (I need to make this machine into a server if it is not.)  So there must be some easy way to tell, but I can't find it.  Thanks.  --Katie

---

### Post by llamakc on 2007-11-01
You can check if the metapackage 'ubuntu-desktop' is installed in Synaptic (if you are in GNOME/KDE chances are high) or by the commandline.

In the terminal

```

dpkg -l | grep ubuntu-desktop

```

If you see THIS, the Desktop version is currently installed.

```

ii  ubuntu-desktop                             1.79                                      The Ubuntu desktop system

```

The version number may vary.

---

### Post by Pumalite on 2007-11-01
If you have a GUI, it's not a Server.

---

