---
title: "Xmms tiene sonido pero otras aplicaciones multimedia no"
date: 2008-04-07
forum: Argentina Team
---

### Post by Apokalyptica79 on 2008-04-07
Hola tengo kubuntu gutsy para 32 bits y tengo el problema de que no puedo reproducir ya sea mp3 o escuchar radio por internet por ningún programa multimedia, como ser mplayer, amarok, xmms y demás.
El xmms funciona bien con mp3 y tiene sonido pero no puedo escuchar radio, cuando ingreso la url se cierra automáticamente, el amarok reproduce pero no tiene sonido y con firefox no tengo sonido tampoco, se ven los videos pero no se escuchan.
Esto es lo que tengo en mi fichero firefoxrc:
[B]# which /dev/dsp wrapper to use
#FIREFOX_DSP="none"
#FIREFOX_DSP="auto"
#FIREFOX_DSP="aesd"
FIREFOX_DSP="aoss"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/bugs/29760](https://launchpad.net/bugs/29760).
[/B]
Traté de instalar todo lo que se refiere a alsa y oss pero no tengo suerte, espero puedan ayudarme.
Otra cosa que traté de hacer fue instalar xine extra plugins pero no puede, aparece en la lista pero no me da la opción de poder seleccionarlo e instalar.
Posteo mi repositorio:
> 
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


#deb [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) dapper-seveas extras
#deb  [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free


Veo que tengo un repositorio con un montón de líneas y me gustaría saber si alguien me puede pasar un repositorio que contenga las líneas necesarias y suficiente como para poder mantener un buen sistema.
Desde ya muchas gracias.

---

### Post by faktorqm on 2008-04-08
Con el tema de los repos vos tenes que decidir que tipo de programas queres instalar, y vas habilitando o sacando repositorios. Si queres los no soportados oficialmente, los que estan en prueba, etcetc. Digamos, lo unico que no podrias sacar seria el de las actualizaciones de seguridad, que se yo. Salu2!

---

### Post by Apokalyptica79 on 2008-04-08
Hola, reinstalé kubuntu, edité mi sources.list cambiandole de nombre y creando un nuevo sources.list con unos repositorios que saqué de internet y actualicé, por suerte no tuve ningún tipo de problemas.
Ahora en firefox puedo ver y escuchar sin ningún problema los videos de youtube, pero sigo sin poder escuchar radio con el amarok, veo que reproduce el stream pero no se escucha nada y probé cambiar la configuración con oss y alsa y no tengo suerte.
Desde ya agradezco cualquier sugerencia y/o tipo de ayuda.
Gracias.
Saludos.

---

### Post by ariel on 2008-04-09
Si amarok funciona OK con mp3 pero con la radio no se escucha, te recomiendo que pruebes SMPLayer, es muy facil de usar y anda muy bien con streams de radio. Yo lo estoy usando ahora para escuchar bbc news, por ejemplo.

[http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.ram](http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.ram)

---

### Post by Apokalyptica79 on 2008-04-10
Hola, mirá en ubuntu puedo escuchar la radio pero con el programa bmpx, pero ahora mi problema es que mi firefox NO TIENE SONIDO, ya probé todo y no hay caso.
Acá dejo mi /etc/firefox/firefoxrc:
# which /dev/dsp wrapper to use
#FIREFOX_DSP="none"
FIREFOX_DSP="esd"
#FIREFOX_DSP="aoss"
# Note that "auto" and "esd" involve the use of esddsp, which
# is known to be buggy and to make Firefox unstable.
# See [https://launchpad.net/bugs/29760](https://launchpad.net/bugs/29760).
Cualquier ayuda es muy útil, desde ya muchas gracias.

---

### Post by ariel on 2008-04-10
Que raro. 

Podes probar 

```
aoss firefox
```

...y ver que onda.

Tambien podes probar con:

```
alsamixer
```

y ver que si hay algun canal muteado.

Yo ya pase mi desktop a hardy que ahora usa pulseaudio sobre un nuevo alsa. Por primera vez en mi vida linux puedo estar escuchando musica con audacious y pasar un videito de youtube o ver un trailer con sonido, todo con sonido simultaneo. Wow, todavia estoy impresionado. 

...asi que si no le encontras la vuelta a tu problema, te recomiendo que esperes solo unos dias y hagas te instales hardy final.

---

### Post by Apokalyptica79 on 2008-04-11
Hola ariel, probé lo de aoss firefox y nada, lo que me pasa es que una vez que instalo ubuntu puedo escuchar sin problemas y ver videos sin problemas, pero una vez que apago la pc y al otro dia la prendo y quiero ver algun video, lo veo sin ningún drama pero no consigo escuchar nada, pero puedo escuchar radio y mp3, eso es lo raro. Sinceramente no entiendo que me está faltando.
Saludos.

---

