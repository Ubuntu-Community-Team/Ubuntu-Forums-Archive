---
title: "Soy nuevo ... preguntas ..."
date: 2008-06-15
forum: Argentina Team
---

### Post by julianch89 on 2008-06-15
Hola soy nuevo en ubuntu y tengo un par de dudas que me queria sacar .. a ver si alguien me ayuda ... bueno primero tengo una notebook e instale ubuntu 8.04 .. la ultima version .. pero no me anda el modo suspension ni hibernacion .. se me queda y no hay forma que despierte ... dps .. no se como hacer para configurar las redes inalambricas ,si es que hay q configurar algo .. por  q cuando apreto la solapita de conexion no me aparece ninguna conexion inalambrica y estuve en lugares con redes, con la red cableada no tengo ningun problema me la reconoce al toque .. y bueno dps si alguien me recomienda un p2p para linux .. al estilo ares, buenisimo.

Desde ya muchas gracias ...

---

### Post by madelaki on 2008-06-15
Queda claro que Ubuntu no esta hecho para laptops. Tiene varios problemas bastante serios. De hecho, el problema que tenes con la red inalambrica es el peor de esta version. Busca en [Googlubuntu]("http://www.googlubuntu.com/") el modelo de tu laptop/placa. En cuanto al tema de la hibernacion, es un problema viejo a causa del hardware sin solucion. 
> 
me recomienda un p2p para linux .. al estilo ares, buenisimo.

Por que todo el mundo esta tan obsesionado con los P2P? :confused:
El mas popular es [aMule]("http://www.amule.org/").

---

### Post by pol666 on 2008-06-15
> **madelaki said:**
> 
Por que todo el mundo esta tan obsesionado con los P2P? :confused:
El mas popular es [aMule]("http://www.amule.org/").


Por que es la posta para bajar. el torrent no siempre rinde

Usa **Amule **para la red ed2k (emule) y **Limewire **para la red Gnutella, si queres usar la red Ares podes bajarte el mismo de windows y emularlo con el programa para correr aplicaciones win32: **wine **
Si queres usar Torrent, yo uso Azureus, pero es medio confuso, podes usar varios, hay muchos clientes Torrent,

---

### Post by madelaki on 2008-06-15
Yo nunca tuve el mas minimo problema descargando de HTTP/FTP. Obviamente eso no significa que ustedes esten igual, pero me resulto raro que alguien que recien se mete en GNU/Linux pregunte por un cliente de P2P, hay cosas mas importantes.

---

### Post by ramiro_md on 2008-06-15
ESte how to es muy bueno para poder instalar ares en ubuntu. ESpero que te sirva.
[http://www.ubuntu-es.org/index.php?q=node/48196](http://www.ubuntu-es.org/index.php?q=node/48196)

---

### Post by julianch89 on 2008-06-15
Gracias .. igual se hicieron mucha historia por lo de p2p .. y era una boludes .. lo mas importante era lo de las redes wifi .. ya lo otro se que es un problema que viene con ubuntu lamentablemente .. pregunte por un p2p ..por q estoy trantando de pasarme completamente a a linux y hay equivalencias que quiero encontrar .. tmb si alguien me dice un compilador de pascal ...o me pasa la dire de freepascal para bajarlo ... y un buen programa para codificar ..tipo al estilo de context ...

---

### Post by SLA_leandrin on 2008-06-15
Bueno, lo primero que tenés que hacer es decirnos exactamente que placa WiFi tenés, a partir de ahi te podemos ir ayudando.

---

### Post by xpelaox on 2008-06-15
es muy posible que puedas instalar los drivers privativos en sistema-->Administracion-->controladores de hardware y ahi habilitarlos, pero igual no podemos saber si esto sirve hasta saber que placa tenes:P

---

### Post by luks911 on 2008-06-16
> **julianch89 said:**
> lo mas importante era lo de las redes wifi .. ya lo otro se que es un problema que viene con ubuntu lamentablemente .. 

Como dijeron por ahí, lo principal es que digas cuál es la placa wifi, de un modo u otro creo que funcionan todas. Aunque puede dar algo de trabajo, Ubuntu funciona en notebooks. 8)
Y para lograr que suspenda, si sabés algo de inglés [acá hay un breve instructivo]("http://www.linlap.com/wiki/Getting+suspend+and+hibernate+working+in+Ubuntu+7.10") de una muy buena página sobre cómo hacer andar las notebooks en linux. Es originalmente para el 7.10, pero debe funcionar igual.

