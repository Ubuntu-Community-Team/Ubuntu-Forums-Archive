---
title: "Are yoy root? Help soy NW!!"
date: 2007-03-17
forum: Argentina Team
---

### Post by angelcab on 2007-03-17
Bueno les cuento que anoche me decidi e instale Ubuntu v 6.06 LTS for your 64-bits Pc todo joya muy lindo pero quiero reproducir un mp3 y no me deja ... bueno busco en San google como hacer esto y tambien como instalar mi modem Huawei MT 810 pero al querer usar la consola me tira este error ... 
> matanga@matanga-desktop:~$ apt-get install build-essential linux-headers-2.6.15- 23-amd64-generic
E: No se pudo abrir el fichero de bloqueo '/var/lib/dpkg/lock' - open (13 Permis o denegado)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
matanga@matanga-desktop:~$


No se que hacer !! tengo un solo usuario por ende deberia de ser root-

---

### Post by Darth Trix on 2007-03-17
Administrador no es lo mismo que root.

---

### Post by marianom on 2007-03-17
te está faltando el comando sudo para invocar la instruccion como root:

```
sudo apt-get install build-essential linux-headers-2.6.15- 23-amd64-generic
```

Más al respecto, [acá]("https://help.ubuntu.com/community/RootSudo").

---

### Post by marianom on 2007-03-17
Con respecto al tema de reproducir mp3 y otros formatos restringidos (y restrictivos) lee [este documento]("https://help.ubuntu.com/community/RestrictedFormats") que con seguridad te será de ayuda.

---

### Post by angelcab on 2007-03-17
Muchas Gracias por la ayuda estoy navegando desde mi ubuntu !! Gracias totales por la ayuda espero poder ayudar a difundir  Gnu Linux !! 

Que linda sensacion de libertad !!

Edit: No me andan los mp3 y mi ingles no es muy bueno ... alguna otra ayuda?

---

### Post by TattooedFish on 2007-03-17
> **angelcab said:**
> No me andan los mp3 y mi ingles no es muy bueno ... alguna otra ayuda?

Si tu inglés no es bueno, fijate acá, todo está en castellano:
[http://ubuntuguide.org/wiki/Ubuntu_dapper_es](http://ubuntuguide.org/wiki/Ubuntu_dapper_es)

Te diría que guardes esa dirección, la UbuntuGuide (para cualquiera sea el idioma que uno use en su Ubuntu) es una fuente de consulta ineludible y muy útil cuando recién se acaba de instalar el sistema y hay que ir agregando cosas.
Ni bien entrás a la página, bajá un poco hasta donde está el índice de contenidos, fijate primero en *["4.1 Cómo agregar repositorios nuevos"]("http://ubuntuguide.org/wiki/Ubuntu_dapper_es#C.C3.B3mo_agregar_repositorios_nuevos")* y seguí las indicaciones; después de eso fijate en *["6.19 Cómo instalar Codecs Multimedia"]("http://ubuntuguide.org/wiki/Ubuntu_dapper_es#C.C3.B3mo_instalar_Codecs_Multimedia")*.
Según las instrucciones, dice que hay que reiniciar GNOME para que todo ande, lo hacés presionando las teclas Ctrl, Alt y Backspace/Retroceso al mismo tiempo.

Con esto deberías tener todo listo. Después instalate el XMMS y listo (bah, usá el reproductor que quieras, el XMMS es como una especie de clon del Winamp antiguo, chiquito en la pantalla y fácil de usar).

Las instrucciones las copié porque no sabría darte indicaciones más precisas, yo uso el Ubuntu 6.10 en inglés y en una máquina común (es decir, no de 64-bits), y no sé cuáles son las diferencias con el 6.06. Pero siguiendo esas instrucciones todo debería funcionar.

---

### Post by angelcab on 2007-03-18
> **TattooedFish said:**
> Si tu inglés no es bueno, fijate acá, todo está en castellano:
[http://ubuntuguide.org/wiki/Ubuntu_dapper_es](http://ubuntuguide.org/wiki/Ubuntu_dapper_es)

Te diría que guardes esa dirección, la UbuntuGuide (para cualquiera sea el idioma que uno use en su Ubuntu) es una fuente de consulta ineludible y muy útil cuando recién se acaba de instalar el sistema y hay que ir agregando cosas.
Ni bien entrás a la página, bajá un poco hasta donde está el índice de contenidos, fijate primero en *["4.1 Cómo agregar repositorios nuevos"]("http://ubuntuguide.org/wiki/Ubuntu_dapper_es#C.C3.B3mo_agregar_repositorios_nuevos")* y seguí las indicaciones; después de eso fijate en *["6.19 Cómo instalar Codecs Multimedia"]("http://ubuntuguide.org/wiki/Ubuntu_dapper_es#C.C3.B3mo_instalar_Codecs_Multimedia")*.
Según las instrucciones, dice que hay que reiniciar GNOME para que todo ande, lo hacés presionando las teclas Ctrl, Alt y Backspace/Retroceso al mismo tiempo.

Con esto deberías tener todo listo. Después instalate el XMMS y listo (bah, usá el reproductor que quieras, el XMMS es como una especie de clon del Winamp antiguo, chiquito en la pantalla y fácil de usar).

Las instrucciones las copié porque no sabría darte indicaciones más precisas, yo uso el Ubuntu 6.10 en inglés y en una máquina común (es decir, no de 64-bits), y no sé cuáles son las diferencias con el 6.06. Pero siguiendo esas instrucciones todo debería funcionar.


Gracias me andubo Joya y la info que me diste esta increible :-)

---

### Post by felipelerena on 2007-03-18
sin animo de ofender a nadie... creo que es el comentario mas tierno e inocente de la historia del universo

---

### Post by lavaramano on 2007-03-20
> **felipelerena said:**
> sin animo de ofender a nadie... creo que es el comentario mas tierno e inocente de la historia del universo

:lolflag:

---

