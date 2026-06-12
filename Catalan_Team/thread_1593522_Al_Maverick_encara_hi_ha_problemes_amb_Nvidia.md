---
title: "Al Maverick encara hi ha problemes amb Nvidia?"
date: 2010-10-11
forum: Catalan Team
---

### Post by Ivan Roig on 2010-10-11
Hola Ubuntaires!
 
Fullejant alguns fòrums en anglès he conclòs que el nou Ubuntu (el Maverick) segueix donant problemes amb les targetes gràfiques Nvidia (motiu pel qual no vaig fer el salt al Lucyd i segueixo amb el Koala). Ara bé, les meves mancances (més en terminologia informàtica i linuxera que no pas amb l'anglès) fan que sigui incapaç d'entendre si són el mateix tipus de problemes (és a dir, difícils de solucionar per a un profà com jo) o ara ja serien una mica més senzills. ¿En sabeu res?

---

### Post by epileg on 2010-10-11
Jo només sé que tinc una tarja de vídeo nvidia amb els controladors privatius a Ubuntu 10.04 i em funciona correctament.

De quina mena de problemes parles?

---

### Post by Ivan Roig on 2010-10-12
Hola Epíleg,

el problema exacte, com que ja en fa un any, no el recordo. La simptomatologia era que, un cop vaig instal·lar la Lucid des de zero (vaig voler aprofitar per a formatar el disc dur), en reiniciar-se l'ordinador la pantalla se'm quedava en negre. Com que era un portàtil, el vaig dur a casa mons pares i des del seu ordinador vaig consultar fòrums per a provar de solucionar-ho, però no me'n vaig poder sortir malgrat haver-hi perdut el temps i la paciència de 2 tardes senceres. Cal considerar, a sobre, que el meu lector de CD funciona una de cada 10 vegades (el meu ordinador és un fòssil, gairebé), amb lo que algunes parts del procés es feien molt i molt lentes i desesperants. Com que necessitava l'ordinador i no volia perdre la xaveta, finalment vaig llançar la tovallola i optar per reinstal·lar-me el Koala. 

PD: a l'ordinador de mon pare (que encara en sap menys de Linux que jo) també hi roman el Koala, per la por que no li passés el mateix que al meu.

---

### Post by epileg on 2010-10-12
Has provat a crear/personalitzar un fitxer «xorg.conf»? Si l'ordinador és tant vell com dius, potser és problema de que la pantalla no informa correctament de les seves característiques.

Quan a l'unitat de cd no ho sé. A Koala no et falla gens ni mica i a Lucid sip? És estrany.

---

### Post by guillemsola on 2010-10-12
Jo tinc un parell de gràfiques NVidia amb 10.04 que ara he passat a 10.10 i sense problemes. Potser és per fer servir la versió lliure del driver, la de nvidia a mi no m'ha donat cap problema.

Respecte el CD, has probat a netejar-lo amb un bastó de netejar orelles i una mica d'alcohol? arq que aixó té fàcil solució amb un pendrive i el unetbootin

salut

---

### Post by Daerun on 2010-10-13
> **Ivan Roig said:**
> PD: a l'ordinador de mon pare (que encara en sap menys de Linux que jo) també hi roman el Koala, per la por que no li passés el mateix que al meu.

En principi, els sobretaula no tenen problemes amb Nvidia, o com a mínim no en donen tants com els portàtils.

---

### Post by wgarcia on 2010-10-14
Jo crec que en general estan força resolts els problemes, més des que van aparèixer els mòduls "noveau" que estan al propi nucli. És possible que en les noves instal·lacions que hagis provat s'hagi posat per defecte aquests mòduls dels nuclis, però que per les targetes que tens als ordinadors que menciones encara vagi millor els mòduls provistos pel propi NVIDIA. 

Potser ajudaria saber exactament de quina targeta gràfica es tracta, cosa que pots veure obrint una terminal (Aplicacions -> Accessoris -> Terminal), entrant el següent:

lspci | grep VGA

i prement "Intro".

---

### Post by Ivan Roig on 2010-10-14
Hola Ubuntaires!
 
gràcies pels tots els consells, però per culpa d'un imprevist no podré disposar del meu ordinador fins diumenge, i no he pogut fer-hi res del que m'heu dit. Diumenge us ho explico.
 
PD: Perdoneu un missatge que no aporta res, però em semblava lleig si m'estava uns dies sense dir res quan havia estat jo qui havia obert el fil i quan he rebut tantes respostes i tan agraïbles.

---

