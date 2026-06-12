---
title: "how to install Asus driver?"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by valucha on 2007-06-01
[COLOR="DarkOrchid"]I've founded the linux driver for my sound problem in the Asus Homepage. [(here)]("http://support.asus.com/download/download_item.aspx?model=M2N-MX&product=1&type=Latest&SLanguage=en-us#")
But I don't know how to install them...

Does anybody know??? :(




(sorry about my English)[/COLOR]

---

### Post by Brightbelt on 2007-06-01
I don't know about the Asus driver specifically, but if there are contents in the driver folder at all, look for a Readme file or an Install file. Oftentimes, the instructions for installing are given in those files.

I hope this helps, ...Frank B.

---

### Post by valucha on 2007-06-02
> **Brightbelt said:**
> I don't know about the Asus driver specifically, but if there are contents in the driver folder at all, look for a Readme file or an Install file. Oftentimes, the instructions for installing are given in those files.

I hope this helps, ...Frank B.

[COLOR="DarkOrchid"]No, the Readme is only for the changelogs.[/COLOR]

---

### Post by valucha on 2007-06-02
[COLOR="DarkOrchid"]I've done the ./configure and, after install all the dependences i've typed "make" and got this.[/COLOR]
> Making all in include
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/include'
make  all-am
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/include'
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/include'
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/include'
Making all in alsactl
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsactl'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsactl'
Making all in alsaconf
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsaconf'
Making all in po
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsaconf/po'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsaconf/po'
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsaconf'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsaconf'
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsaconf'
Making all in alsamixer
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsamixer'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/alsamixer'
Making all in amidi
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/amidi'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/amidi'
Making all in amixer
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/amixer'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/amixer'
Making all in aplay
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/aplay'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/aplay'
Making all in iecset
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/iecset'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/iecset'
Making all in seq
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq'
Making all in aconnect
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq/aconnect'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq/aconnect'
Making all in aplaymidi
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq/aplaymidi'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq/aplaymidi'
Making all in aseqdump
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq/aseqdump'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq/aseqdump'
Making all in aseqnet
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq/aseqnet'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq/aseqnet'
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq'
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/seq'
Making all in speaker-test
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/speaker-test'
Making all in samples
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/speaker-test/samples'
make[2]: No se hace nada para `all'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/speaker-test/samples'
make[2]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/speaker-test'
make[2]: No se hace nada para `all-am'.
make[2]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/speaker-test'
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/speaker-test'
Making all in utils
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/utils'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/utils'
Making all in m4
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/m4'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/m4'
Making all in po
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11/po'
make[1]: No se hace nada para `all'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11/po'
make[1]: se ingresa al directorio `/home/valentina/.Trash/alsa-utils-1.0.11'
make[1]: No se hace nada para `all-am'.
make[1]: se sale del directorio `/home/valentina/.Trash/alsa-utils-1.0.11'


[COLOR="DarkOrchid"]Sory but i've Ubuntu in spanish[/COLOR]

---

### Post by neurotic_nemesis on 2007-06-08
but does this solve the problem?
i have exactly the same problem. i thought that atleast version 7.04 will have full support for M2N-MX, but they still haven't sorted it out :(

---

