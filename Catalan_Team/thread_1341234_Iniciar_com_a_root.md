---
title: "Iniciar com a root"
date: 2009-11-29
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2009-11-29
Bones,
Voldria saber si es pot configurar Ubuntu 9.10 per permetre d'iniciar sessió com a root.
A l'anterior versió, anant a sistema - administració - finestra d'entrada, es podia fer. Però ara no ho veig!
Gracies.

---

### Post by papapep on 2009-11-29
La pregunta, més que "com", és "per a què"?? Ja saps que és **més que desaconsellable**, fer-ho.

---

### Post by Miquel Ubuntero on 2009-11-30
Hola Papapep,
Per què?
Bé, en alguna ocasió m'ha passat de no poder entrar al meu usuari o que l'entorn d'escriptori s'ha anat a norris.
Aleshores, una opció és entrar com a root i mirar de reparar el problema.
La idea és tindre una opció, amb entorn gràfic, per entrar al sistema.
A veure que en penses.
Salut!

---

### Post by ifanlo on 2009-12-01
Hola, miquel!

> **Miquel Ubuntero said:**
> Bones,
Voldria saber si es pot configurar Ubuntu 9.10 per permetre d'iniciar sessió com a root.
A l'anterior versió, anant a sistema - administració - finestra d'entrada, es podia fer. Però ara no ho veig!
Gracies.

La resposta es sí.
:-)

Però suposo que vols saber com...  ;-)

Primer, si encara no has assignat un password a root ho pots fer amb
```
$ sudo passwd
```Després, en versions anteriors es podia tocar una línia de l'arxiu /etc/gdm/gdm.conf, però veig que això ha canviat i ara s'ha de fer al /etc/gdm/custom.conf, el qual -collonada total- no està comentat i obliga a anar a veure /usr/share/gdm/defaults.conf, el qual, al seu torn no existeix!  genial!

Finalment trobo els exemples a /usr/share/doc/gdm/examples/defaults.conf.  Però l'arxiu no conté cap informació.  Anem bé!

Se m'acut consultar l'arxiu /etc/gdm.conf.dpkg-bak, a on es troba una còpia de seguretat de la versió anterior.  Aquí puc veure que hi havia una directiva AllowRoot=false dins la secció security.

Així que penso que només cal afegir a la corresponent secció del custom.conf

```
[security]
AllowRoot=true
```Ara falta comprovar si això es una directiva que continua vigent a la 2.28.  A veure... Funciona!

M'havia picat perquè recordava haver-ho fet anteriorment i m'emprenyava que ara costés tant.

Només caldrà que facis com a la SuSE, un fons de pantalla vermell llampant tot ple de bombes explosives!  :-D

Salut,

---

### Post by papapep on 2009-12-01
Jo es que trobo **absolutament fora de lloc** ni tan sols plantejar-se accedir com a root per a res a l'entorn gràfic. I, a més, és un **molt mal exemple pels nouvinguts** que poden pensar que és una metodologia bona i habitual. No entenc per a què pot fer falta, **es pot fer absolutament tot** sense obrir les portes d'aquesta manera, i **trenca completament tota la filosofia de seguretat** dels sistemes operatius *nix. Suposo que ha quedat clar el que vull dir.

---

