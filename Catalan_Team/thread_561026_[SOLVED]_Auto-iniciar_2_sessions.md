---
title: "[SOLVED] Auto-iniciar 2 sessions"
date: 2007-09-27
forum: Catalan Team
---

### Post by slink on 2007-09-27
Hola, 

voldria configurar l'ordinador (ubuntu 7.04) perque iniciés automàticament 2 sessions. 

Puc activar l'inici automàtic, o bé, l'inici automàtic retardat, però no m'en surto per auto-activar a dos usuaris. 

Se m'acuden dues possibles sol.lucions:

1) Editar l'arxiu [FONT="Courier New"]/etc/gdm/gdm.conf-custom[/FONT]
    Puc afegir diferents usuaris?

exemple:

```
      AutomaticLoginEnable=true
      AutomaticLogin=usuari1
      AutomaticLogin=usuari2
```


2) Afegir a les opcions d'inici de sessió de usuari1 (auto-iniciat) una comanda com:

     [FONT="Courier New"]sudo login usuari2[/FONT]

  però em respon que "[FONT="Courier New"]login només es pot usar desde un nivell 'sh' més baix[/FONT]"


Molt possiblement existeix alguna altra sol.lució...

Gràcies

---

### Post by CarlesOriol on 2007-09-27
Com a curiositat. 

Quin és l'objectiu de la 2a sessió?

---

### Post by slink on 2007-09-27
> Quin és l'objectiu de la 2a sessió?


L'objectiu de la 2a sessió és que un usuari pugui treballar sense haver de veure els programes que s'han auto-activat a la primera sessió. 

És un cas molt semblant a [aquest post]("http://ubuntuforums.org/showthread.php?t=235497") , que estic estudiant ara mateix.

---

### Post by CarlesOriol on 2007-09-27
Quins programes? 

Perdona que sigui tant incisiu... es que em sembla que ho podries fer d'una altra manera.

---

### Post by slink on 2007-09-27
> Quins programes?

aMule i Azureus  :confused:

---

### Post by CarlesOriol on 2007-09-27
M'ho imaginava.

Saps que ambdos sistemes tenen versions que funcionen com a dimonis.

En amule tens el **amule-daemon** que pots controlar per html i va de conya. Per executar aquest no cal ni iniciar sesió!

La resta post usar el mldonkey

---

### Post by slink on 2007-09-27
Estava mirant l'aMuleWeb però al tenir adreça IP dinàmica... és un [garbuix]("http://ec.grec.net/lexicx.jsp?GECART=0068720") ...

Miraré aquests que em comentes.

De moment he posat un 
```

#!/bin/bash
/usr/bin/gnome-screensaver
sleep 2
/usr/bin/gnome-screensaver-command -l
```


a l'inici de la sessió del primer usuari.

Mercès de totes formes!

---

### Post by CarlesOriol on 2007-09-27
No home. L'accés fes-lo contra la IP 127.0.0.1 (localhost).

---

### Post by slink on 2007-09-27
Perdona, em referia a controlar l'aMule remotament...

Estic googlejant però, no tindràs a mà enllaços de l'amule-daemon ( és l'aMuled?)

---

### Post by CarlesOriol on 2007-09-27
Està als repositoris

sudo apt-get install amule-daemon

---

### Post by slink on 2007-12-12
Ei, com que em vaig cansar d'intentar auto-iniciar 2 usuaris, vaig instal.lar l' aRuc-Dimoni:twisted:!
És una me-ra-ve-lla!
Gràcies pel consell!

---

