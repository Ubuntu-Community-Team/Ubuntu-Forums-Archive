---
title: "Que distro usar.."
date: 2007-11-18
forum: Argentina Team
---

### Post by benzema on 2007-11-18
Bueno mi consulta es la siguiente actualmente uso ubuntu 7.10 ,hace dos semanas que lo uso y lo veo facil al menos pude configurar todo y colocar todo en su lugar,lo que quiero saber se que hay distintas distribuciones ,y quiero saber a grandes rasgos que diferencias tienen entre las suguientes tres:

.Ubuntu
.Kubuntu
.Xubuntu

Diferencias como:

.Configuracion de internet y aplicaciones
.Compatiblidad con hardware, las tres reconocen el mismo hardware?porque ubuntu me reconocio todo lo OnBoard
.Manera de trabajar
.Rendimiento
.Etc etc etc ,bla bla bla

Saludos.


Posdata:Puedo correr cualquiera de los sistemas,me sobra hardware,es para saber un poquito mas nada mas.

Edit:
Tambien quiero saber que aplicaiones vienen pre-instaladas ..

---

### Post by Ardghal on 2007-11-18
Las diferencias son en el escritorio y las aplicaciones que traen. Siendo que podés instalar el escritorio de KDE en el Ubuntu normal, me parece que la compatibilidad de hardware es la misma.

Sobre la configuración a internet: creo que es igual en todos, ya que cuando agregué KDE a Ubuntu, no tuve que configurar nada; me pude conectar como lo hacía en Gnome.

No se qué querés decir con *manera de trabajar*. Si es por el escritorio, en KDE tenés muchas más opciones para configurar todo. En Gnome es más simple, y aunque no usé Xfce, si es parecido a Fluxbox, debe ser todo minimalista y con aun menos opciones a simple vista. Tendrías que probarlos, sólo es cuestión de bajarlos con apt. Nisiquiera hay que instalar otro SO.

Sobre rendimiento, Ubuntu está bien, con KDE noto que algunas aplicaciones tardan un poco más en iniciarse. Xfce, se supone que es el más liviano de los tres.  Y las aplicaciones que traen deben serlo tambien.

Para saber las aplicaciones pre-instaladas de cada versión, podrías ver en el sitio de cada uno. [Kubuntu.org]("http://kubuntu.org/") y [Xubuntu.org]("http://xubuntu.org/")

---

### Post by facundocorradini on 2007-11-18
Hola benzema

Ubuntu ya lo conoces, todo muy rapido y sencillo.

Kubuntu es igual pero con KDE, un entorno de escritorio mas parecido al de windows....
Por ahí las aplicaciones son un poco mas pesaditas... Trae programas distintos, no trae compiz...
Por ahí tenés un poco más de conguración para tunearlo y eso, pero personalmente prefiero gnome (-- plz no flamear el post!!!--)

Xubuntu trae Xfce, el cual es bastante parecido a Gnome pero más liviano (no tiene nada que ver con fluxbox!!!) 
Tiene algunas aplicaciones mas livianas tambien.


mi consejo es que si querés probarlos, los bajes desde synaptic. 

Instalar KDE o XFCE buscandolo te instalará solo el entorno gráfico, si quieres probar tambien las aplicaciones que trae, puedes poner "marcar paquetes por tarea" y allí selecciones Kubuntu Desktop y/o Xubuntu Desktop. ojo, que se te va a llenar los menus de aplicaciones si mezclas los tres ...

---

### Post by clasificado on 2007-11-19
Kubuntu trae KDE que trae al Konqueror.

Y eso salva tooooooooooodo lo malo de kde.

(y tambien trae Kontact, y kopete)

clasificado

---

### Post by xpelaox on 2007-11-19
coincido con facundocorradini lo mejor es probar, elejir entre Ubuntu y Kubuntu, a mi parecer es mas cuestion de gustos, en cambio tengo entendido que Xubuntu esta orientado quizas a computadoras mas viejas.

Saludos!

---

### Post by el escocés on 2007-11-19
siempre puedes bajar un liveCD de cada uno y probarlo, pero es verdad que los programas de KDE son un poco más pesados.

---

### Post by leo_rockway on 2007-11-19
elegir gnome o kde es cuestion de gustos (y de fanatismo), no por nada siempre que se saca el tema empieza una flame war, jaja.

yo cuando empece con linux me instale muchos escritorios distintos y me quede con el que mas me convencia y hasta el dia de hoy lo sigo usando.

sinceramente, la persona indicada para decidir cual es mejor escritorio sos vos.

---

### Post by benzema on 2007-11-19
> **leo_rockway said:**
> elegir gnome o kde es cuestion de gustos (y de fanatismo), no por nada siempre que se saca el tema empieza una flame war, jaja.

yo cuando empece con linux me instale muchos escritorios distintos y me quede con el que mas me convencia y hasta el dia de hoy lo sigo usando.

sinceramente, la persona indicada para decidir cual es mejor escritorio sos vos.


Bueno ire probando,me faltan 2 horas para terminar de bajar xubuntu lo rpobare y luego bajare kubuntu a ver ki onda ,despues dare mi opinion de cada uno ..
Saludos

---

### Post by fscodelaro on 2007-11-19
Si vas a probar los liveCDs y te gusta alguno hay formas de instalar otros escritorios (KDE, XFCE) en tu ubuntu actual conservando toda tu configuracion, etc.
Yo por ejemplo empecé con ubuntu y despues instalé kubuntu solamente ingresando:

```
sudo apt-get install kubuntu-desktop
```

Hay algunos problemas, como que los menúes se hacen demasiado largos. Después aprendí en el sitio [http://psychocats.net/ubuntu/kde-core](http://psychocats.net/ubuntu/kde-core) que en realidad me hubiera convenido poner:

```
sudo apt-get install kde-core
```

Que instala sólo lo básico de KDE sin todas las aplicaciones que lo acompañana en ubuntu. Pero bueno, me fui de tema, a lo que voy es que si querés instalar otros escritorios luego de probar no reinstales tu pc, solamente agrega ese componente y despues sacá el gnome si quisieras hacer el reemplazo.

---

### Post by Hernán-Amaya on 2007-11-20
Hola, podes probar como ya te dijeron Kubuntu y Xubuntu con sus respectivos escritorios, pero tenés la posibilidad de instalarte otros escritorios como enlightenment[1], flubox[2], icewn[3]

[1] como instalar en gutsy enlightenment entra [acá]("http://linuxman.blogsome.com/2007/09/22/usando-enlightenment-e17-en-ubuntu-gutsy-gibbon/")
[2] esta en los repositorios, [acá]("http://www.ubuntu-es.org/index.php?q=node/57532") te dejo un como configurarlo
[3] esta en los repositorios, [acá]("http://www.ubuntu-es.org/index.php?q=node/7658") te dejo como configurarlo

---

### Post by facundocorradini on 2007-11-20
Coincido con Hernan, hay escritorios alternativos que estan muy buenos.

Yo uso y recomiendo Enlightenment. Es una bestia de animaciónes y es impresionantemente ligero.   Pero ojo, es bastante distinto de los otros y puede que cueste acostumbrarse...

---

