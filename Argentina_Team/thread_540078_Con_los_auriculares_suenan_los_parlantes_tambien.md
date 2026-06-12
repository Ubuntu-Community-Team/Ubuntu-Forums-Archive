---
title: "Con los auriculares suenan los parlantes tambien?"
date: 2007-09-01
forum: Argentina Team
---

### Post by FlyerDie on 2007-09-01
Estimados, 
Esta consulta la he realizado en otro lugar sin exito :(

Resulta que tengo una Olivetti 610 ( mother con chipset Intel 945GM1940GML), con audio Realtek ALC883, pero lo ve como Intel HDA en ubuntu.

Mi instalacion es es Feisty 7.04, con ultima actualizacion de repositorios de ALSA.

Ahora bien, mi problema se presenta cuando quiero escuchar musica desde los auriculares, al conectarlos sale sonido de los mismos...pero no se mutean los parlantes externos...:confused:
intente por todos los medios mutear desde el alsa-mixer con diferentes combinaciones pero nada...sigo igual.
Es mas, el control de volumen es exactamente el mismo para los 2, osea no tengo forma de hacer mute sin mutear al otro.

Alguno tuvo el mismo problema? o conoce como solucionarlo...:KS

---

### Post by FlyerDie on 2007-09-02
ni idea no? :(
he leido que pasa con varias marcas de notebook, siendo el "problema" con el chipset...puede ser?

---

### Post by faktorqm on 2007-09-03
Hola men, disculpa que no te respondí antes, lo ví recién este post.

HDA es por High Definition Audio. eso es normal, no te preocupes. El bug del que hablas está reportado en Launchpad, y no pasa solo con este integrado, sino pude ver que pasa al menos con 3.

aca esta: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/114053](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/114053)

en este post del foro de ubuntu en ingles, aparece un chabon que lo soluciono, pero era que no tenia sonido. igual es de agosto de 2006, fijate bien que onda, seguro te sirve, pero esta desactualizado.

[http://ubuntuforums.org/showthread.php?t=202555](http://ubuntuforums.org/showthread.php?t=202555)

aca hay uno que dice que le anda, creo que es el segundo post, probalo:

[http://ubuntuforums.org/showthread.php?t=329412](http://ubuntuforums.org/showthread.php?t=329412)


guia de problemas generales para problemas de audio:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

lo ultimo: no entendi lo que quizo decir, pero es actual el post:

[http://ubuntuforums.org/showthread.php?t=362403](http://ubuntuforums.org/showthread.php?t=362403)

Bueno men, espero que esto te sirva. Por todo lo que leí hay bastantes problemas con esta placa de sonido, y con la alc888 tambien, pero el 50% no tiene sonido, y al otro 50% le pasa lo tuyo. Desde ya, si solucionas el problema, ya sea que tengas que cambiar los volumenes a mano o se cambie solo, describi que fue lo que hiciste por si le pasa a otro. Nos vemos!!!

---

### Post by gfer66 on 2007-09-12
Tengo también la Olivetti 610 con Feisty. Actualicé ALSA a 1.10.14 y probé con todas las opciones a agregar a "model=xxx". Sigue todo igual, al enchufar los auriculares no se mutean los parlantes. Como workaround estoy usando una tarjeta de sonido USB, pero ahora tengo otro problema: Los videos Flash de YouTube, DailyMotion y similares no salen a la tarjeta externa!

---

### Post by FlyerDie on 2007-09-12
> **gfer66 said:**
> Tengo también la Olivetti 610 con Feisty. Actualicé ALSA a 1.10.14 y probé con todas las opciones a agregar a "model=xxx". Sigue todo igual, al enchufar los auriculares no se mutean los parlantes. Como workaround estoy usando una tarjeta de sonido USB, pero ahora tengo otro problema: Los videos Flash de YouTube, DailyMotion y similares no salen a la tarjeta externa!

jua..no quiero llegar al punto de poner una placa USB:(
Estoy a la espera latente que los fanaticos de las Oli en MaximoPC puedan tirar una punta

---

### Post by niko_3100 on 2007-09-13
Te comento que con mi notebook compaq v3415 tambien pasa eso que decis, creo que debe ser un problema mas bien de alsa que de las notebooks.

---

### Post by zspikes on 2007-09-13
> **niko_3100 said:**
> Te comento que con mi notebook compaq v3415 tambien pasa eso que decis, creo que debe ser un problema mas bien de alsa que de las notebooks.

Tal cual... tengo una compaq C500 y tengo el mismo problema bajo ubuntu, pero no es asi con musix o debian.
Con musix anda solo el conmutador, ni un drama, y bajo debian se puede controlar el volumen de los parlantes y de los auriculares por separado.

Creo q es un problema de drivers

---

### Post by por100pre1 on 2007-09-13
Yo tengo audio Realtek en mi HP a1719n, tengo la misma situación. Sin embargo, para mi esto es una ventaja, no tengo que estar desconectando los audífonos para escuchar los altoparlantes. En Windows Vista, por ejemplo, tengo que seleccionar uno de los dos, lo que me resulta muy fastidioso.

Cosas de la vida, lo que para unos es una desdicha, para otros puede ser una delicia. :)

---

### Post by hernan blau on 2007-09-13
Como dije en otro post tengo la Realtek High Definition y al poner los auriculares se cortan los parlantes pero no se escuchan los auriculares. Disculpen pero no entiendo inglés. Gracias

---

### Post by Teno on 2007-09-13
Probaste lo siguiente??? A mi me paso y me resulto, con el msimo chipset en otra laptop:


Agrega esta linea en /etc/modprobe.d/alsa-base

options snd-hda-intel model=laptop

Y reinicia la maquina.

Avisaaaa!!!

---

### Post by FlyerDie on 2007-09-13
me siento contenido emocionalmente....:lolflag:

Vi que salio ALSA 1.10.15RC1...ahora me surge la duda, el ALSA son los drivers o es el MIXER de sonido?
Pregunto para saber si probando sirve de algo.

---

### Post by Hei Ku on 2007-09-13
alsa, por lo que entiendo, es el subsistema de sonido. No los drivers especificos para una placa, sino todo el sistema que se encarga del sonido. 

Y despues tenes el alsa-mixer, que ese sí es el mixer de audio.

---

### Post by FlyerDie on 2007-10-25
aun no actualice a 7.10 ... y sigo con este problemilla.

El 7.10 me dara la solucion? alguien sabe? :confused:

---

### Post by hernan blau on 2007-10-25
Hola, yo instalé en limpio 7.10. Suena el parlante, cuando enchugo los auriculares se cortan los parlantes pero no suenan los auriculares. Estoy igual que con Feisty. Lo que si me mejoró Gutsy fue la wi-fi que ahora funciona bien en el modo itinerante y antes no, había que configurar la red aérea en forma manual.

---

### Post by niko_3100 on 2007-10-25
Buen dato ese del wifi que placa wifi tenes??

---

### Post by FlyerDie on 2007-10-26
> **hernan blau said:**
> Hola, yo instalé en limpio 7.10. Suena el parlante, cuando enchugo los auriculares se cortan los parlantes pero no suenan los auriculares. Estoy igual que con Feisty. Lo que si me mejoró Gutsy fue la wi-fi que ahora funciona bien en el modo itinerante y antes no, había que configurar la red aérea en forma manual.

Te fijaste que en el alsa-mixer no estuviera los auriculares en mute no?

A que le llaman modo itinerante? es que tengo el ubuntu en ingles....:lolflag:

---

### Post by hernan blau on 2007-10-26
Hola. Flyerdie: Respecto del alsamixer no me aparecen los auriculares, sólo el front (parlante), mic y pcm. Es el eterno problema.
"Itinerante" se llama el modo en que la pc capta las redes inalámbricas y con sólo hacer click en una red detectada se engancha en esta y podés navegar. Si no lo hace automáticamente, debes poner el modo manual e insertar la red a la que querés acceder.

Niko: Acá te tiro el resultado de "lspci":

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
Gracias a todos y seguiré atento.
Cordialmente, HB

---

### Post by loopeando on 2007-10-28
Tengo el mismo problema con mi Lenovo 3000 N100.

El problema del *headphone jack sense* fue solucionado con el kernel que viene por default en Feisty, volvio a ser un problema con un update de kernel en Feisty y sigue en Gutsy.

Igual fijate en la pagina de Realtek que habia drivers actualizados para ALSA que probablemente solucionen tu problema. Mi HDA usa otro codec, Analog Devices AD1986A, por lo que no pude probar esta solucion. Fijate si a vos te sirve.

Te dejo los reportes de bug que encontre en Launchpad a ver si te sirven:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134146](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/134146)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88546](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/88546)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136810)

---

### Post by FlyerDie on 2007-10-29
si...son los que he visto, pero lamentablemente no han dado solucion aun:(

---

### Post by loopeando on 2007-10-29
Estoy en la misma que vos, lastima que hice una formatee antes de instalar Gutsy. Sino seguiria con Feisty, con el kernel en default, hasta que se solucione.

---

### Post by gfer66 on 2007-11-11
Buenas noticias!!!

Funcionó en mi Olibook 610, pero calculo que debería andar en general para la Realtek ALC883.

Simplemente hay que agregar al final de  /etc/modprobe.d/alsa-base esta línea:

```
options snd-hda-intel model=OPCION
```

Donde OPCION puede ser alguna de estas:

```
          3stack-dig    3-jack with SPDIF I/O
          6stack-dig    6-jack digital with SPDIF I/O
          3stack-6ch    3-jack 6-channel
          3stack-6ch-dig 3-jack 6-channel with SPDIF I/O
          6stack-dig-demo  6-jack digital for Intel demo board
          acer          Acer laptops (Travelmate 3012WTMi, Aspire 5600, etc)
          medion        Medion Laptops
          targa-dig     Targa/MSI
          targa-2ch-dig Targs/MSI with 2-channel
          laptop-eapd   3-jack with SPDIF I/O and EAPD (Clevo M540JE, M550JE)
          auto          auto-config reading BIOS (default)

```

Ingresar la misma línea al final de /etc/modules, pero sin el  "options" del comienzo.

Resetear y listo!

Para la Olivetti 610 la opción 3stack-dig anda.

La solución completa, y para otros modelos de Intel HDA, [aquí]("http://ubuntuforums.org/showthread.php?t=588089").

---

