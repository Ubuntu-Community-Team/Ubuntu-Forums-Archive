---
title: "problema con wine"
date: 2007-11-21
forum: Argentina Team
---

### Post by Pabliich on 2007-11-21
al instalar wine me sale este error 

crossfire@ZonaHacker:~$ sudo apt-get install wine
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
crossfire@ZonaHacker:~$ 


ayuda pliz

---

### Post by natille on 2007-11-21
¿Por que no usa Synaptic para instalar? Esta en los repositories.

Tambien, si todavia tiene problemas, hay un sitio web: [http://www.winehq.org](http://www.winehq.org)
No sé si haya sitio en castellano...

---

### Post by Mauro22 on 2007-11-21
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Ahi te lo dice, pone

> dpkg --configure -a

en la consola para arreglar el problema!

---

### Post by Pabliich on 2007-11-21
**me dice que el error esta en que el paquete de virtua box debe reinstalarse pero no se encuentra el archivo.. como lo borro? o lo reinstalo?**

---

### Post by Mauro22 on 2007-11-21
Hace:

sudo apt-get install nombredelpaquete. No se si es virtuabox, virtual-box, etc etc, pone el que te tira...

a ver que pasa..

---

### Post by sajnox on 2007-11-21
Para desinstalar un programa podes hacerlo en dos maneras

Graficamente

Entra en synaptic, buscar por virttual box y marcar para desinstalar

Por consolo

```
 sudo apt-get remove "nombre del programa"
```

Que pasa si ejecutas el comando que te marca Mauro22??

---

### Post by ubuntu27 on 2007-11-22
> **Pabliich said:**
> al instalar wine me sale este error 

crossfire@ZonaHacker:~$ sudo apt-get install wine
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
crossfire@ZonaHacker:~$ 


ayuda pliz

ese error ocurre cuando dpkg ha sido interrumpido. Un ejemplo seria que estas bajando un programa con apt-get, y de pronto por alguna razon la computadora se apaga ( i.e. se corta la luz)

abre el terminal y escribe lo siguiente

```
sudo dpkg --configure -a
```

eso corregira el error.

---

### Post by Pabliich on 2007-11-23
amigos ayuda por favor.. cualqier cosa que hago me aparece
[B]
E: el paquete virtual box necesita ser reinstalado pero no se encuentra el archivo.. ya no me anda internet ni beryl.. no puedo hacer nada.. todo causado por eso.. pàra todo me da ese errorr[/B]

---

### Post by Pabliich on 2007-11-23
Hola tuve exactamente el mismo problema pero encontré la solución pero al primer intento no funciono pero después SI FUNCIONO!!!

me saque la solución de esta página :
[http://www.ubuntu-es.org/index.php?q=node/46265](http://www.ubuntu-es.org/index.php?q=node/46265)
y esta es la solución posteada:

sudo dpkg --remove --force-remove-reinstreq virtualbox
dpkg - aviso, no se tendrá en cuenta el problema por estar activa
una opción --force:
El paquete está en un estado muy malo e inconsistente - debe reinstalarlo
antes de intentar desinstalarlo.
(Leyendo la base de datos ...
dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`virtualbox', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.
94408 ficheros y directorios instalados actualmente.)
Desinstalando virtualbox ...

en pocas palabras copia y ejecuta este código en la consola sudo dpkg --remove --force-remove-reinstreq virtualbox

---

### Post by sajnox on 2007-11-23
Si despues queres instalar virtual box avisa que te doy una mano para hacerlo, en mi opinion lo mejor es agregarlo al repositorio y desde ahi instalarlo, asi ademas siempre lo tenes al dia

---

