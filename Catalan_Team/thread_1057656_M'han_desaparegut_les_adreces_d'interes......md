---
title: "M'han desaparegut les adreces d'interes....."
date: 2009-02-02
forum: Catalan Team
---

### Post by manelfus on 2009-02-02
Hola  aixi com sona :M'han desaparegut les adreces d'interes... i tambe la fletxa per tirar-hi enrere del google.
  Cada vegade que he de buscar algo he de escriure-ho de nou.
La causa el haver-hi ficat un  adaptador per veure un planol ,la questio es que no se com tornar-hi a tindre les adreces sense haver-hi de  reinstalar el firefox.
 he estat intentan trobar la solucio pero ... res de res
Tambe hem surten aquests errors a la consola d'errors del firefox(un dels molts):

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE) [nsIJSCID.getService]"  nsresult: "0x80570016 (NS_ERROR_XPC_GS_RETURNED_FAILURE)"  location: "JS frame :: file:///usr/lib/xulrunner-1.9.0.5/modules/utils.js :: anonymous :: line 96"  data: no]  



 si algu sap com poguer solucionar-ho l'hi estaria molt agraït  merces 

salut  
 Manel

---

### Post by jerec on 2009-02-02
El directori del firefox es troba a aquesta ruta (el directori del final pot ésser diferent, ja que el crea aleatoriament)

# .mozilla/firefox/o9yritx4.default~/

a dins hi tens un fitxer que es diu bookmarks.html , revisa si hi es

També tens un directori que es diu bookmakbackups , mira en aquest enllaç com es fa per recuperar els backups que tenen com a extensió .json
[http://kb.mozillazine.org/Bookmarks]("http://kb.mozillazine.org/Bookmarks")

Per el altre problema que et passa, recordo que en alguna actualització em va passar el mateix.
Ho vaig arreglar a les males, carregant-me el directori del firefox perquè ell el torni a crear (movent-lo per ésser exactes.)

així dons a dins del teu home

# cd ..mozilla/
# mv firefox firefox_OLD

quant arrenquis t'arrencara com si fos la primera vegada. 
Ull que hauràs de restaurar els bookmarks, themes, i altres que hagis personalitzat.

---

### Post by manelfus on 2009-02-03
Merces Jerec per la teva resposta al final he pogut recuperar les adreces fent servir la eina de recuperació  mitjançant els arxius .json lo de el firefox no se com ho he fet però a tornat a estar be he mogut el arxiu firefox com hem deies però no m'ho tornava a crear per la qual cosa o tornava a desfer així fins que a tornat a funcionar(la fletxa de tornar enrera) val vinga salut

Manel

---

### Post by SiscoGarcia on 2009-02-03
Manel, cal acabar posant [SOLVED] per tal que qui vingui darrere pugui saber que en aquest fil hi trobarà una solució al problema que planteges.

EDITO: Recorda el [fil d'iniciació]("http://ubuntuforums.org/showthread.php?t=599965").

---

### Post by manelfus on 2009-02-03
Val Siscu ja ho se però pense que això esta resolt aquest mati dos quarts de nou i encare pot haver gent que poguí posar el seu gra de sorra.

De totes totes no es l'única cosa que m'ha passat, però cert es que crec que es per el mateix motiu així doncs me ha desaparegut també tot l'historial de el promt quant li dones a la fletxa cap a dalt et doni l'ultim comand escrit, i també (això des de l'instalacio del 8.10) el poguer apagar-ho des de la part dreta  a dalt de la pantalla (de fet he tingut també que afegir-hi un element nou, el de apagar , al quadre).

Lo curiós del cas es que solament m'ha passat amb una de les 4 maquines que tinc????? totes elles actualitzades al 8.10 ja et dic estic flipant, be dons fins sempre 
salut 
Manel

---

