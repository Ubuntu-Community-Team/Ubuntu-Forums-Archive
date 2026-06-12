---
title: "sobre easyubuntu y automatix"
date: 2007-07-08
forum: Argentina Team
---

### Post by Kantier on 2007-07-08
digo, vio... creo que taría copado un sticky diciendo "NO USEN ESTO, REVIENTA EL BALANCE ECOLÓGICO DE SUS SISTEMAS".

hasta donde tengo entendido, esos "facilitadores" no aportan nada por encima de apt-get y además ***** en temas delicados.

se podría poner una explicanción de qué es apt-get (y por qué apt gets you).

o por ahi es nomás un delirio mío... díganme ustedes, queridos co-foristas :D

---

### Post by sdm_cacto on 2007-07-08
A mi no me trajo problemas... nose, creo q funciona bien automatix ...a vos q t pasó?

---

### Post by marianom on 2007-07-08
Canonical ha hecho simpre la expresa aclaración que no soportarán ni aceptarán reclamos por el uso ni de Automatix ni EasyUbuntu. Personalmente coincido que son aplicaciones peligrosas y si te paseas un rato por el foro general cuando hay una actualización de Automatix vas a ver varios reclamos por problemas generados. Mi opinión: es una ruleta, a veces te va a tocar.

---

### Post by Kantier on 2007-07-08
> **sdm_cacto said:**
> A mi no me trajo problemas... nose, creo q funciona bien automatix ...a vos q t pasó?
a mi personalmente no me pasó nada, pero como dice marianom a mucha gente si. el punto es evitarse estas situaciones::

P: se me rompió esto, ¿qué hago?
R: depende, cómo lo instalaste
P: con automatix
R: *se golpea la cabeza contra el monitor*

---

### Post by marianom on 2007-07-08
Una vez, hace como un año, se mandaron una grosa, ya no me acuerdo cual (algo con el X11 me parece). Ultimamente lo que está pasando es que cuando actualizan el sources.list agregan (sin intención, eso es más que obvio) algunos errores e impiden que pueda ser leído correctamente.

---

### Post by undiaperfecto on 2007-07-08
Yo recomiendo usar automatix para los codecs y algun que otro programa.
Pero para instalar los drivers de nvidia, recomiendo hacerlo por consola, porque automatix es una loteria.
Y amsn te instala una version muy mala.

---

### Post by Darth Trix on 2007-07-08
No todo lo que se tiene que bajar con easyubuntu y autimatix es peligroso. 
Hay muchos paquetes que tenes que bajar si o si  de esos repos no porque sean peligrosos, sino porque por imbecilidad o lobby empresario son ilegales en los Estados Unidos y Canonicla no los puede poner en sus repos oficiales.

---

### Post by Kantier on 2007-07-08
> **Darth Trix said:**
> No todo lo que se tiene que bajar con easyubuntu y autimatix es peligroso. 
Hay muchos paquetes que tenes que bajar si o si  de esos repos no porque sean peligrosos, sino porque por imbecilidad o lobby empresario son ilegales en los Estados Unidos y Canonicla no los puede poner en sus repos oficiales.
uhm.. ¿repos 3rd party?

este es el /etc/apt/sources.list de mi maquina: (o sea, la lista de repositorios para apt-get)

```

## feisty
deb http://ar.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

## Major bug fix updates produced after the final release of the distribution.
deb http://ar.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

## BACKPORTS
deb http://ar.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

## SECURITY
deb http://ar.archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb-src http://ar.archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse


## MoBlock - ip blacklist anti-MAFIAA
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main

## WineHQ - Ubuntu 7.04 "Feisty Fawn"
deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main

## Beryl
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main

## Elbuntu
# deb http://e17.sos-sts.com feisty e17
deb http://edevelop.org/~lut1n/ubuntu feisty e17


# SPring - Ubuntu Edgy Eft -- ANDA, PERO REVISAR REPO DE FEISTY!!!
deb http://www.osrts.info/~tvo/deb edgy spring

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://packages.medibuntu.org/ feisty free non-free


## KDE 3.5.7
# deb http://kubuntu.org/packages/kde-357 feisty main

## The Mana World
deb http://bertram.ifrance.com/ ubuntu edgy

## Google Repos
deb http://dl.google.com/linux/deb/ stable non-free

```

mi punto siendo: EasyUbuntu y Automatix te instalan cosas "a mano" que podrían instalarse poniendo un repo extra en el sources.list y bajando las cosas, o en el peor de los casos mirando los repos y bajando los .deb que corresponden. no es demasiado dificil hacer un script que haga eso, con variaciones para cada distro. creo que me voy a poner a programar un script en bash para instalar ese tipo de cosas. paso 1: investigar cómo hago para que muestre un frontend en gtk/qt y que sea mínimamente utilizable.

---

### Post by Hex_Mandos on 2007-07-08
Yo hice un script en bash precisamente para hacer eso, es facilísimo. Podés usar zenity para tener una interfaz gráfica vía cuadros de diálogo. Si querés, hay un script que se llama SciBuntu que instala programas científicos, podés googlearlo y usarlo como modelo.

---

### Post by marianom on 2007-07-08
> **Darth Trix said:**
> No todo lo que se tiene que bajar con easyubuntu y autimatix es peligroso. 
Hay muchos paquetes que tenes que bajar si o si  de esos repos no porque sean peligrosos, sino porque por imbecilidad o lobby empresario son ilegales en los Estados Unidos y Canonicla no los puede poner en sus repos oficiales.

El problema no son los paquetes en sí, creo más bien que es el packaging.

---

### Post by Hex_Mandos on 2007-07-08
En realidad, hay paquetes que en EEUU son de legalidad dudosa. Ej: w32codecs y libdvdcss2. Acá no están prohibidos (w32codecs es más complicado, pero en la medida que no lo vendas no debería ser punible), pero  una empresa como Canonical es lógico que quiera evitar cualquier responsabilidad civil o penal.

---

