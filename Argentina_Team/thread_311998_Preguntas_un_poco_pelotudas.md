---
title: "Preguntas un poco pelotudas"
date: 2006-12-03
forum: Argentina Team
---

### Post by Hex_Mandos on 2006-12-03
Hola, anoche instale Kubuntu (edgy) por primera vez. Jamas en mi vida use un SO Linux o Unix, aunque tengo bastante experiencia con DOS/Windows. Estuve jugando un poco, haciendo pruebas, instale Automatix 2 y el desktop Gnome entre otras cosas. Pero no puedo hacer andar un par de cuestiones:

1) Como hago para configurar el teclado cosa que si trato de poner acentos no me queden "as´i"?

2) Tengo que alinear mi impresora (una Laserjet 5l vieja pero eficiente), y segun leo en linuxprinting.org el driver recomendado es HPLIP. Ahora, lo tengo bajado en un archivo .run, como lo ejecuto? O lo instalo como driver? La impresora ya anda, pero me interesan las herramientas de mantenimiento.

3) Como hago para formatear y particionar mi segundo disco? Anoche quise instalar Windows XP, pero el turro no reconocia sus propias particiones. Entonces me canse e instale Kubuntu (prueba de que cualquier infeliz puede instalar una distro como esta sin mucho drama, por lo menos fue mas facil que Windows). Usar un diskette booteable no puedo, porque mi disketera hace años que no funciona (salvo para juntar polvo).

4) Tengo entendido que cuando instale WinXP voy a tener que reinstalar grub para poder elegir desde que disco bootear. Como lo hago?

Gracias

---

### Post by Hex_Mandos on 2006-12-03
Revisando en Synaptic, veo que el paquete HPLIP ya esta instalado, pero no se como hacer para usarlo. Alguien tiene alguna idea?

---

### Post by lavaramano on 2006-12-03
[http://www.ubuntuforums.org/showthread.php?t=184838](http://www.ubuntuforums.org/showthread.php?t=184838)

quizas eso te sirva, es para impresoras hp
como no tengo impresora, no tengo idea de si sirve o no :D
suerte.

---

### Post by user1397 on 2006-12-03
> **Hex_Mandos said:**
> Hola, anoche instale Kubuntu (edgy) por primera vez. Jamas en mi vida use un SO Linux o Unix, aunque tengo bastante experiencia con DOS/Windows. Estuve jugando un poco, haciendo pruebas, instale Automatix 2 y el desktop Gnome entre otras cosas. Pero no puedo hacer andar un par de cuestiones:

1) Como hago para configurar el teclado cosa que si trato de poner acentos no me queden "as´i"?

2) Tengo que alinear mi impresora (una Laserjet 5l vieja pero eficiente), y segun leo en linuxprinting.org el driver recomendado es HPLIP. Ahora, lo tengo bajado en un archivo .run, como lo ejecuto? O lo instalo como driver? La impresora ya anda, pero me interesan las herramientas de mantenimiento.

3) Como hago para formatear y particionar mi segundo disco? Anoche quise instalar Windows XP, pero el turro no reconocia sus propias particiones. Entonces me canse e instale Kubuntu (prueba de que cualquier infeliz puede instalar una distro como esta sin mucho drama, por lo menos fue mas facil que Windows). Usar un diskette booteable no puedo, porque mi disketera hace años que no funciona (salvo para juntar polvo).

4) Tengo entendido que cuando instale WinXP voy a tener que reinstalar grub para poder elegir desde que disco bootear. Como lo hago?

Gracias
1) no se...

2) si podes hablar ingles, podes probar mi guia sobre la instalacion de impresoras HP.  Buscala en mi firma.

3) Primero, debemos saber como esta conectado tu segundo disco a tu computadora.  Dime que dice el terminal  (Kmenu > System > Konsole) cuando tipeas:
```
sudo fdisk -l
```4) Yo sugiero que instales windows primero, y despues kubuntu.  usando el cd "live" de kubuntu, andate a Kmenu > System > QtParted

es un programa que particiona tu disco como quieras.  ahi, particiona tu disco para que tengo una particion de NTFS (windows) y uno para ext 3 (kubuntu)

---

### Post by Hex_Mandos on 2006-12-03
Gracias! Lei el post, pero el problema sigue: no encuentro manera de usar el HPLIP. La impresora ya la configure, anda. Pero la tengo que alinear, para lo que necesito el programita de mantenimiento. Lo bajaria para windows, pero como no quiere dejarse instalar estoy un poco jodido.

(Edit: la respuesta era para lavaramano)

Gracias erik, el fdisk me da esto:

Disco /dev/hdb: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1               1        2612    20980858+   7  HPFS/NTFS
/dev/hdb2            2613       14592    96229350    f  W95 Ext'd (LBA)
/dev/hdb5            2613       14592    96229318+   e  W95 FAT16 (LBA)


Disco /dev/hdb: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1               1        2612    20980858+   7  HPFS/NTFS
/dev/hdb2            2613       14592    96229350    f  W95 Ext'd (LBA)
/dev/hdb5            2613       14592    96229318+   e  W95 FAT16 (LBA)

El disco en el que quiero instalar windows es el hdb.

Sobre el orden de instalacion, hubiera instalado windows antes, pero no reconocia las particiones sin darme una opcion de que hacer. Por eso queria tener instalado algun SO para formatear el disco, cosa que despues Windows no diera error.

---

### Post by felipelerena on 2006-12-03
off topic: que es tu "signatura"?

