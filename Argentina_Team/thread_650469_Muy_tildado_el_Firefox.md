---
title: "Muy tildado el Firefox"
date: 2007-12-26
forum: Argentina Team
---

### Post by mapuche001 on 2007-12-26
Gente, perdon por mi ignorancia, pero soy novato en esto.
La cuestion es que no podia cargar la pagina de clarin, ni ver los videos de TN, actualice los plugin del firefox y ahora esta totalmente lento, se me tilda todo. lo tengo q cerrar si o si.  Que hago¿?
AH...
otra cosa...
como hago para ver los subtitulos de las peli? las tengo en formato AVI y los sub en srt
Espero q me ayuden pq el firefox me esta sacando!!!

---

### Post by margori on 2007-12-26
Hola Mapuche:

Te pido nos des un poco mas de informacion de los programas que estas usando:
- Version  de Ubuntu tenes
- Versiones de Firefox
- Lista de Add-Ons y plugin
- Los pasos un poco mas detallados que hicieron que firefox se volviera lento.

Por otro lado, te aconsejo que crees un nuevo hilo para temas diferentes: un hilo firefox, un hilo codecs. 

En esto ultimo, lo subtitulso dependen del programa que uses para reproducir la pelicula. Te aconsejo usar VLC. Para que funcione corretamente acordate de instalar el paquete vlc-plugin-esd, y cambiar la codificacion de textos de subtitulos de default a ISO-8859-1, sino no se veran las frases con letras acentuadas.

---

### Post by mapuche001 on 2007-12-26
Gracoas Margori,
la version q tengo es la 7.10 y la de firefox es 2.0.0.11 y la lista de Add-Ons y plugin no se de donde saberlo
Y de crear otro hilo para un tema diferente....me mataste! con suerte q pude escribir un post!


Off topic: Q paso con la LOCOmotora??

---

### Post by Oktubre on 2007-12-26
Hola, 

para ver los subtitulos tenes que llamarlos de la misma manera (exactamente igual) que el archivo AVI pero con extension SRT. El soft (por ej el Totem) te los va a tomar solo.

En cuato al Firefox, puede ser que solo necesites instalarle el plug-in de Flash o quizas algo adicional. Primero proba instalandote el Flash.

Saludos,

---

### Post by margori on 2007-12-26
> **mapuche001 said:**
> ... y la lista de Add-Ons y plugin no se de donde saberlo

Los add-ons los podes ver en Firefox -> Herramientas -> Agregados

Tenes las extensions (add-ons en si), temas e idiomas.

Para ver los plug-in, en la barra de direcciones pone about:plugins

 Si eres nuevo en ubuntu seguro que lo tenes al firefox base (sin tuning ;) ) asi que la lentitud se puede deber a otra cosa.

Te aconsejo darle una ojeada al monitor de sistema. En el se ven todos los procesos, uso de cpu y demás yerbas.

Para ver mas finamente que es lo que pasa por tu compu, podes abrir un terminal y escribir: ps -A  
La A es mayusculas, linux discrimina mayusculas y minusculas.

te dara una lista mas completa de los procesos de la compu.

Fijate y contanos.

---

### Post by mapuche001 on 2007-12-26
Tal cual decis. no tengo nada instalado en las extensiones.
Capaz q me exprese mal. La maquina funciona perfecto salvo cuando abro el firefox y en especial la pagina de clarin. cuando carga una propanda de hitachi creo q es...se empieza a tildar. salvo por eso la maquina funciona de diez. 
otra pregunta, y esta me da mucha verguenza... como abro un terminal?

---

### Post by margori on 2007-12-26
> **mapuche001 said:**
> ... no podia cargar la pagina de clarin, ni ver los videos de TN, actualice los plugin del firefox y ahora esta totalmente lento...

Explicame bien que es lo que actualizaste, ya que si no tenes plugins instalados no tendrias que haber actulizado nada.

Puede ser que no tengas o este mal instalado el Java Runtime. Se utiliza para ejecutar los objetos incrustado en la pagina que te permiten ver los videos.

Como hacerlo, te vas al menu Sistema -> Administración -> Gestor de Paquetes Synaptic

Buscas el paquete sun-java6-jre y sun-java6-plugin. Los instalas si no estan instalados o reinstalas si ya lo están.

Donde esta el terminal?: Programas -> Accesorios -> Terminal.

Con un terminal le das comandos a linux. En algunas ocasiones es mucho comodo que utilizar el raton. No te asustes que se aprende a manejar con un poco de tiempo y paciencia. Por ejemplo ls te dice el contenido de un directorio, man ls te da un manual de ls (con Q se sale)

---

### Post by margori on 2007-12-26
Mapuche, te aconsejo darle una ojeada a esta pagina [Guia ubuntu]("http://www.guia-ubuntu.org/index.php?title=Portada")

Obtendra muchas respuestas.

Por otro lado, no tengas miedo o verguenza de preguntar. Primero, ninguno de los chicos y chicas que están aca nacio con todo el conocimiento. Segundo, no mordemos ;) Terceo, creo que esta escrito en [Reglas para el foro]("http://ubuntuforums.org/showthread.php?t=361022") que no se puede hacer.

---

