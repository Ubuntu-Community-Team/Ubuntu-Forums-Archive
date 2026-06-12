---
title: "[SOLVED] Amarok [no tira-error]"
date: 2007-09-25
forum: Catalan Team
---

### Post by prostata on 2007-09-25
Companys:

Quan arrenco amarok, no tira i em dona aquest missatge:

DCOP Communications error

There was an error setting up interprocess communications for KDE.
Could not reader network communication list:
     /home/joep/.DCOPserver_josep-descktop_0

Please check that the "dcoperserver" program is running.

A veure, fins aquí els meus coneixements d'anglès, bé. Ara d'ubuntu.

¿què ès tot això i com ho arreglo????

Gràcies

---

### Post by Ferri on 2007-09-25
Fes Control+Esc.
Busca el dcopserver, si hi és, continua. Si no, diria que tens un problema greu al teu KDE, torna a posar un post i intentarem veure com s'arregla.
Obre la teva home amb el Konqueror.
Si no ho tens activat, activa "visualitza els fitxers ocults" al menú "visualitza".
Mira si hi ha el fitxer ".DCOPserver_josep-descktop_0".
Si hi és, fes clic dret, tria "propietats" i allà "permisos".
Assegura't tenir-hi permís de lectura i escriptura.

---

### Post by prostata on 2007-09-25
> **Ferri said:**
> Fes Control+Esc.
Busca el dcopserver, si hi és, continua. Si no, diria que tens un problema greu al teu KDE, torna a posar un post i intentarem veure com s'arregla.
Obre la teva home amb el Konqueror.
Si no ho tens activat, activa "visualitza els fitxers ocults" al menú "visualitza".
Mira si hi ha el fitxer ".DCOPserver_josep-descktop_0".
Si hi és, fes clic dret, tria "propietats" i allà "permisos".
Assegura't tenir-hi permís de lectura i escriptura.

Ferri:

M'he oblidat de dir-lo pero no faig servir KDE, i això és el que m'ha despistat, del que em dius evidentment no hi ha res al meu home. no existeis el fixer DCOPserver.........
Fa dies vaig tornar a Ubuntu feysti fawn i que jo sàpigue això es Gnome, no pas KDE. Per ampliar-te l'info, et dic que la partició de HD que tinc destinada per a distros Linux, la vaig "processar" seguint les instruccions d'instal-lació del Fesyti, per tant no va quedar ni rastre de l'antiga instalació en entorn KDE.

Espero que aquesta info t'ajudi a que em puguis ajudar ;-)

Salut

---

### Post by prostata on 2007-09-25
He trobat un soft, Exaile, que si fa o no fa, fa el mateix que amarok, si tens alguna sol-lució doncs, Ok sino, amb Exaile ja faig...gràcies

---

### Post by papapep on 2007-09-25
Próstata: Tu pots tenir el Gnome instal·lat, però Amaro**[COLOR="Red"]k[/COLOR]** és una aplicació de KDE, com K3B, per exemple.
.
Això és el perquè l'error et parla de KDE

Respecte el teu problema, prova amb:

```
sudo chown -R joep:joep /home/joep/.*
```

---

### Post by pespin on 2007-09-25
Per si t'interesa la opinió, hi ha un parell de persones al IRC que acabem d'instal·lar-nos el exaile i n'estem bastant contents.

---

### Post by prostata on 2007-09-26
> **papapep said:**
> Próstata: Tu pots tenir el Gnome instal·lat, però Amaro**[COLOR="Red"]k[/COLOR]** és una aplicació de KDE, com K3B, per exemple.
.
Això és el perquè l'error et parla de KDE

Respecte el teu problema, prova amb:

```
sudo chown -R joep:joep /home/joep/.*
```

Gràcies fent això i afegin naturalment una s a cada joep ( ;-) ) a funcionat, gràcies

---

### Post by papapep on 2007-09-26
Jo ho vaig treure d'aquí:

> There was an error setting up interprocess communications for KDE.
Could not reader network communication list:
/home/[COLOR="Red"]**joep**[/COLOR]/.DCOPserver_josep-descktop_0

Sigui com sigui, m'alegro que t'hagi funcionat.

---

### Post by Ferri on 2007-09-26
Com a comentari addicional, només dir que si t'ha funcionat la solució d'en Papapep, és que el fitxer ".DCOPserver_josep-descktop_0" sí que existia, i no tenia configurats els permisos correctament. La solució que havia posat jo és exactament la mateixa, només que fent servir l'entorn gràfic de KDE, ja que, parlant d'Amarok, vaig suposar que era el que tenies.

---

