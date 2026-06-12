---
title: "Nuevo en Ubuntu: Duda entre Ubuntu y Ubuntu Estudio"
date: 2007-11-21
forum: Argentina Team
---

### Post by BiTFx on 2007-11-21
Hola, quería preguntarles si en **Ubuntu** puedo utilizar programas de edición multimedia profesional de audio, video y gráficos, tal cual lo hace **Ubuntu Studio**.
 
La verdad que hoy he probado el **Live CD** de **Ubuntu 7.10** para procesadores de 64 bits, primera vez que tengo contacto con **Linux** y me incliné por esta distribución (tuve algunos inconvenientes después de iniciar **Ubuntu**, pero grabaré de nuevo la imagen y luego les cuento como anduvo, ya que al chequear el CD me dice que tiene 1 archivo dañado).
 
**Uso principal que le daré a Linux**: diseño web (php, mysql, html), un poco de diseño gráfico, edición y streaming de audio y video, y por supuesto, aprender bastante sobre Linux.
 
**Uso secundario**: Navegar por internet (web, ftp, p2p, chat, mensajeros, etc), escuchar música, ver videos y un poco de programación.
 
**Conocimientos**: usuario avanzado de MS Windows, MS-Dos, programacón en C++.
 
**Mi PC**: Placa Madre M2NPV-VM, Video NVIDIA GeForce 6150 (on board), Procesador AMD64 Athlon X2 3600+, 1 Gb de Ram, Disco Rígido de 250 Gb Sata 2 (particionado en 2).
 
Espero haber puesto los datos correctos y no haberme sobrepasado, estuve leyendo la guia que publicaron en el post de arriba y me hace falta su consejo para empezar de lleno.
 
Muchas gracias por su ayuda.

---

### Post by sajnox on 2007-11-21
Los programas los podes correr en ambos sistemas de la misma manera (son los dos Ubuntu) la diferencia mayor esta en el software que viene incluido en el Live CD

Si ya tenes Ubuntu desde sistema/administracion/synatptic podes agregar las aplicaciones, busca por Ubuntu Studio y podes agregar lo que mas te interese de Ubuntu Studio

Si mal no recuerdo alguna vez lei por ahi que el Ubuntu Studio tiene un Kernel con alguna modificacion para que sea de respuesta mas rapida (low latency), pero no me animo a asegurartelo 100%

Que lo disfrutes!!!

---

### Post by BiTFx on 2007-11-21
Ok, gracias por la respuesta, me quedo tranquilo entonces, voy a instalar Ubuntu 7.10 y después le agrego las aplicaciones que me hagan falta.
 
De todas formas, voy a hacer la instalación y ver que pasa luego, soy muy nuevo en Ubuntu.

---

### Post by JorgeGhersa on 2007-11-22
Confirmo lo dicho por sajnox: el kernel del ubuntu studio es el Real-Time ( optimizado para achicar la latencia ); así que quizás te convenga ponerle ubuntu studio de primera y después agregar lo que quieras del ubuntu "normal" que viceversa; porque dudo que puedas cambiar de núcleo fácilmente ( es decir, en términos de novato ) después...

