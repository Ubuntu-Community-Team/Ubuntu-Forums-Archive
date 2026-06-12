---
title: "problemas con placa nvidia fx 5200"
date: 2007-03-14
forum: Argentina Team
---

### Post by juan-korth on 2007-03-14
hola me llamo juan y hace 2 años que huso ubuntu pero cuando cambie de placa de video antes una geforce 2 ahora una fx 5200 me dego de andar no la aceleracion grafica si no el glx probe con los drivers nuevos probe con envy el escript de instalacion automatica de nvidia me comunique con envidia y me digieron que el problema no esta en los drivers si no en el compositor x en este caso gdm quiero solucionar el problema de cuando pongo en la consola glxgears en ves de aparecer los engranages aparece una ventana en  negro y despues se cierra y en el termina aparece core dumped me gustaria solucionarlo para instalar el beryl y juegos

---

### Post by zspikes on 2007-03-14
q raro che, yo tb tengo la 5200 y le instale los drivers con el envy y no me dio ningun problema. Seguro q hiciste todo bien?
Igual si hay algun problema mayor creo q te va a ayudar mejor alguien mas, yo soy medio novato en esto de ubuntu :S

suerte!

---

### Post by el_itur on 2007-03-15
busca el nvidia-installer.log seguramente debe estar en /var/log/ y mandalo a nvidia a travez de este foro
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

son muy buena gente y los desarrolladores responden todo el tiempo, si no sabés ingles, y... vas a tener que conseguir un amigo. :P

---

### Post by strugart on 2007-03-17
No aclaras si la placa es nueva o usada...
Tambien creo q es posible que algun trasistor (o mejor dicho varios) se hayan jodido, por eso no te anda la aceleracion 3d (bastante tipico en esas placas). Te recomendaria probar con otra placa y si te anda es la placa. Si no te anda es que has cometido algun error en el procedimiento de instalacin de drivers (proba con automatix2 o alguno de esos asi es mas facil). Espero haber podido ayudar. Strugart

---

### Post by TattooedFish on 2007-03-17
El Envy debería hacer funcionar todo sin problema. Puede ser que, como dice strugart, haya un problema de hardware.

Por las dudas, no sé si esto funciona así pero pregunto: ¿desinstalaste primero los drivers anteriores, para volver a instalarlos cuando cambiaste de placa? Dada la diferencia entre la GF2 y la FX5200, es posible que la configuración de los drivers sea distinta. Estoy haciendo suposiciones, no sé si esto sea así.

---

### Post by jpmorelli on 2007-03-18
> **juan-korth said:**
>  el problema no esta en los drivers si no en el compositor x en este caso gdm quiero solucionar el problema de cuando pongo en la consola glxgears en ves de aparecer los engranages aparece una ventana en  negro y despues se cierra y en el termina aparece core dumped me gustaria solucionarlo para instalar el beryl y juegos

Según esto el tema no es ni nvidia, ni beryl ni nada...si glxgears es el salvapantallas de KDE a mi me pasaba exactamente eso cuando tenía beryl activado, ya que no anda  o andaba, nunca más lo probé con algunas versiones del driver de nvidia para Linux, es cuestión de esperar... si no es el salvapantallas de lo que están hablando tienen derecho a reirse solo por un rato y luego hagan caso omiso a este post.

---

