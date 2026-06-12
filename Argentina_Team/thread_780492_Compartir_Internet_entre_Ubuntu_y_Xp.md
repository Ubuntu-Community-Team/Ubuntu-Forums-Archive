---
title: "Compartir Internet entre Ubuntu y Xp"
date: 2008-05-03
forum: Argentina Team
---

### Post by cricri1991 on 2008-05-03
[SIZE="3"][SIZE="3"][FONT="Comic Sans MS"]Hola a todos!!.. tengo una gran duda que no me pude sacar en ningun  foro o web. 

El tema es asi..

Tengo un modem **speedtouch 330 USB (proveedor Speedy)** en la maquina con **Ubuntu** andando con internet y todo :D , pero también tengo una PC con **Window$ XP**. Tengo un ***_cable de red cruzado conectado entre las dos PC, pero no se como compartir internet entre las dos_*** :(

[CENTER][IMG]http://tbn0.google.com/images?q=tbn:-7ds9-KOeHYMuM:http://downloadsource.net/img/25232c80e009f608074db85ffaaa9409.jpg[/IMG][/CENTER]

Porfavor ayudenme que solo me falta esto para poder usar el ubuntu a full sin que otros me molesten por no tener internet en la otra PC :mrgreen:[/FONT][/SIZE][/SIZE]

---

### Post by margori on 2008-05-03
La clave esta en los iptables, al menos yo la encontre ahi. Es toda una historia.

Te paso un link: [http://www.pello.info/filez/firewall/iptables.html](http://www.pello.info/filez/firewall/iptables.html) 

Es aspero pero si lo entendes y haces andar, en tu vida tendras problemas de configurar iptables, enrutamiento y demas yerbas.

---

### Post by cricri1991 on 2008-05-03
Gracias.. parece un poco complicado.. pero me parece que voy a comprar el **Modem HUAWEI SmartAX MT882** y lo conecto de una y listo :D

---

### Post by MeduZa on 2008-05-04
no es tan dificil como te pusieron arriba, es mas facil, si encuentro como, te posteo, tenes que crear un bridge entre las 2 placas y eso creo que son 3 comandos o 2

---

### Post by margori on 2008-05-04
> **cricri1991 said:**
> Gracias.. parece un poco complicado.. pero me parece que voy a comprar el **Modem HUAWEI SmartAX MT882** y lo conecto de una y listo :D

Cambiando el modem no vas a solucionar tu problema, ya que a linux aun no lo tendrías configurado para encaminar los paquetes.

---

### Post by pante on 2008-05-05
Te podés instalar el Firestarter, que es un firewall pero que te da la opción de compartir Internet.

---

### Post by guisheca on 2008-05-05
Yo tengo el smartax mt882 y es una buena solución, la conexión por red la tengo en mi pc con ubuntu, y la conexión por usb va para la notebook de mi hermana con xp.

---

### Post by cricri1991 on 2008-05-06
Claro.. si.. cuando me compre una notebook le pongo Ubuntu con el cable de red y a la otra con Xp le pongo el USB :D

---

### Post by margori on 2008-05-06
> **cricri1991 said:**
> ... le pongo Ubuntu con el cable de red y a la otra con Xp le pongo el USB :D

Me descolocaste con esa solución. Nunca se me hubiera ocurrido enchufar un puerto a cada máquina.

Lo otro que se me ocurre es que enchufes el modem a un hub via ethernet (cable de red) y todas las compus al hub.

---

### Post by cricri1991 on 2008-05-07
UHH esa está buena.. osea conecto al modem al hub y de ahi tengo como 5 bocas para varias maquinas? cuanto puede estar uno ethernet? :D

---

### Post by sergiom99 on 2008-05-07
> **cricri1991 said:**
> UHH esa está buena.. osea conecto al modem al hub y de ahi tengo como 5 bocas para varias maquinas? cuanto puede estar uno ethernet? :D

a mi con fibertel nunca me anduvo.
porque ellos asignan una IP a cada MAC de modem, entonces cuando habia mas de una maquina en la red, solo navegaba una. si pedis otra IP te habilitan dos bocas.

Con un router te evitas esto, y ademas puede discar por el modem (y muchas otras cosas que el hub no haria). Ahora no estan tan caros. El hub es solo un "bifurcador" de la red.

Espero no haber chamuyado demasiado, pero asi fue mi experiencia.
saludos/

---

### Post by cricri1991 on 2008-05-07
> **sergiom99 said:**
> a mi con fibertel nunca me anduvo.
porque ellos asignan una IP a cada MAC de modem, entonces cuando habia mas de una maquina en la red, solo navegaba una. si pedis otra IP te habilitan dos bocas.

Con un router te evitas esto, y ademas puede discar por el modem (y muchas otras cosas que el hub no haria). Ahora no estan tan caros. El hub es solo un "bifurcador" de la red.

Espero no haber chamuyado demasiado, pero asi fue mi experiencia.
saludos/

Yo tengo Speedy 1Mb , tengo un solo modem (Huawei axsmart MT882) pienso que con un hub ethernet andaria bien no? :D

---

### Post by sergiom99 on 2008-05-07
> **cricri1991 said:**
> Yo tengo Speedy 1Mb , tengo un solo modem (Huawei axsmart MT882) pienso que con un hub ethernet andaria bien no? :D
no me animaria a afirmartelo.
con un router seguro, pero un hub....mmmm no se.

espera a ver si alguien que tenga ADSL te lo confirma.

---

### Post by faktorqm on 2008-05-08
> **cricri1991 said:**
> Yo tengo Speedy 1Mb , tengo un solo modem (Huawei axsmart MT882) pienso que con un hub ethernet andaria bien no? :D

hub, olvidate. No podes conectar una boca a cada pc por que no trae un switch adentro el modem. lo que si te pido encarecidamente es que me digas de donde lo sacaste, quien te lo dijo, o en que pagina web lo viste....

switch noga 8 bocas 50 pesos en mercado libre.... y listo el pollo!

---

### Post by fgl82 on 2008-05-08
Yo cuando tenía NAT (ahora tengo un router) tenía dos placas de red en la máquina principal, digamos, la que se encargaba del NAT.

Lo que hacía era darle por un lado una dirección ip fija a una de las placas de red y la otra tenía la dirección que le asignaba fibertel.

La máquina que se conectaba a internet a través de la "principal" , tenía a su vez obviamente una placa de red con otra ip fija y configurado para que su gateway y su dns fuera la dirección estática de la máquina principal.

Luego corría unos comandos por consola, los tengo en mi casa si querés después te los paso, y todo pipi cucú.

A mí la duda que me entra es: ¿con un modem usb y una placa de red en la máquina principal, se consigue el mismo efecto? ¿toma el usb como una "segunda placa de red" digamos?

---

### Post by faktorqm on 2008-05-08
si, asi es. en realidad lo que estas haciendo ahi es conectar una interfaz de red por usb, asi como todos conocemos las placas por isa, pci, hay por usb, pci express, firewire, etc.
Ahora recien despues de tantos años se estan vendiendo celulares con conexion usb que ofician de modems para conectarte a internet, aunke un poco opacado por wifi y tecnologias como 3g, pero al fin son modems.
De hecho, hay algunas notebooks de gente que pregunta en el foro, que tienen una placa de red wifi pero internamente estan conectadas a traves del usb. 
Cuando salio el usb, la idea era "reemplazar" al pci, y que todo sea por usb, lo que pasa es que tenia muchas limitaciones. (el video para empezar).
Ahora se esta pasando mucho a pci-express y se esta trabajando muy duro en la norma usb 3, que promete ser buena la verdad, pero para los discos hasta que no salga usb 3 el sata 2 es lo mejor. Salu2!

---

### Post by fgl82 on 2008-05-08
> **faktorqm said:**
> si, asi es. en realidad lo que estas haciendo ahi es conectar una interfaz de red por usb, asi como todos conocemos las placas por isa, pci, hay por usb, pci express, firewire, etc.
Ahora recien despues de tantos años se estan vendiendo celulares con conexion usb que ofician de modems para conectarte a internet, aunke un poco opacado por wifi y tecnologias como 3g, pero al fin son modems.
De hecho, hay algunas notebooks de gente que pregunta en el foro, que tienen una placa de red wifi pero internamente estan conectadas a traves del usb. 
Cuando salio el usb, la idea era "reemplazar" al pci, y que todo sea por usb, lo que pasa es que tenia muchas limitaciones. (el video para empezar).
Ahora se esta pasando mucho a pci-express y se esta trabajando muy duro en la norma usb 3, que promete ser buena la verdad, pero para los discos hasta que no salga usb 3 el sata 2 es lo mejor. Salu2!

Ah ok, ¡¡¡gracias por sacarme de la duda y aportar  aún más info!!! :)

pd: dejo una vez más, por si el OP vuelve a leer este thread, el ofrecimiento de enviarle los comandos que yo usaba para "natear", para que pruebe a ver si le sirven

---

### Post by margori on 2008-05-08
Segun esta pagina [http://www.adslzone.net/huawei.html](http://www.adslzone.net/huawei.html) el aparato en cuestión es un modem/router. Es decir no solo se comunica con el proveedor de internet sino que puede poseer un IP desde el lado del proveedor, y otro desde la red local.

Entonces, en teoria, este router puede conectarse a internet y compertirlo localmente a traves de un hub, switch o router local.

Lo que hay que hacer es:
1 - El hub va a ser el centro de la red.
2 - Conectar todas las compus al hub, con IP 192.168.1.x, siendo x mayor a 1. Ya que la dirección 192.168.1.1 es la que posee el modem por defecto. Y todas con puertas de enlace (gateway) 192.168.1.1, y los números de DNS que nos dio nuestro ISP. (200.62.2.180 puede servir)
3 - Hacemos lo que dice esta pagina [http://www.adslzone.net/tutorial-46.14.html](http://www.adslzone.net/tutorial-46.14.html)
4 - Y listo, ya tenemos internet en la red.

De hecho esto seria mas facil si el router tiene servicio de DHCP.

Por favor, verifiquen esta informacion. Todo depende de que realmente el aparato en cuestion sea router, sino es otro el camino a seguir.

---

