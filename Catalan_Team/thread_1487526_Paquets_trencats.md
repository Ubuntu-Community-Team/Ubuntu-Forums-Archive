---
title: "Paquets trencats"
date: 2010-05-19
forum: Catalan Team
---

### Post by jamasca on 2010-05-19
Hola

He actualitzat el Hardy Heron amb el Lucid Lynx. El problema és que tenc un paquet trencat, concretament el flashpugin. Vaig a Synaptic per reparar el paquet i me diu

"El paquet està en un estat molt dolent e inconsistent - el tindreu que  reinstal·lar abans d'intentar desinstal·lar-lo"

Intento reinstalar-ho però no me deixa. Me diu el mateix, que  tenc que reinstalar. I no sé que fer.  Soc principant

Salutacions

---

### Post by wgarcia on 2010-05-19
Obre una terminal de comandes (Aplicacions -> Accessories -> Terminal)

Entra la següent línia i clica "intro":

ls /var/lib/dpkg/info/flashplugin-nonfree.prerm

Si surt una línia que diu 

/var/lib/dpkg/info/flashplugin-installer-prerm

Segueix els següents passos, entrant cada línia a la terminal i prement "intro":

1.

sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm
sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree

Això hauria d'aturar tots els errors referents a aquest paquet 


2.

- Obre Sistema -> Administració -> "Software sources" (no sé com està traduït, el meu sistema està en anglès) i a la pestanya "Other software" (és la segona pestanya, tampoc sé com està traduït) mira si està habilitat "Deshabilitat per actualitzció a Lucid, Medibuntu" o alguna cosa així. Si no està escollit, escull'ho.
- Obre Sistema -> Administració -> Gestor de paquets synaptic i busca flashplugin-installer i instal·la'l.

---

### Post by jamasca on 2010-05-19
Moltes gràcies wgarcia . Ha funcionat perfectment. Si no és abusar massa me podries dir què signifiquen aquests comands. Més que res per si me torna a passar una cosa semblant

---

### Post by wgarcia on 2010-05-19
Els primers "ls" era per veure si tenies un arxiu remanent de l'actualització que t'impedia actualitzar aquest paquet. 

El que comença amb "rm" remou aquet arxiu, un cop comprovat que sí que hi és (si ls hagués dit "no trobat" no hauria estat aquest problema). 

Els que comencen amb "dpkg" remouen completament el paquet en qüestió. 

(Suposo que li vas afegir "sudo" endavant d'algunes comandes, ara he editat la meva resposta perquè "sudo" et dóna privilegis per fer algunes coses al sistema)

Recorda també de canviar el tema d'aquest fil a "Solved" amb el menú "Thread Tools" a dalt d'aquesta pàgina.

---