### Post by mapuche001 on 2007-12-26
margori, muchisimas gracias, prometo  leer la guia. 
Ahora por lo menos no se me tilda tanto como antes, desistale unos plugin  gnash  y ahora esta un poquito mejor...pero no es la gran cosa..
Y esta si que es la ultima pregunta q hago, (por lo menos hasta mañana, jeje) podes ver TN en vivo? pq me dice q lo reporduce el Windows Media Player?

---

### Post by margori on 2007-12-27
> podes ver TN en vivo? pq me dice q lo reporduce el Windows Media Player?

Lamentablemente no tengo suficiente ancho de banda para ver video online, pero me voy a [www.tn.com.ar](www.tn.com.ar) y alcanzo a ver algo de la señal en vivo.

En la pagina [https://addons.mozilla.org/es-ES/firefox/browse/type:7](https://addons.mozilla.org/es-ES/firefox/browse/type:7) dice que no existe un plugin por parte de microsoft para firefox en linux (obvio ja) pero si existe un plugin de los chicos de GNome. En synaptic buscate el paquete totem-mozilla e instalalo. Verifica en about:plugins en firefox que estan asociados el tipo MIME application/x-mplayer2 al plugin nuevo.

Se que te puede sonar a chino basico, pero bueno, pregunta lo que no entiendas.

---

### Post by Hei Ku on 2007-12-27
El problema que tenes me parece que es con el plugin de flash (gnash) algunos reportaron que tenian problemas con ese. Fijate en este mismo foro que hubo varias preguntas al respecto.

---

### Post by mapuche001 on 2007-12-28
margori, gracias por la rpta, ya puedo ver tn en vivo. Y creo q el problema pasa por la instalacion de un plugin, gnash creo q era. ya lo desistale, instale otro, ahora carga la pagina, pero no esta funcionando del todo agil
me tira estos errores el firefox:
Error: uncaught exception: [Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIDOMScreen.width]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: [http://www.masoportunidades.clarin.com/cg/js/certifica2.js](http://www.masoportunidades.clarin.com/cg/js/certifica2.js) :: hitCertifica :: line 6"  data: no]
Error: $ is not defined
Archivo Fuente: [http://ubuntuforums.org/showthread.php?p=4029318#post4029318](http://ubuntuforums.org/showthread.php?p=4029318#post4029318)
Línea: 1813

y estas advertencias:

Advertencia: Error in parsing value for property 'display'.  Declaration dropped.
Archivo Fuente: [http://www.clarin.com/shared/v9/css/global.css](http://www.clarin.com/shared/v9/css/global.css)
Línea: 14
Advertencia: Error in parsing value for property 'background'.  Declaration dropped.
Archivo Fuente: [http://www.clarin.com/shared/v9/css/home.css](http://www.clarin.com/shared/v9/css/home.css)
Línea: 14
Advertencia: Error in parsing value for property 'line-height'.  Declaration dropped.
Archivo Fuente: [http://www.clarin.com/shared/v9/css/home.css](http://www.clarin.com/shared/v9/css/home.css)
Línea: 105
Advertencia: Error in parsing value for property 'line-height'.  Declaration dropped.
Archivo Fuente: [http://www.clarin.com/shared/v9/css/home.css](http://www.clarin.com/shared/v9/css/home.css)
Línea: 110
Advertencia: Error in parsing value for property 'font'.  Declaration dropped.
Archivo Fuente: [http://www.clarin.com/shared/v9/css/home.css](http://www.clarin.com/shared/v9/css/home.css)
Línea: 319
Advertencia: Se esperaba color pero se encontró ';'.  Error in parsing value for property 'background-color'.  Declaration dropped.
Archivo Fuente: [http://partnerfeed.itsfogo.com/partnerfeed.aspx?PartnerFeedID=1296&RefererID=IKZ5VIVPMQ6YV84LO36&Width=468&ZoneID=34758&target=bwin&adid=6847&language=4&codepage=&gmt=-4&partnerTargetLink=&partnerField=itsfogoTargetLink](http://partnerfeed.itsfogo.com/partnerfeed.aspx?PartnerFeedID=1296&RefererID=IKZ5VIVPMQ6YV84LO36&Width=468&ZoneID=34758&target=bwin&adid=6847&language=4&codepage=&gmt=-4&partnerTargetLink=&partnerField=itsfogoTargetLink)
Línea: 0
Advertencia: Se esperaba fin de valor para la propiedad pero se encontró 'font-weight'.  Error in parsing value for property 'background'.  Declaration dropped.
Archivo Fuente: [http://ubuntuforums.org/clientscript/vbulletin_css/style-4a44d1c2-00074.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-4a44d1c2-00074.css)
Línea: 1961
Advertencia: Error in parsing value for property 'display'.  Declaration dropped.
Archivo Fuente: [http://ubuntuforums.org/showthread.php?p=4029318#post4029318](http://ubuntuforums.org/showthread.php?p=4029318#post4029318)
Línea: 0

---

### Post by faktorqm on 2007-12-30
ese tipo de cosas es por que no respetan los estandares. quiza me ekivoque, ojo, pero todos los errores de parseo por lo general se deben a que el ke hizo la pagina no respeto los estandares del lenguaje. salu2!

---

