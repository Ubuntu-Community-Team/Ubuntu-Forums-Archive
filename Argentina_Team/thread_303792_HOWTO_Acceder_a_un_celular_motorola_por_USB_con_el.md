---
title: "HOWTO: Acceder a un celular motorola por USB con el Moto4Lin"
date: 2006-11-20
forum: Argentina Team
---

### Post by kalel on 2006-11-20
Modelos soportados oficialmente

[B]
C350, C350l, C380, C650, V180, V220, V300, V500, V547, V600, E398, E1000[/B] (hay muchos modelos que no se ven, pero puede que funcionen, entre ellos v3)

Si tu telefono motorola funciona con Moto4Lin, pero no esta en la lista oficial, aderilo al moto4lin wiki, Modelos soportados y completa que USB ID tiene. Así otros puden tener acceso a esa info.

[B]#Requirmientos

Instalar lo siguiente. [/B]

**Nota: Tenemos 2 opciones para instalar el moto4lin, Opción A (bajando la fuente y compilarlo), Opción B (agregar un repo al sources.list y hacer apt-get), esto es a gusto del que lo instala. **

[B][U]
Instalación Opción A[/U][/B]

```
 ~$sudo apt-get install cvs
~$sudo apt-get install libqt3-mt-dev
~$sudo apt-get install zlib1g-dev
~$sudo apt-get install libusb-dev

```

 **#Instalar moto4lin**

Vamos a conseguir la fuente de moto4lin de un repsitorio cvs. Puede ser que salga un error de cvs en esta parte, no darle bola, y seguir. Si te pide contraseña, dale enter.


```
~$cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin login
~$cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/moto4lin co -P moto4lin
```

**#Ahora a compilar la fuente**

```
~$cd moto4lin
~/moto4lin$qmake
~/moto4lin$make
~/moto4lin$sudo make install 
```

Si recibis cualquier error de compilación, probablemente te falten librerias requeridas, trata de mirar(examinar) los mensajes de error para entender lo que te falta. Si todo va bien, vas a tener instalado moto4lin.

[COLOR="black"]**_Instalacion Opción B_**[/COLOR]


**Aca les dejo un repositorio de donde pueden sakar el moto4lin ya compilado**

```
Pongan en /etc/sources.list :
deb http://3v1n0.tuxfamily.org edgy 3v1n0

Agreguen la llave
wget http://3v1n0.tuxfamily.org/EDD1E155.gpg -O- | sudo apt-key add -

Updateen las listas:
sudo apt-get update

Instalen el pakete con:
sudo apt-get install moto4lin
```



[B]
#Configurar moto4lin[/B]

Conecta tu celular a la PC

Abri el moto4lin

```
~$sudo moto4lin
```
Necesitas correrlo como root, para poder configurarlo y asi tb para usarlo, toadvia no pude encontrarle la vuelta para usarlo con un usuario normal.


Andá a: Settings -> Preferences...
Setea 'ACM Device' = '/dev/ttyACM0'

Mira bien lo siguiente

'AT Vendor ID',
'AT Product ID',
'P2K Vendor ID',
'P2K Product ID'.


Click en 'Update List' recupera una lista de AT Vendor ID' and 'AT Product ID' y todos tus dispositivos USB. Econtrá tu celular AT IDs en la lista.
Selcciona 'Switch to P2K' -> si salió bien, te tiene que tirar el mensaje Phone pluged as P2K en la barra de estado de la venta principal.
Clickea 'Update List' otra vez asi te trae el 'P2K Vendor ID' and 'P2K Product ID para todos tus disposotivos USB.

Alternativamente podes buscar la info de AT y P2K IDs de tu cel [ACÁ]("http://moto4lin.sourceforge.net/wiki/Category:Models")


cerrá el moto4lin

abrilo otra vez

Chequea si todo esta bien,
[B]
Settings -> Preferences -> Switch to P2K' para tratar de conectar.[/B]

si todo va bien te va a quedar como en la screen

**Mi configuracion de V300**

[IMG]http://img99.imageshack.us/img99/3803/configfd6.jpg[/IMG]

[B]
Moto4Lin Funcionando[/B]


[IMG]http://img293.imageshack.us/img293/2676/moto4linps9.jpg[/IMG]

Suerte, cualquier cosa avisen


**Este howto, fue tomado y traducido de este Thread **[http://ubuntuforums.org/showthread.php?t=56253&highlight=v300](http://ubuntuforums.org/showthread.php?t=56253&highlight=v300)

**como me funcionó y me pareció copado, lo puse acá** :-D

---

### Post by Nemesis Teufel on 2006-11-20
tenes idea si funciona con los motorola de nextel?
no tengo usb, pero si funciona me lo compro :-D

---

### Post by kalel on 2006-11-20
no sabria decirte, que modelo es??? por ahi salta en algun lado.se que hicieron andar telefonos motorola que estan fuera de la lista oficial de celulares soportados.

---

### Post by Nemesis Teufel on 2006-11-20
es un i205 el mas basico y barato.. pero irrompible!!:twisted:

---

### Post by QUASAR_FREAK on 2006-11-22
kal84 agrega la instalacion sin compilar que puse en 3darg al principio del howto, asi keda mas piola =)

Aca hay otro que usa gammu como backend.

[http://gmobilebrowser.sourceforge.net/](http://gmobilebrowser.sourceforge.net/)

---

### Post by kalel on 2006-11-22
listo Q, ya esta agregado, grax =)

---

### Post by NeoDaVe on 2007-03-23
Confirmado, funciona también con Motorola v1075.

Solo hay que poner lo siguiente a la hora de configurar el dispositivo:

ACM Device: /dev/ttyACM0
AT Vendor ID: 22b8
AT Product ID: 3002
P2K Vendor ID: 22b8
P2K Product ID: 3001

Buen manual kalel (o traducción, da igual :D)

Gracias! Ya tengo una razón menos para emular win ;)

---

### Post by kalel on 2007-03-23
:guitar:  =P, gracias

---

### Post by DuckMan on 2007-03-24
agregate el motorola v235, va como piña

de hecho, si buscas en este foro tmb habia hecho una guia xD pero la tuya es mejor asi q fue

pd: no hace falta agregar repos para instalarlo, yo lo veo en synaptic por default :O

---

### Post by valucha on 2007-04-16
[COLOR="DarkOrchid"]llegué hasta el 2do paso cuando me pide la contraseña.. aprieto enter y me aparece esto:

Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/moto4lin
CVS password:   <--- aca pongo enter. 
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host[/COLOR]

---

### Post by kalel on 2007-04-16
> **valucha said:**
> [COLOR="DarkOrchid"]llegué hasta el 2do paso cuando me pide la contraseña.. aprieto enter y me aparece esto:

Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/moto4lin
CVS password:   <--- aca pongo enter. 
cvs [login aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: No route to host[/COLOR]

Proba con la **Opcion B** y decime como fue, yo despues lo pruebo en casa con la **Opcion A** y si no me funka modifico en howto.

---

### Post by atari130xe on 2007-04-16
Pregunta: Tengo un Sony Ericsson Z520a con bluetooth, alguien intentó hacerlo funcionar con Ubuntu?

---

### Post by sartrejp on 2008-09-12
Alguno sabe como puedo solucionar este error? tengo un v3, se conecta el moto 4 lin, pero me dice que no puede conseguir el nombre del telefono, ni el driver, ni nada.
Por la consola sale asi

(E_getPhoneName: E001)
(E_getDriveName: E001)
(E_fileCount: E002)
(E_getDriveName: E001)


si alguno sabe.... gracias

---

