---
title: "cal un connector"
date: 2015-06-02
forum: Catalan Team
---

### Post by josep-maria on 2015-06-02
He actualitzat l'ubuntu de la versió 14.04 a la 15.04, a un processador intel core 2 duo.
Ara no puc veure les pàgines d'un diari, que fins ara veia bé. 
Surt un avís que diu "cal un connector per mostrar aquest contingut"
La pàgina del diari està tota grisa amb un dibuix, però hi si faig clic, s'obre una altra finestra, i llavors sí que les veig bé.
He mirat als paràmetres del sistema quin connector cal, però no ho puc saber.

---

### Post by wgarcia on 2015-06-02
Si has saltat de la 14.04 directament a la 15.04 i t'ha funcionat, has tingut molta sort, perquè normalment, excepte de versió de llarg termini a versió de llarg termini, per exemple de 12.04 a 14.04, s'ha d'anar actualitzant versió per versió: 14:04 -> 14.10 -> 15.04. 

Però en tot cas el més probable és que et falti configurar bé alguna cosa del flash, això que descrius és típic d'això. 

Normalment amb:
```
sudo apt-get install flashplugin-installer
```

s'hauria d'arreglar.

---

### Post by josep-maria on 2015-06-02
Ja he fet això de
sudo apt-get install flashplugin-installer
i ha anat bé. Gràcies.

---