Acá hay más data:
[http://www.vivalinux.com.ar/distros/ubuntu-studio-7.10.html](http://www.vivalinux.com.ar/distros/ubuntu-studio-7.10.html)
[http://www.nictuku.com.ar/blog/2007/09/06/kernel-realtime-en-ubuntu-patchs-de-thomas-gleixner-e-ingo-molnar/](http://www.nictuku.com.ar/blog/2007/09/06/kernel-realtime-en-ubuntu-patchs-de-thomas-gleixner-e-ingo-molnar/)

---

### Post by facundocorradini on 2007-11-22
Perdon gente, pero cual es la ventaja real que ofrece ese Kernel Real Time??...
............................................................................................................................

Yo le recomendaría instalar Ubuntu y luego instalarle lo que necesite:

> Uso principal que le daré a Linux: diseño web (php, mysql, html), un poco de diseño gráfico, edición y streaming de audio y video, y por supuesto, aprender bastante sobre Linux.

Vas a necesitar instalarte un LAMP: para ello, en synaptic vas a edicion->marcar paquetes por tarea y eliges servidor LAMP. 
Tambien tenés que instalar algún editor: ahí te puede venir bien Bluefish, Screem o Quanta

Diseño Grafico: si te das manija, Gimp puede irte muy bien. Para vectorial, Inkscape es lo máximo. Edición de Audio: Audacity. 
> 
Uso secundario: Navegar por internet (web, ftp, p2p, chat, mensajeros, etc), escuchar música, ver videos y un poco de programación.

Estas tranquilo. para web te recomiendo usar firefox, y agregarle un par de extensiones:
- Firebug para depurar tus webs, Web Developer te da un monton de herramientas muy utiles...  El FTP te recomiendo usar FireFTP, tambien una extensión de firefox.

Para P2P, te puede venir muy bien Frostwire (bajate el .deb de la web) y para los torrents Deluge es lo máximo.  
Chat: Xchat (IRC)
Mensajería: te recomiendo quedarte con Pidgin.

saludos y bienvenido!

---

### Post by BiTFx on 2007-11-22
Uhhhh, gente, muchisimas gracias, muy buena y bastante info!!!
 
Pensaba poner un post nuevo preguntando sobre aplicaciones para cubrir mis requerimientos, pero **facundocorradini** me dejó clarísima esa parte, muchas gracias!!!
 
Vi que **JorgeGhersa** y **Sajnox** recomiendan el Ubuntu Studio, y **facundocorradini** me recomienda Ubuntu.
 
Agradezco su interés, como novato en esto, prefiero comenzar con **Ubuntu**, ya que he estado buscando información sobre esta Distribución, y es como que me he "encariñado" y me despierta curiosidad probarla. 
 
Seguramente luego de pasar un tiempo utilizándolo pueda optar por otras distribuciones o aprender a poner aplicaciones compatibles, pero agradeciendo su interés voy a comenzar con **Ubuntu**, ese va a ser el primer paso.
 
Espero su ayuda, Muchas Gracias.
 
Ahora estoy descargando la iso del DVD, asi tengo mas variedad de aplicaciones para echar mano.

---

### Post by por100pre1 on 2007-11-22
Puedes instalar Ubuntu 7.10 y luego instalar Ubuntu Studio con todos sus programas usando este comando en Terminal (**Aplicaciones> Accesorios> Terminal**):

```
sudo aptitude install linux-rt ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

---

### Post by JorgeGhersa on 2007-11-22
Yo decía de U.S. porque no es "otra distribución" distinta y potencialmente más compleja, es el mismo querido ubuntu de siempre ( con gnome, synaptic, etc. ) pero con el kernel aquel, que no sé si puede ponerse una vez andando sobre un ubuntu común.

La ventaja es que ese kernel está mejorado para evitar o minimizar la latencia, es decir, el tiempito entre pedirle algo a la máquina y que lo haga; cosa que para audio es bastante importante para que los tiempos peguen justo... En un núcleo común, ese tiempo depende de las distintas cosas que estén andando a la vez y cuál tiene prioridad; en el RT creo que lo que pedís nuevo se pone a andar de una, sin esperar nada. ( Creo, tampoco sé tanto ).

---

### Post by por100pre1 on 2007-11-22
> **JorgeGhersa said:**
> ...pero con el kernel aquel, que no sé si puede ponerse una vez andando sobre un ubuntu común.

La ventaja es que ese kernel está mejorado para evitar o minimizar la latencia, es decir, el tiempito entre pedirle algo a la máquina y que lo haga; cosa que para audio es bastante importante para que los tiempos peguen justo... En un núcleo común, ese tiempo depende de las distintas cosas que estén andando a la vez y cuál tiene prioridad; en el RT creo que lo que pedís nuevo se pone a andar de una, sin esperar nada. ( Creo, tampoco sé tanto ).

Si, el kernel se puede agregar a Ubuntu Gutsy regular, asi:

```
sudo aptitude install linux-rt
```

Quienes usen Feisty pueden agregar este:

```
sudo aptitude install linux-lowlatency
```

---

### Post by xpelaox on 2007-11-22
> **facundocorradini said:**
> Perdon gente, pero cual es la ventaja real que ofrece ese Kernel Real Time??...
............................................................................................................................

Yo le recomendaría instalar Ubuntu y luego instalarle lo que necesite:



Vas a necesitar instalarte un LAMP: para ello, en synaptic vas a edicion->marcar paquetes por tarea y eliges servidor LAMP. 
Tambien tenés que instalar algún editor: ahí te puede venir bien Bluefish, Screem o Quanta

Diseño Grafico: si te das manija, Gimp puede irte muy bien. Para vectorial, Inkscape es lo máximo. Edición de Audio: Audacity. 


Estas tranquilo. para web te recomiendo usar firefox, y agregarle un par de extensiones:
- Firebug para depurar tus webs, Web Developer te da un monton de herramientas muy utiles...  El FTP te recomiendo usar FireFTP, tambien una extensión de firefox.

Para P2P, te puede venir muy bien Frostwire (bajate el .deb de la web) y para los torrents Deluge es lo máximo.  
Chat: Xchat (IRC)
Mensajería: te recomiendo quedarte con Pidgin.

saludos y bienvenido!

Disculpen que me valla un poco del topic, estoy aprendiendo PHP, e instale lamp como dijo facundocorradini, queria saber exactamente como es que tengo que hacer para poder abrir mis archivos de PHP, se que tengo que entrar a localhost/ el nombre de mi archivo.... pero no se en que carpeta tengo que poner los archivos.

Gracias y perdon por desvirtuar un pokito

---

### Post by Paularg on 2007-11-22
Sajnox, esta en lo correcto, el kernel es distinto (low latency). Te recomiendo usar el STD 7.10 y agregarle los paquetes de software que quieras via synaptics. 

Luego cuando tengas que upgradear a futuras versiones via el gestor de Actualizaciones, vas a tener menos inconvenientes.

Ademas hay ciertas funcionalidades de manejo de los drivers restrictivos via ventanas de gnome muy simples y utiles.

El Ubuntu Studio que yo instale estaba basado en 7.04.

Bueno, que disfrutes "el viaje"

---

