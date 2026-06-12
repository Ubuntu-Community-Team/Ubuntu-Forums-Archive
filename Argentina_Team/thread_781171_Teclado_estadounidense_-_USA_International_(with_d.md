---
title: "Teclado estadounidense - USA International (with dead keys)"
date: 2008-05-04
forum: Argentina Team
---

### Post by Kabezon on 2008-05-04
Desde que instale HH que no me funciona mas la configuracion de mi teclado para poder usar tildes. Tengo un teclado yankee, asi que lo habia seteado para que Alt sea la tecla para componer ( con Alt+tal letra = tal simbolo). La cosa es que ahora ya no funca! Es un bajon no poder usar tildes, sobretodo cuando tengo que escribir algo enserio. No me explico por que dejo de funcionar -.-! Alguno sabe que puede ser?

---

### Post by MeduZa on 2008-05-04
> **Kabezon said:**
> Desde que instale HH que no me funciona mas la configuracion de mi teclado para poder usar tildes. Tengo un teclado yankee, asi que lo habia seteado para que Alt sea la tecla para componer ( con Alt+tal letra = tal simbolo). La cosa es que ahora ya no funca! Es un bajon no poder usar tildes, sobretodo cuando tengo que escribir algo enserio. No me explico por que dejo de funcionar -.-! Alguno sabe que puede ser?

yo tambien tengo el teclado ese sin lo de dead keys y lo setie llendo a teclado layout y activando la tecla componer o composer.
despues es simple sumas dos o mas teclas: a + ' = á y cosas asi.

Suerte

---

### Post by fbianconi on 2008-05-04
Yo lo que hice es en el archivo /etc/X11/xorg.conf, en la sección de teclado
metés estas dos líneas:
```
  option "XkbLayout" "us"
  option "XkbVariant" "intl"
```
a mí me quedó así:
```

  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
  option "XkbVariant" "intl"

```
guardá todo,
cerrás sesión,
rearrancás xorg (ctrl+alt+backspace)
y volver a inicairla.
(podés matar el servidor X con ctrl+alt+backspace con una sesión abierta, pero mejor si cerrás sesión primero)

---

### Post by Kabezon on 2008-05-07
> **MeduZa said:**
> yo tambien tengo el teclado ese sin lo de dead keys y lo setie llendo a teclado layout y activando la tecla componer o composer.
despues es simple sumas dos o mas teclas: a + ' = á y cosas asi.

Suerte
Eso mismo hice yo! Puedo poner tildes y demás haciéndolo cómo vos me explicás, pero, por ejemplo, cómo abro signo de interrogación o exclamación? Antes hacía Alt+1 y me salia abrir signo de exclamación, o Alt+? y me salía el de interrogación abierto, ya no :S!

> **fbianconi said:**
> Yo lo que hice es en el archivo /etc/X11/xorg.conf, en la sección de teclado
metés estas dos líneas:
```
  option "XkbLayout" "us"
  option "XkbVariant" "intl"
```
a mí me quedó así:
```

  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc104"
  option "XkbLayout" "us"
  option "XkbVariant" "intl"

```
guardá todo,
cerrás sesión,
rearrancás xorg (ctrl+alt+backspace)
y volver a inicairla.
(podés matar el servidor X con ctrl+alt+backspace con una sesión abierta, pero mejor si cerrás sesión primero)
Quedo en la misma que antes, el alt sigue sin funcionar :S

---

### Post by MeduZa on 2008-05-07
> **Kabezon said:**
> Eso mismo hice yo! Puedo poner tildes y demás haciéndolo cómo vos me explicás, pero, por ejemplo, cómo abro signo de interrogación o exclamación? Antes hacía Alt+1 y me salia abrir signo de exclamación, o Alt+? y me salía el de interrogación abierto, ya no :S!


Quedo en la misma que antes, el alt sigue sin funcionar :S

abrir signo: [componer] + [shift] + ? + ?

comunmente las ¿? se hacen con la misma tecla mas la misma tecla

ejemplos: ¡! ¿? y asi con todo
es muy intuitivo y usando la imaginacion sacas muchas cosas utiles como:

O + c = © ; O + r = ® ; c + | = ¢ ; o + e = œ ; a + e æ y mucho mas ;)

---