---

### Post by lavaramano on 2006-12-03
@felipelerena: signatura = signature = firmita, lo que sea. se entendio.

@hex_mandos: el link que te pase es la guia que tiene erik1397 en su 'firma', asi que el sabria mejor que yo los pasos a seguir 

saludos

---

### Post by beuno on 2006-12-04
> **Hex_Mandos said:**
> 

3) Como hago para formatear y particionar mi segundo disco? Anoche quise instalar Windows XP, pero el turro no reconocia sus propias particiones. Entonces me canse e instale Kubuntu (prueba de que cualquier infeliz puede instalar una distro como esta sin mucho drama, por lo menos fue mas facil que Windows). Usar un diskette booteable no puedo, porque mi disketera hace años que no funciona (salvo para juntar polvo).

Instala el gparted que es como el partition magic y lo hace graficamente desde ahi (no se si vas a querer andar jugando con los discos desde la consola si no estas acostumbrado).
Podes buscarlo en synaptic o con el comando:
```
sudo aptitude install gparted
```
Te va a agregar un item en el menu.


> **Hex_Mandos said:**
> 
4) Tengo entendido que cuando instale WinXP voy a tener que reinstalar grub para poder elegir desde que disco bootear. Como lo hago?

Windows te va a sobreescribir el MBR al instalar.
Te diria que antes de instalar windows te bajes un LiveCD de ubuntu.
Si te manejas bien con el ingles, aca tenes como restaurarlo:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Si no te manejas bien, cuando hayas instalado windows, volve y hacemos juntos un paso por paso.


Suerte!

---

### Post by Hex_Mandos on 2006-12-05
El foro me estaba dando algunos problemas para loguearme, asi que no pude responder antes.

Ya solucione practicamente todos los problemas. Windows no queria saber nada con instalarse en el slave, asi que tuve que formatear de vuelta el disco master para mandar a Windows ahí. De paso aproveche para jugar un poco con las particiones (la primera vez las hice automaticamente). Igualmente, hoy tuve que instalar Ubuntu un par de veces mas por quilombos que armé tratando de configurar la placa de video (reventé el X, aparentemente, asi que recibía un error similar a la pantalla azul de la muerte de Windows). Ubuntu tiene mi record de "Sistema Operativo instalado mas veces en un lapso de 24 horas", lo que no está mal si pensamos que la instalación es verdaderamente mas user-friendly que la de Windows.

Con el teclado me resigné, y pasé al layout America Latina (a secas). No es exactamente el mismo que tengo (el mío es el segundo de la lista), pero me deja usar tildes, lo que se me hace fundamental.

Lo único que me falta es el tema de la impresora. El tema no es el driver (se instala facilísimo, hay miles de impresoras como esta dando vueltas todavía, es muy barata), sino la "caja de herramientas" que incluye el programita para alinear el toner. Me fijé si HP la tiene en su sitio para Windows (para algo tiene que servir, no?), y tampoco la encuentro. Es un pequeño quilombito, esta la compré usada y no recuerdo si alguna vez tuve los drivers originales. Voy a tener que revisar las cajas viejas.

Gracias por la ayuda, gente.

---

### Post by DuckMan on 2006-12-05
respecto a la impresora, creo q hay un paquete q viene con las utilidades de HP!

y si reventaste el Xorg no haace falta reinstalar, no sabes las veces q me paso, generalmente solo basta con reconfigurar el paquete o editar desde la consola lo q cambiaste. Para esto ultimo usas "sudo nano /etc/X11/xorg.conf" y ahi cambias todo

---

### Post by felipelerena on 2006-12-05
> **Hex_Mandos said:**
> Igualmente, hoy tuve que instalar Ubuntu un par de veces mas por quilombos que armé tratando de configurar la placa de video (reventé el X, aparentemente, asi que recibía un error similar a la pantalla azul de la muerte de Windows). Ubuntu tiene mi record de "Sistema Operativo instalado mas veces en un lapso de 24 horas", lo que no está mal si pensamos que la instalación es verdaderamente mas user-friendly que la de Windows.

No, negro, esto no es Windows, (IUPI) no necesitas instalar de nuevo el sistema opertativo cuando jodes un paquete nomas.

Consejos:
cuando hayas jodido el X hace esto:
```
sudo dpkg-reconfigure xserver-xorg
```
cuando hayas cagado otro paquete hace esto:
```
sudo aptitud reinstall nombre-del-paquete
```

---

### Post by Hex_Mandos on 2006-12-06
Gracias por el dato! Me imaginaba que era arreglable, pero en el momento no tenia la menor idea de como hacerlo, y mi manejo del terminal es todavía muy rudimentario. Por suerte use DOS durante años en mi infancia, así que no estoy tan perdido como el usuario promedio de Windows, pero igual todavía me supera un poco. 

(detalle: creo que te faltó la última letra de 'aptitude' :P)

---

### Post by felipelerena on 2006-12-06
> **Hex_Mandos said:**
> 
(detalle: creo que te faltó la última letra de 'aptitude' :P)
Eh... estaba probando tus conocimientos, mi joven Padawan.
(D'oh) jejeje.
si estas en el horno alguna vez y necesitas entrar a alguna pagina para buscar como solucionarlo te recomiendo usar un browser de consola que se llama "w3m".
se instala como todos los demas paquetes.

y entras a la pagina que quieras poniendo
```
w3m www.google.com
```
saludos

---

