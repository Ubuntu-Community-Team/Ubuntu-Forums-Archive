---
title: "Problemes amb el so i amb l'apagada del sistema"
date: 2010-08-04
forum: Catalan Team
---

### Post by deybeat on 2010-08-04
Bones a totes i a tots;

A vore si em podeu donar un cop de ma pq estic una mica desesperat amb el tema. He estat mirant pel fòrum a veure si hi havia un fil que en parlés però no l'he trobat, us explico:

Tinc un ACER Aspire 2930 amb l'Ubuntu 10.04 instal·lat (versió 64 bits). He anat actualitzant per internet cada versió desde la 7.10 (crec) i no he tingut cap problema serio a destacar.

Des de que tinc la versió 10.04 m'he adonat de que sovint s'inicia el sistema sense so i a més, a l'hora d'apagar no hi surt l'opció, només hi ha la de sortir de la sessió i una altre que ara mateix no se quina és... i he d'apagar el portàtil a pel amb el botó de power. Algú més te aquest problema?¿ Desconec si el sistema pateix altres mancances quan passa aixó...

A vore si trobem la solució

Gràcies!

---

### Post by wgarcia on 2010-08-04
Semblen com dos problems diferents, potser fora millor obrir un fil per cada u. 

En quan al so: com reestableixes el so quan no el tens?

Respecte al problema que no surti l'opció de tancar el sistema, quan sols et surt aquesta opció que dius sols deixa tancar la sessió, si fas un clic amb el botó dret sobre l'opció i esculls "Quant a", què és el que diu?

---

### Post by akyra on 2010-08-04
Respecta la icono d'apagar el equip, has intentat posar en la barra de menú la "Mini Aplicación de indicadores de sesion"? Aquesta és la icona que t'apareix totes les opcions d'apagar i encendra l'equip.

Adeu

---

### Post by kimet on 2010-08-04
> Des de que tinc la versió 10.04 m'he adonat de que sovint s'inicia el sistema sense so 

De vegades m'havia passat que al arrencar el sistema s'oblidava alguns processos, normalment el ratolí o el so.
I, segons vaig entendre, el sistema, per tal d'accelerar el procés d'arrencada ho fà arrencant processos en paral.lel, aquest tenen que estar organitzats en un ordre determinat per no interferir entre ells.
 
Pots fer una ullada a:
[http://manpages.ubuntu.com/manpages/karmic/man8/startpar.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/startpar.8.html)

Jo ho vaig arreglar, desactivant l'arrencada en paral.lel canviant al fitxer /etc/init.d/rc
**CONCURRENCY=makefile per CONCURRENCY=none** (en ordinador amb cpu d'un sol nucli i amb un S.O. diferent al teu)
Lo que no vol dir que sigui la sol.lució al teu problema però podría ser una pista.

Salut

---

### Post by deybeat on 2010-08-06
a vore;

Crec que no són 2 problemes diferents. Per alguna raó que encara no se, a vegades el sistema arrenca malament, i això fa que certes coses no funcionin bé. 

Ho vaig mirar per internet i a un fòrum un noi explicava el mateix problema però ningú en sabia res.

Jo me'n adono de que la cosa no ha carregat bé pq el so no funciona, aleshores intento apagar-lo mitjançant la icona d'ubuntu de la barra de l'escriptori i en comptes de sortir-me les típiques opcions de "atura, reinicia, hiberna... ) em surt hiberna i no se que més...

:(

---

