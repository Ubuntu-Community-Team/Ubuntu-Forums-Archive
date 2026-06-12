---
title: "[SOLVED] Problema amb disc extern convertit a intern"
date: 2007-10-30
forum: Catalan Team
---

### Post by manelolesa on 2007-10-30
He desmuntat un disc extern USB i l'he posat com intern.
Es un disc amb una partició NTFS, Ubuntu el veu però no mes puc accedir amb ROOT.
Abans quan estava endollat com USB  si que tenia accés.
He fet el NTFS-CONFIG i continuo sense accedir.

Salut i gracies

](*,)

---

### Post by manelolesa on 2007-10-31
[COLOR=Black]Ja está.
No es muntava al iniciar Ubuntu.
He afeit la linia /dev/sdb1[/COLOR] *[COLOR=Black] /media/disk2 ntfs-3g defaults,locale=ca_AD 0 0 [/COLOR]*[COLOR=Black]al fitxer /etc/fstab i andando.[/COLOR][I][COLOR=Black]

slt[/COLOR]
[/I]

---

