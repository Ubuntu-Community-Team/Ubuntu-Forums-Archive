---
title: "Corrector gramatical catalá Thunderbird"
date: 2007-11-21
forum: Catalan Team
---

### Post by prostata on 2007-11-21
Bon dia:

Avui m'he donat que al fer l'actualització a gibbon, el ThunderBird m'ha perdut ¿? el corrector gramatical de catalá. he fet el següent per re-instal-lar-lo, pero no em dona cap resultat, podeu indicar-me on rau l'error?? gràcies

Dins el TB, he fet descarregar mes diccionaris
dins la pàgina primer he fet: sel-leccionar diccionari catalá-instalar. Teòricament s'ha instal-lat però no surt per en lloc.
l'altre opció ha estat, seleccionar amb botó dret del mouse l'arxiu, desar-lo en un directori i desprès al firefox Eines/complements/extensions/instalar...no proueix cap efecte.
De fet dins complements extensions veig el diccionari catalá, pero no apareix dins el thunderbird...

què estic fent malament???
gràcies

---

### Post by Ferri on 2007-11-21
> **prostata said:**
> l'altre opció ha estat, seleccionar amb botó dret del mouse l'arxiu, desar-lo en un directori i desprès al firefox Eines/complements/extensions/instalar...no proueix cap efecte.
Les extensions de Thunderbird les has d'instal·lar des de Thunderbird i no ho pots fer directament com al Firefox. Les has de desar, com ja has fet, i després, des del **Thunderbird**, a Eines->Complements->Instal·la, navega a la carpeta on hagis desat l'extensió.
Per cert, quan dius corrector gramatical vols dir corrector ortogràfic (no conec l'existència del corrector gramatical, però si hi és el vull)?

---

### Post by prostata on 2007-11-21
Ferri, avans m'he oblidat de descriu-re aquesta opció què també he fet. Però el resultat continua igual, no apareix-en els correctors ortogràfics.. ¿?

---

### Post by jodufi on 2007-11-22
Ferri, pots trobar un corrector gramatical a:
[http://parles.upf.es/corrector/index.aspx]("http://parles.upf.es/corrector/index.aspx")
Funciona en línia i també el pots baixar.

Salut

P.S. Si, ja sé que el tema del fil era un altre ....

---

### Post by lpargemi on 2007-11-24
Hola

A mi el corrector ortogràfic en català només m'ha funcionat bé al Thunderbird després d'haver-lo instal.lat al firefox. 

Potser es casualitat, però la seqüència ha estat aquesta. I en dues ocasions m'ha passat el mateix.

Salut

Lluís

---

### Post by eselma on 2007-11-26
> **prostata said:**
> Bon dia: Avui m'he adonat que al fer l'actualització a gibbon, el ThunderBird m'ha perdut ¿? el corrector gramatical de català.He fet el següent per re-instal-lar-lo, pero no em dona cap resultat, podeu indicar-me on rau l'error?? gràcies

Dins el TB, he fet descarregar mes diccionaris dins la pàgina primer he fet: sel·leccionar diccionari català-insta·llar. Teòricament s'ha instal-lat però no surt per en lloc. L'altre opció ha estat, seleccionar amb botó dret del mouse l'arxiu, desar-lo en un directori i desprès al firefox Eines/complements/extensions/insta·llar...no produeix cap efecte.
De fet dins complements extensions veig el diccionari català, però no apareix dins el thunderbird... què estic fent malament???
gràcies

El programari de Mozilla (*Firefox, Thunderbird*, etc) usen el corrector *MySpell*; l'*OpenOffic*e també. Com que els usuaris normalment usem els correctors en els mateixos idiomes sigui quina sigui l'aplicació, això pot produir triplicar (pel cap baix) el nombre total de diccionaris instal·lats. Per tal d'aprofitar millor els recursos, Ubuntu (en el meu cas [COLOR="Blue"]Kubuntu[/COLOR]) els instal·la en un directori únic, i aplica *enllaços tous* des de cada aplicació fins al directori centralitzat, que és el que té els diccionaris "físicament".

Aquesta solució simple es complica pel fet que l'*OpenOffic*e necessita els diccionaris amb el nom en format [COLOR="Red"]*ca_ES.dic*[/COLOR] en lloc de l'original *ca-ES.dic*, per exemple. Cap problema: han posat enllaços tous al directori [COLOR="Purple"]/usr/share/myspell/dicts/ooo[/COLOR] que dupliquen cada fitxer amb els dos noms. Llavors, lògicament, si obres el desplegable de tria de diccionaris al *Thunderbird*, a més de sortir-te "[COLOR="DarkGreen"]Català/Espanya[/COLOR]" també et surt "[COLOR="Red"]ca_ES[/COLOR]" o una cosa semblant. Normalment escric en català i en anglès; alguna vegada en castellà o francès, i aquest reguitzell de diccionaris em fa nosa. 

Les aplicacions de *Mozilla* tenen els diccionaris a:

*/usr/lib/thunderbird/dictionaries/*            i

*/sr/lib/firefox/dictionaries/*

**Compte:** abans eren a */usr/lib/mozilla-thunderbird/components/myspell* ; potser per això no s'instal·len bé els diccionaris des del lloc web de *Mozilla*, si és això el que has fet.

En el meu cas he fet el següent (hi ha altres formes, potser més senzilles de fer-ho, però a mi em va bé aquesta):

_ Tot això cal fer-ho com a administrador amb *sudo*_. 

[LIST]
[*]Traslladar (pots copiar-los) els diccionaris que vulguis (els pots descarregar del lloc web, jo els tinc en format *tgz* a un repositori intern) a */usr/share/myspell/dicts/  *  en format ca-ES.dic i ca-ES.aff (només aquests fitxers).


[*]Posar enllaços tous al directori inferior *(/usr/share/myspell/dicts/ooo*) cap als diccionaris dels nivell superior, però donant-los-hi el format [COLOR="Red"]ca_ES.dic[/COLOR] i [COLOR="Red"]ca_ES.aff[/COLOR]. Deixa-hi els fitxers de guionatge (HYPH) i els *Thesaurus* (jo n'hi afegeixo un de català que vaig trobar en algun lloc).  Pots aprofitar per treure els fitxers corresponents a l'ucrainès, anglès de Zimbawe i altres llengües exòtiques que ens han encolomat si no les uses.


[*]Actualitzar la llista del fitxer *dictionary.ls*t de l'Open Office (òbviament, fent còpia de seguretat de l'original). Pots aprofitar per treure les referències a les llengües que has suprimit abans.


[*]Posar un enllaç al directori /usr/lib/thunderbird que apunti a /usr/share/myspell/dicts amb el nom "dictionaries" així:

```

$cd /usr/lib/thunderbird
$ sudo ln -s /usr/share/myspell/dicts/ dictionaries
```

[*] Repetir l'operació amb el Firefox:
```

cd /usr/lib/firefox
$ sudo ln -s /usr/share/myspell/dicts/ dictionaries
```

[*]L'equivalent, ara amb l'Open Office:
```

$cd /usr/lib/openoffice/share/dict/
$ sudo ln -s /usr/share/myspell/dicts/ooo 
```
que és on hi ha els fitxers (i els enllaços) corresponents a l'*OpenOffice*, si has fet bé el primer pas.


[*]Comprovar que tot va bé.
[/LIST]
 Jo ho tinc així des dels temps de la *Dapper Drake* (amb els directoris en vigor llavors) i mai no he tingut problemes.

---

