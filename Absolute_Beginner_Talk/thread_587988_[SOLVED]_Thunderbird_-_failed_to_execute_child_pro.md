---
title: "[SOLVED] Thunderbird - failed to execute child process, tried reinstall too."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-10-23
Could not launch application, no such file or directory.

i decided to go back to repo since updates seem to be coming through much quicker. So I uninstalled ubuntuzilla by following the instructions.

Firefox works fine but TB seems to have been borked some how.

I'm sure someone out there can untangle this one. Already tried reinstall.

---

### Post by realvz on 2007-10-23
This is because they renamed the program that runs Thunderbird

Just remove your old launcher from the titlebar, and drag the new one from the Applications > Internet menu to your titlebar.

---

### Post by philinux on 2007-10-23
Thanks for reply - already tried that. It must me a link or something.

---

### Post by realvz on 2007-10-23
can you post the output of when you try to launch thunderbird though terminal;

---

### Post by philinux on 2007-10-23
Very Weird
```
thunderbird
The program 'thunderbird' is currently not installed.  You can install it by typing:
sudo apt-get install thunderbird

```

However its installed in synaptic and if i browse to /var/lib/thunderbird and run thunderbird shell script it runs fine. There are no broken packages. The only odd thing is a file searchjplugins which says its link is broken it points to /usr/share/thunderbird/searchplugins but there is no such folder.

However this does not seem to stop the shell script from finding my config files etc.

---

### Post by philinux on 2007-10-23
Uninstalled it and then reinstalled.

---

