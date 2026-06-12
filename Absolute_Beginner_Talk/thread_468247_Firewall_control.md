---
title: "Firewall control"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-06-08
I know that ubuntu comes default with all ports closed, but how can i open them again? (at least temporarily)

---

### Post by starcraft.man on 2007-06-08
> **Tyke91 said:**
> I know that ubuntu comes default with all ports closed, but how can i open them again? (at least temporarily)

Easy. Firestarter is what your looking for, its a GUI for the IPtables. 

Enable universe in your sources files. System > Administration > Software Sources. Enable the universe one on the main screen.

Then, just open a Terminal (Applications > Accessories > Terminal) and type this in:

```
sudo aptitude install firestarter
```

Then you can start it up from the menu I think. Have fun :). More [info on it here]("http://www.fs-security.com/"), including documentation. It's fairly straight forward to use the GUI.

---

### Post by Shazaam on 2007-06-08
Good info for Firestarter here...
[http://ubuntuforums.org/showthread.php?t=187899&highlight=krazypenguin+firestarter](http://ubuntuforums.org/showthread.php?t=187899&highlight=krazypenguin+firestarter)

---

### Post by steve.horsley on 2007-06-08
The reason all the ports are closed is that there are no services listening for incoming connections. By default, the firewall isn't blocking anything.

If you want to "open a port", all you need to do is start a server process that listens on that port.

---

