---
title: "firefox and wicd GUI suddenly started segfaulting."
date: 2008-11-02
forum: Arch and derivatives
---

### Post by hessiess on 2008-11-02
like the title says, these applications suddenly started segfaulting when ran. only thing ive changed is running a system update yesterday, and everything was working fine afterwords... untill today that is.
       
```
[a@a-laptop ~]$ firefox

(firefox:8946): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",

(firefox:8946): Gtk-WARNING **: Unable to locate theme engine in module_path: "thinice",

(firefox:8946): Gtk-WARNING **: Unable to locate theme engine in module_path: "crux-engine",

(firefox:8946): Gtk-WARNING **: Unable to locate theme engine in module_path: "thinice",

(firefox:8946): Gtk-WARNING **: Unable to locate theme engine in module_path: "thinice",
Segmentation fault
[a@a-laptop ~]$ 
```

```
[a@a-laptop ~]$ /usr/lib/wicd/gui.py
/usr/lib/wicd/gui.py:1223: GtkWarning: Unable to locate theme engine in module_path: "clearlooks",
  self.wTree = gtk.glade.XML(gladefile)
/usr/lib/wicd/gui.py:1223: GtkWarning: Unable to locate theme engine in module_path: "thinice",
  self.wTree = gtk.glade.XML(gladefile)
/usr/lib/wicd/gui.py:1223: GtkWarning: Unable to locate theme engine in module_path: "crux-engine",
  self.wTree = gtk.glade.XML(gladefile)
refreshing...
Segmentation fault
```
anoyingly there is nothing perticually usefal in the terminal output, the GTK wornings have bean around for several months without any problems, GVim still works fine and that also displays the same errors.

Any help would be greatly appreceated.

as the arch forums are back, im moving the thread there.

---

