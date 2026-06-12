---
title: "Wine i Encore"
date: 2007-10-09
forum: Catalan Team
---

### Post by Asus4 on 2007-10-09
Salut!

He instal·lat el programa "Encore" d'edició de partitures en Windows. Mitjançant el Wine se m'ha instal·lat correctament, però, alhora d'executar-lo m'apareix un error just al principi:

"[B]Unable to initialize MIDI DLLs.
Make sure Encore has been installed properly.[/B]"

No entenc què m'està dient. Algú m'ho pot traduïr?

Cal que digui que, si l'error no es pot solucionar tampoc seria tant greu. Hi ha programes de partitures per Ubuntu, el que passa és que els que vaig provar fins ara (note edit, denemo) els he trobat un pèl complicats d'utilització i perquè enganyar-nos, estava molt ben acostumat al "Encore" hehehe..

Apa, un salut ubuntaires!

---

### Post by papapep on 2007-10-09
> "Unable to initialize MIDI DLLs.

No es poden inicialitzar les llibreries dinàmiques MIDI.

> Make sure Encore has been installed properly."

Assegureu-vos que Encore s'ha instal·lat correctament.

---

### Post by CarlesOriol on 2007-10-10
Seguint les instruccions que t'he donat a l'altre fil jo he pogut executar el band in a box amb el wine.

Comprova que tinguis carregat el modprobe snd-seq, que tinguis el timidity com a servei i que el gestor de so que usis al timidity sigui el mateix que tens configurat al winecfg

---

### Post by Asus4 on 2007-10-10
> Comprova que tinguis carregat el modprobe snd-seq, que tinguis el timidity com a servei i que el gestor de so que usis al timidity sigui el mateix que tens configurat al winecfg

Perdona la meva ignorància...però amb el Wine em faig un lio i no sé exactament com funciona:

-Com puc comprovar que tingui carregat el **modprobe snd-seq**?

-Com puc saber si tinc el **timidity** com a servei?

-Com puc saber quin és el **gestor de so que tinc configurat al Winecfg** i canviar-lo al mateix que tinc al timidity?

---

### Post by Ferri on 2007-10-10
No sé si és exactament el que busques, però jo algun cop he fet servir Lilypond + Denemo per editar alguna partitura per al meu fill i m'ha anat prou bé.

---

### Post by Asus4 on 2007-10-14
En principi amb el midi no tinc cap problema, el que passa és que em sorgeixen complicacions al utilitzar el Wine. Com puc fer per solucionar   això?
Tal com m'ha dit en CarlesOriol, haig de: 

- comprovar que tingui carregat el modprobe snd-seq

- saber si tinc el timidity com a servei

- saber quin és el gestor de so que tinc configurat al Winecfg i canviar-lo al mateix que tinc al timidity

Però el que passa és que no sé com fer tot això...
Em podeu ajudar? Gràcies!

Per cert, si el Band-in-a-Box es pot instalar perfectament (tal com ha dit en CarlesOriol, jo no ho he provat encara, però no descarto fer-ho), l'error que tinc és incompatibilitat total del Encore per funcionar amb el Wine, o és que tinc alguna cosa mal configurada?

Val a dir que vaig seguir al peu de la lletra l manual que em vau detallar a l'altre post "problemes amb midi".

Salut!

---

### Post by papapep on 2007-10-14
> - comprovar que tingui carregat el modprobe snd-seq

- saber si tinc el timidity com a servei

- saber quin és el gestor de so que tinc configurat al Winecfg i canviar-lo al mateix que tinc al timidity

Com va dir en Harry l'Esbudellador, anem a pams....;-)

1) Per saber si tens qualsevol mòdul carregat:

```
lsmod |grep snd-seq
```

com que a vegades costa saber el nom exacte del mòdul es pot ficar només part del nom:

```
lsmod | grep snd
```

Si no poses el "|grep snd" et sortiran tots els mòduls carregats en aquest moment.

2) Saber si tens el timidity com a servei:

Si vas a Sistema > Administració > Serveis, veuràs tots els serveis que tens i si estan activats o no.

3) Sobre el gestor de so i el wine i tot plegat, ni idea. Ho sento.

---

### Post by Asus4 on 2007-10-14
He provat d'instal·lar el Band-in-a-Box amb el Wine i em funciona. El puc executar, escoltar el midi i tota la pesca.

L'única pega és que em funciona però molt lent. Triga a executar-se, quan li dic que reprodueixi una peça l'ordinador es col·lapsa una mica i quan toco alguna altra aplicació la musica va a batzegades. Suposo que la solució a aquest problema seria millorar a nivell de maquinari l'ordinador, perquè ja fa bastant temps que no li toco res (AMD 1Gh, GeForce2, 756mb RAM...) és un ordinador força antic.

D'altra banda, el problema amb l'Encore segueix persistent. Deu ser problema del mateix programa...

Val a dir que he trobat un manual força interessant per midi, [aquí el deixo per qui el necessiti]("http://www.google.es/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fdracks.googlepages.com%2Fmanual.pdf&ei=_Y0SR7ahNqbywwGa3ZnLDw&usg=AFQjCNElV9P-IKUCKTkK8o65a4rdK3mRaA&sig2=ygm3sBvffSLTEoKkxnhQ3A").

Fins aviat!;)

---

