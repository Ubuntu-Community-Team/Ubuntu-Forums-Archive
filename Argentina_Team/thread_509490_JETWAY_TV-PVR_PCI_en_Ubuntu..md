---
title: "JETWAY TV-PVR PCI en Ubuntu."
date: 2007-07-25
forum: Argentina Team
---

### Post by User21 on 2007-07-25
Tengo la placa de TV Jetway TV-PVR PCI (ese es el nombre comercial en la caja.)
Tiene una etiketa ke dice VS-TV878RF y el lspci me tira esto:

```
 01:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at d8000000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

01:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at d8001000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>
```No la he podido hacer funcionar despues de vaaarios intentos, con diferentes COMOs y horas invertidas. Si alguien conoce como hacerlo, soy todo oidos (u ojos, en este caso). Estoy seguro ke no es el TVTime.

COMO DEBO PROCEDER ? **No kiero ver TV en Win...** :(

---

### Post by User21 on 2008-02-04
Dando vueltas para ver cómo configurar el mando a distancia infrarrojo de mi placa de TV (si, el control remoto), volví a encontrar este POST PROPIO donde pedía ayuda acerca de como configurarla, alla por julio del '07, cuando aun tenia mi particion con XP!!! Hoy, màs maduro (LOL!) escribí este pequeño resumen de como logré hacerlo.

Pues aqui va como la hice funcionar:

1) Removí el modulo que carga por defecto, el bttv (al menos con este tipo de placas, no?)
```
sudo rmmod bttv
sudo rmmod bt878
```2) Encontré en la [lista de placas de TV]("http://personal.telefonica.terra.es/web/ceec/otros/tarjetas.html") que la mia es clon de la 78 y tiene un sintonizador Phillips y dispone de radio FM; pues cargué el modulo necesario con las opciones:
```
sudo modprobe bttv card=78 tuner=5 radio=1
```3) Cheque si todo esta correcto tirando un dmesg y obtengo:
```
 [  880.169295] bttv: Bt8xx card found (0).
[  880.169313] bttv0: Bt878 (rev 17) at 0000:01:09.0, irq: 19, latency: 32, mmio: 0xd8000000
[  880.169325] bttv0: using: Jetway TV/Capture JW-TV878-FBK, Kworld KW-TV878RF [card=78,insmod option]
[  880.169362] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[  880.176467] bttv0: using tuner=5
[  880.176475] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[  880.177261] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[  880.177974] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[  880.212960] tuner 2-0060: All bytes are equal. It is not a TEA5767
[  880.212968] tuner 2-0060: chip found @ 0xc0 (bt878 #0 [sw])
[  880.213191] tuner 2-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[  880.213305] tuner 2-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[  880.222053] bttv0: registered device video1
[  880.222086] bttv0: registered device vbi0
[  880.222109] bttv0: registered device radio0
[  880.222135] bttv0: PLL: 28636363 => 35468950 .. ok
```Ahora, reconocida la tarjeta de TV, puedo usarla con cualquier programa de TV o FM según la ruta la dispositivo (/dev/video1 y /dev/radio0 , en mi caso particular).

Como paso final, edito el archivo de opciones de los modulos, de manera que cada vez que arranque Ubuntu, me reconozca apropiadamente la tarjeta:
```
 sudo gedit /etc/modprobe.d/options
```
y al final del archivo agrego "options bttv card=78 tuner=5 radio=1", guardo y cierro.

**Ahora, debo encontrar la forma de hacerle funcionar el control remoto, ya que me reconoce el dispositivo de captura infrarroja, pero no logro hacerlo funcionar y no se compilar el modulo lirc_gpio !!! u_U  Ojala pueda hacerlo, y no me tome otro año mas! JAJAJA! **

---

### Post by User21 on 2008-05-02
Hace poco me mudé. Donde antes vivía, no tenia cable, y obtenía una muy pobre recepción de TV por aire, tanto en mi TV como en mi PC. Creo que mi anterior casa está ubicada en un "punto oscuro" de recepción, porque incluso los celulares a veces no tomaban llamadas! 
Ahora, en mi nueva casa, tengo cable, y obtuve mejores resultados con el siguiente comando:
```
sudo modprobe bttv card=78 tuner=8 radio=1
```
Al parecer, tomaba tanto con tuner 5, como con tuner 8, pero esta vez, el cambio es bastante mas significativo!
Espero le sea útil a alguien! Saludos! :)

---

