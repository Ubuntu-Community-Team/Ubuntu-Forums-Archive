---
title: "Triple boot"
date: 2007-01-28
forum: Argentina Team
---

### Post by loopeando on 2007-01-28
Siendo este mi primer post vengo a pedirles ayuda.

El tema es este, yo tengo en mi primer disco (hda1) Windows XP y Ubuntu y en el segundo (sda1) una particion libre para probar Windows Vista y el resto del espacio para multimedia.

Al tener XP y Ubuntu ya instalados tengo la duda de si al instalar Vista voy a mandarme un moco y arruinar el GRUB.

¿Como hago para tener a los 3 SO en el GRUB sin problemas?

Gracias!

P.D: Todavia no instale Vista para no mandarme la cagada.

---

### Post by beuno on 2007-01-28
No vas a romper nada que no vayas a poder arreglar con un poco de ganas.
El tema es que al instalar windows sobreescribe el MBR (donde se instala el grub), y no tenes mas acceso a linux.
Te recomiendo instalar primero todos los windows que puedas soportar y despues Linux al final.

---

### Post by BlackHero on 2007-01-29
si por que si aunque tengas windows instalado en la particio hda y ubuntu en la siguiente y si te mandas un moco por ejemplo formatear el grub o algo asi por el estilo y aunque vos creas que esta todo bien por que tenes todavia windows intacto en el supuesto disco C no tenes swap y el grub te diceGRUB ERROR 17
nose por que lo de error ni lo de 17 ya que estaba todo borradito xD

---

### Post by screening on 2007-01-29
Con super grub disk no se puede reparar la mbr? hablo en este caso puntual...

---

### Post by BlackHero on 2007-01-29
ni idea :P lo preferente calculo poniendome a pensar seria poner el cd de ubuntu alternate que tiene un sistema de restore o sino el mismo live cd y volver a instalar dejando intacta la hda0 si es a eso lo que te referis nose que es eso de la super grub xD

---

### Post by Oktubre on 2007-01-29
Si vas a seguir booteando con el HDA1 no tendrias problema de instalar algo en SDA1, ya que te va a tomar el boot loader que este en HDA1.

Para hacerlo mas tranquilo, yo desconectaria el HDA1 mientras instalas el Windows Vista en SDA1, y luego conectaria el HDA1 y modificaria el Grub para que puedas levantar el Windows Vista.

---

### Post by Hex_Mandos on 2007-01-31
Che, como se hace para instalar mas de un Win? A mi el XP me exigía ir al Primary Master, y no aceptaba el otro disco rígido.

---

### Post by cocotapioca on 2007-01-31
mas de un win en una maquina?? es como una pesadilla!!! jaja, supongo q desconectando los disco y luego volviendolos a conectar y usando algun multiboot. O usa el vmware ....

---

### Post by Nemesis Teufel on 2007-01-31
Hablando de booteos..

Si en una imac le pongo un ubuntu x86.. que puede llegar a pasar?
1. Explota (dudo, aunque seria divertido y costoso)
2. Me lo reconoce pero me diria: ja.. que haces con esa cagadita aca? vola de aca pibe..
3. Mi no entender.
4. Bueno.. funciona como la mona pero hago lo q puedo.
5. Funciona todo OK.

---

### Post by euzkoarima on 2007-02-01
> **Nemesis Teufel said:**
> Hablando de booteos..

Si en una imac le pongo un ubuntu x86.. que puede llegar a pasar?
1. Explota (dudo, aunque seria divertido y costoso)
2. Me lo reconoce pero me diria: ja.. que haces con esa cagadita aca? vola de aca pibe..
3. Mi no entender.
4. Bueno.. funciona como la mona pero hago lo q puedo.
5. Funciona todo OK.

Supongo que algo entre 4 y 5. Cuando salieron las primeras mac con intel recuerdo haber leído varias noticias de gente que instalaba con exito alguna distribución x86 de linux.

---

### Post by Hex_Mandos on 2007-02-01
Supongo que dependerá de la arquitectura: si la iMac es PPC, dudo que lo puedas instalar. Si es x86, debería andar bien. Digo, parece una obviedad, pero es lo que se me ocurre sin haber probado una Mac jamás (bah, el viejo de un amigo tenía una porque era ingeniero en sonido, pero fue hace unos 15 años...)

---

### Post by euzkoarima on 2007-02-02
Si la mac es PPC podes instalar sin problema alguno la version PPC de ubuntu. Si es intel el mayor problema al principio tenía que ver con que esas mac no usan BIOS sino el nuevo EFI para arrancar la máquina. Haciendo memoria recordé haber leído algún articulo sobre instalar OSX, Win y Linux en las mac. Asi que google un poquito y encontré [Este Artículo]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp") al respecto.

---

