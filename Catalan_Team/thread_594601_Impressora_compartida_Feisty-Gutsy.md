---
title: "Impressora compartida Feisty-Gutsy"
date: 2007-10-28
forum: Catalan Team
---

### Post by shimoda on 2007-10-28
Hola!

M'he actualitzat a Gutsy des de Feisty i poc a poc he arreglat els problemets que he tingut... Però hi ha una cosa que no hi ha manera que em funcioni!

Tinc una impressora compartida des d'un altre ordinador (encara amb Feisty). 
Abans els dos ordinadors la compartien sense problema. Des que m'he passat a Gutsy, no em detecta la impressora compartida de l'altre ordinador.

En canvi, les carpetes compartides segueixen funcionant a la perfecció. 
Tot està compartit a través de samba, i no he canviat res de la configuració (simplement he actualitzat).

Què podria ser?

Aquest és el smb.conf de l'ordinador amb l'impressora (el Feisty)

```
[global]
workgroup = XARXA
server string = Samba server
security = user
log file = /var/log/samba/smb.txt
encrypt passwords = true
wins support = no
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700
[CarpComp]
path = /home/josep/CarpComp
available = yes
browsable = yes
public = no
guest ok = no
writable = yes
valid users = josep
```

Alguna idea? He provat de posar public=yes però la impressora segueix sense aparèixer...

---

### Post by papapep on 2007-10-28
Això és tot el fitxer de configuració?? Enganxa'ns la resta, si us plau.

---

### Post by shimoda on 2007-10-28
gràcies per respondre tan ràpid papapep!

Doncs sí, aquest és el smb.conf sencer, i amb feisty funcionava perfectament...:roll:

---

### Post by jodufi on 2007-10-28
A mi em va passar el mateix, tenia un ordinador amb Feisty i l'altre amb Gusty i no em va funcionar.
Ara tinc dos ordinadors amb Gusty i em funciona perfectament.
Simplement he activat el samba i he utilitzat la nova eina de gestió d'impressores, que li he dit que busqui impressores mitjançant samba i l'ha trobat ràpidament.

Salut

---

