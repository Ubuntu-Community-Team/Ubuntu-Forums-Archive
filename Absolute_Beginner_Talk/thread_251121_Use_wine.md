---
title: "Use wine"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by jbumgar on 2006-09-05
I'm new to linux and Ubuntu.  I installed wine using synaptic.  But I don't see it in my applications list at the top. How would I add it to the applications list?  I tried the add/remove but didn't wine listed.

---

### Post by DSn0wMan on 2006-09-05
In my experience I have only run it from the command line. 

For instance: If you wanted to install something from a cdrom you would type

```

sudo wine /media/cdrom

```
assuming that "/media/cdrom" is the path to your cd.

You can type:
```

man wine

```
To read the help files for the wine command

---

### Post by orb9220 on 2006-09-05
wine is a command not so much an application. To config wine hit alt-f2 and enter winecfg or enter in a terminal.

To install an app like dvdshrink you would open a term and enter:
sudo wine dvdshrink32.exe and follow the install procedure.
Wine creates a phony or fake c: windows directory tree to install stuff to.
After installing app you need to do the winecfg thing agian and click on add app button to configure the app.

Hope this helped a little.

---

