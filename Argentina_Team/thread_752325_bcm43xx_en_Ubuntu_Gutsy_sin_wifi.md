---
title: "bcm43xx en Ubuntu Gutsy sin wifi"
date: 2008-04-11
forum: Argentina Team
---

### Post by Apokalyptica79 on 2008-04-11
Hola, bueno instalé ubuntu gutsy en mi notebook una AMD Turion 64, pero es el ubuntu de 32, la placa wifi es una **Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)**, instalé por apt el *bcm43xx-fwcutter* y una vez instalado eso fui a Sistema --> Administración --> Gestor de controladores restringidos y activé el casillero de Firmware para la familia de chipsets Broadcom 43xx y me aparece la tilde verde diciendo en uso y la luz del wifi está prendida del todo, el problema es que no tiene conexión alguna.
Configuré poniendo el nombre de la red, la clave y lo puse en wpa personal y nada.
Cualquier ayuda y/o idea es bienvenida.
Muchas gracias.

---

### Post by sdm_cacto on 2008-04-11
El driver que queres usar es una c@g@d@, yo pase por el mismo problea, lo que tenes q hacer es buscarte una buena guia para activar Ndiswrapper, anda barbaro.

Yo creo q la saque de [www.ubuntu1501.com](www.ubuntu1501.com)

mcuha suerte... y paciencia

---

### Post by Apokalyptica79 on 2008-04-11
Hola sdm_cacto, voy a hecharle un vistazo, mientras voy a seguir  tratando con esto un poco más, sino me dedicaré en el finde o en algun otro tiempito al sitio que me pasaste, muchas gracias.
Me olvidé de decir, mi notebook es una Acer Aspire 5000, más precisamente una Aspire 5003WLCi.
Saludos

---

### Post by leo_rockway on 2008-04-11
Yo use bcm43xx sin ningún problema en Gutsy. En Hardy lo cambiaron por b43.

---

### Post by Mister X on 2008-04-11
Con mi anterior notebook y la misma placa que la tuya, en Feisty, de la unica forma que pude hacer andar la wifi fue con ndiswrapper.
No se ahora, pero te recomendaria que uses ndiswrapper, es muy sencillo

---

### Post by Apipote on 2008-04-11
Mmmmm...Broadcom y Ubuntu, olvidate, al menos por ahora. Veremos que pasa en Hardy.

Podés como bien te sugirieron acá truchar los drivers del xp, si no va en contra de tus principios.

Slds

---

### Post by SLA_leandrin on 2008-04-11
> **Apipote said:**
> Mmmmm...Broadcom y Ubuntu, olvidate, al menos por ahora. Veremos que pasa en Hardy.

Podés como bien te sugirieron acá truchar los drivers del xp, si no va en contra de tus principios.

Slds

No... a mi me anda de lujo.

Seguí las instrucciones de esta página;


[http://lepedre.com/?p=46]("http://lepedre.com/?p=46")


Me anda igual q si tuviese Window$,

---

### Post by leo_rockway on 2008-04-11
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

Con esa placa en Feisty y en Gutsy jamás tuve problema con bcm43xx y ahora tampoco tengo problema en Hardy con b43.

---

### Post by Apipote on 2008-04-12
Ufa Sla, me hiciste ilusionar...sigue siendo ndiswrapper+drivers de xp. No me gusta mezclar xp en linux.
Sueño, con que alguna vez, ubuntu tome todo mi hardware sin hacer cosas raras.
Slds y gracias.

---

### Post by SLA_leandrin on 2008-04-13
> **Apipote said:**
> 
Sueño, con que alguna vez, ubuntu tome todo mi hardware sin hacer cosas raras.


Veremos que pasa en la 8.04

Esperemos que levante todo!!

---

### Post by leo_rockway on 2008-04-13
> **Apipote said:**
> 
Sueño, con que alguna vez, ubuntu tome todo mi hardware sin hacer cosas raras.


Soy dueño de una laptop con la diabólica trinidad (ATI, Broadcom, Sigmatel).

Prefiero toda la vida tener que instalar desde los __repos__ los paquetes b43-fwcutter o xorg-driver-fglrx que ponerme a perseguir por toda la web los drivers para XP (la laptop vino con Vi$ta). Y cuando logré instalar XP (que bastante poco me duró igual) ni siquiera funcionaban los botones multimedia...
Tener que mendigar drivers es cosas raras...

Y a mí mi laptop de la diabólica trinidad me funciona a la perfección con Kubuntu GNU/Linux.

La culpa es de Broadcom no de GNU/Linux. Es necesario hacer la aclaración para que no se nos olvide.

---

