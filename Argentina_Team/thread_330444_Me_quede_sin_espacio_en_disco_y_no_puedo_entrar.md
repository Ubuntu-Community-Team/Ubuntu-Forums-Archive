---
title: "Me quede sin espacio en disco y no puedo entrar"
date: 2007-01-03
forum: Argentina Team
---

### Post by Nemesis Teufel on 2007-01-03
Buscando fotitos con el Picasa, me aparece un mensaje diciendo que mi disco estaba lleno (ya que seguramente usa espacio del disco para no cargar la ram). No le di bola.. pense que solo cargaba los archivos temporalmente. 
La prox. vez que inicie la PC no me dejó: ingreso user y pass y amagó a entrar, pero volvió al screen de login.. lo hice un par de veces hasta que me aparecio un cartel que decia masomenos asi:
GDM intenta entrar pero no puede x falta de espacio en el disco. Contacte al administrador.

Probé entrando en kde, gnome, xfce, modo prueba de fallo, ubuntu recovery mode, etc y nada.

Como me las puedo arreglar? Con el livecd podria montar la partición de ubuntu, para entrar y borrar algunas cosas?

---

### Post by felipelerena on 2007-01-03
probaste con el live?
pones el live y accedes al disco... te lo automountea...

---

### Post by Nemesis Teufel on 2007-01-03
No se me monta (que mal suena).
Como lo hago manualmente? Siempre tengo este tipo de problemas con el disco :S (si, ya se, x boludo)

---

### Post by tzulberti on 2007-01-03
Lo que podes hacer es en vez de loguarte al X, usar una consola. Desde ahi seguramente te vas a poder loguear...

---

### Post by Nemesis Teufel on 2007-01-03
> Lo que podes hacer es en vez de loguarte al X, usar una consola. Desde ahi seguramente te vas a poder loguear...

Creo haber hecho eso y tmp pude.

---

### Post by NicolásB on 2007-01-03
Cuando cargue el gdm apretá ctrl+alt+f1, tendría que aparecer una consola para logearte.
Una vez adentro mira que tira el comando "mount" (para saber si esta montada la partición /) y "df -h" para ver el espacio disponible.

---

### Post by Nemesis Teufel on 2007-01-03
Bueno, logré montar el disco.
Borre un par de cosas y me quede con un poco mas de 1.20 gbs libres, creo que **muuucho** mas que suficiente para entrar, pero aun asi el error persiste.

Tome nota de lo que me dice; acá esta:
> GDM no pudo escribir en su archivo de autorización. Esto puede significar que no tiene espacio en disco o que su directorio personal no se pudo abrir para su escritura. En cualquier caso no es posible iniciar la sesión. Contacte con el administrador del sistema.

---

### Post by Dies on 2007-01-03
Suena a un problema con permisos.
Para saber si ese es el caso, puede utilizar la consola para crear una cuenta nueva.
ctrl-alt-F1

sudo adduser guest

Conteste las preguntas y despues exit, ctrl-alt-F7, trate de entrar con la cuenta que acaba de crear.

---

### Post by felipelerena on 2007-01-03
para, antes de meterte a crear usuarios y ver lo de los permisos hacete un ```
sudo dpkg-reconfigure gdm
``` a ver que pasa

---

### Post by Nemesis Teufel on 2007-01-04
bueno.. hice: 

```
sudo dpkg-reconfigure gdm
```

y me dice:

> Login incorrect
Login timed out after 60 seconds
Ubuntu 6.10 Nemesis-Desktop tty1

cuando hago: 
```
Sudo adduser guest
```
directamente me dice: login incorrect. No llego a contestar nada..

Me parece raro, es como que no hace caso al sudo..

---

### Post by ubuntu27 on 2007-01-04
> **Nemesis Teufel said:**
> Bueno, logré montar el disco.
Borre un par de cosas y me quede con un poco mas de 1.20 gbs libres, creo que **muuucho** mas que suficiente para entrar, pero aun asi el error persiste.

Tome nota de lo que me dice; acá esta:

1 GB es muy poco >< :(  yo me "mataria" si tuviera ese problema... 
Bueno no tanto, yo tambien tuve ese problema que tu tienes. Lo que hice era hacer un backup (copia de seguridad) de mis archivos _importantes _ y reinstalar Ubuntu (Apoveche la ocacion para instalar la nueva version de Ubuntu, Edgy Eft).

Pero, no creo que quieras hacer eso tu :P


Has esto:
Al cargar el GDM (donde escribes tu username y password para iniciar X) Anda a la Consola real:
```
CTRL+ALT+F1
```

 y escribe
```

df -H
``` 

eso te mostrara cuanto de espacio libre tienes en tu disco. PEgalo esa informacion aqui.


Ahora

```
sudo apt-get clean
```

para Limpiar o eliminar archivos no necesarios en la sistema. (Paquetes de instalacion que se baja al instalar programas, etc)


Con esto no sera suficiente, pero, algo es algo.
Lo resto es elminar tus propios archivos...  (copia tus archivos en un CD, disco,... algun otro medio externo)

---

### Post by ubuntu27 on 2007-01-04
Intrucciones para borrar archivos desde el terminal/consola

Anda a tu directorio Home

```
cd /home/tu-nombre-de-usuario/
```

Ver el contenido de ese directorio:

```
ls
``` 

Decide cual eliminar

```
rm nombre-del-archivo
```

Eliminar carpeta/directorio
```

rm -rf nombre-carpeta
```

Repitir los pasos para otras directorios... 

no te olvides 

d /home/tu-nombre-de-usuario/Desktop

tambien (si que tienes algun archivo alli)

Reinicar la computadora:

```
sudo shutdown -r now
```
**O**
```
sudo reboot now
```

---

### Post by NicolásB on 2007-01-04
> **Nemesis Teufel said:**
> 
[...] directamente me dice: login incorrect. No llego a contestar nada..
Me parece raro, es como que no hace caso al sudo..

Perdon por la pregunta obvia, pero ¿estás logueado en la consola? ¿el pasword para el comando "sudo" esta bien?
Proba logeandote como root sino.

[QUOTE=Ubuntu27]
1 GB es muy poco ><  yo me "mataria" si tuviera ese problema...
[/QUOTE]

No se si un gb es poco o no para "/" pero por lo menos debería cargar gnome.

[QUOTE=Nemesis Teufel]
Tome nota de lo que me dice; acá esta:
Quote:GDM no pudo escribir en su archivo de autorización. Esto puede significar que no tiene espacio en disco o que su directorio personal no se pudo abrir para su escritura. En cualquier caso no es posible iniciar la sesión. Contacte con el administrador del sistema.
[/QUOTE]

Logeate en una consola y hace "ls -la /home/" para ver si tenés permisos de escritura (y sos dueño) de tu carpeta. Sino, con "chmod" y "chown" podés cambiar los permisos.

---

### Post by ubuntu27 on 2007-01-05
Nemesis Teufel, me gustaria saber como te va. 
Solucionaste el problema?

---

### Post by Nemesis Teufel on 2007-01-07
Perdón por la ausencia temporal y desinterés en el tema.. estaba bajoneado y no queria a ponerme a configurar mi GDM (mal de amores.. u.u)

Ahora que el bajón se fué y no hay mas mal de amores retomo:

> 1 GB es muy poco ><  yo me "mataria" si tuviera ese problema... 
Lo curioso es que tengo la misma capacidad que vos: 120 gb. Tengo mucha musica, je.


> yo tambien tuve ese problema que tu tienes. Lo que hice era hacer un backup (copia de seguridad) de mis archivos importantes  y reinstalar Ubuntu 
Si, me imagino que es la solución mas facil, pero realmente no quiero hacerlo por cada error que tenga. Si no me queda otra lo haré, pero tiene (supongo) que haber una explicación a esto..
Con hacer backup no tengo problema.. puedo pasar a otro disco la info que tengo en ubuntu y fue. 
Para pasarlo al disco de windows; tenría hacer esto:
Con el livecd monto el disco de windows, el de ubuntu y le doy soporte a ntfs para pasar los archivos ahi, no?

--
> 
Logeate en una consola y hace "ls -la /home/" para ver si tenés permisos de escritura (y sos dueño) de tu carpeta. Sino, con "chmod" y "chown" podés cambiar los permisos.
Mas despacio cerebrito!! :)
Qué logro con hacer eso? Para qué es?
Supongamos que soy dueño del permiso.. entonces?
y si no lo soy?

---

### Post by Dies on 2007-01-07
> **Nemesis Teufel said:**
> 
Mas despacio cerebrito!! :)
Qué logro con hacer eso? Para qué es?
Supongamos que soy dueño del permiso.. entonces?

Entonces creo que los dos estariamos sorprendidos  :-k 

Por eso te dije que trates con una cuenta nueva, para comprobar que ese era el problema, es facil hacer una cuenta nueva y despues borrarla. Pero lo que te dijo Nicolas es la manera correcta, solo que la mia te da mas esperanza si funciona. :mrgreen: 

> **Nemesis Teufel said:**
> y si no lo soy?
](*,) 
Pues no puedes usar esa cuenta hasta que los permisos sean corregidos.
En esa carpeta solo tu debes poder escribir y leer nadie mas debe tener derechos.

---

### Post by ubuntu27 on 2007-01-07
> **Nemesis Teufel said:**
> Perdón por la ausencia temporal y desinterés en el tema.. estaba bajoneado y no queria a ponerme a configurar mi GDM (mal de amores.. u.u)



Lo curioso es que tengo la misma capacidad que vos: 120 gb. Tengo mucha musica, je.

Hehe, yo tambien lo llene mi disco con Musica y video muchas veces :D Ahora tengo poca musica en mi disco, les queme al  CD y los borre de mi HD.

