---
title: "amule y disc dur"
date: 2007-08-20
forum: Catalan Team
---

### Post by muleta on 2007-08-20
Acabo d'instal·lar l'amule i sembla que me'n estic sortint prou bé de configurar-ho tot. Ja he introduït els fitxers temp però ara no sé com farcir la carpeta Incoming.

Vaig extreure la que tenia a l'emule i l'estic copiant a l'escriptori perque no sé on posar-la. No trobo cap procediment automatitzat que m'ho faciliti desde amule ni desd Ubuntu. 

Había pensat en arrossegar-la fins a l'interior de Incoming d'amule però no trobo la manera de poder veure les carpetes.

Tampoc no sé com trobar totes les carpetes del disc dur, de la part no particionada, com mirar l'espai que em queda lliure al disc, com netejar-lo, etc.

He de dir que m'estreno avui a UBUNTU i ho veig tot tan diferent que em desoriento. :confused:

---

### Post by CarlesOriol on 2007-08-21
Per veure el contingut del disc dur pots usar la eina baobab.

Aplicacions -> Accesoris > Analitzador de l'ús de disc

Tens el contingut de l'amule a la carpeta oculta .aMule ( /home/elteunom/.aMule ) a la teva carpeta home d'usuari. Els arxius de descarrega temporal de l'altre sistema crec que no et funcionaran.

---

### Post by muleta on 2007-08-21
Gràcies, Carles, ja ho he vist tot en forma de gràfics en escanejar les carpetes.

Ara em queda per resoldre com introduïr l'antiga carpeta Incoming de l'emule o els seus fitxers a la nova Incoming de l'amule per a poder-los compartir.

Tampoc no sé com obrir la nova Incoming per extreure'n els fitxers que hi vagin entrant.

---

### Post by guillemsola on 2007-08-21
Hola

Potser el teu problema és que no tens activa l'ordre de veure fitxers ocults al navegador de fitxers. El punt de la carpeta .aMule indica que és oculta. La trobaras al menú Llocs - Carpeta d'inici.

Si ja la veus només tens que buscar a dins d'aquesta la carpeta Incoming i copiar els arxius que vulguis compartir.

El sistema de fitxers en linux és diferent al de windows però l'emule i l'amule s'entenen perfectament. De fet jo vaig fer servir durant força temps les mateixes carpetes per emule i amule pels temporals i Incomings sense cap problema.

Salut!

---

### Post by CarlesOriol on 2007-08-21
Ctrl + H mostra els arxius ocults.

---

### Post by muleta on 2007-08-21
OSTRES... 

WOOOOOOOOW...

Al·lucino!!. Això és genial. Ja ho tinc tot a la vista i ho he pogut resoldre.

Abans entrava a Inici i no hi véia res.

M'estic animant, potser continoaré amb Ubuntu, ja volia entornar-me a Win.

A través d'els forums d'amule he trobat una configuració recomanada que m'ha permès passar d'una descàrrega de 2 (amb la configuración per defecte) a 150. M'estava deprimint, abans.

Crec que em quedo, ja aniré aprenent coses, de mica en mica.

Gràcies a tots dos.

---

### Post by guillemsola on 2007-08-21
Pensa que totes les coses noves requereixen un aprenentage. Com que estas acostumat  al windows l'ubuntu set fa pesat, si no tires la tovallola veuras que d'aquí a un temps el windows el trobaràs mancat de recursos per solucionar les coses.

Ànim!

---

### Post by albert-I on 2007-08-23
M'ho pots passar :)
això de la velocitat i el fet que de tant en tant em desaparegui.:confused::confused:> **muleta said:**
> 

A través d'els forums d'amule he trobat una configuració recomanada que m'ha permès passar d'una descàrrega de 2 (amb la configuración per defecte) a 150. M'estava deprimint, abans.


---

### Post by papapep on 2007-08-23
No sé si és el que la Muleta vol dir, però per a obtenir bons ratios de descàrrega l'únic que has de fer és obrir el port 4662 TCP tant al teu router (i dirigir-lo al teu ordinador), com al teu ordinador si tens el tallafocs activat, un cop fet el qual, et permetrà que els servidors et donin una ID alta (preferent). També estaria bé obrir i redirigir el 4672 UDP. 

No sé si m'he explicat.

---

### Post by muleta on 2007-08-23
No, no em referia a això que t'indica en Papapep, si bé és fonamental.

Jo ho havia fet, fins i tot provant altres ports que no estéssin tan saturats i res, només baixava un màxim de 2.

Ara no ho trobo però recordo que a [http://forum.amule.org/](http://forum.amule.org/) hi vaig trobar una fórmula per saber quines velocitats de càrrega i descàrrega has de configurar en funció de la velocitat de la teva connexió.

Va ser decisiu. Amb tot, encara no he obtingut les baixades del emule. Suposo que també és qüestió d'anar-lo coneixent i provant.

---

