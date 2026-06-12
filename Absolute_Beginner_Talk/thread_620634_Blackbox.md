---
title: "Blackbox?"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by superbenny on 2007-11-22
Hey I just installed blackbox on my Kubuntu 7.04 laptop and when i update /home/(my name)/.blackbox/blackbox.rc it doesnt change when i restart x. for instance, I changed the first line, session.styleFile: /usr/share/blackbox/styles/grey to /home/bene/.blackbox/noble, where my theme is located and it doesnt change. i also changed the names of the desktops and those do not update. am i editing the wrong config file or just missing something entirely?

thanks

ben

---

### Post by Dr Small on 2007-11-22
Have you restarted blackbox after changing these settings ?

---

### Post by superbenny on 2007-11-22
logged out of kubuntu, restarted X, and logged back in.

---

### Post by Dr Small on 2007-11-22
How are you launching blackbox? From the GDM menu and selecting the Blackbox Session ?

---

### Post by superbenny on 2007-11-22
yes

i also shut down the computer for the night and turned it back on the next day and it still was just a simple gray theme.

---

### Post by Dr Small on 2007-11-22
Do you have a .blackbox folder ? I don't. My configuration file is called .blackboxrc in /home/drsmall/
If you theme file is located in /home/bene/noble, then in your .blackboxrc file, it should say:
```
session.styleFile:	/home/bene/noble
```

---

### Post by superbenny on 2007-11-22
yes, i do have a /.blackbox folder

i triple checked the path to make sure it was pointing to the correct file

---

