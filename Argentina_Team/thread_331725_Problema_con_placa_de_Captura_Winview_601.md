---
title: "Problema con placa de Captura Winview 601"
date: 2007-01-05
forum: Argentina Team
---

### Post by newtonfn on 2007-01-05
No sabía que había en este lugar un foro en español mucho menos argentino, y me alegra, ya que  me permite hacer una pregunta en mi propio lenguaje (y los otros foros en español que vi son terribles)

Resulta que tengo una placa de captura bastante vieja, una Leadtek Winview 601 la cual solo tiene soporte para Windows98.

Esta placa está basada en el chip Conexant bt848 y gracias a prueba y error usando los drivers genéricos en Windows XP descubrí que tiene un sintonizador Temic NTSC (4032 FY5)

Como con la mayoría de las placas tan viejas, no esta soportada la autodetección asi que tengo que configurarla a mano, lo cual hago con el siguiente comando:

```
sudo mdprobe bttv card=17 tuner=6 radio=0
```

Si luego me fijo en dmesg la salida de ese comando el cual es
```

[17181616.680000] bttv: driver version 0.9.16 loaded
[17181616.680000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17181616.680000] bttv: Bt8xx card found (0).
[17181616.680000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC1] -> GSI 16 (level, high) -> IRQ 225
[17181616.680000] bttv0: Bt848 (rev 18) at 0000:01:0a.0, irq: 225, latency: 32, mmio: 0xdc001000
[17181616.680000] bttv0: using: Leadtek WinView 601 [card=17,insmod option]
[17181616.680000] bttv0: gpio: en=00000000, out=00000000 in=00000000 [init]
[17181616.684000] bttv0: using tuner=6
[17181616.688000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17181616.692000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17181616.692000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17181616.752000] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[17181616.804000] tuner 2-0061: chip found @ 0xc2 (bt848 #0 [sw])
[17181616.804000] tuner 2-0061: type set to 6 (Temic NTSC (4032 FY5))
[17181616.808000] tuner 2-0063: chip found @ 0xc6 (bt848 #0 [sw])
[17181616.836000] bttv0: registered device video0
[17181616.836000] bttv0: registered device vbi0
[17181616.840000] bttv0: registered device radio0

```

Luego de todo esto, usando el programa tvtime y configurándolo para usar la tan estandar norma de televisión PAL-NC (¿Además de argentina algún otro pais en el mundo la usa?) puedo ver todos los canales sin el menor problema.

El problema es que solo puedo verlos, porque el sonido es de terror. Entrecortado, bajo, horrible, con ruido, en fin, quitan las pocsas ganas de ver tv que podría tener.

Investigando un poco, me di cuenta que el programa tvtime por algún motivo no esta pudiendo controlar el sonido en la placa. No funciona el mute de la placa, ni puede subir y bajarlo (desde la placa) y no se el motivo ya que ningun mensaje de error veo en ninguna parte.

A veces, si cargo el módulo btaudio que en teoria es para placas mas modernas ( al menos chip bt878 ) comienza a funcionar mágicamente todo bien, pudiendo bajar y subir el volumen de la placa, el sonido sale tan impoluto como esta placa puede, anda el mute todo de maravilla.

Pero otras veces (y estas son las mas), siguiendo exactamente el mismo procedimiento no puedo arreglar el problema.

Busqué por internet, y pareciera que nadie tiene un problema siquiera similar con esta placa. Pero la mayoria de las personas dicen que la placa tiene un sintonizador Philips, pero cuando intento configurar ese sintonizador obtengo como resultado el hecho de ni tener imagen. Tal vez la versión de esta placa con un Temic es algo especial de argentina, no lo se...

Exactamente el mismo problema tengo usando los drivers genéricos en WindowsXP, pero en windows a veces podía solucionarlo desenchufando la pc y volviendola a enchufar (no era suficiente apagarla, necesitaba dejar sin energia el mother, aparentemente mi mother cuando se apaga sigue alimentando a los puertos pci)

Pero usando los drivers originales en Windows98 nada de esto sucede, por lo que quiero creer mi problema tiene solución.

En fin, alguien tendrá alguna idea de que está pasando con mi placa? alguna sugerencia? algo?

Para más información, tengo una palca de captura Leadtek Winview 601 en un mother Asus A7N8X Deluxe (Usando Ubuntu Edgy)

Desde ya muchisimas gracias a cualquiera que me pueda ayudar, e incluso al que haya leido todo este post bastante extenso y aburrido.

---

### Post by tzulberti on 2007-01-05
Desde el tvtime, se puede configurar algo del sonido. 
Probastes con las distintas configuracione que ahi aparecen?

---

### Post by newtonfn on 2007-01-05
Desde la interfaz del TvTime he probado con todas las opciones que he encontrado. Estas opciones son para subir o bajar el sonido desde la placa (que no es lo mismo que usar el mixer, el mixer anda bien, el rpoblema es el sonido de la placa), cambiando el standard de sonido de PAL-I a PAL-DK y no se cual más habia (probe con todos aunque no se cual es el correcto), incluso mandandole comandos desde el CLI al TvTime para que haga el mute (ya que no encontre como hacerlo desde intefaz gráfica)

En fin, en las pocas veces que anda todo bien estos comandos son acatados a la perfección, pero cuando tengo estos problemas de sonido son completamente ignorados.

---

