---
title: "gestor d'actualitzacions"
date: 2022-05-03
forum: Catalan Team
---

### Post by josep-maria on 2022-05-03
He volgut actualitzar a l'ubuntu 22-04. A mig fer, s'ha aturat, i el pc s'ha apagat. L'he engegat, i funciona, però ara si faig clic a sistema > administració > gestor d'actualitzacions, no fa res de res. Tinc l'ubuntu 21-10 Mate 1.26.0. Com puc fer que torni a funcionar?

---

### Post by jmaspons on 2022-05-03
Mira d'actualitzar i finalitzar la configuració dels possibles paquets que hagin quedat a mitges.

```

sudo dpkg --configure -a
sudo apt update
sudo apt full-ugrade

```

A vera què passa amb això.

---

### Post by josep-maria on 2022-05-03
Després de
```
sudo dpkg --configure -a
sudo apt update
sudo apt full-ugrade
```

surt això:
```
E: Dependències no satisfetes. Proveu amb «apt --fix-broken install» sense paquets (o especifiqueu una solució).
```

Si fico apt apt --fix-broken install, surt això:
```
E: No s'ha pogut obrir el fitxer de blocat /var/lib/dpkg/lock-frontend - open (13: S’ha denegat el permís)
E: No es pot obtenir el bloqueig de la interfície del dpkg (/var/lib/dpkg/lock-frontend). Sou root?
```

---

### Post by wgarcia on 2022-05-04
Hauries de fer:

```
sudo apt -f install
```

Si acaba la instal·lació, també caldrà fer:

```
sudo apt autoremove
```

per eliminar els paquets obsolets un cop actualitzat tot.

---

### Post by josep-maria on 2022-05-11
Al final ha ficat l'ubuntu 22.04, però m'ha esborrat totes les adreces d'interès del firefox.
Moltes gràcies.

---

### Post by wgarcia on 2022-05-11
Obre un altre fil sobre el problema del Firefox, és possible que es pugui resoldre.

---

