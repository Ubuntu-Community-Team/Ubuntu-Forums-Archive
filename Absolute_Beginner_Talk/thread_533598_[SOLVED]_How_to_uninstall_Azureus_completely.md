---
title: "[SOLVED] How to uninstall Azureus completely?"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-08-24
I've had a problem with Azureus, it crashed during the night and now refuses to work at all.  I've tried Add/Remove to reinstall but it still won't work. 

How do I remove all traces of it from everywhere so I can install a truly fresh copy?

---

### Post by felicity on 2007-08-24
You might try..

```
sudo apt-get purge remove azureus
```

update your locate database with
```
sudo updatedb
```

then locate the folders/files that the config files are in

```
locate azureus
```

then delete them.

---

### Post by aberadam on 2007-08-24
Thanks, but: 

> adam@adam-desktop:~$ sudo apt-get purge remove azureus
E: Invalid operation purge


---

### Post by swoll1980 on 2007-08-24
take the remove out

---

### Post by Arwen on 2007-08-24
Maybe it's :sudo apt-get --purge  azureus  ??

---

### Post by aberadam on 2007-08-24
Thanks, but: 

> adam@adam-desktop:~$  sudo apt-get purge azurerus
E: Invalid operation purge


Hahahah, this is funny... but what's going on, how come it won't work?

---

### Post by swoll1980 on 2007-08-24
just go to synaptics and select it for complete removal

---

### Post by aberadam on 2007-08-24
Oh I spelt the program name wrong... damn.

---

### Post by aberadam on 2007-08-24
Haha: 

> adam@adam-desktop:~$  sudo apt-get purge azureus
E: Invalid operation purge


---

### Post by swoll1980 on 2007-08-24
or try sudo aptitude purge azureus or sudo apt-get remove purge  one of these has to work

---

### Post by aberadam on 2007-08-24
Brilliant, thanks Bloor75.

---

### Post by aberadam on 2007-08-24
Thanks for the full rundown felicity.

---

