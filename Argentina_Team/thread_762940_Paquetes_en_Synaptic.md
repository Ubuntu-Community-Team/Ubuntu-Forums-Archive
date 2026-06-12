---
title: "Paquetes en Synaptic"
date: 2008-04-22
forum: Argentina Team
---

### Post by AzureSky07 on 2008-04-22
Hola gente, la verdad estuve intentando y no he logrado nada, quisiera saber si  hay alguna forma de meter un paquete .deb que me halla bajado en el synaptic para luego poder generar un script de descarga donde me incluya todas las dependencias ( porque es muy molesto estar bajando uno a uno ) y despues, como ejecuto ese script de descarga?

Saludos AzureSky

PD: perdon por tantas molestias :P

---

### Post by faktorqm on 2008-04-22
Hola, no molestas. No entendi que queres hacer, lei tu post varias veces. Que intentaste haer? para hacer que? como lo hiciste? "METI" meter a donde?
si queres instalar un .deb el comando es 

```
sudo dpkg -i archivo.deb
```

Si queres hacer un script que te instale las dependencias desde ya te digo que no hace falta, por que ya lo hace el synaptic o el apt-get o el aptitude como mas te guste. Se mas explicito y te digo que hacer :P Salu2!

---

### Post by AzureSky07 on 2008-04-23
hola, perdon la demora de la respuesta y la mala explicacion :P lo que quiero hacer es agarrar un paquete cualquiera ( que no este dentro del Synaptic ) y usar dicho programa para que me genere el script de descarga con todas las dependencias que dicho paquete necesite.

Espero haberme expresado mejor.

Saludos AzureSky

---

### Post by Hernán-Amaya on 2008-04-23
fijate si esto te sirve explica como instalar aplicaciones sin internet:

