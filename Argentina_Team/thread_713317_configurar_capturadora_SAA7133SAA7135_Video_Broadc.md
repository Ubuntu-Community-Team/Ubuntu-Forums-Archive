---
title: "configurar capturadora SAA7133/SAA7135 Video Broadcast Decoder para tvtime"
date: 2008-03-02
forum: Argentina Team
---

### Post by 400c on 2008-03-02
tengo un problema con  una capturadora de tv integrada:

SAA7133/SAA7135 Video Broadcast Decoder
Philips Semiconductors
Avermedia Technologies Inc

quiero usar el tvtime, mas que para ver la tele lo que quiero es poder usar la entrada s-video. Como viene por defecto no funciona nada. Yo soy un novato total, como viene el ubunu me sirve para casi todo lo que quiero sin problemas.
Logré tener imagen, a lo bruto, casi sin saber lo que hacía y también sonido. Pero todo "atado con alambre" y ahora a la hora de la verdad, fui a probar lo que en realidad quiero usar que es una consola y el video se bien pero no " lo bien que debería" y el sonido se escucha , pero con retardo. 
Supongo que para hacerlo bien tendría que seguir[ este]("http://gentoo-wiki.com/HARDWARE_saa7134") tutorial pero ya de entrada mi capturadora no esta y cuando hago un dmesg (lo dice el tuto) no me sale nada parecido a lo que dice ahi.
Sigue con algo de cargar modulos y compilar el kernel, cosa que veo mas alla de mis capacidades.
Di mas vueltas por ahi, y cambiando el /etc/tvtime/tvtime.xml y el /home/luis/.tvtime/tvtime.xml, además de copiar y pegar en un terminal culquier cosa que encontraba por ahí, logre ver el s-video pero no la tele (igual la tele no me importa, de momento)
[ cosas que encontraba por ahi]("http://www.ubuntu-es.org/index.php?q=node/73168")i, [otra]("http://www.mistermod.com/foros/index.php?showtopic=3089"),[ otra]("http://linuxtv.org/v4lwiki/index.php/Generic_SAA7134_Card_Installation").
Así logré imagen. En el proceso el xawtv (que tambien estaba probando) dejó de funcionar. Pero en el tvtime se ve, no genial pero se ve. (la tele digital bajo vista media center, se ve el doble de mejor)
Ahora el problema es el sonido. Si abro el tvtime como viene, no se escucha nada, pero según leí en[ esta]("http://foros.ubuntu-cl.org/viewtopic.php?t=2128") página, poniendo:
tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay - 
en un terminal, abro un tvtime que Si tiene sonido. Pero el problema es que tiene retardo.

Como hago para que todo vaya bien? mejorar la imagen y arreglar lo del sonido? realmente tengo que agregar módulos al kernel? Puede hacerlo un novato?

se que no debería haber metido lo primero que se me cruzaba en el terminal y que ahora todo es más difícil, pero si no lo hacía y no veía la imagen y el sonido retardado ya hubiese abandonado todo y seguiría luchando con mi mugroso vista ;) 

Si hace falta formateo todo, total el vista (la otra particion que ya solo uso para ver la tele) como siempre va fatal.




pd. por cierto la webcam tampoco va. Solo va la entrada composite y la s-video

---

### Post by User21 on 2008-03-02
Danos lo que sale por terminal con lspci y lsusb y te vamos a poder ayudar mejor.

---

### Post by tzulberti on 2008-03-03
Para la placa de video mirate el post #24 y 26 de esto: [http://ubuntuforums.org/showthread.php?t=304444](http://ubuntuforums.org/showthread.php?t=304444)

Para habilitar el sonido tenes que habilitar la "Line In" en el Gnome (doble clic sobre el icono de sonido, y sacale el mute y subilo).

Lo de la camara web no tengo ni idea.

---

### Post by 400c on 2008-03-03
gracias por las respuestas.

Los comandos lspci y lsusb en el terminal, no hacen nada. No se si a eso es a lo que te referías.
En cuanto al otro post. lo estuve viendo, pero nada. El sonido del gnome ya lo habilite, y si hago como dicen en el post 

Mini How-to:
en /etc/modprobe.d/ crear un archivo llamado saa7134 con el siguiente contenido:
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 tuner=37 card=51
Paso 2: reiniciar

pierdo la imagen y el sonido. Además de las entrada de s-video. Puedo tener sonido en composite con el comando que les mencioné:

tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay - 

pero me quedo sin imagen.

lo de la norma, yo estoy en españa, si no pongo pal60 la consola con la que estoy probando (x360) no me deja jugar a los juegos . Igualmente la 360 la tengo por unos días para arreglar esto lo que en ralidad quiero es la ps3 por s-video.

Si hay alguna otra forma mejor de hacerlo (sin el tvtime) yo encantado. Lo que mas quiero, mas que la tele o el composite, es la entrada s-video.

creo que el problema esta aca. esto es un fragmento de lo que obtengo haciendo un dmesg

[   13.220000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   13.220000] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   13.240000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   13.240000] PCI: Enabling device 0000:08:05.0 (0000 -> 0002)
[   13.240000] ACPI: PCI Interrupt 0000:08:05.0[A] -> GSI 19 (level, low) -> IRQ 20
[   13.240000] saa7133[0]: found at 0000:08:05.0, rev: 209, irq: 20, latency: 64, mmio: 0xde005800
[   13.240000] saa7133[0]: subsystem: 1461:e836, board: Philips Tiger reference design [card=81,insmod option]
[   13.240000] saa7133[0]: board init: gpio is a400000
[   13.292000] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[   13.376000] saa7133[0]: i2c eeprom 00: 61 14 36 e8 00 00 00 00 00 00 00 00 00 00 00 00
[   13.376000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   13.376000] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 00 ff ff ff ff
[   13.376000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.376000] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 00 ff ff ff ff ff ff ff ff ff ff
[   13.376000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.376000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.376000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   13.404000] saa7133[0]: registered device video1 [v4l2]
[   13.404000] saa7133[0]: registered device vbi0
[   13.404000] saa7133[0]: registered device radio0
[   13.452000] lirc_dev: lirc_register_plugin: sample_rate: 0
[   13.464000] lirc_mceusb2[2]: SMK eHome Infrared Transceiver on usb4:2
[   13.464000] usbcore: registered new interface driver lirc_mceusb2
[   13.484000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   13.484000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   13.512000] saa7133[0]/dvb: frontend initialization failed
[   13.552000] cs: IO port probe 0x100-0x3af: clean.
[   13.556000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   13.556000] cs: IO port probe 0x820-0x8ff: clean.
[   13.560000] cs: IO port probe 0xc00-0xcf7: clean.
[   13.560000] saa7134 ALSA driver for DMA sound loaded
[   13.560000] saa7133[0]/alsa: saa7133[0] at 0xde005800 irq 20 registered as card -2

según vi por ahi, creo que debería tener mas lineas con saa7134. que es el i2c?, lei por ahi que tambien era importante.

bueno gracias denuevo y saludos

---

### Post by tzulberti on 2008-03-03
Hola. Si, la configuracion que te pase es para la argentina, por eso es españa no creo que te funcion. La configuracion inicial esta bien, lo que deberia es el nro que aparece despues de turner. La argentina usa PAL_NC y por eso tiene ese valor. No se que valor se usa en tu caso, pero lo podes sacar dehttp://gentoo-wiki.com/HARDWARE_saa7134. 

Depaso, hay figura algo de i2c.

Saludos,
TZ

---

