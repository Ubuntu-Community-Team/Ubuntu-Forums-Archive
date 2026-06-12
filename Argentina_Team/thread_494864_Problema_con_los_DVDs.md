---
title: "Problema con los DVDs"
date: 2007-07-07
forum: Argentina Team
---

### Post by Hex_Mandos on 2007-07-07
Estoy probando mi laptop nueva, y es un caño. Pero tengo un problema con la reproducción de DVDs. Instalé todos los paquetes y codecs necesarios (libdvdcss, etc) y de dos originales que probé, uno no anda (o anda a medias con VLC). Probé reproduciendo con totem-gstreamer, totem-xine, gxine, kaffeine y vlc, y no consigo que ande.También probé borrándolos y volviéndolos a instalar, pero no hay caso. Alguien tiene idea de como solucionar esto?

---

### Post by Al_maverick on 2007-07-07
primero tenemos que saber cual es el problema. Para eso, lo mejor es que abras una consola y corras el kaffeine, por ejemplo, desde ahi. De esa forma los errores que haya los va a mostrar en la consola. Eso postealo aca y a partir de eso podemos ayudarte mas facilmente.

---

### Post by Darth Trix on 2007-07-07
> **Al_maverick said:**
> primero tenemos que saber cual es el problema. Para eso, lo mejor es que abras una consola y corras el kaffeine, por ejemplo, desde ahi. De esa forma los errores que haya los va a mostrar en la consola. Eso postealo aca y a partir de eso podemos ayudarte mas facilmente.

El keffeine le funciona perfectamente, reproduce cualquier otra cosa excepto DVDs originales.
Le dice que el DVD esta codificado y que no puede reproducirlo.

---

### Post by Al_maverick on 2007-07-07
Eso era lo que necesitaba. Lo que le falta es el deCSS, para evitar la "proteccion".
El paquete que tenes que instalar desde adept o synaptic es el libdvdcss2.

De todas maneras, te recomendaria que vieras esta direccion, para info mas completa sobre formatos restringidos. Ahi tenes mas info de por qué no viene incluido por defecto, y como instalar cada uno. Es corto y simple, en 5min deberias tenerlo andando.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Esta en ingles, asi que cualquier duda avisanos.

---

### Post by Hex_Mandos on 2007-07-07
No, tengo los 4 paquetes de reproduccion de dvds (libdvdcss2, libdvdread, etc). De hecho, otro DVD original me anda. Y el que no me anda funca bien en la otra máquina que tengo con Ubuntu, a la que no le instalé nada raro (solo los mismos paquetes, desde el repo de Medibuntu).

Pero el señor oscuro Darth Trix me acaba de pasar el dato final via Jabber: el tema era el seteo de la región. La pasé a 4 y anda perfecto. Odio a las distribuidoras que encriptan su contenido , viva la piratería (digo, porque la peli era piratas del caribe 2... no, no es ****).

En serio. Ahora estoy convencido de que la piratería, además de legal (para uso doméstico, art 19 de la CN) es totalmente moral: con un DVD comprado en el tren no hubiera tenido problema, hubiera andado bárbaro sin escándalo. La encriptación es una estafa.

---

### Post by Al_maverick on 2007-07-08
En general, esas medidas de "proteccion" afectan al usuario comun, y no al verdadero pirata. Pero a los medios les encanta hacer sentir al consumador promedio, su cliente, como si fuera un delincuente, y privarlo de sus derechos con esa excusa.
Mientras tanto, los verdaderos "piratas", esos q se llenan de plata vendiendo copias truchas a $5 en el tren, siguen ganando mejor que nunca. Y no me sorprenderia que estuvieran relacionados de alguna forma con los mismos que "luchan contra la pirateria".

---

