---
title: "Ubuntu con RAID"
date: 2007-09-09
forum: Argentina Team
---

### Post by angelqpro on 2007-09-09
Amigos: Soy nuevo aquí, al igual que con Ubuntu, y Linux en general.
Hace ya años que estoy trabajando con computadoras, pero en el entorno Windows. y cada día lo odio más (aunque me da laburo).
Entonces, por esta vez pasaré al otro lado del mostrador, y en vez de ayudar a otros, pido ayuda.
El hecho es que trabajo en una importante Consultora de Ingeniería, con 25 computadoras, 9 impresoras, 1 plotter y un server.
Y tengo muchas ganas de instalar Ubuntu.
Al Presi le encantó
Pero tropiezo con esto:
Hay tres impresoras laser Kyocera, y no encuentro los drivers.
Al instalar el Ubuntu en una maquina con RAID, no me lo detecta, sino que me aparecen los discos en forma individual. Y esto es crucial, porque los últimos equipos que estoy construyendo son RAID. 
Y el Server (con Win Server 2003) tiene un RAID 0 +1.
Necesito un CAD equivalente en prestaciones al AutoCAD 2005 de Autodesk
Me cuesta mucho el modo texto de consola. (ya me olvide de la época del assembler de las Sinclair y del DOS).

El problema que tengo en forma inmediata es el del RAID 0 en una PC que estoy construyendo.

Y luego, encontrar una solución general al tema drivers.

l
Les agradezco desde ya. Y espero que pronto vuelva a hacer lo que acostumbro a hacer en el otro entorno.
A su disposición en el tema Hardware.

---

### Post by qsr.nrwn on 2007-09-09
Procura poner tu pregunta en inglés de otra manera no obtendrás respuesta alguna.

Hay una guia para configurar RAID en

[https://help.ubuntu.com/community/Installation/FileServerWithRAID?highlight=%28RAID%29](https://help.ubuntu.com/community/Installation/FileServerWithRAID?highlight=%28RAID%29)

Suerte

---

### Post by Hei Ku on 2007-09-09
Creo que podrias empezar por configurar los servers en Linux, si logras hacer andar los RAID, que no creo que tengas problemas. Pero si en los desktops usas AutoCAD, te veo complicado. Hay programas similares, pero por lo que tengo entendido, todavia estan por detras en cuanto a prestaciones, sobre todo de las ultimas versiones.
Asi que yo empezaria con Samba, reemplazando los servidores, y seguiria despacito desde ahi. No trates de reemplazar todo junto o vas a pasar un trago amargo que va a hacer que la gente no quiera volver a escuchar sobre Linux en tu empresa.

---

### Post by rretamar on 2007-09-09
Un consejo: primero instala Linux en tu casa. Probalo, estudialo, descoselo.
Y después, recién después de pasada esa etapa (que no es de días, sino de muchos meses, dándole y dándole), presentalo en el trabajo (y de forma gradual, teniendo en mente si implantar linux REALMENTE SE JUSTIFICA). Nunca, pero nunca (salvo que seas el dueño ;)) uses equipos/personal del trabajo como cobayos. Se te puede volver todo en contra.

Todo a su tiempo.

Saludetes !

---

### Post by angelqpro on 2007-09-09
> **rretamar said:**
> Un consejo: primero instala Linux en tu casa. Probalo, estudialo, descoselo.
Y después, recién después de pasada esa etapa (que no es de días, sino de muchos meses, dándole y dándole), presentalo en el trabajo (y de forma gradual, teniendo en mente si implantar linux REALMENTE SE JUSTIFICA). Nunca, pero nunca (salvo que seas el dueño ;)) uses equipos/personal del trabajo como cobayos. Se te puede volver todo en contra.

Todo a su tiempo.

Saludetes !

Estoy de acuerdo. Lo instalé en un equipo que acabo de construir alli, y nada más. Y estoy en vías de hacerlo en la mía de casa, pero primero tengo que mejorarla.
Gracias

---

### Post by angelqpro on 2007-09-09
> **qsr.nrwn said:**
> Procura poner tu pregunta en inglés de otra manera no obtendrás respuesta alguna.

Hay una guia para configurar RAID en

