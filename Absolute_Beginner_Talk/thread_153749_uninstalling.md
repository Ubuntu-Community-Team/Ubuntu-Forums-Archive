---
title: "uninstalling"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by veighjay on 2006-04-01
can you just delete a folder to uninstall a program?

mainly in relation to my previous thread:
[http://www.ubuntuforums.org/showthread.php?t=153717](http://www.ubuntuforums.org/showthread.php?t=153717)

thanks.

---

### Post by red_Marvin on 2006-04-01
It depends on how you installed it.
- With apt-get or synaptic:
sudo apt-get remove packagename
- With the program's own installing program/script:
Hopefully the install program/script has an uninstall option.
Elsewise it *might* work by deleting all files it installed, but it's not always
easy to track them down, and it's potentially unhealthy for your system.

---

### Post by Omnios on 2006-04-01
You might want to look into checkinstall in synaptic. Basicly it allows you to use the checkinstall command instead of the install command and builds a deb package that you can later uninstall with synaptic under local installs. Only draw back is it does not always work with every package.

---

### Post by veighjay on 2006-04-01
[QUOTE=red_Marvin]It depends on how you installed it.
- With apt-get or synaptic:
sudo apt-get remove packagename
- With the program's own installing program/script:
Hopefully the install program/script has an uninstall option.
Elsewise it *might* work by deleting all files it installed, but it's not always
easy to track them down, and it's potentially unhealthy for your system.[/QUOTE]

it's in reference to a program with its own install script. it does have an uninstall script, but i get error messages. if your interested, i've put them up here:
[http://www.ubuntuforums.org/showthread.php?t=153717](http://www.ubuntuforums.org/showthread.php?t=153717)

thanks....

---

