---
title: "teclat en anglès per defecte Ubuntu 13.10"
date: 2014-01-07
forum: Catalan Team
---

### Post by fvilaubi on 2014-01-07
He actualitzat el sistema al meu equip portàtil, que estava en 13.04, i a la barra de dalt a la dreta, al costat de les connexions de xarxa tinc una nova icona amb l'idioma del teclat "entrada de text". si faig clic em diu:
 · Es Català (Espanya, L amb punt volat)
   En Anglès (EUA)
es a dir, sembla seleccionat el català. Però per exemple al accent obert em sut [  i al - hi trobo /
sembla el teclat anglès.

Simplement trio En (el punt es posa a En, i a la barra diu un quadre amb En), torno a triar Es català, i el teclat funciona perfectament. 

A la versió 13.04 no tenia cap problema de teclat. L'ordinador te arrencada UEFI. I al fer aquesta actualització m'ha aparegut el iniciador de tota la vida per triar si vull Ubuntu o Windows (que porta l'equip de serie). Vull dir que abans, fins la 13.04 que tenia instalada, si volia pasar a Windows havia de reiniciar i aturar amb F12 l'arrencada, per triar quin sistema volia des del menu boot del equip. Ara ho tinc a un menú que als 8 sg. arrenca automàticament Ubuntu 13.10.

Sabeu que puc fer per triar el teclat correctament a l'arrancada del usuari?

---

### Post by wgarcia on 2014-01-08
Aquest és un problema que ha aparegut amb la versió 13.10. En primer lloc han posat l'indicador que veus al plafó superior (es pot ocultar a "Paràmetres de Sistema" -> "Entrada de text"), per canviar ràpid de teclat, però hi ha alguna cosa al gestor d'entrada al sistema (lightdm) que canvia el teclat sense que tu vulguis.

Mira si alguna de les solucions suggerides en aquesta pàgina et serveixen:

[http://askubuntu.com/questions/362973/keyboard-layout-switches-to-english-each-time-i-reboot](http://askubuntu.com/questions/362973/keyboard-layout-switches-to-english-each-time-i-reboot)

Jo provaria primer la que diu de posar el teclat que vols per defecte en primer lloc de la llista a "Entrada de text", si no està ja primer en la llista.

---

### Post by mendia87 on 2014-01-08
Hola,

Sóc un nou usuari d'Ubuntu, Per si algú li fos útil...

Porto tota la tarda amb la collonada del teclat. He provat de tot, al final com dius he provat el quadrat de d'alt. El cas és que si posava en "Ca" seguia patint aquesta distribució de caràcters. Finalment he provat posant el quadre en "Es", és a dir en espanyol, vet aquí, que m'ha funcionat. Ja he fet la prova de reiniciar el sistema i tot. Funciona bé. 

Salut

---

### Post by wgarcia on 2014-01-09
És possible que el "Ca" no funciona perquè el teclat que tenim a la major part d'ordinadors no es reconeix com a tal sinó com a "Es", oi? Bé, en tot cas a veure si és veritat que s'arregla així. Ja també tinc "Spanish" a la primera línea de la finestra d' "Entrada de text".

---

### Post by fvilaubi on 2014-01-10
Bon dia,
He estat mirant les recomanacions que em proposaves que mires a l'enllaç del "askubuntu", i jo ja tenia el Català a dalt com a primera opció. De fet com us explicava, simplememt triant "Anglès" i tot seguit un altre cop deixar-ho en "Català" era sufucient per que funcionés bé.... fins al proper reboot.

Pero la proposta que fa l'italià de triar "Permet diferents fonts per cada finestra" i la subopció "la nova finestra usa la font per defecte" ha estat suficient per solucionar el problema. Ara sempre tinc el teclat correcte al arrancar l'equip. Dono per bona la sol·lució doncs pel que em sembla no m'afecta al funcionament normal.

D'altra banda constato que la pantalla no esta traduida al català. Si aconsegueixo recordar com s'entra miraré de donar un cop de mà, ara que tinc fresc tot això, i fer la proposta de traducció si encara està pendent.

Molt agraït a tots pels vostres comentaris.
Francesc.

---

### Post by wgarcia on 2014-01-10
L'enllaç al lloc per traduir és:

[https://translations.launchpad.net/ubuntu/saucy/+lang/ca](https://translations.launchpad.net/ubuntu/saucy/+lang/ca)

I en particular aquestes cadenes no traduïdes es poden trobar a:

[https://translations.launchpad.net/ubuntu/saucy/+source/gnome-control-center/+pots/gnome-control-center-2.0/ca/+translate?show=untranslated](https://translations.launchpad.net/ubuntu/saucy/+source/gnome-control-center/+pots/gnome-control-center-2.0/ca/+translate?show=untranslated)

---

