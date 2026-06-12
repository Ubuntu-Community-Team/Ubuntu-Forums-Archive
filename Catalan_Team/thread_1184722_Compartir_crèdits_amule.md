---
title: "Compartir crèdits amule"
date: 2009-06-11
forum: Catalan Team
---

### Post by simfomet on 2009-06-11
Hola a tothom!

He instal·lat amule 2.2.5 i voldria compartir crédits entre emule i amule. Googlejant he trobat una manera però la primera instrucció que hem diu que fiqui a la consola es cd ~/.aMule i en aquesta ordre ja hem dóna un error i surt, bash: cd: /home/albert/ .aMule: No such file or directory. 

A què es deu? Que puc fer per solventar-ho? Segurament és fàcil però sóc un desastre amb la consola i les ordres.

---

### Post by PatrickVogeli on 2009-06-11
has comprovat que la carpeta .aMule existeix?? Es possible que encara no hagis iniciat mai l'aMule i per aixo no t'ha creat la carpeta¿¿

Fes el següent:
cd
dir .aMule

i enganxa el resultat aqui.

salut

---

### Post by simfomet on 2009-06-12
Tenies tota la raó del món i no havia executat encara amule. La veritat que no sabia que no es creava la carpeta fins que s'executava.

Per mirar de compartir crèdits amb emule he escrit a la consola:

cd ~/.aMule
  ln -sf /media/c/archiv~1/emule/config/preferences.dat preferences.dat
 ln -sf /media/c/archiv~1/emule/config/cryptkey.dat cryptkey.dat
 ln -sf /media/c/archiv~1/emule/config/clients.met clients.met
 Per compartir la llista de servidors:
 ln -sf /media/c/archiv~1/emule/config/addresses.dat addresses.dat
 ln -sf /media/c/archiv~1/emule/config/server.met server.met
 ln -sf /media/c/archiv~1/emule/config/staticservers.dat staticservers.dat


A la consola no m'ha sortit cap missatge d'error ni ok ni res al donar-li enter després de cada sentència. Llavors he obert amule on prèviament havia canviat les carpetes on desar les baixades i els temporals i ha començat a fer hash com és lògic però m'ha donat missatges que em porten a pensar que no està ben fet l'enllaç amb els crèdits d'emule. Com ho puc saber? Això és el que em diu:


2009-06-12 20:27:54: Starting aMule 2.2.5 using wxGTK2 v2.8.10
2009-06-12 20:27:54: CFile: Error when opening file (/home/albert/.aMule/preferences.dat): No such file or directory
2009-06-12 20:27:54: CFile: Error when opening file (/home/albert/.aMule/preferences.dat): No such file or directory
2009-06-12 20:27:54: No s'ha trobat el fitxer 'cryptkey.dat', creant-lo.
2009-06-12 20:27:54: Credits: Failed to create new RSA keypair: FileSink: error opening file for writing: /home/albert/.aMule/cryptkey.dat
2009-06-12 20:27:54: Credits: Error while initializing encryption keys: FileStore: error opening file for reading: /home/albert/.aMule/cryptkey.dat
2009-06-12 20:27:54: S'està carregant els filtres IP 'ipfilter.dat' i 'ipfilter_static.dat'.
2009-06-12 20:27:54: S'han carregat 0 rangs IP des de '/home/albert/.aMule/ipfilter.dat'. S'han descartat 0 línies malformades.
2009-06-12 20:27:54: S'han carregat 0 rangs IP des de '/home/albert/.aMule/ipfilter_static.dat'. S'han descartat 0 línies malformades.
2009-06-12 20:27:54: Les connexions externes estan inhabilitades al fitxer de configuració
2009-06-12 20:27:54: Created Server UDP-Socket at port 62528
2009-06-12 20:27:54: Created Client UDP-Socket at port 62535

