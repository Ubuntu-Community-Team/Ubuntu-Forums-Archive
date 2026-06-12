---
title: "Còpia a discs USB excessivament lenta"
date: 2009-08-31
forum: Catalan Team
---

### Post by jaumety on 2009-08-31
Hola bones, el problema és que he actualitzat "ubuntu server 9.04" i quan faig una copia a discs USB ara em va molt més lent que abans d'actualitzar. per exemple abans copiar 1,4GB em tardava uns 4 minuts i ara me'n tarda uns 60.
Alguna idea?

Gràcies.

---

### Post by papapep on 2009-08-31
El teu ordinador fa servir processador AMD? sembla que hi ha molta gent amb aquest processador que té problemes d'aquests.
Bé, sigui com sigui, hi ha moltíssima gent que comenta aquest problema, i una de les solucions sembla que podria passar per descarregar un parell de mòduls i tornar-los a carregar en l'ordre correcte:

```
sudo rmmod ehci_hcd
sudo rmmod uhci_hcd
sudo modprobe ehci_hcd
sudo modprobe uhci_hcd
```

Si així et funcionés millor, caldria configurar l'ordinador per a que es carreguin els mòduls en l'ordre correcte també a l'arrencada, sinó cada cop hauries de fer això.

---

### Post by jaumety on 2009-08-31
al intentar executar la comanda "sudo rmmod ehci_hcd" em dona això:

ERROR: Module ehci_hcd does not exist in /proc/modules.

Moltes gràcies.

---

### Post by PatrickVogeli on 2009-08-31
> **papapep said:**
> El teu ordinador fa servir processador AMD? sembla que hi ha molta gent amb aquest processador que té problemes d'aquests.
Bé, sigui com sigui, hi ha moltíssima gent que comenta aquest problema, i una de les solucions sembla que podria passar per descarregar un parell de mòduls i tornar-los a carregar en l'ordre correcte:

```
sudo rmmod ehci_hcd
sudo rmmod uhci_hcd
sudo modprobe ehci_hcd
sudo modprobe uhci_hcd
```

Si així et funcionés millor, caldria configurar l'ordinador per a que es carreguin els mòduls en l'ordre correcte també a l'arrencada, sinó cada cop hauries de fer això.
Aixo no funcionara, ja que a Jaunty els moduls USB estan integrats al kernel i no son moduls que es puguin carregar o descarregar.

Hi ha gent que diu que ha millorat instal·lant un kernel més nous, de no se quin PPA. Aqui tens el fil on s'en parla: [http://ubuntuforums.org/showthread.php?t=1150108](http://ubuntuforums.org/showthread.php?t=1150108)

---

### Post by jaumety on 2009-09-03
Ja ho he trobat, no era problema de l'ubuntu, era problema del disc ja amb un altre disc em funciona tot correctament.

Gràcies.

---

### Post by MiquelBLL on 2009-09-06
A mi no es que em copiï molt lent pero el que si em passa es que mai em copia a la mateixa velocitat, de vegades cuan copia a un llapis o a un disc extern em copia una vegada a 15 M/S altres a 2 M/S altres a 8 M/S etc, aixo a la mateixa sessió es una cosa que no he entes mai. Tinc AMD Turion 64 i clar 9.04.

---

