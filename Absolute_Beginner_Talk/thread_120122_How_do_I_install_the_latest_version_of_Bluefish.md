---
title: "How do I install the latest version of Bluefish?"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by stroopwafel on 2006-01-20
I installed bluefish using sudo apt-get install bluefish.

This doens't give me the latest version though. How do I install the latest version after downloading a rpm or tar.gz file?

---

### Post by morphodone on 2006-01-20
i have bluefish installed with apt-get and it's the latest version 1.0.4

---

### Post by stroopwafel on 2006-01-20
[QUOTE=morphodone]i have bluefish installed with apt-get and it's the latest version 1.0.4[/QUOTE]
I just removed the package and reinstalled it and it. It ended with these messages:
```
Unpacking bluefish (from .../bluefish_1.0.1-0ubuntu3_i386.deb) ...
Setting up bluefish (1.0.1-0ubuntu3) ...
***
* Updating MIME database in /usr/share/mime...
***

```

How come I get an older version?

I typed:```
sudo apt-get install bluefish
```

---

### Post by dueY on 2006-01-20
If you still have the rpm file you can use ALIEN to install it.
```
sudo alien -k [name of rpm file.rpm]
```

---

### Post by morphodone on 2006-01-20
[QUOTE=stroopwafel]How come I get an older version?[/QUOTE]

you need to enable backports according to my synaptic...

---

### Post by stroopwafel on 2006-01-21
[QUOTE=morphodone]you need to enable backports according to my synaptic...[/QUOTE]
I enabled the backports and now it's working: THANKS.

---

