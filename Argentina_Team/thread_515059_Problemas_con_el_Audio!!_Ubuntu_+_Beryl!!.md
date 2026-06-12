---
title: "Problemas con el Audio!! Ubuntu + Beryl!!"
date: 2007-08-01
forum: Argentina Team
---

### Post by Sion Tux on 2007-08-01
Hola,

        Tengo una Notebook Compaq Presario v3017 instalado Ubuntu 7.04 + Beryl! y no tengo audio, ya instale las versiones nuevas del ASLA el icono de sonido esta en Sonidos esta todo en autodetectar, ya me dijeron lo de VirusXP que al pareceer hay que reiniciar la maquina sin la fuente de poder pero no da resultado, lo que mas me intriga es que tuve sonido durante dos dias y luego ya no tuve mas, el volumen de todo esta al maximo, tengo la impresion de que algo esta mal configurado pero no puedo determinar que es.

Ubuntu este excelente y es por eso que quiero migrara de SO pero sin sonido no tiene sentido ya que la uso mas que nada para ver peliculas y escuchar musica, me gustaria poder resolver el problema sin tener que reinstalar Ubuntu, simplemente para que si en un futuro vuelve a pasar o le pasa a alguien saber como resolverlo.

Yo segui los pasos de este link [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) pero  me parece que son para placas Intel y la mia es una Nvidia (HDA Nvidia Conexant CX20549) y todo sin resultado.

Les agradeceria me den una mano ya que estoy atascado con este problema hace dias y me gustaria poder resolverlo de una vez para eliminar Guindows de mi maquina del todo. 

Muchas Gracias de antemano.

Federico.

---

### Post by Sion Tux on 2007-08-02
Hola Amigos, Por favor alguna ayuda o comentario para poder resolver este problema que tengo con el sonido, ya googlie una semana y no encuentro nada que lo resuelva,

Muchas gracias

Federico.

---

### Post by sxxs on 2007-08-20
La verdad soy novato, pero voy a hacer lo posible para ayudarte con ese tema., aplicando lo que aprendi intentando instalar el modem de arnet (huawei smart). Lo mas probable es que le hayas "roto" alguno de los repositores, segun lo que vi estubiste siguiendo un manual de instalacion de los drivers de ubuntu 6.06, y por que e visto a cambiado mucho la forma de instalar algunos dispocitivos (a mi me paso con el modem)., La forma en que yo lo solucione a mi problema luego de mandarme varios lios intentando forzar la instalacion de Linux-Headers-2.6.15-generic es reinstalando el ubuntu 7.04, solamente   formateando donde esta el punto de montaje /
Otra cosa que es bueno recordar ¡si funciona no lo toques!

---

### Post by leo_rockway on 2007-08-20
> **Sion Tux said:**
> me parece que son para placas Intel y la mia es una Nvidia (HDA Nvidia Conexant CX20549)

fijate q las nvidia tienen chip intel. en alsa-project.org, si buscas nvidia te manda a las intel8x0.

---

### Post by sajnox on 2007-08-20
Hola,

A mi me paso algo parecido (tenia sonido y luego dejo de funcionar).

En primer lugar verifica que es lo que te dertecta la PC (si por algun motivo te detecta dos placas de sonido, te puede dirigir el sonido a erroneamente)

Para comprobarlo en una consola proba esto

$ asoundconf list

y fijate que responde, lo que responde es la/s placa/s de sonido que detecta.

Si detecta mas de una o, aunque haya detectado una sola proba con esto

$ sudo asoundconf set-default-card CARD

CARD = al nombre de la placa que te devolvio el asoundconf list (el nombre escribilo TAL CUAL ESTA EN LA RESPUESTA (MAYUSCULAS Y MINUSCULAS)

Fijate si funciona, ojala te ayude

Saludos

Leitraot

---

### Post by Hei Ku on 2007-08-20
te fijaste en el alsa-mixer que esten todos los volumenes bien? Puede parecer superfluo, pero a mi me paso que me detectaba la placa de sonido, pero me ponia el volumen de ciertos canales en 0, asi que no se escuchaba nada igual.

---

