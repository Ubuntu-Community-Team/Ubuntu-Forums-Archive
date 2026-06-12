---
title: "Programa rebedor"
date: 2007-10-21
forum: Catalan Team
---

### Post by cunic on 2007-10-21
Hola a tots!

Sóc un nou usuari de linux, de fet fa pocs dies que vaig instalar Ubuntu 7.10, diria que el mateix dia en que va sortir. Fins ara no he tingut cap problema i de fet n'estic molt satisfet.

Avui però, quan l'he iniciat, just quan hauria d'apareixer la pantalla on em demana el nom d'usuari i la contrasenya em surt un missatge que diu així:

"El programa rebedor sembla estar fallant. S'intentarà utilitzar-ne un de diferent."

Li dic d'Acord i em queda la pantalla negra amb 5 línies de text que diuen el següent:

* Starting anac(h)ronistic cron anacron                     [OK]
* Starting deferred execution scheduler atd             [OK]
* Starting periodic command scheduler crond            [OK]
* Checking battery state...                                        [OK]
* Running local boot scripts (/etc/rc.local)                 [OK]

I així es queda. No sé què he de fer ni perquè em surt això. Val a dir que els meus coneixements de linux són pràcticament nuls i potser això que em passa és una ximpleria, però no sé què puc fer.

Gràcies!

---

### Post by Kosimo on 2007-10-22
Entenc que no pots entrar en mode gràfic i se't queda en mode text.

Intenta excriure això:  startx

---

### Post by orestesmas on 2007-10-23
Penso que aquestes línies no hi tenen res a veure. Simplement són restes dels missatges que el sistema emet en arrencar però que normalment no es veuen perquè queden "tapats" per l'arrencada gràfica.

Jo miraria de fer el que diu kosimo, però diferent. Prem les tecles Ctrl+Alt+F1 i aleshores entra en una consola de text posant el teu nom d'usuari i la contrasenya (no es veu res quan fiques la contrasenya, és normal)

una vegada entrat al sistema, fes el que et diu ell: posa "startx" i si no arrenca mira d'anotar els missatges d'error que et dóni. Els importants comencen per "(EE)"

---