[http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones](http://www.guia-ubuntu.org/index.php?title=A%C3%B1adir_aplicaciones)

si tenes alguna duda antes de preguntar aca entra en la guía que hay muchas cosas y está muy piola!

[http://www.guia-ubuntu.org](http://www.guia-ubuntu.org)

---

### Post by RJQ on 2008-04-23
La mayoría de los .deb tienen ya un script que le dice a tu instalador cuales dependencias necesitas si estas conectado al internet no tienes que hacer nada mas que esperar a que las baje e instale, si por otro lado tienes todas las dependencias listas en alguna carpeta puedes hacer de esta un repositorio para el synaptic. desconozco si funciona igual para .rpms

---

### Post by AzureSky07 on 2008-04-23
Bueno, les comento lo que quiero hacer y que he logrado hasta ahora. El tema es asi: Tengo el ubuntu instalado en un VMware en mi trabajo ( con coneccion a internet ) y lo que quiero es bajarme todo lo que necesite el paquete que quiero instalar para hacerlo en la maquina de mi casa que no tiene internet.

Ahora, un ejemplo, el envy ( para instalar los drivers des placas nvidia ) no figura en el de aplicaciones en Synaptic, que tengo que hacer para que aparezca? ( esto lo hago para saber que dependencias bajarme )

Otro ejemplo, tengo un programa sin instalar, genero el scrip de descarga y que hago con ese archivo? como lo uso o con que programa?

Saludos AzureSky

---

### Post by MeduZa on 2008-04-23
> **AzureSky07 said:**
> Bueno, les comento lo que quiero hacer y que he logrado hasta ahora. El tema es asi: Tengo el ubuntu instalado en un VMware en mi trabajo ( con coneccion a internet ) y lo que quiero es bajarme todo lo que necesite el paquete que quiero instalar para hacerlo en la maquina de mi casa que no tiene internet.

Ahora, un ejemplo, el envy ( para instalar los drivers des placas nvidia ) no figura en el de aplicaciones en Synaptic, que tengo que hacer para que aparezca? ( esto lo hago para saber que dependencias bajarme )

Otro ejemplo, tengo un programa sin instalar, genero el scrip de descarga y que hago con ese archivo? como lo uso o con que programa?

Saludos AzureSky

ahi una opcion que dice solo bajar lo paquetes pero no instalarlos, apt-get -d creo que es

---

### Post by euzkoarima on 2008-04-23
Ok, con el VMWare en definitiva tenes un ubuntu con banda ancha y otro sin. En synaptic podes pedir que te genere un script, correrlo en la que tiene banada ancha y luego incorporar todo desde synaptic en la pc que no tiene conexión.

Si el .deb no esta en los repositorios una posibilidad es que puedas agregar el repositorio de quien publica el soft, y entonces podemos aplicar la "solución synaptic".
Si no es el caso, NO se si el instaldor de paquetes GDebi tiene o no la capacidad de generar un script. Si no lo la tiene, por lo que vi en la red googleando es que hay un comando apt-zip para esos casos, y que dicho sea paso está en los [repositorios de ubuntu]("http://packages.ubuntu.com/apt-zip").
te paso los links que encontré que creo te pueden ser útiles
[http://linux.about.com/cs/linux101/g/aptzip.htm](http://linux.about.com/cs/linux101/g/aptzip.htm)
[http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/](http://ubuntu.wordpress.com/2005/09/22/upgrade-install-ubuntu-on-slow-internet/)
[http://bulma.net/impresion.phtml?nIdNoticia=1795](http://bulma.net/impresion.phtml?nIdNoticia=1795)
[http://pwet.fr/man/linux/administration_systeme/apt_zip](http://pwet.fr/man/linux/administration_systeme/apt_zip)

Saludos

---

### Post by sajnox on 2008-04-23
> **AzureSky07 said:**
> 

Otro ejemplo, tengo un programa sin instalar, genero el scrip de descarga y que hago con ese archivo? como lo uso o con que programa?

Saludos AzureSky

Doble click y la opcion de que lo ejecute en un terminal, si abris el script con un editor de textos vas a ver que lo que hace es ejecutar wget por cada paquete.

Si vas a bajar muchos paquetes abri una carpeta nueva y copia ahi el script ya que los baja a la carpeta desde donde lo ejecutas.

Ahora, si lo haces desde una maquina virtual me parece que tal vez es mejor que uses APTonCD, en la maquina virtual descargas todo los programas que queres y despues con APTonCD te los llevas a tu casa.

mas info en [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by EnriqueK on 2008-04-24
Para poder instalar todo tipo de paquetes desde los repositorios sin tener conexión a Internet, lo mejor es clonar los índices de repositorios de otro equipo que si tenga conexión, para logra ello copia el archivo **sources.list **y además el contenido completo de la carpeta **/var/lib/apt/lists** 
Luego de haberlos puesto en el equipo sin conexión, haz un** sudo apt-get update** y con eso ya tienes instalado los índices de repositorios, solo queda usar **Synaptic** para instalar todo lo que quieras, desde actualizaciones, hasta programas, siempre que dichos paquetes estén contemplados en los repositorios cuyos índices hayas clonado, para hacer esto luego de haber seleccionado los paquetes a instalar desde Synaptic, generas un Script de descargas de paquetes en donde contienen las URLs de descargas las cuales se pueden efectivizar con cualquier equipo con conexión, también usando Synatic los instalas en tu equipo.
El método explicado inclusive es aplicable si creas los índices en cualquier equipo , basta correr en el Live Cd de instalación , introduces un sourcet.list ....etc, tambien en estos casos se puede clonar los índices para llevarlos a un equipo sin conexión.

---

### Post by AzureSky07 on 2008-04-24
Muchisimas gracias a todos por la ayuda me ha servido de mucho. Ahora quisiera hacerles unas consultas si me lo permiten.

cuando ejecuto el script de descarga me arroja este mensaje:

azuresky@Valhalla:~$ wget -c [http://security.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4-minimal_2.4.4-6ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4-minimal_2.4.4-6ubuntu4.1_i386.deb)
--08:10:09--  [http://security.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4-minimal_2.4.4-6ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.4/python2.4-minimal_2.4.4-6ubuntu4.1_i386.deb)
           => `python2.4-minimal_2.4.4-6ubuntu4.1_i386.deb'
Resolviendo security.ubuntu.com... falló: Nombre ó servicio desconocido.

lo curioso de esto es que copio la misma ruta en el firefox y lo baja.

otra consulta, en mi maquina ( la que no tiene internet ) no me reconoce la maldita lectora :S no puedo hacer que me aparezca la lectora en ubuntu ( y eso que al bootear lo detecta y usa  al igual que en windows, sabrian como solucionar esto? ya estuve intentando pero no consegui nada =/

saludos AzureSky

---

### Post by EnriqueK on 2008-04-24
El Script que genera el Synaptic adolece de una falla, eso al menos es así para Feisty, no se si lo habrán corregido, la falla está en que pone por ejemplo wget -chttp.......  lo que hay que corregir es dejar un espacio entre c y http  o sea cada URL de descargas debería quedar así wget -c http..... , esto se hace fácil con el editor gedit usando buscar  -> Reeemplazar . También puedes usar **Firefox** y para ello descarga las extensiones **DownThemAll** (gestor de descargtas) y **Linkification **(convierte texto plano en Link) .
Para la segunda pregunta, intenta con poner **mount /cdrom**

---

### Post by AzureSky07 on 2008-04-24
gracias, probare pero aclaro que el -c y el http estan separados en el script. Con respecto a lo del CD entre en equipo e hice click derecho sobre la unidad de cd y puse montar ( imagino sera lo mismo ) me tiro algo sobre el  hda que no entendi :S

---

