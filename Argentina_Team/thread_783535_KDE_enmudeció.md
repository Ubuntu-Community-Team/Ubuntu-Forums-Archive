---
title: "KDE enmudeció"
date: 2008-05-05
forum: Argentina Team
---

### Post by Liber18 on 2008-05-05
Hola gente !  este post lo puse en ubuntu.es pero como no obtuve respuesto me atrevo a molestar a la comunidad de ubunteros de mi pais (pienso que debe ser algo simple pero, la verdad, "no doy pie con bola")

Hola, necesito ayuda

No se por que razon, desde hace unos 10 dias me he quedado totalmente sin sonido en KDE (por alguna actualización "automática"?). Hasta hace un par de semanas todo funcionaba y no he actualizado mi 7.10, ni el kde 3.5 .

No solo no tengo ningún sonido de sistema, sino que muchas aplicaciones lanzadas desde los íconos del escritorio o el menú, se quedan "mudas" y otras no.

Por ejemplo el firefox, lanzado desde los íconos no reproduce sonido (reproduce los videos mudos), no obstante si lo lanzo desde la konsole (escribiendo el comando "firefox") tiene sonido. Lo mismo ocurre con algún juego como el tmw (por comando tiene música y sonido, desde el menú juegos no) y con kttsmgr que es mudo, en tanto desde la consola festival suena bien [(A propósito de festival: no logro acoplar los módulos OGI - hice un post aquí pero aun no obtuve respuesta-)]. Noatun directamente no tiene sonido cualquiera sea la manera de arrancarlo (será porque llamandolo desde la consola se instala en la sub-barra de inicio rápido y hay que abrirlo desde alli ?)
Otras aplicaciones, en tanto, como xmms, tienen sonido sin importar desde donde los inicio.

El demonio artsd está siempre presente, le asigné el bit SUID a artswrapper para lograr prioridad en tiempo real (un consejo que apareció en una busqueda en google) pero nada lo resuelve : mi KDE se ha vuelto mudo y "enmudece" la mayoria de las aplicaciones que lanza.

Realmente no logro entender que puede estar sucediendo, asi que espero ayuda .

Los 3 últimos posts mios en este foro no han obtenido ninguna respuesta, asi que esta vez espero un poco mas de suerte.

Muchas gracias por adelantado

---

### Post by atatiducken on 2008-05-06
te entiendo, es frustrante no conseguir las respuestas, pero todos los que estamos aca estamos con la intencion de ayudar a los demas y hacer q esta comunidad crezca y mejore, posteo para q tu post no se pierda asi conseguis respuesta de los q mas saben.

la verdad ni idea q puede pasar en tu kde :), de ultima cuando no sepas mas a q pegarle o tocar, pegate un install nuevo, jeje yo instale 3 veces ya hardy, toque demasiado, asi se aprende jeje
un abrazo

---

### Post by Hei Ku on 2008-05-06
un dato importante seria que placa tenes, y que arranques alguno de los programas sin sonido desde la consola para ver si tiran algun mensaje.

---

### Post by leo_rockway on 2008-05-07
> **Liber18 said:**
> 
Los 3 últimos posts mios en este foro no han obtenido ninguna respuesta, asi que esta vez espero un poco mas de suerte.


"Posts: 1"

Confused... :confused:

EDIT: ah, es un copy paste del de ubuntu-es... that changes __EVERYTHING__!

EDIT2: kcontrol > sonido y multimedia > sistema de sonido
Contanos que está activado y que no y que valores numéricos tenés (tanto en el tab "General" como en el de "Hardware") y también decinos si "Probar sonido" funciona desde ahí.

---

### Post by niko_3100 on 2008-05-07
Hace una cosa si tenes una version de winwos proba si ahi te levanta el sonido bien. Si ahi levanta el sonido bien hace lo siguiente apaga la computadora enteraa, desenchufala de la corriente espera un minuto mas o menos y volvela a enchufar. A mi me pasaba con feisty que si estaba en win xp y despues reiniciaba y levantaba feisty no me reproducia los sonidos, ninguno de ninguno, encontre la solucion desenchufandola esperando un toque y volviendo a enchufar todo y ahi levantaba el sonido, OJO yo tengo una notebook no pc de escritorio.

---

