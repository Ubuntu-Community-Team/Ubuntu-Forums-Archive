---
title: "Sources.list"
date: 2007-10-24
forum: Catalan Team
---

### Post by prostata on 2007-10-24
Toquinejat la terminal he vist el munt d'arxius sources.list que tinc, mireu:

josep@josep-desktop:/etc/apt$ ls
apt.conf.d                        sources.list_backup_200709252045
apt.conf.save                     sources.list_backup_200709261120
secring.gpg                       sources.list.d
sources.list                      sources.list.distUpgrade
sources.list~                     sources.list.save
sources.list_backup_200709241238  trustdb.gpg
sources.list_backup_200709241722  trusted.gpg
sources.list_backup_200709241759  trusted.gpg~
sources.list_backup_200709241930
josep@josep-desktop:/etc/apt$ 

Son tots necessaris?
I si no quins puc esborrar?

Gràcies

---

### Post by papapep on 2007-10-24
Aquests crec que són els importants:


apt.conf.d
sources.list
sources.list.distUpgrade
secring.gpg
sources.list.d
trustdb.gpg
trusted.gpg

La resta de fitxers són còpies de seguretat i versions antigues dels originals.

---

