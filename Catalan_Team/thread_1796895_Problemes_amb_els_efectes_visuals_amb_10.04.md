---
title: "Problemes amb els efectes visuals amb 10.04"
date: 2011-07-04
forum: Catalan Team
---

### Post by pmezquita on 2011-07-04
A veure, en primer lloc em presente soc un ubuntaire d'aquells amb més voluntat que coneiximents; salut a tothom. 
Com no, tinc un problema d'aquells que et porten dies i dies de feina i mal de caps i que, fins i tot, un company amb més sabiesa que jo ha estat incapaç de resoldre.
Bé la questió és que recentment he instal·lat la versió 10.04 i quina és la sorpresa que no a les finestres no em ixien els iconets aquests de minimitzar, maximitzar i tancar. Junt amb el meu col·lega hem trobat una solució que consisteix en entrar a sistema /preferencies/aparença i un cop en aparença prémer en efectes visuals punxar en normal. Quan reinicie torna a apareixer en cap (efecte visual) torne a punxar en normal i la cosa marxa bé. El que m'agradaria es saber si algú se li acudeix una sol·lució  per tal de no tenir que fer aquesta operació cada cop que engegue l'ordinador.
Gràcies per la vostra atenció.

---

### Post by quitus on 2011-07-05
Entenc que no apareix el "tema" es a dir el marc que acompanya a les finestres i on apareixen les icones de minimitzar etc...

Pots instal·lar emerald que es un gestor de "temes" per compiz-fusion.

Instal·la també l'editor de la configuració del compiz i en efectes/decoració de la finestra hi ha un lloc on diu:

Ordre: gtk-window-decorator --replace

Ho canvies per: emerald --replace


A veure si tenim sort.

Salut

---

### Post by pmezquita on 2011-07-06
En primer lloc gràcies per la teua resposta. A veure, he fet el que m'has dit però on havia de posar:
gtk-window-decorator -replace. posa usr/bin/compiz-decorator.

---

### Post by quitus on 2011-07-06
Jo tinc la 11.04, segurament be d'aquí, però cap problema, substitueix la línia que tens per la de emerald, si no funciona, sempre podràs tornar enrere tornan a posar la línia original.

salut

---

### Post by pmezquita on 2011-07-09
A veure, ho he provat tot i no funciona. Seguiré trastejant, de moment, només cal cada cop que engegue l'ordinador posar-li els efectes visuals; misteriosament desapareixen cada cop que reinicie. No obstant, gràcies de nou.

---

### Post by wgarcia on 2011-07-10
Prova ALT-F2 i aquí escriure

rm -fr ~/.gconf/apps/compiz

això esborrarà les configuracions de compiz que tens que potser t'estiguin posant en "efectes visuals" sense voler. Aquest directori s'autorecrea si es necessari, i per tant no hi ha perill en esborrar-lo, que jo sàpiga. Penso també que si rehabilites els efectes visuals un cop esborrat aquest directori, apareixeran els controls de les finestres, perquè potser hi hagi a la configuració de compiz alguna cosa malament que no els deixi aparèixer.

---

### Post by pmezquita on 2011-07-11
He escrit el que m'has dit al terminal i res. Us donaré més dades, he generat un nou usuari, bé a d'aquest nou usuari li ixen les finestres com cal. Aleshores, pense que tal vegada al actualitzar al 10.04 alguna cosa de la meua configuració anterior està fent que marxe mal, el que no sé és el que.

---