### Post by Liber18 on 2008-05-10
Hola a todos
Disculpen mi "cuelgue" pero estuve unos dias sin acceso a internet.
Gracias atatiduken por mantener vivo el post,
Gracias Hei Ku , tengo una vieja SBLive con todos sus puertos perfectamente reconocidos por el OS: lanzando las aplicaciones desde la consola suenan bien y no tiran ningun mensaje de error. Artsd está siempre corriendo...pero KDE no tiene sonido y contagia su mudez a las aplicaciones que arranco cliqueando en sus íconos.
Gracias leo y nico: en el Kcontrol -> sonido y mul...  ->sistema (y notificaciones)  ya he cambiado todo decenas de veces (todo parece bien, normal, pero nunca el boton prueba emite ningun sonido).Eso lo expliqué en el primer post.
Parece posible que hubiese otro demonio de sonido interfiriendo con kde, pero no logro figurarme cual (esd no está instalado en mi sistema).
Pero entiendan : la misma aplicación que no suena llamándola desde el menú de kde, si la cierro y la vuelvo a lanzar desde la consola (aunque sea la konsole de kde) suena "joya"   :()
Respeco a la sugerencia de nico, sí, tengo un win$ 98 en algún rinconcito del duro, pero no suelo visitarlo demasiado seguido. La placa de sonido funciona bien tanto allí como en Linux . Solo el sonido en kde es el problema..
Parece que a ninguno se nos "cae una idea" .... pero no es algo tn grave como para reinstalar todo. Yo supongo que alguna actualización (de esas medio automáticas) de algo fue la causante de esto.

Gracias a todos igual, pero no me resigno a que nosotros, linuxeros, pensemos en reinstalar , a la winchot, ante los problemas : Para que queremos software libre y código fuente si no es para estudiarlo, no?

---

### Post by Hei Ku on 2008-05-10
me referia a konsole, la terminal de kde. Arrancar el Amarok, por ejemplo desde ahi, y ver que pasa? Tambien funciona sin problemas?
Por lo que lei, me parecio por casualidad que KDE no es tu sistema principal? Instalaste Ubuntu primero y sobre eso Kubuntu?

---

### Post by WanderingKnight on 2008-05-10
No se me ocurre mucho, pero probá matando el daemon artsd y volviéndolo a correr. También podes probar crearte una cuenta de root y ver que pasa ahí.

---

### Post by mauriciog on 2008-05-10
Me ocurrió exactamente lo mismo con Ubuntu 8.04 hace un par de días luego de hacer una actualización del sistema y lo resolví reinstalado el paquete Ubuntu Restricted Extras.
Espero que te sirva de ayuda.
Saludos!

PD: en tu caso deberías reinstalar Kubuntu Restricted Extras.

---

### Post by WanderingKnight on 2008-05-10
ubuntu-restricted-extras es el mismo paquete para todas las versiones. No hay ninguna biblioteca que tenga que ver con GTK o Qt ahi.

---

### Post by Liber18 on 2008-05-12
Hola de vuelta (todo sigue igual)
Trato de responder individualmente, dado que las sugerencias difieren:

Hei Ku
- No tengo instalado el amarok , y no veo ninguna necesidad de hacerlo (ya tengo suficiente con xmms,  noatun, juk, etc y no escucho demasiada música en la pc) .No obstante, te aclaro (tal como puse en el primer post) que festival "habla" correctamente arrancado desde la konsole, en tanto kttsmgr (una especie de interfaz gráfica de kde para festival) ,cambie lo que cambie en la configuración, no suena. Tambien pasa lo mismo con tmw (the mana world) que suena perfectamente arrancándolo desde la konsole (o cualquier otra consola, obvio) y en cambio corre mudo cliqueando desde menú->juegos ..(etc) 
--Tienes razón, en principio instalé Xubuntu (buscando lo mas "livianito" dado la antigüedad del hard) pero no me gustó  (ni me resultó funcional) asi que instalé KDE3.5 (no instalé todo el paquete Kubuntu Desktop) y Blackbox por si me faltaba memoria, pero no necesité usarlo.
--En general te (les) aclaro que esta "mudez" de kde comenzó hace apenas un mes : Durante meses no tuve ningún problema

WanderingKnight
El demonio artsd ya lo debo haber matado y arrancado de mil maneras distintas unas, digamos, mil veces...
Con respecto a los permisos, he probado, con todos los riesgos del caso, "SUIDeando" (chmod +s) casi todo por allí (ya lo puse en el primer post)

mauriciog
Restricted extras lo tengo instalado y actualizado (te aclaro que no quiero instalar por ahora el 8.4 así que debo cuidarme mucho con las versiones). No obstante, probé reinstalarlo sin resultado alguno (si verificas en synaptic -> archivos instalados, verás que aparentemente no instala demasiado....

NOTA: Una idea media disparatada : alguien sabe de algún conflicto entre arts y sox, pues creo que tuve que instalarlo hace poco (en tal caso preferiria el kde mudo )

---

### Post by Hei Ku on 2008-05-12
me parece que lo que tenes es una instalacion a medias. En una de las ultimas actualizaciones de kde cambiaron como maneja el daemon de sonido y no lo debe estar tomando bien.
Te recomendaria instalar el kubuntu-desktop, e incluso fijarte porque esta el kde 3.5.9. Vos supongo que debes tener el 3.5.8
Tambien fijate en el kdm.log porque algo debe aparecer ahi.

---

