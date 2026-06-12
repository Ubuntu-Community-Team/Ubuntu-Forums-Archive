---
title: "diversos usuaris amb lucid"
date: 2010-03-26
forum: Catalan Team
---

### Post by SiscoGarcia on 2010-03-26
Hola gent,

Aquí fent proves amb la lucid.

Hem detectat un problema amb diverses màquines (un portàtil Visa Clip amb Lubuntu i un Dell Vostro 230S amb ubuntu) i és que només funciona l'usuari creat en primer lloc. No permet canviar d'usuaris. En sabeu alguna cosa? No he trobat res a cal Google :(

---

### Post by papapep on 2010-03-26
I si en arrencar tries un o altre funcionen? o tampoc i només funciona l'usuari "instal·lador"?

---

### Post by SiscoGarcia on 2010-03-26
No funcionen de cap manera, ni canviant d'usuari ni en arrancar. Només funciona l'usuari "instal·lador".

---

### Post by papapep on 2010-03-26
I si l'afegeixes a manilla amb un:

```
sudo useradd -m nouusuari
```

i

```
sudo passwd nouusuari (i li assignes una contrassenya)
```

tampoc furula?

---

### Post by SiscoGarcia on 2010-03-26
Acabo de provar-ho amb la lubuntu i la teua proposta no m'ha funcionat, en canvi he pogut accedir amb un dels usuaris que ja tenia creats amb anterioritat que tenia privilegis d'administrador també.

mmmm continuaré investigant! Ja explicaré.

EDITO: Acabo de provar d'entrar amb un altre usuari creat amb anterioritat sense privilegis d'administrador i tampoc no he aconseguit entrar-hi.

---

### Post by SiscoGarcia on 2010-03-26
Ara ha funcionat. Calia "activar" el compte. M'explico, he hagut d'anar a "usuaris i grups" i activar l'usuari perquè no ho estava (hi havia la casella "enable user" desactivada). Ho he fet i ha funcionat. Però no m'ha servit per l'usuari no administrador que tenia creat de forma gràfica amb anterioritat :(

Merci ;)

---

### Post by papapep on 2010-03-26
Uhm, alguna cosa se m'escapa, Sisco:

On dius que hi ha la caixa de verificació aquesta per habilitar l'usuari?? He buscat, crec, a tot arreu de l'eina gràfica de gestió d'usuaris i no ho he sapigut trobar.

[http://yfrog.com/5sscreenshot003tp](http://yfrog.com/5sscreenshot003tp)

Com s'havia creat aquest usuari? amb la mateixa eina gràfica? per l'intérpret d'ordres? Jo ho he provat a la mv que tinc de la 10.04 completament actualitzada i no m'he trobat amb res del que esmentes.

---

### Post by SiscoGarcia on 2010-03-26
No se t'escapa res,... i ara.

Sí que és aquesta l'eina gràfica a què em refereixo. La caixa que et comento només surt quan l'usuari no està habilitat. Els havia creat des d'aquesta mateixa eina, i no puc entendre perquè passa això.

Si vols provar-ho, pots fer-ho des d'aquesta eina que mostres anant a "advanced settings" i allà a "Avançats" triar l'opció "Dissable account". Així és com et surtirà l'opció que esmento; sento no poder passar-te una captura, no sé si és la lubuntu o la màquina però no puc fer-ho :(

---

### Post by papapep on 2010-03-26
Que no, que no, que jo no tinc aquesta opció, i no em surt on tu dius que la trobes:

[http://img189.yfrog.com/img189/2308/screenshot004pl.png](http://img189.yfrog.com/img189/2308/screenshot004pl.png)

misteris a les fosques, hoyga...

Ja tens la màquina 100% actualitzada? Si és una Lubuntu, potser han tocat alguna cosa, no sé..

---

### Post by SiscoGarcia on 2010-03-26
> **papapep said:**
> Que no, que no, que jo no tinc aquesta opció, i no em surt on tu dius que la trobes:

[http://img189.yfrog.com/img189/2308/screenshot004pl.png](http://img189.yfrog.com/img189/2308/screenshot004pl.png)

misteris a les fosques, hoyga...

Doncs a mi sí que em surt (adjunto captura); a més amb un altre ordinador on hi he instal·lat la lucid amb gnome i hi he afegit nous usuaris a manilla.

> **papapep said:**
> Ja tens la màquina 100% actualitzada? Si és una Lubuntu, potser han tocat alguna cosa, no sé..

Tinc la màquina 100% actualitzada. Pensava que era la Lubuntu, però també em passa amb l'ubuntu :(

Si de cas demà en parlem, ara vaig a sobar... que ja és hora.

---

### Post by SiscoGarcia on 2010-04-10
Ja he pogut crear usuaris nous i accedir-hi sense problemes. Suposo que s'ha resolt amb alguna actualització.

Per cert, ja es pot tornar a marcar els fils com a [Solved] ;)

---