Saludos

---

### Post by julianch89 on 2008-06-16
si eso de loscontroladores de hardware lo habia visto antes y me habia aparecido broadcom b43 wireless driver ..le puse para habilitar.. y me tiro un par de ventanas y como no sabia si era ese el driver de la placa .. le puse cancelar un par de veces para no mandarme una ***** .. pero ahora que me decis q ese es el driver .. le pongo devuelta para habilitar .. y me aparece q se nesecita reiniciar el sistema  .. lo reinicio y me aparece de vuelta lo mimso .. ahi le puse una pic de la ventana .. fijense si tienen una solucion buenazo .. igual gracias de por se .. :P

---

### Post by SLA_leandrin on 2008-06-16
OK, yo tengo la misma placa que vos.

Tenés que hacer lo siguiente;

```

sudo gedit /etc/modprobe.d/blacklist

```

En el archivo que se te abre, asegurate de tener estas líneas;

```

blacklist bcm43xx
blacklist b43

```

Siguiente paso;

```
sudo apt-get remove bcm43xx-fwcutter
echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local

```

OK, ahora a bajar los drivers de la placa (para winchot)
[URL="http://www.stosha.net/WLANBroadcom.tar.gz"]
http://www.stosha.net/WLANBroadcom.tar.gz[/URL]

Una vez que los hayas bajado, los descomprimís;

```
tar -xzvf WLANBroadcom.tar.gz
```

Entras al directorio, y hacemos lo siguiente;

```
cd WLANBroadcom
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo gedit /etc/modules

```

y en ese archivo, agregás al final

```
ndiswrapper
```

grabás el archivo, cerrás, y en la consola;

```
sudo modprobe ndiswrapper

sudo ndiswrapper -m
```

Reinicias la máquina y debería funcionar. 
Hacelo, es más sencillo de lo que parece, cualquier cosa pegá el grito...

Suerte!

---

### Post by julianch89 on 2008-06-16
desde ya muchas ganas por la onda :p...pero cuando me fijo al principio si estan esas dos lineas que me pusiste al principio.. solo veo la primera .. la otra ni idea .. te paso el codigo :


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi





no segui con los pasos... q hago ??

---

### Post by SLA_leandrin on 2008-06-16
Dode dice

> # replaced by b43 and ssb.
blacklist bcm43xx

agregale 

blacklist b43

para que te quede:


```
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43
```

OJO: el resto del archivo dejalo como estaba antes!

---

### Post by julianch89 on 2008-06-20
no tenes msn??? por q tengo un par de dudas y capaz q es mas rapido por ahi ... :p

---

### Post by leo_rockway on 2008-06-21
> **julianch89 said:**
> no tenes msn??? por q tengo un par de dudas y capaz q es mas rapido por ahi ... :p

La onda es que esto quede indexado para futuras referencias.

---

### Post by julianch89 on 2008-06-30
bueno volvi dps de un tiempo... x q donde estudio no tengo internet y cada tanto vengo a mi casa :P .. bueno paso a comentar .. aviso es mi primera experiencia en lunux y en la linea de comando asi q si me tienen pasiencia mejor :D ... bueno.. llegue hasta la parte de bajarme los drivers.... me lo baje .. al escritorio...  y no entiendo dps q tengo q hacer .. si descomprimirlo o poner la linea de codigo que dice ahi ... igual probre de poner la linea de codigo... y no encuentra el fichero .. asi q no tengo ni idea q tengo q hacer ..pliz ayuda

---

