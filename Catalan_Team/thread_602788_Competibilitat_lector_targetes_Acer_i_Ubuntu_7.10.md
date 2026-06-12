---
title: "Competibilitat lector targetes Acer i Ubuntu 7.10"
date: 2007-11-04
forum: Catalan Team
---

### Post by Minotaure on 2007-11-04
Hola, aquest és el meu primer missatge en aquest fòrum.
Sóc nou en el ús d'Ubuntu i de Linux en general. Només fa un mes que m'he instal·lat l'Ubuntu 7.04.

El sistema operatiu em funciona bé però tinc un problema: no em detecta el lector de targetes 5 en 1 (SD, etc) que té el meu portàtil **Acer Aspire 5633** (que és on tinc instal·lat l'Ubuntu). De fet tampoc em detecta la càmera però això ja no en precupa gaire perquè no l'havia fet servir mai amb Windows, en canvi el lector de targetes SD sí que el feia servir en Windows.

Ara he vist que hi ha disponible la versió 7.10 de l'Ubuntu. La meva pregunta és: algú sap si amb la nova versió em detectarà el lector de targetes? Ho dic perquè vaig llegir un fil per Internet on en teoria s'havia arreglat aquest problema de compatibilitat però abans d'instal·lar la nova versió m'agradaria saber si em solucionarà el problema (ja que si no me'l soluciona instal·laria la versió 7.10 més endavant).

La dades que em surten posant la comanda lspci a la consola són les següents:
[I]06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)[/I]

Moltes gràcies per endavant.

---

### Post by jodufi on 2007-11-04
Si diuen que la nova versió soluciona el problema, pots provar-ho sense instal·lar-la.
Simplement executa la versió 7.10 des d'un CD, sense instal·lar-la, i prova com funciona.

Salut

---

### Post by papapep on 2007-11-04
Aquí:

[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5633WLMi](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5633WLMi)

diuen que el lector funciona perfectament sense fer res amb Gutsy.

---

### Post by Minotaure on 2007-11-05
Gràcies PapaPep per la pàgina que has facilitat on s'informa de les compatibilitats amb el meu model concret de portàtil. Així sembla ser que el problema ja està solucionat amb la 7.10.

De totes maneres faré el què diu el jodufi de provar-ho primer des de DVD (no hi havia pensat en aquesta possibilitat !!).

---

