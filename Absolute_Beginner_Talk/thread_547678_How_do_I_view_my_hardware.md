---
title: "How do I view my hardware?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by Shoadow56 on 2007-09-10
I'm brand new to Ubuntu and I'm trying to figure out how to view my hardware so I can find the right wireless drivers for my laptop. Is there a certain command that you have to use in the terminal to view your hardware or an application for it?

---

### Post by Maestro23 on 2007-09-10
You can go to your Menu Bar:

System>> Prefs>> Hardware Info

*Will bring the Device Manager.

---

### Post by Shoadow56 on 2007-09-10
Works, thanks! I couldn't find it before, lol.

---

### Post by hyper_ch on 2007-09-10
or in the terminal enter
```

lspci

```
to list the pci devices or
```

lsusb

```
to list the usb devices

I know know parts of the name of the hardware component you could also do a grep:

```

lspci | grep nVidia

```
That will then list pci devices only that have "nVidia" in it.

P.S.: Remember "nvidia" isn't the same as "nVidia"

---

### Post by andreid on 2007-09-10
Or, to have the info formatted in html:
$sudo apt-get install lshw
$sudo lshw -html > my-hardware.html (yes, a single dash in -html)
$firefox my-hardware.html

---

