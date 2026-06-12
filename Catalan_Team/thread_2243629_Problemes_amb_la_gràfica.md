---
title: "Problemes amb la gràfica"
date: 2014-09-10
forum: Catalan Team
---

### Post by OriolFusterCabrera on 2014-09-10
Bon dia,

(Disculpeu-me els accents estranys, us escric des d'un teclat italià)

Em dic Oriol i sòc usuari veterà d'Ubuntu i del fòrum (logambusi, era), però feia molt que no hi entrava i sembla que amb el canvi a Ubuntu One he perdut la forma d'entrar-hi.

Vos escric perquè estic patint d'un problema que de fet és bastant reincident, i que va lligat a la gràfica del meu portàtil. Durant la darrera actualitzaciò de sistema sembla que va canviar alguna de les configuracions bàsiques i la gràfica se'n va anar a passejar. Des de llavors no puc entrar a cap banda, ni tan sols en consola. 

Pel que sé, el meu ordinador és un AMD II P320 DUal-Core. La info que tinc de la gràfica és que seria ATI VER010.094.001.047.037038. O alguna cosa aixins :?

Quan provo d'entrar en mode consola no aclarixo res. He descarregat una imatge d'Ubuntu per a USB per a recuperar els tres o quatre arxius importants i fer una instal.laciò des de zero (que em fa bastanta falta, igualment), però em trobo amb la mateixa cosa: quan se'm carrega el menù d'inici de l'USB, la gràfica peta i no puc avançar. I quan em surt el menù de "mode gràfica d'urgència" i intento entrar des de la consola de nou (per fer un apt-get update o alguna cosa aixins) l'ordinador es queda fregit.

I arribats a este punt, honestament, ja no sé per on tirar sense marejar-vos. Vos marejo, per tant :) Alguna idea o proposta? Em serviria molt d'ajut.

Gràcies mil!:lolflag:

---

### Post by wgarcia on 2014-09-10
Benvingut Oriol un altre cop per aquestes contrades. Hauries de proveir el màxim d'informació possible sobre el teu ordinador, és a dir la marca i model, la targeta gràfica que porta i quin sistema d'Ubuntu estàs intentant instal·lar (l'estàndard o alguna variant). 

Si no saps quina targeta gràfica té, entra en mode consola i fes

```

lspci | grep -i vga

```

i t'ho mostrarà, tot i que em sembla que comentaves que tampoc pots entrar en mode consola?

---

### Post by OriolFusterCabrera on 2014-09-10
Exactament, no puc entrar-hi :(

---

### Post by OriolFusterCabrera on 2014-09-10
El més estrany de tot plegat és que una de les vegades que he provat d'entrar amb l'USB s'ha carregat tot de forma correcta. 

En apagar-lo tot seguit per canviar-lo de lloc i connectar-lo a internet, però, ja no m'ha funcionat més, sempre m'ha sortit l'error de la gràfica. 

No podria haver-hi també un tema d'escalfament, o alguna cosa aixins?

---

### Post by wgarcia on 2014-09-10
Potser sí, sempre pot haver-hi una fallada de maquinari. 

Pots iniciar un llapis USB amb Ubuntu? No has comentat quina versió d'Ubuntu estàs intentant instal·lar ni quina és la marca i model del teu ordinador. Suposo pel que dius que la targeta gràfica no saps quina és.

---

### Post by OriolFusterCabrera on 2014-09-10
La versiò que estic intentant instal.lar és la darrera, la del web oficial. 

L'USB l'he intentat iniciar però es queda fregit a mitja càrrega i em diu *Error de gràfica*. 

El model l'he copiat en el post inicial, però no estic segur que sigue això.

---

### Post by wgarcia on 2014-09-12
Potser es pot provar instal·lar la versió mínima, que ve sense gràfica, i després completar la instal·lació instal·lant tota la resta. Aquesta versió mínima la pots baixar d'aquí:

Versió 32 bits:
[http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso)

Versió 65 bits:
[http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-amd64/current/images/netboot/mini.iso)

Has de crear un USB arrencable amb una d'aquestes imatges.

Perquè funcioni l'ordinador ha de tenir accés a Internet.

---

