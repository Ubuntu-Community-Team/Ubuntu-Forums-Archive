---
title: "Contrasenya a un .txt"
date: 2011-06-27
forum: Catalan Team
---

### Post by xanxu on 2011-06-27
Hola a tots,

No sóc nou al Linux, però faig un servei usuari, atrevint-me a obrir el terminal quant menys millor.
El meu problema és que no trobo la solució per posar contrasenyes a documents de text senzill (el que en windows seria un .txt). He buscat solucions i he trobat un programa que es diu Seahorse, però el que jo vull és molt més senzill, una simple opció de posar una contrasenya per tal de que quan el vulgui obrir sigui necessari escriure-la.

Sabeu com fer-ho o un programa senzill?

Sóc usuari linux mint 11, però crec que aquesta questió pot entrar en el fet d'utilitzar gnome, independentment de la distro.

Moltes gràcies.

---

### Post by wgarcia on 2011-06-27
Amb gpg , un cop creada la teva signatura privada, 

gpg --encrypt <nom del fitxer> 

deixarà una còpia encriptada <nom del fitxer>.gpg, i quan facis 

gpg --decrypt <nom del fitxer>.gpg > <nom del fitxer>

et demanarà el teu "passphrase" i recuperarà el fitxer original.

Altres opcions són crear un "zip" amb clau, treure-li permisos de lectura excepte per al teu usuari, o posar-li en propietat de "root" i que sols tu coneguis la clau de root. I per últim encriptar tot el teu "home".

---

### Post by xanxu on 2011-06-27
Ja esta, ha estat tant fàcil com fer-lo arxiu invisible amb un punt davant. He fet lo de root. Moltes gràcies per la resposta tant ràpida!

---

### Post by orestesmas on 2011-06-28
Home, entre protegir-lo amb contrasenya i això que tu dius hi ha un abisme. N'hi ha prou amb fer «ls -d .*» per obtenir un llistat de tots els fitxers i directoris ocults, i després fer un «cat nom_del_fitxer» per revelar el seu contingut.

Si realment vols impedir que algú el llegeixi l'has d'encriptar, ja sigui amb el gpg com t'ha dit el walter (però cal que tinguis una clau gpg creada) o bé més senzillament creant un fitxer comprimit (ZIP) amb password.

Això darrer es faria amb

```

zip -e fitxer.zip fitxer_a_protegir.txt

```

Et demanarà el password 2 vegades.

I per visualitzar-lo cal fer 

```

unzip -p fitxer.zip

```

---

### Post by xanxu on 2011-06-28
Si si, és cert que hi ha molta diferència. A mi el que m'importava era que no es pogués veure o bé que si es veia fos complicat entrar-hi. De moment així crec que ja esta bé. De totes maneres els comandaments del zip me'ls guardo.
Moltes gràcies.

---

