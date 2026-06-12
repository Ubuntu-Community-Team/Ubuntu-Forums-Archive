---
title: "actualitzar xubuntu des de la terminal"
date: 2009-05-23
forum: Catalan Team
---

### Post by bratac on 2009-05-23
Bones,

tinc un ordinador amb xubuntu i windows. Volia actualitzar l'xubuntu però em dóna un error a l'inici que no us puc dir quin és perquè em surt la lletra tan petita que no la puc llegir. Aquest error fa surt un cop he posat l'usuari i la contrasenya i no em permet arribar a l'escriptori.
Puc iniciar sessió des de la terminal i voldria actualitzar el sistema via terminal. Algú em pot dir les ordres que hi he de posar?

Si no he pensat baixar-me l'xubuntu últim i fer-ho des del cd però tinc por d'esborrar algun fitxer perdut del windows.

Em podeu donar un cop de mà?

Gràcies

---

### Post by oriolsbd on 2009-05-23
Pot ser problema de falta d'espai en alguna partició? Pots mirar-ho així:
```
df -m
```

Salut!

---

### Post by bratac on 2009-05-23
Bones,

em dóna algun problema amb la x11, com si hi faltés algun fitxer però la lletra per defecte és tant petita que només n'he pogut deduir el següent:

./x11 després continua però sóc incapaç de veure'n el problema.

he actualitzat fent sudo update-manager -d i el problema continua. 
he intentat arreglar-ho engegant l'ordinador des de mode segur i arreglant els problemes amb la x11 i no em funciona.

Per tant he pensat que el millor seria esborrar l'xubuntu vell i instal·lar-ne un de nou. Com que no hi tinc fitxers no em fa patir perdre la informació. L'únic que vull tenir clar és que no em carregaré res del windows.

gràcies.

---

### Post by RainCT on 2009-05-23
Fes Ctrl+Alt+F1, inicia sessió i amb "less ~/.xsession-errors" pots mirar a veure is l'error ha quedat enregistrat.

I no, no li passarà res al Windows al reinsta&#320;lar sempre i quant triïs bé les particions.

---

### Post by bratac on 2009-05-23
Moltíssimes gràcies, de nou, per tot!

---

### Post by bratac on 2009-05-26
Al final he decidit instal·lar el sistema de nou. L'instal·lador em demana unes dades que no entenc (...) Un cop sóc al gestor de particions engego el gestor manual i des d'allà vull escriure sobre la partició que ja té l'xubuntu. Llavors em demana el sistema de fitxers i el punt de muntatge. El sistema de fitxers entenc que és el «sistema de fitxers transaccional ext3 però el punt de muntatge no sé quin he de seleccionar. El que vull fer és instal·lar l'xubuntu de nou sense tocar el windows, res més.

Algú em pot dir què he de fer?

gràcies!

---

### Post by torracastanyes on 2009-05-26
Doncs, depenent de com tinguis el disc partit, hi haurà una partició NTFS, que és la de Windows, i per tant no l'has de tocar.

Després has d'identificar la partició SWAP i seleccionar com a sistema de fitxers "espai d'intercanvi", ja no et demanarà punt de muntatge.

Ara només necessites una partició ext3 (o ext4, si vols) amb punt de muntatge "/"per instalar el sistema. Si vols tenir els teus arxius separats, pots fer una altre partició amb el mateix sistema de fitxers i amb punt de muntatge "/home".

Si ja teníes una partició separada per les teves dades, l'has de mantenir amb el sistema de fitxers que tingui, el punt de muntatge "/home" i seleccionar la opció "no formatar", per que conservi les dades que hi hagi.

No sé si t'ajudo o t'enredo encara més.

Que hi hagi sort.

---

### Post by oriolsbd on 2009-05-26
A més del que indica el Torracastanyes, a la partició de Windows (la ntfs) li pots dir que te la munti a "/windows" o "/fitxers" (o el nom que vulguis) però, sobretot, _INDICANT QUE NO LA FORMATI_. Així podràs veure des de Ubuntu tots els fitxers de Windows a partir del directori "/windows" (o el que hagis escollit).

---

### Post by bratac on 2009-05-26
Moltes gràcies a tots ja ho he fet i funciona!!

---