[https://help.ubuntu.com/community/Installation/FileServerWithRAID?highlight=%28RAID%29](https://help.ubuntu.com/community/Installation/FileServerWithRAID?highlight=%28RAID%29)

Suerte

Gracias, amigo. El tuto está bueno, lo cargué en un pen drive para imprimirlo en la oficina.
En cuanto al idioma, ¿no es este el foro de Argentina?

---

### Post by angelqpro on 2007-09-09
> **Hei Ku said:**
> Creo que podrias empezar por configurar los servers en Linux, si logras hacer andar los RAID, que no creo que tengas problemas. Pero si en los desktops usas AutoCAD, te veo complicado. Hay programas similares, pero por lo que tengo entendido, todavia estan por detras en cuanto a prestaciones, sobre todo de las ultimas versiones.
Asi que yo empezaria con Samba, reemplazando los servidores, y seguiria despacito desde ahi. No trates de reemplazar todo junto o vas a pasar un trago amargo que va a hacer que la gente no quiera volver a escuchar sobre Linux en tu empresa.

Por ahora lo que haré será instalarlo en doble booteo en alguna máquina, y en el server. El equipo que construí, e instalé Windows y Ubuntu, es para el presidente de la empresa.
Pero es difícil el cambio de hábitos en la gente. Tienes razón en tu concepto.
Inclusive tengo un DVD de Solaris que me enviaron, que aun no he probado
Gracias

---

### Post by Hei Ku on 2007-09-09
Yo apuntaria hacia el fuerte de Linux, el area de servidores. Usando Samba, Apache, etc. para reemplazar los web servers, file y print servers, etc. Y una vez que tengas eso dominado, tipo en 1 año, seguir con el resto. Por empezar, te tenes que dar tiempo a vos mismo para acostumbrarte al linux, y eso es imposible con un usuario zapateandote en la cabeza porque no puede abrir un .doc.

---

### Post by faktorqm on 2007-09-11
Yo particularmente, aconsejo OpenBSD para servidores. El otro dia en una nota que me comentaron por ahi decia que Linus Torvalds, si hubiese sabido de la existencia del desarrollo de OpenBSD, ni se hubiera molestado en crear el núcleo de linux. zarapado no?
volvamos a lo nuestro. si de todas maneras decidis instalar ubuntu server, tampoco te recomiendo samba. si usas win server 2003 te convendria instalar openldap, para mantener la seguridad en toda la red. 
con respecto a las kyocera no se que decirte, busca bien en google y cia.
con respecto a lo del RAID, busca un post en este mismo foro que un chabon pregunto lo mismo y le tire un par de cables.
el chabon ese que te dijo del idioma, que le paso? se confundio la kbza..... ajjaja salu2!!

---

### Post by qsr.nrwn on 2007-09-19
> **faktorqm said:**
> 
el chabon ese que te dijo del idioma, que le paso? se confundio la kbza..... ajjaja salu2!!

no había visto la barra de localización "Ubuntu Forums > The Ubuntu Forum Community > Other Community Discussions > Ubuntu LoCo Team Forums > International LoCo Teams > Argentina Team > Ubuntu con RAID", perdón por la confusión

---

### Post by LaHire on 2007-09-19
> **Hei Ku said:**
> Yo apuntaria hacia el fuerte de Linux, el area de servidores. Usando Samba, Apache, etc. para reemplazar los web servers, file y print servers, etc. Y una vez que tengas eso dominado, tipo en 1 año, seguir con el resto. Por empezar, te tenes que dar tiempo a vos mismo para acostumbrarte al linux, y eso es imposible con un usuario zapateandote en la cabeza porque no puede abrir un .doc.


Coincido, 
hay que evitar hacer éxodos...la gran mayoría siempre terminaron mal....

Por eso, pasito a paso :), viendo y consultado con tus co-workers...

Y si, importante

date un tiempito para conocerlo, así cuando te enfrentes a las cosas "de todos los días", estés más preparado :)

éxitos! 

Y por cierto, lo que dice el pincha del foro (o faktorqm), si bien es una muy buena idea (porq freeBSD es bestial para servidores...en el buen sentido, claro), es...mejor que empieces con algo "más sencillo" y potente como es...Ubuntu, para después ver que camino tomar (aunq seguro q con Ubuntu Server te conformás, plus de que el diablito es malo!, el Pingüino es mejor (no interpretar politicamente) ) 
Saludos!

---

### Post by faktorqm on 2007-09-19
> **LaHire said:**
> 
Y por cierto, lo que dice el pincha del foro (o faktorqm), si bien es una muy buena idea (porq freeBSD es bestial para servidores...en el buen sentido, claro), es...mejor que empieces con algo "más sencillo" y potente como es...Ubuntu, para después ver que camino tomar (aunq seguro q con Ubuntu Server te conformás, plus de que el diablito es malo!, el Pingüino es mejor (no interpretar politicamente) ) 
Saludos!

Si, tenes razón, el freeBSD, es mas dificil de usar y menos amigable que el mas feo de los linux. recordemos que siguiendo la linea de desarrollo de los sistemas operativos, bsd deriva del unix de la universidad de berkeley (por favor corrijanme si me fallo la memoria) modificado del unix original.
vos fijate, capaz como dicen aca te conviene empezar despacio, trankilo, y capaz dentro de 2 años ya tenes super cancha en todo, y ahi te fijas que onda.
salu2!!!

---

### Post by pokapeski on 2008-03-11
yo tengo mis servidores en openbsd y no tengo ni una queja sobre ellos. bajo mi punto de vista son de lo mejor.

respecto a la pregunta, anoche llegue a este hilo buscando una solucion para instalar algo debianita con RAID (desesperado llegue a considerar meter RedHat, no me lo tengan en cuenta, por favor :P) y vi la documentacion que hay mas arriba en esta piola. Me resulto algo difusa. Finalmente opte por escoger "instalacion en modo texto" y ahi lo haces de una sin problemas.

---

### Post by faktorqm on 2008-03-12
groso pokapeski, aprovecho para preguntarte (sin haber pasado primero por google):

1) las reglas para iptables cambian mucho para pf?
2) usas samba para compartir archivos? no "rompe" la seguridad del sistema? existe algun port para openbsd que este probado que es seguro?

graciela y disculpa las molestias!

---

