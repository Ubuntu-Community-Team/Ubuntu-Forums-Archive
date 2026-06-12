---
title: "DropBox - 2 Instancias"
date: 2010-11-23
forum: Catalan Team
---

### Post by tanreb20 on 2010-11-23
Bones!

Tinc instalat el dropbox posat a la carpeta /meda/DADES/Dropbox /particio compartida amb windows)

He intentat fer aquest manual [http://wiki.dropbox.com/TipsAndTricks/MultipleInstancesOnUnix](http://wiki.dropbox.com/TipsAndTricks/MultipleInstancesOnUnix) per tal de poder tenir 2 instancies de Dropbox obertes, ja que m'interessa molt tenir-los

En un primer moment ha funcionat, pero no entenc molt bé xq ara no i no hi ha manera de fer-ho anar.

La segona instancia la tinc a /media/DADES/IMPRESSORA/Dropbox.

Algú el fa servir? Sap com s'0ha de fer? Xq m'estic agobiant ya!!!

PD: L'error que em dona al intentar executar la segona instancia és:

```
alorma@Hogwarts:~$ HOME=/media/DADES/IMPRESSORA/Dropbox/ /usr/bin/dropbox start -i
Starting Dropbox...Traceback (most recent call last):
  File "/usr/bin/dropbox", line 259, in handle_ok
    self.dont_show_again_align.hide()
AttributeError: 'DownloadDialog' object has no attribute 'dont_show_again_align'
Done!

```

---

### Post by tanreb20 on 2010-11-23
És igual, he decidit fer servir només un!

---

