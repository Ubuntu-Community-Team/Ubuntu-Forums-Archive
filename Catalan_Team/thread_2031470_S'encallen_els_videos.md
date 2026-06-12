---
title: "S'encallen els videos"
date: 2012-07-22
forum: Catalan Team
---

### Post by dmolner on 2012-07-22
Hola,

Després de resoldre diferents problemes amb la versió 12.04, ara hem trobo que els vídeos i l'àudio s'encalla.

El que vull dir es que es queda fent un cicle curt d'un tros del vídeo (com un CD ratllat) i després segueix la reproducció.
Això hem passa tant amb vídeos de la xarxa com del meu disc dur.

Podeu ajudar-me?

Gràcies.

---

### Post by wgarcia on 2012-07-22
Com sempre és convenient que donis el màxim d'informació del teu model d'ordinador, targeta gràfica si la saps. exactament quina aplicació i com l'estàs fent servir quan et passa això, etc.

---

### Post by dmolner on 2012-07-22
Hola,

Pot dir-me com mirar el maquinari?
Hi ha alguna instrucció?

Hem passa amb qualsevol reproductor i tant si es del meu disc dur com si es de Internet.

---

### Post by wgarcia on 2012-07-22
El model de l'ordinador suposo que el tens per algun lloc. En quant al maquinari, el millor és obrir una terminal i escriure:

```
sudo lshw
```

Si et digués que no troba aquesta instrucció, hauràs de fer prèviament

```
sudo apt-get install lshw
```

Tot el que surt l'hauries de copiar i enganxar a 

[http://paste.ubuntu.com](http://paste.ubuntu.com)

i enganxar aquí l'enllaç que surti.

---

### Post by dmolner on 2012-07-23
El Pc es un que m'ha muntat un amic.
Caixa Thermaltake, placa base Asus...

Aquí teniu la parrafada que surt.
[http://paste.ubuntu.com/1107119/](http://paste.ubuntu.com/1107119/)

Gràcies.

---

### Post by wgarcia on 2012-07-24
Doncs la teva gràfica es Intel 2nd generation, en principi no hauria de haver-hi problemes, els controladors són oberts i estan integrats al nucli de Linux. 

Potser pots fer una prova a veure si el sistema gràfic per defecte està causant alguna interferència, entrant a l'escriptori amb l'opció Ubuntu 2D en comptes de Ubuntu (la pots escollir a la pantalla d'entrada on entres l'usuari i la clau clicant sobre el logo d'Ubuntu, si no et surt la pantalla d'entrada, o sigui entres directament a l'escriptori en inicar l'ordinador, l'has d'habilitar a Paràmetres del sistema -> Sistema -> Comptes d'usuari i inhabilitar l'entrada automàtica). 

Un cop que entris proves els vídeos a veure si segueix passant això, si continua passant torna a entrar a l'escriptori Ubuntu (no Ubuntu 2D) i es pot continuar provant coses.

---

### Post by dmolner on 2012-07-24
Dons no.

He entrat amb l'opció Ubuntu 2D i segueix fent el mateix.

Gràcies.

---

### Post by wgarcia on 2012-07-25
Dos suggeriments més:

1) Tens ubuntu-restricted-extras instal·lat? Ho pots mirar al Centre de Programari.

2) Passa amb tots els formats de vídeo, o sols amb algun tipus de format, per exemple "Flash"?

---

### Post by dmolner on 2012-07-25
Sembla que tinc instal·lada la versió 57, no?
ubuntu-restricted-extras 57

Hem passa amb youtube, tv3, 
Si pots dir-me alguna web per provar altres arxius.

---

### Post by wgarcia on 2012-07-26
Pots provar dos diferents a veure si és un problema de flash. Primer un en format HTML5:

[http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&ved=0CH8QFjAG&url=http%3A%2F%2Fwww.808.dk%2F%3Fcode-html-5-video&ei=tOcQUMaVJeah0QWj3YCwAg&usg=AFQjCNFVkU7NiMY5W2SQpJybKQq0Yk-Dsg&sig2=fRXOcrPMwOjt4NDTySHLDg](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=7&ved=0CH8QFjAG&url=http%3A%2F%2Fwww.808.dk%2F%3Fcode-html-5-video&ei=tOcQUMaVJeah0QWj3YCwAg&usg=AFQjCNFVkU7NiMY5W2SQpJybKQq0Yk-Dsg&sig2=fRXOcrPMwOjt4NDTySHLDg)

i ara un de Flash, per exemple

[http://www.youtube.com/watch?v=B8tSMKGbnW0](http://www.youtube.com/watch?v=B8tSMKGbnW0)

Pots reproduir el teu problema amb aquests exemples?

---

### Post by dmolner on 2012-07-26
Tots dos s'enganxen :-(

---

### Post by wgarcia on 2012-07-27
Si baixes un vídeo a l'ordinador, i el reprodueixes directament a l'ordinador, també "s'enganxen"?

---

### Post by dmolner on 2012-07-27
> **wgarcia said:**
> Si baixes un vídeo a l'ordinador, i el reprodueixes directament a l'ordinador, també "s'enganxen"?

Si ho vaig comentar al post inicial.
Hem passa tant amb els vídeos de Internet com amb els del disc dur.
També amb algun joc tipus Flash.

Estic pensant si no pot ser algun problema del PC que falli de tant en tant i només ho noto amb els vídeos o l'àudio.

---

### Post by wgarcia on 2012-07-28
Una altra manera d'intentar obtenir més informació és la següent. Descarrega't algun vídeo a, per exemple, la teva carpeta d'inici. Suposem que es diu video.flv. Obre una terminal, navega si no està ja a la carpeta d'inici. Corre el vídeo des de la terminal amb, per exemple, "totem", amb:

```
totem video.flv
```

Mira a la terminal a veure si surten algunes línies d'advertiment o error, i si és el cas engantxa-les aquí.

I encara una altra manera que no hem provat. Entra al compte convidat i mira si també s'observa el problema amb aquest compte.

---

### Post by dmolner on 2012-07-28
Això es el que hem surt:

(totem:6593): GLib-GObject-CRITICAL **: Read/writable property 'object' on class 'ZeitgeistDpPlugin' has type 'TotemObject' which is not exactly equal to the type 'GObject' of the property on the interface 'PeasActivatable'

S'ha encallat varies vegades.
He mirat amb el monitor del sistema i cap dels 4 processadors ha arribat al 20%.

Amb l'usuari convidat el mateix vídeo des de Internet no s'enganxa en cap moment.

Gràcies per ajuda que m'estas donant.

---

### Post by wgarcia on 2012-07-28
Doncs si amb l'usuari convidat no s'enganxa en cap moment, sembla que és un problema del teu usuari. Tens moltes configuracions, o podries crear-te un altre usuari? Vull dir: favorits del navegador, i altres configuracions que es puguin perdre si crees el nou usuari.

Per una altra part el missatge que has enganxat de "totem" també em surt a mi, per tant no sembla ser la causa del problema, perquè a mi no se m'enganxen.

---

