---
title: "Boot only to command prompt"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by Harley_Dog on 2007-03-24
Could someone please clarify this process for me.  I have Ubuntu running as a virtual machine on an old desktop.  I would like to minimize the CPU/RAM load buy not booting to the desktop, a command prompt is fine.  Can someone please explain how to do this.  Also, if I need the desktop, how can I load it, then unload.

Thanks
Harley

---

### Post by schwascore on 2007-03-24
First install BUM (Boot Up Manager)

```
sudo apt-get install bum
```

It will show up under System --> Administration

Open it up and turn off Gnome Display Manager, that should work. To turn GDM back on all you have to do at the command line is this:

```
sudo /etc/init.d/gdm start 
```

---

