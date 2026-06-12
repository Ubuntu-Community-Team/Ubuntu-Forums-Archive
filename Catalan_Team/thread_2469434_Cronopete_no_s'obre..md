---
title: "Cronopete no s'obre."
date: 2021-11-29
forum: Catalan Team
---

### Post by guillemtusell on 2021-11-29
Bon dia.

Nou (però molt) a Linux, Ubuntu 20.04.3 LTS

Instal·lo .deb del programa cronopete, però no s'obre.

He buscat i he trobat problema similar amb la sol·lució (per LinuxMint)  [COLOR=#2E8B57][FONT=Monaco]sudo apt install libxapp1/tricia 
[/FONT][/COLOR]però si ho provo, terminal em diu: 
[I]
E: No s'ha trobat la versió puntual «tricia» per a «libxapp1»
[/I]
Un cop de mà?

Edito: tinc instal·lat el reproductor "foobar200". En fer la insta·lació de cronopete em sembla, i no sé x quina raó, que tots els arxius han anat a petar a snap/foobar2000/common  (¿?)

Gràcies

---

### Post by jmaspons on 2021-11-29
En principi, si el .deb està bé i pensat per Ubuntu, ja hauria de gestionar les dependències d'altres paquets si ho instal·les amb gdebi.

```
sudo gdebi FITXER.deb
```

Com ho instal·les?

Si vols resoldre manualment les dependències i necessites libxapp1, prova de no especificar la versió a veure si la que ve per defecte ja és compatible.

```
sudo apt install libxapp1
```

---

### Post by guillemtusell on 2021-11-29
Sol·lucionat. Gràcies.

---

