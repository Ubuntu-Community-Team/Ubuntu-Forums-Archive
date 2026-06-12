---
title: "Potser us trobeu amb aquest problema (esporàdic) a la karmic"
date: 2009-10-30
forum: Catalan Team
---

### Post by orestesmas on 2009-10-30
[SIZE="4"]Símptoma:[/SIZE]

En rearrencar el PC, no carreguen les X. Comencem a tremolar pensant que ja ho tenim tot espatllat.

[SIZE="4"]Situació:[/SIZE]

- Versió de (*)ubuntu: 9.10 (karmic)
- Acabem d'actualitzar el sistema
- Tenim una targeta gràfica Nvidia (potser també passa amb les ATI), amb un controlador [B]privatiu
[/B]
[SIZE="4"]Explicació:[/SIZE]

A la karmic han accelerat molt l'arrencada, a base de llançar processos en paral·lel, que anteriorment es llançaven de forma estrictament seqüencial. Ara, per exemple, les X es carreguen bastant aviat, mentre el sistema encara està efectuant tasques d'inicialització en paral·lel.

A priori això no ha de ser un problema si les tasques concurrents (en paral·lel) no interfereixen entre si, però hi ha (almenys) un cas en que si que ho fan. M'explico:

Si hem actualitzat el sistema i aquesta actualització comporta un canvi de kernel, se'ns demanarà de reiniciar per tal de carregar el nucli nou. Però aquest nucli nou requereix recompilar el mòdul de la targeta gràfica, si aquest és privatiu, perquè les restriccions legals impedeixen distribuir-lo ja compilat pel nou nucli.

Afortunadament, un sistema anomenat DKMS farà la compilació per nosaltres automàticament en arrencar el sistema. El problema és que aquesta compilació triga força (depenent de la màquina) i llavors passa que les X intenten engegar en paral·lel i, en no tenir encara el mòdul compilat fallen, i el sistema ens obsequia amb una bonica pantalla negra.

[SIZE="4"]Solució:[/SIZE]

deixar que acabi de recompilar (ho veurem perquè cessa l'activitat de disc) i tornar a reiniciar. Ara ja podrà carregar el mòdul nou.

---

### Post by jaume69 on 2009-10-31
Quedem avisats,gràcies!!.

Jo l´he instal.lat de nou i verdaderament funciona bastant bé,amb **Gnome**,moltes millores,i coses que han quedat penjades,però...,no es pot tenir tot en un CD Live.
**KDE** és més per profesionals o màquines potents i o en bon estat,relativament...
Jo fa temps que no uso **KDE**,ja en tinc prou ambb **Gnome**.:)

Molts usuaris de **Gnu/Linux** els hi ha agradat bastant en nou **Windows 7**,pel que he vist.
Salut.

---

### Post by SiscoGarcia on 2009-11-01
> **jaume69 said:**
> Molts usuaris de **Gnu/Linux** els hi ha agradat bastant en nou **Windows 7**,pel que he vist.

Jaume, què et passa amb el Windows que aprofites qualsevol fil per parlar-ne?

No oblidis que aquest és un fòrum d'ubuntu, sisplau.

---

### Post by PatrickVogeli on 2009-11-01
> **SiscoGarcia said:**
> Jaume, què et passa amb el Windows que aprofites qualsevol fil per parlar-ne?

No oblidis que aquest és un fòrum d'ubuntu, sisplau.
Ja ho havia dit jo en un altre tema, que sembla que esta un pel obsessionat! :D

EDIT: ara que hi penso.. no sera un talp de microsoft no? xD

---

### Post by SiscoGarcia on 2009-11-01
> **PatrickVogeli said:**
> ara que hi penso.. no sera un talp de microsoft no? xD

En qualsevol cas, jo entenc que no som aquí per parlar de microsoft ni dels seus productes, que ja té prou plataformes que li fan publicitat...

---

### Post by jaume69 on 2009-11-01
Carai,que no es pot parlar de **Microsoft**?.si és així,que els moderadors rectifiquin o esborrin els fils i ja està.
Per una vegada que sembla que Microsoft fa les coses bé i que **Ubuntu** sembla que també.Però Gnu/linux te el camí més fàcil,o no,no ho sé..

-El problema que jo tinc és que no entenc ni de **Gnu/Linux** ni de **Microsoft** a fons...,però ara ja no son hores...

Salud i força.

---

### Post by SiscoGarcia on 2009-11-01
El problema des del meu punt de vista és que aquest no és el lloc per parlar de coses que no tenen a veure amb ubuntu ni amb el programari lliure. A mi el tema MS no m'interessa, no el faig anar, simplement; i suposo que a la resta tampoc; o en qualsevol cas, si els interessa aniran a informar-se a un altre lloc. Personalment et demanaria que deixessis d'insistir amb aquest tema, si tant t'interessa segur que trobes un munt de llocs on discutir i informar-te, però no crec que aquest sigui el millor lloc, aquí estem per una altra cosa.

No crec que calgui la intervenció de cap administrador del fòrum per explicar-te una obvietat com aquesta: això és el fòrum d'ubuntu en català.

---

### Post by Rubunter on 2009-11-02
Si parlessis en rus tampoc seria el lloc adequat per a tu.

---

### Post by jaume69 on 2009-11-02
*-Per una vegada que sembla que Microsoft fa les coses bé i que Ubuntu sembla que també.Però Gnu/linux te el camí més fàcil,o no,no ho sé..*
Perdò,volia dir que ara que els dos grans del software evolucionen conjunts.

-**Ja miraré no parlar-ne de Microsoft**,però a vegades és bo fer petits apunts sense entrar en el tema,com és el que ha passat a aquest fil.
Gràcies.
Salut.

---

