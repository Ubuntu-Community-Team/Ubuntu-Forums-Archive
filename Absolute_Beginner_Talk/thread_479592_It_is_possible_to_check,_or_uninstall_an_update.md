---
title: "It is possible to check, or uninstall an update?"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Kosimo on 2007-06-20
Hi guys.

Simple question.
It is possible to see on a list all updates I installed on my system and then uninstall some of them if I want?

On Feisty.

Thks.

---

### Post by atria on 2007-06-20
I'm not sure whether if it is possible to list the recently updated package (perhaps check the logs?)

Remove packages with
```
sudo aptitude purge <packagename>
```

or with synaptic. Either will work fine.

[edit]
If you used aptitude for updates, the logs are stored in /var/log/aptitude
[/edit]

---

### Post by wonk-o-matic on 2007-06-20
In Synaptic there's a history to view.  I do things manually, so that's all the Gnome I know.

---

