---
title: "Executa amb usuari normal script que demana password de ROOT"
date: 2007-10-27
forum: Catalan Team
---

### Post by manelolesa on 2007-10-27
Tinc un script per connectar a Internet amb modem USB.
Cada vegada que l'executo em demana el pasword de ROOT i voldria executar-lo sense que me'l demanes. Suposo que aixó s'arregla donan permissos d'execució al script pero com fa servir un dispositiu USB crec que es te que fer algo mes , no ?
:confused:
slt

---

### Post by orestesmas on 2007-10-27
Per executar un script amb permisos de root has d'activar el bit SUID dels permisos de l'script. Això es fa (suposant que ja és executable) amb l'ordre

sudo chmod u+s <nom de l'script>

Vés molt amb compte amb això. Ara, qualsevol usuari que tingui permisos per executar aquest fitxer podrà fer com a root tot allò que s'hagi estipulat dins del fitxer. Algunes causes de perill potencial són:

- Hi ha un error en aquest script que fa coses que tu no havies previst
- L'script té permisos d'escriptura per tothom: això permet que qualsevol el modifiqui i li afegeixi instruccions potencialment perilloses que s'executaran amb privilegis d'administrador.

Quant a la pregunta de si s'ha de fer alguna cosa més perquè s'usa un dispositiu USB, doncs no ho sé: tot dependrà de com hagi detectat el sistema el mòdem USB i quins permisos li hagi assignat el sistema udev.

---

### Post by manelolesa on 2007-10-27
No calien permisos de execució.
El scipt llençava tres comandes amb sudo.
Li he tret els sudo i no he tingut cap problema per executar-lo. Suposo que els sudo deuen ser per que no es connectin a Internet tots els  usuaris.

slt

---

### Post by kukat on 2007-10-29
El sudo està a Ubuntu per a fer tarees de Administrador sense ser-ho. Crec que posant-lo una vegada a un script ja en deus de tindre prou. No te res a veure amb conectar-se a Internet. ;)

---

