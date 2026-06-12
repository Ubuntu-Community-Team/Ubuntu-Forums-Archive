---
title: "Paràmetres de xarxa no es desen"
date: 2007-08-25
forum: Catalan Team
---

### Post by guillemsola on 2007-08-25
Hola

Tinc un problema amb la xarxa i el portàtil. Vaig a sistema-administració-xarxa pestanya general i poso el meu nom del domini pq sinó no hem troba els altres pcs de la xarxa. 

Doncs resulta que la configuració no es desa quant reinicio. He provat creant una ubicació i aquesta es crea però no la carrega per defecte.

Així doncs cada vegada he d'accedir a la configuració de la xarxa per configurar el domini.

He de dir que en el pc fixe això no hem passa.

Què pot estar malament?

Gràcies!

---

### Post by lluisanunez on 2007-08-26
Com et connectes amb el portàtil? Amb el Network Manager i wifi? Tens activat  "Enable roaming" potser?

---

### Post by guillemsola on 2007-08-26
Sí, em conecto amb el portàtil i amb el NetworkManger 0.6.4.

Suposo que enable roaming es referix a habilita el mode itinerant, i si és així, si que el tinc activat. Però si desactiva això serà capaç de conectar-se a totes les wifi que faig servir habitualment sense problemes?

I ja que hi som cada vegada em pregunta la clau del gestor d'anells de clau. Vaig llegir que havia de baixar l'última versió del PAM keyring  i la vaig compilar. Després havia d'editar /etc/pam.d i afegir unes linies. Però sempre em pregunta la clau. No hi ha una manera més senzilla?

Salut!

---

### Post by lluisanunez on 2007-08-26
A mi m'havia passat el Network Manager m'esborrava les configuracions de xarxa quan el posava en "mode itinerant". Ara, però, no em passa. 
Mira a Sistema >> Administració >> Xarxa >> Hosts, si tens associat el nom del teu ordinador a l'adreça 127.0.0.1

---

### Post by guillemsola on 2007-08-27
No t'he acabat d'entendre. A veure, a la meva llista de host hi ha

127.0.0.1 localhost
127.0.1.1 nom_de_la_maquna.DOMINI

He provat a canviar 127.0.0.1 per nom_de_la_maquina.DOMINI en comptes del localhost, però segueix igual.

Per exemple jo vull posar un nom de domini a paràmetres de xarxa però aquest nom no es desa i l'he de posar cada vegada que arrenco el portàtil.

Hi ha algun arxiu de configuració que pugui modificar i em salti el menú del gnome?.

gràcies

---

### Post by lluisanunez on 2007-08-27
Uf, a mi em sembla correcte com ho tens (127.0.0.1 i 127.0.1.1 són alies). L'arxiu on es guarda el nom de host és /etc/hostname, mira si el pots editar i si networkmanager el reescriu després de connectar-te --sé que reescriu el fitxer /etc/resolv.conf
Ho sento però no en sé més...

---