> **Nemesis Teufel said:**
> 
Si, me imagino que es la solución mas facil, pero realmente no quiero hacerlo por cada error que tenga. Si no me queda otra lo haré, pero tiene (supongo) que haber una explicación a esto..
Con hacer backup no tengo problema.. puedo pasar a otro disco la info que tengo en ubuntu y fue. 
Para pasarlo al disco de windows; tenría hacer esto:
Con el livecd monto el disco de windows, el de ubuntu y le doy soporte a ntfs para pasar los archivos ahi, no?

--


Si, puede funcionar eso. La escritura NTFS desde GNU/Linux ha madurado segun dicen sus creadores. Pero, la gente todavia tienen miedo de probarlo.

Para estar al lado seguro, mejor accede tus archivos que estan en Ubuntu desde Windows. 

Ya que mencionaste Windows, me imagino que tienes Dual-Boot.

Usa este programa: [Explore2fs ]("http://www.chrysocome.net/explore2fs")

Ese programa te permitira acceder ext3 desde Windows.

Al abrir ese programa, veras que tus directorios en ext3 seran visibles. Anda en el directorio donde estan tus archivos que quieres hacer copia, y click en "extraer" o "extract"  y escoje donde extraer (donde guardar).

Suerte.

Ah, de cierto, si tienes archivos que tengan letras no latinas como Japones, Chino, etc. Usa la version beta 1.08 BETA. (Si eres como yo, tendras muchas musicas asiaticas)

Todavia no esta en fase final, pero, no me ha fallado a mi. Las versiones actuales no tienen soporte de Caracteres no-latinos.

---

### Post by Nemesis Teufel on 2007-01-09
Gracias! Esta muy bueno el programa ese, aunque no me hizo falta. Acabo de arreglar el problema. Me costó mucho la verdad...

Bootié a Ubuntu, en vez de poner mi usuario puse el de mi vieja primero y magicamente entró.. acto seguido entre con el mio, aunque la X se abrio para el ojete con reiniciarla anduvo de maravilla. Son errores pavos que se solucionan de la manera mas fácil.

Me siento un estupido pero con suerte.

Beuno: resuelto.

---

### Post by felipelerena on 2007-01-09
copado... pero. no entiendo... lo arreglaste logueandote como tu vieja?

---

### Post by Nemesis Teufel on 2007-01-09
emm.. si.. asi de técnico como te lo comento.. 
Si mal no recuerdo, creo haberme logueado con el user d mi vieja y me habia pasado lo mismo..

O se arregló solo o es el power de mi vieja ubuntera (?) que se puso feliz cuando se entero que "arreglé" la "pc" (hay que hablarle con vocabulario simplificado..) y podía jugar a su jueguito de chinos y mandar "imeils" y usar el "muñequito" (en windows no le funca el msn en su usuario y no le pongo el acceso directo a hotmail para que use ubuntu :D)

---

### Post by ubuntu27 on 2007-01-09
Nemesis Teufel me alegra que solucionaste tu problema :) , aunque sea magicamente :rolleyes: 

Elminaste archvos no necesarios para obtener mas espacio libre.
Seguro eso es lo que soluciono.

---

### Post by Nemesis Teufel on 2007-01-09
Si, eliminé archivos, pero fue totalmente indiferente a eso, ya que borré hace rato las cosas y de la última vez a esta que lo probe, no había eliminado nada nuevo.

Hay ciertas cosas que no conviene indagar. Mejor que queden así que están bien :P

---

### Post by felipelerena on 2007-01-09
en conclusion... se arregló solo. no entiendo, en mi experiencia personal las cosas o se rompen o se arreglan solas, pero ambas no...

---

### Post by Nemesis Teufel on 2007-01-09
> en conclusion... se arregló solo. no entiendo, en mi experiencia personal las cosas o se rompen o se arreglan solas, pero ambas no...

> Hay ciertas cosas que no conviene indagar. Mejor que queden así que están bien :P


Soy tan deforme que YO si puedo. Con el flash me pasó lo mismo.. ahora me funciona de maravilla.. se ve que el soft le cuesta adaptarse a mi (?)

---

### Post by felipelerena on 2007-01-09
ok, te banco, mejor no hacer preguntas...

---

### Post by ubuntu27 on 2007-01-12
Es como que si la computadora tuviera un alma y decide por si mismo si debe de funcionar bien o que si debe de "romperse" a proposito para enojar a su maestro y dueño :D  

Las computadoras les encantan ver la expresion en la cara que tienen la gente cuando algo ocurre. :twisted:

---

### Post by Nemesis Teufel on 2007-01-12
sudo chistek
password: *****

Es que los computadores ya pensamos (wtf!) 

Y nos gusta ver cuando nuestro dueño pone esa cara de: te romperia de una patada pero sos tan cara.

A su vez, de los errores se aprenden y ud aprende cuando yo dejo de funcionar, o simplemente.. no tengo ganas de trabajar..

Pero luego de un rato desistimos y volvemos a la normalidad.

Apagando Sesión.

---

