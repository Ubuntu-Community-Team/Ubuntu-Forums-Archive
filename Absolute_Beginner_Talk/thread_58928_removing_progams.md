---
title: "removing progams"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by evansa4 on 2005-08-22
Hi guys i got the antivirus and it out of date how do i remove it

---

### Post by bored2k on 2005-08-22
[QUOTE=evansa4]Hi guys i got the antivirus and it out of date how do i remove it[/QUOTE]
 What antivirus ? How did you install it ?

---

### Post by evansa4 on 2005-08-22
via this web site [http://www.ubuntuguide.org/#installclamav](http://www.ubuntuguide.org/#installclamav)

---

### Post by Kvark on 2005-08-22
This command will cause apt-get to remove clamav:
```
sudo apt-get remove clamav
```

If you perfer the graphical alternative synaptic, then search for clamav in synaptic, click the checkbox next to clamav and select mark for removal in the menu that pops up.

---

