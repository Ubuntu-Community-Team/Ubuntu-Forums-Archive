---
title: "No puc obrir ni el sinaptic ni el gestor d'actualitzacions"
date: 2010-11-19
forum: Catalan Team
---

### Post by RicardKp on 2010-11-19
Hola, a tothom,

Com que no me'n sortia d'instal·lar el Libreoffice he provat d'instal·lar el repositori corresponent per fer-ho i m'ha sortit un error a l'afegir el repositori. Llavors he volgut anar al llistat de repositoris i ja no he pogut entrar ni al sinaptic ni al gestor d'actualitzacions, al intentar de carregar-los em surt aquest error:

[I][B]No es pot inicialitzar la informació dels paquets

S'ha produït un error irresoluble mentre s'inicialitzava la informació de paquets.

Informeu d'aquest error de l'update-manager i incloeu el missatge següent:

'E:El tipus «‘deb» no és conegut en la línia 56 de la llista de fonts /etc/apt/sources.list'[/B][/I]

Algú em pot ajudar?

Moltes gràcies per endavant.

Ricard

---

### Post by wgarcia on 2010-11-20
Sembla que tens alguna línia afegida a aquest fitxer "/etc/apt/sources.list" (que és on s'especiquen les diferents fonts de programari) que genera un error i impedeix executar les aplicacions d'actualitzacions. 

Per anar sobre segur el millor és que adjuntis aquest fitxer perquè es pugui veure quines línies s'han d'esborrar perquè torni a xutar.

---

### Post by RicardKp on 2010-11-20
Moltes gràcies, wgarcia,

Ja he entrat com a root a "/etc/apt/sources.list", he esborrat la línia 56 que era la de Libreoffice i ja funciona tot perfectament.

Moltes gràcies.

---