2009-06-12 20:27:54:  - aMule 2.2.5 using wxGTK2 v2.8.10 basat en eMule.
2009-06-12 20:27:54:    S'està executant sobre Linux 2.6.28-11-generic x86_64
2009-06-12 20:27:54:  - Visiteu [http://www.amule.org](http://www.amule.org) per a comprovar si hi ha disponible una versió nova.

2009-06-12 20:27:54: S'han carregat 248 imatges de banderes.
2009-06-12 20:27:54: S'està carregant el fitxer server.met: /home/albert/.aMule/server.met
2009-06-12 20:27:54: No s'ha trobat el fitxer server.met!
2009-06-12 20:27:54: AVÍS: /media/ARXIU/Emule/Temp/001.part pot ser corrupte (-3600)
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 002.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/002.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 002.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '002.part.met'
2009-06-12 20:27:54: AVÍS: /media/ARXIU/Emule/Temp/003.part pot ser corrupte (-3600)
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 004.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/004.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 004.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '004.part.met'
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 006.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/006.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 006.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '006.part.met'
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 007.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/007.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 007.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '007.part.met'
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 009.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/009.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 009.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '009.part.met'
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 010.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/010.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 010.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '010.part.met'
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 011.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/011.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 011.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '011.part.met'
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 015.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/015.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 015.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '015.part.met'
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 019.part.met ==>
2009-06-12 20:27:54: S'està intentant carregar la còpia del fitxer met des de /media/ARXIU/Emule/Temp/019.part.met.bak
2009-06-12 20:27:54: ERROR: Versió del fitxer part.met invàlida: 019.part.met ==>
2009-06-12 20:27:54: ERROR: No s'ha pogut carregar la còpia de seguretat. Cerqueu '.part.met recovery solutions' a [http://forum.amule.org](http://forum.amule.org)
2009-06-12 20:27:54: PartFiles: ERROR: Failed to load PartFile '019.part.met'
2009-06-12 20:27:54: Trobats 2 fitxers de parts
2009-06-12 20:27:54: S'han trobat 2 fitxers compartits coneguts, 51 desconeguts
2009-06-12 20:27:54: La vostra versió de l'aMule és l'última.
2009-06-12 20:27:59: Hasher: S'està començant la creació del resum MD4 per al fitxer: 001.part
2009-06-12 20:28:12: ThreadScheduler: Completed task 'Hashing - /media/ARXIU/Emule/Temp/001.part', 52 tasks remaining.
2009-06-12 20:28:12: Hasher: S'està començant la creació del resum MD4 per al fitxer: 003.part

---

### Post by simfomet on 2009-06-15
Alguna idea sobre si està l'enllaç per compartir crèdits ben fet?

---

### Post by oriolsbd on 2009-06-15
Hola, per la informació que passes, poden ser dues coses (o més, però a mi se'm venen dues al cap). :-)

- La partició on tens Windows està sempre muntada a /media/c? O simplement la vas muntar per a fer els enllaços? Si és el segon cas, el que passa és que quan va a través de l'enllaç no troba la informació original.

- L'altre possible motiu (i que crec que és el correcte) és que suposo que no t'ha fet bé els enllaços. Si fas (per exemple):
```
ls -l ~/.aMule/server.met
```
Et mostra l'enllaç com a no existent? (si és així, a mi se'm mostra el nom de fitxer en vermell amb fons negre). Crec que és perquè el directori d'origen de l'enllaç (el de Windows) hi ha el "archiv~1". Si és aquest el cas, el millor que pots fer és esborrar els enllaços que has creat i tornar-los a refer, però escrivint els noms de directori completament. En aquest cas, ajuda't de la tecla "Tab". Per exemple, quan tinguis escrit "/media/c/arc" prem la tecla "Tab" i et completarà la resta. Ull, és possible que hagis d'escriure la "A" en majúscula. És a dir "/media/c/Arc" i prémer "Tab". Una altra opció és crear els enllaços des del Nautilus.

Salut!

---

### Post by simfomet on 2009-07-11
Hola,

  perdona que no hagi respòs abans però no m'he pogut ocupar del tema fins ara. He configurat les particions ntfs perquè es carreguin automàticament al iniciar i evitar sorpreses.
A més, he comprovat amb l'ordre que citaves i em respon:

-rw-r--r-- 1 simfomet simfomet 5 2009-06-13 12:06 /home/simfomet/.aMule/server.met

No em surt ni amb vermell ni res, així doncs entenc que l'enllaç està ben fet no?

---

### Post by oriolsbd on 2009-07-11
Pel que et respon a la comanda, l'enllaç no està ben fet. Si estigués ben fet, et sortiria una cosa semblant a:
-rw-r--r-- 1 simfomet simfomet 5 2009-06-13 12:06 /home/simfomet/.aMule/server.met -> /media/c/archiv~1/emule/config/server.met

Prova d'eliminar el fitxer (fent abans una còpia de seguretat) i tornar a generar l'enllaç seguint les recomanacions que et donava.

Salut! :-)

---

### Post by simfomet on 2009-07-13
Em podries concretar una mica com fer-ho això de borrar els fitxers i demés, vaig una mica peix amb tot plegat.

Gràcies.

---

### Post by papapep on 2009-07-13
Simfomet: [aquí]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes") tens un breu tutorial de les ordres més bàsiques de l'intérpret d'ordres. No dubtis en plantejar els dubtes que se't creïn. Mira't cp, mv i rm per a copiar, canviar de nom i esborrar fitxers. [Aquí]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Manipulant%20fitxers") tens l'apartat específic.

---

### Post by oriolsbd on 2009-07-15
He mirat bé els teus missatges, i em sembla que el problema és un altre. Els enllaços els has creat a /home/simfonet/.aMule, i l'aMule et diu que els està buscant a /home/albert/.aMule. Utilitzes l'aMule amb un usuari diferent del que has creat els enllaços? Hauries de tornar a crear els enllaós a /home/albert/.aMule (tal i com ja vas fer a /home/simfonet/.aMule).

Salut!

---

