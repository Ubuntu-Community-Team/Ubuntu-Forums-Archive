---
title: "Instalacion Ubuntu -CALL FOR HELP!!!!!"
date: 2008-05-07
forum: Argentina Team
---

### Post by dgcampos on 2008-05-07
Buenas :


a todos los amantes de linux, este es un llamado de ayuda. Como veran, esta es la situacion :

1.- He conseguido que en la empresa donde trabajo donaran unas maquinas viejas para una escuela.

2.- Esas maquinas son unas IBM con pentium III, 128MB RAM y c/u con un disco de 10GB.

3.- Lamentablemente, todavia tienen win98, y a pesar mis mejores esfuerzos, no he podido instalar el ubuntu 8.04 en esta maquina.

4.- He intentado hacerlas arrancar desde el CD-ROM, pero ninguna distribucion ha podido arrancar (ni el ubuntu, ni el Debian, ni otra distro de seg. que ahora no recuerdo el nombre). No se porque, pero directamente no arrancan. La secuencia de booteo sigue, y luego termina cargando el win98.

5.- Sin embargo, al intentar leer el CD-ROM desde el win98 una vez arrancado, puedo ver los archivos, e incluso el debian levanto una pagina web cuando lo puse.

6.- Tratando de hacer un diskette de arranque (no pude conseguir diskettes en la oficina, yo ya no tengo ninguno pero un amigo me consiguio uno que tenia guardado por ahi) usando el NWWrite o como diablos se llame y no pudo hacerme un diskette de arranque, bien porque no pude copiar el sbm.bin (el  maldito DOS decia que el diskette no tenia espacio) o bien por el cuando lo lograba, el maldito win98 me decia que no tenia formato, y cuando lo ponia en arranque, no hacia nada :(.

En fin, ademas de los problemas con el BIOS de estas maquinas para que arrancaran desde el CD-ROM, no puedo sentirme mas frustado que nunca, pero no me doy por vencido y tengo la esperanza que puedo instalar alguna distro mas chica que ubuntu (estoy bajandome un vector linux para probar) y darle a los chicos de esta escuela, lo que realmente deberian aprender.

No se si es posible hacer otra cosa, pero la verdad es que necesito la ayuda de ustedes para instalar linux en estas maquinas. Los chicos no esperan menos de mi y mi esfuerzo espero valga la pena.

Para que mas o menos se ubiquen quien escribe, trabajo en sistemas hace mucho, estoy usando Debian en este momento desde mi laptop, y uso Ubuntu en mi desktop tambien(tambien tengo el windows).

Humildemente, no lo se todo, aunque conozco mucho de lo mio, no puedo apretar en todas partes, y la instalacion no es mi fuerte precisamente.

Si quieren darme una mano, les estare profundamente agradecido, vivo en Pcia Bs As y trabajo en capital. Manden PMs para contactarme.

Muchas gracias a todos,

**dgc**

---

### Post by pol666 on 2008-05-07
L verdad no te puedo ayudar solo te recomiento que para esas pc lo ideal es XUBUNTU

---

### Post by guillermolisi on 2008-05-07
Requerimientos minimos de memoria RAM para instalar 8.04 desde un LiveCD: aconsejan no menos de 256 Mb.

Para menos que eso, usa la distribucion que viene en el CD alternate para 32 bits desktop.

Si logras instalar, me parece que 128Mb para un Gnome o KDE con algun juego didactico y/o aplicaciones de oficina, va a ser muy poco.

Si las maquinas van a un colegio, mi consejo seria que instales el metapaquete de Edubuntu (tambien desde el CD Alternate). Es un Gnome personalizado graficamente y contiene aplicaciones didacticas y de apoyo a la enseñanza, inclusive hasta podrian planificar examenes en red (usando LTS).

Hay otras distribuciones GNU/Linux que podrian funcionar algo mejor por ser mas compactas y menos demandantes en recursos, pero en general algo incomodas a la hora de actualizar (sobre todo si te acostumbraste al sistema de repositorios de Debian/Ubuntu).

---

### Post by dgcampos on 2008-05-07
> **guillermolisi said:**
> Requerimientos minimos de memoria RAM para instalar 8.04 desde un LiveCD: aconsejan no menos de 256 Mb.

Para menos que eso, usa la distribucion que viene en el CD alternate para 32 bits desktop.

Si logras instalar, me parece que 128Mb para un Gnome o KDE con algun juego didactico y/o aplicaciones de oficina, va a ser muy poco.

Si las maquinas van a un colegio, mi consejo seria que instales el metapaquete de Edubuntu (tambien desde el CD Alternate). Es un Gnome personalizado graficamente y contiene aplicaciones didacticas y de apoyo a la enseñanza, inclusive hasta podrian planificar examenes en red (usando LTS).

Hay otras distribuciones GNU/Linux que podrian funcionar algo mejor por ser mas compactas y menos demandantes en recursos, pero en general algo incomodas a la hora de actualizar (sobre todo si te acostumbraste al sistema de repositorios de Debian/Ubuntu).

Tambien tengo el edubuntu, gracias por la ayuda!!! que es eso de CD alternate???? en realidad si prefiero el sistema de repositorios Debian/Ubuntu como lo planteas, entiendo que es mas facil de entender para los que recien empiezan, como los chicos.

tenes un link sobre el CD alternate? te juro no sabia nada de eso.

Gracias de nuevo!!!!

saludos,

dgc

---

### Post by guillermolisi on 2008-05-07
Fijate en este link, en Ingles, que tenes mas info ademas de la respectiva sobre el alternate CD:

[http://www.edubuntu.org/Download](http://www.edubuntu.org/Download)

Los CD alternate te permiten instalar sin interface grafica, en modo texto tal como haces con Debian.

Sobre una instalacion basica agregas los paquetes que quieras via apt-get, aptitude, etc., pero siempre en modo caracter hasta que instales un escritorio grafico (ya teniendo en marcha el SO).

---

### Post by atatiducken on 2008-05-08
al igual q pol666 yo creo q xubuntu correria mejor, o simplemente correria, tendrias que instalarlo desde el alternate CD, aca tenes una guia de como instalar desde el alternate CD, es para ubuntu pero te va a servir **[LINK]("http://tuxpepino.wordpress.com/2008/04/29/instalar-ubuntu-alternate-cd/")**


No se si puedo decir esto :D pero mejor seria q le pusieras **fluxbuntu**, es una distribucion no oficial pero con los repositorios oficiales (es ubuntu pero con fluxbox), usa fluxbox como gestor de ventanas, es muy rapido y liviano, pero un poco complicado para configurar, pero viene todo configuradito asi q los cambios q deberias hacer son minimos, la pagina es **[http://fluxbuntu.org/intro.html]("http://fluxbuntu.org/intro.html")**


saludos

---

### Post by Ptero-4 on 2008-05-08
Para el arranque haz esto. Primero quema el CD a 4x o 2x. Hay unidades ópticas que no te trabajan bien los CDs quemados a mayores velocidades que esas. Además revisa si el BIOS tiene una opción para pausar o demorar el arranque. Algunas veces la unidad óptica demora mucho en leer y el BIOS termina de repasar el orden de arranque antes que la unidad óptica termine de leer, o si tiene una opción para abrir un menú de arranque, lo cual te sirve porque le daría tiempo a la unidad óptica de leer el CD y por último si nada de esto sirve tendrás que usar el rawrite desde windows para crear el disco de arranque (Windows no lo podrá leer porque usa un formato de archivo que windows no conoce, pero la idea es arrancar el PC con el disco de arranque) y después reinicias el PC (asegúrate que el orden de arranque en el BIOS tenga la unidad de discos flexibles antes del disco duro) con el disco en su unidad.

---

