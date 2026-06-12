---
title: "DVD se ve mal"
date: 2008-05-05
forum: Argentina Team
---

### Post by goliver@arnet.com.ar on 2008-05-05
Hola, instale Ubuntu 8.04 (hardy) y cuando quiero ver un DVD salen todos cuadraditos en vez de la imagen.
Tienen idea de que puede ser?
Tengo instalado todos los codec (GStreamers*).
Lo raro es que la primera vez que lo instale (lo volvi a instalar para ver si se corregia) andaba bien y despues de algunas actualizaciones del sistema se empezo a ver mal.
Los videos de youtube se ven pero no tienen sonido (otro efecto detectado)
Como les dije antes, volvi a instalar Ubuntu 8.04 para ver si se corregia, pero nada.
Espero sugerencias.
Gracias

---

### Post by pante on 2008-05-05
Disculpá el off-topic, pero ¿no te parece peligroso hacer público tu e-Mail? Digo, por el spam y porque es tu nombre de usuario de Arnet, etcétera.

Saludos :)

PS: sobre tu problema con los DVD no puedo ayudarte. Solo que me parece que está protegido contra copia, pero no recuerdo cómo se hace para verlos. :(

---

### Post by atatiducken on 2008-05-06
lo del dvd no se, para lo del audio en firefox tenes q instalar el paquete **libflashsupport**

```
sudo apt-get install libflashsupport
```

saludos :)

---

### Post by faktorqm on 2008-05-06
Te recomiendo que utilices VLC para reproducir cosas. Es super estable y es uno de los mejores. 

```
sudo apt-get install vlc mozilla-plugin-vlc
```

Espero que te haya servido. Salu2!

---

### Post by goliver@arnet.com.ar on 2008-05-06
> **pante said:**
> Disculpá el off-topic, pero ¿no te parece peligroso hacer público tu e-Mail? Digo, por el spam y porque es tu nombre de usuario de Arnet, etcétera.

Saludos :)

PS: sobre tu problema con los DVD no puedo ayudarte. Solo que me parece que está protegido contra copia, pero no recuerdo cómo se hace para verlos. :(

Gracias por el comentario

---

### Post by Mataca on 2008-05-06
Yo, al igual que mi amigo personal Faqtorqm, recomiendo también VLC en mi caso anda de 10. Mplayer es también una excelente opción

Fijate si te falta algun codec que quiza no instalaste, yo cada vez que instalo ubuntu instalo este paquete:

```
sudo aptitude install ubuntu-restricted-extras
```

**Ojo! esto instala muchos paquetes que NO son libres**, como por ejemplo flash. Pero te instala los codecs para DIVX y otras cosas. Quiza te falte algo de eso.

Contanos como te fue

---

### Post by filtro_tuc on 2008-05-06
> **faktorqm said:**
> Te recomiendo que utilices VLC para reproducir cosas. Es super estable y es uno de los mejores. 

```
sudo apt-get install vlc mozilla-plugin-vlc
```

Espero que te haya servido. Salu2!

Segui tu consejo y nada se ve asi.
Sigo probando las otras alternativas.
El problema creo que es de los codec o de alguna biblioteca que cambiaron ultimamente, porque cuando lo instale la primera vez (el dia que salio oficialmente hardy) se veia bien.

---

### Post by filtro_tuc on 2008-05-06
> **Mataca said:**
> Yo, al igual que mi amigo personal Faqtorqm, recomiendo también VLC en mi caso anda de 10. Mplayer es también una excelente opción

Fijate si te falta algun codec que quiza no instalaste, yo cada vez que instalo ubuntu instalo este paquete:

```
sudo aptitude install ubuntu-restricted-extras
```

**Ojo! esto instala muchos paquetes que NO son libres**, como por ejemplo flash. Pero te instala los codecs para DIVX y otras cosas. Quiza te falte algo de eso.

Contanos como te fue

Esto tampoco funciono.

---

### Post by faktorqm on 2008-05-07
che tenes compiz activado? por que me parece que es eso el problema. fijate en tu screenshot que tenes como la marca de agua con el foro atras, y algo se ve del dvd supuestamente, pero mal.
Proba de desactivar compiz y ver el dvd a ver que pasa. Salu2!

---

### Post by hernyman on 2008-05-07
Se le ven cuadraditos porque el DVD, como casi todos los DVDs comerciales está encriptado con CSS. Probá esto:

```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Mas info acá:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Saluditos...

---

### Post by Hernán-Amaya on 2008-05-07
> **hernyman said:**
> Se le ven cuadraditos porque el DVD, como casi todos los DVDs comerciales está encriptado con CSS. Probá esto:

```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Mas info acá:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Saluditos...


y esto también sirve si querés hacer un backup de tu dvd

---

### Post by filtro_tuc on 2008-05-07
> **hernyman said:**
> Se le ven cuadraditos porque el DVD, como casi todos los DVDs comerciales está encriptado con CSS. Probá esto:

```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Mas info acá:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Saluditos...

SIIIIIIIIIIIII esta es la solucion!!!!!!

Muchas gracias!!!!
Esto hay que hacerlo despues de instalar hardy (tenerlo en cuenta)

---

