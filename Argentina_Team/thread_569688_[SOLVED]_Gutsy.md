---
title: "[SOLVED] Gutsy"
date: 2007-10-07
forum: Argentina Team
---

### Post by Vero1 on 2007-10-07
Hola,

Tengo una pregunta.

Cuando salga Gutsy, se podrá actualizar Feisty o habrá que bajarlo en un nuevo CD e instalarlo.

En este último caso, hay que desinstalar Feisty?

Gracias y saludos

---

### Post by Mataca on 2007-10-07
De las dos formas vero, vos elegís cual te parece mas óptima.

Hay que tener en cuenta que si haces una fresh install (desde el cd o sea de 0) vas a tener que instalar nuevamente todos los paquetes de programas que usas ahora que no vengan incluídos en el 7.10.

Ahora si actualizas,  no hace falta hacer nada. Hay gente que recomienda una fresh install por que a veces no funcionan bien, la verdad... no se bien esto último. 

Yo personalmente hare una actualización y si veo q no funca, hago una fresh y listo.

---

### Post by Vero1 on 2007-10-07
Hola Mataca, gracias por contestar.

Recien estuve en el chat y me dijeron que no había problema para actualizar. Sólo hace falta actualizar los repositorios.

Me dijeron que ponga ésto, por si te interesa(o tal vez ya lo sabés)

apt-get update && apt-get upgrade && apt-get dist-upgrade

luego ver si hay actualizaciòn de repositorios.

saludos

---

### Post by Mauro22 on 2007-10-07
Al menos que la actualizacion te de error como a mi, y deje el Ubuntu inusable.


YO recomiendo fresh install

---

### Post by Hei Ku on 2007-10-07
yo vengo actualizando desde el edgy, sin problemas excepto una vez que me olvide de sacar unos repositorios externos.
[B]
Una cosa importante para recordar en el momento de actualizar es deshabilitar temporalmente todos los repositorios no oficiales[/B], para evitar problemas. Y despues de actualizar, fijarse cuáles de estos repositorios que están actualizados para la nueva versión y rehabilitarlos.

Mauro, me parece que tu problema vino más por el lado de que instalaste la beta. En ese caso, estás mucho más expuesto a problemas, y advertido de que puede ser así.

Lo que yo pienso hacer es actualizar un par de semanas después de que salga la instalación, como hice las veces anteriores. También, como precaución, está bueno fijarse en los foros por el hardware de tu pc y ver si la nueva versión tiene algún problema particular. 

Acuerdense que también cambia la versión de kernel, así que están más expuestos a un problema de incompatibilidad de hw que en una update de kernel menor dentro de una misma versión. Un ejemplo de eso son las lectoras SATA de DVD, que cambia mucho el soporte disponible de una versión de kernel a otra.

---

### Post by Vero1 on 2007-10-07
Hola Mauro y Hei Ku,

Mauro, se me cayó el techo cuando te leí. Espero que sea lo que dice Hei Ku con respecto a la versión Beta. No tengo muchas ganas de pasarme otra vez mas de 5 horas para bajar Gutsy.

Hei Ku,

Cómo se deshabilitan los repositorios?

Por mi parte no tengo DVD.

Con lo único que puedo tener problemas, es con Nvidia o tal vez no.

Esperás a propósito unas semanas para instalar la nueva versión o tenés algun motivo en especial?

gracias y saludos

---

### Post by Hei Ku on 2007-10-07
[EDIT]
Los repositorios los podés desactivar a través de Synaptics, creo. Yo edito directamente el sources.list

```

sudo gedit /etc/apt/sources.list

```

[/EDIT]

y ahí le pongo un numeral (#) adelante del nombre de los repositorios.

En cuanto a la espera, es a propósito para ver qué problemas van apareciendo en los foros con la actualización. En general vas a ver que en la primer semana o dos, aparecen un montón de threads describiendo los problemas más comunes en la actualización. Básicamente, las reviso y veo si tengo algo en común con los problemas encontrados. Generalmente las soluciones son simples, pero con esa revisión ya voy preparado.

Te cuento que la última actualización, a Edgy fue muy simple. Si mal no recuerdo, el único problema fue porque me había olvidado de comentar el repositorio del CD de la versión anterior. Una vez que me dí cuenta, lo comenté y ya está. En total el proceso fueron un par de horas, sin contar la bajada de los paquetes actualizados, que la dejé haciendo durante la noche.

Personalmente, creo que el proceso de actualización está bastante aceitado, donde podés encontrarte con problemas es si Gutsy no reconoce algúna cosa de tu PC, pero eso lo tendrías probablemente igual con una instalación nueva.

Y obvio, antes de hacer nada, BACKUP, BACKUP, BACKUP. A ver, repitan después de mi, BACKUP! No los escucho! BACKUP! Más fuerte! BACKUP! :D

---

### Post by msangil on 2007-10-07
Vero,

Acordate que para que salga la versión estable faltan (a HOY Domingo 7 de Octubre) 11 días todavía.

Esperá hasta que se haga el release para instalar / actualizar así te asegurás que la mayoría de los bugs están arreglados y que no vas a tener sorpresas.

EDIT: ... no me di cuenta que pusiste "Cuando salga". No tiene sentido lo que puse. Sorry. HAHAHAHA!

---

### Post by WanderingKnight on 2007-10-07
> 
sudo gedit /etc/apt/sources.txt

Es sources.list :p

---

### Post by Vero1 on 2007-10-08
Hola Hei Ku, Wondering Knight y msangil,

Gracias por vuestras respuestas.

Hei Ku, no tengo nada importante para hacer Backup, salvo en Evolution o sea los correos. Pueden perderse?

Wondering Knight tomo nota.

msangil, estuviste gracioso:)

Bueno, en conclusión, esperaré como me dijeron unas dos semanas antes de upgrade.

saludos

---

### Post by jpmorelli on 2007-10-08
Vero1, si tu "/home" está instalado en una partición diferente a la de tu sistema raíz ( o sea tu "/" ) los correos no se te van a borrar, siempre y cuando hagas una actualizacion o un format de solo la particion de sistema.

---

### Post by Oktubre on 2007-10-09
Hola,

[acá]("http://www.howtogeek.com/howto/linux/upgrade-ubuntu-from-feisty-to-gutsy/") te dejo un link donde explica como hacer el upgrade.

Saludos,

---

### Post by Vero1 on 2007-10-09
Hola jmorelli y oktubre,

Gracias a los dos por responder.

jmorelli,
El disco está particionado en / y swap. nada mas.
Quiere decir que perderé el correo?

oktubre,
gracias por el link.

saludos

p.d.
qué sucede con los bookmarks que tengo en Mozilla-Firefox?

---

### Post by Hei Ku on 2007-10-09
Si sale todo bien, al hacer el upgrade no perdés nada.

Mi recomendación del backup es por si algo sale terriblemente mal (puede fallar, según Tusam) y tenés que reinstalar. En ese caso, siempre mejor tener un backup, para hacer todo más tranquilo. Igual podes reinstalar sobre el mismo disco sin reinstalar, con las opciones de reparación, pero es más complicado.

Más allá de estas, te repito que mi experiencia fue buena, pero siempre es mejor estar preparado. ;)

---

### Post by Mataca on 2007-10-10
[QUOTE=Hei Ku;3492991 Un ejemplo de eso son las lectoras SATA de DVD, que cambia mucho el soporte disponible de una versión de kernel a otra.[/QUOTE]

Seeeeeeeee ojala me ande con el Gutsi ya que NO TENGO LECTORA =( ahora estoy mucho mas ansioso que antes!
Hei Ku groso!

---

### Post by Vero1 on 2007-10-10
Hola a todos los que me contestaron(me dirijo a todos en un solo post por pedido de marianom)

Hei Ku, 

Ya que insistis con el BACKUP, BACKUP, BACHUUUUUUUUUUUUUUP(lo dije bastante fuerte?:) ) quisiera hacer backup de mis correos y Bookmarks de Firefox pero: hay que hacerlo en un CD? Cómo?
En Ubuntu no estoy familiariazada con el Backup. Hay alguna otra forma que no sea grabando en un CD?

gracias y saludos

p.d.
Mi disco está particionado en dos, nada mas. / y swap.

---

### Post by marianom on 2007-10-10
Si tenés otro equipo (digamos que en un red privada), transferí tus archivos de máquina a máquina. Si no, CD o DVD. Old school copy & paste.

Con copiar tu /home salvás todo lo que mencionas (bookmarks -que están en la carpeta .mozilla y mails que deberían estar en alguna carpeta oculta de evolucion, supongo).

Otras opciones, ya son más complicadas (por ejemplo particionar el disco como lo tenés ahora, separando tu /home, e incluso, un backup no está de más).

---

### Post by Vero1 on 2007-10-10
Hola marianom,

No tengo red.
En cuanto a hacer backup en un CD, no sé cómo se puede hacer, ya que "todo" está en /.

El espacio ocupado en este momento es de 3.51 Gib. Por supuesto en un CD no cabe. Además como digo todo está allí, porque reinstalé con el LiveCD,  Ubuntu.

Decís  copiar home, pero repito, no está separado y tampoco sé qué es lo que habría que separar.

Creo que tendré que correr el riesgo de actualizar y ver qué pasa.

Con respecto a backup si pudieras decirme cómo puedo pasar a un CD el correo y los bookmark, sería suficiente.

Gracias.

---

### Post by Hei Ku on 2007-10-10
Tenes que usar un programa para copiar CDs, como el k3b. Ahi podes seleccionar la carpeta que queres grabar en el CD. Te conviene copiar tu carpeta del home completa. Tiene que ser algo como /home/vero.

---

### Post by luchardi on 2007-10-10
Hola a todos, soy Luis de Capital Federa.

Bueno les cuento que la semana pasada actualice a Gusty desde Feisty sin hacer backup y teniendo solo 1 particion... si ya se soy medio Kamikaze ... pero bueno funciono todo.

Tengo una Notebook Pavillion ZT3000 1gb de ram y 32 de video, disco de 60 y creo que nada mas. Si bien con Festy tenía aceleración con Beryl ahora con Gusty todavía no me metí a hacerlo funcionar pero realmente sin aceleración y sin compiz veo que es mucho mas rapido así q no lo extraño.

Si pasé por el bug de tzdata y puse mi zona horaria a berlin y luego volví a buenos aires.

En estos días estan lanzando muchas actualizaciones hasta que se salga el proximo jueves.

Cualquier cosa les cuento mi experiencia y los ayudo !!!
Un abrazo a todos !!

Luchardi !

---

### Post by Vero1 on 2007-10-11
Luchardi, gracias por tu comentario.

Hei Ku, instalé el otro día K3b pero no me sirve. No recuerdo ahora qué me decía pero no lo he podido usar.

De todas formas tengo otro programa para grabar CD pero como le decía a marianom tengo nada mas que / y swap, pero como Luchardi está en la misma situación y le fue bien, pues lo voy a intentar.
Lo que sí quería saber cómo salvar, por lo menos, el correo y los bookmarks, pero no sé cómo se hace.

gracias por tu buena voluntad, una vez mas y esperaré un poco despues que salga la versión final, para actualizar.

saludos

---

### Post by marianom on 2007-10-11
Graba el contenido de tu /home/tuusuario (no importa que este en una partición separada o no, sea como sea tenes un /home/tuusuario) en un CD y/o DVD. Usa cualquier programa, el que más te guste (si metes un CD en blanco en Gnome, hasta solo te pregunta si queres grabar un CD de datos o de sonido).
Si no entra en un CD y no conseguís un programa de DVD por el motivo que sea, grabá varios CDs (es un drag&drop así que solo te tenés que acordar que fue lo grabaste en el último).
Si no queres copiar todo tu home, graba la carpeta .mozilla donde están tus bookmarks y busca la carpeta oculta correspondiente que existe para evolution: .evolution y hace lo mismo.

Y listo.

PD: en general cuando la gente habla del /home, no hacen referencia a una partición del disco con ese nombre, hablan de tu carpeta personal (o sea /home/tuusuario)

---

### Post by Vero1 on 2007-10-14
Cuando uso la herramienta Buscar .mozilla va directamente a mi Carpeta Personal y no encuentra nada. Lo mismo pasa con .evolution.

De qué otra manera se puede buscar?

En mi Carpeta Personal no hay casi nada. Solamente las cosas que he descargado para instalar.

Si busco en Sistema de archivos a .evolution no lo encuentro. A  .mozilla   me muestra 4 archivos, dos de idioma y otros dos que nada tienen que ver con los Bookmarks...

saludos

---

### Post by Montsegur87 on 2007-10-14
```
sudo update-manager -d
```

Ya salio Gutsy

---

### Post by Vero1 on 2007-10-14
Hola Montsegur87

No iba a salir el 18?

Aparte me sale un error de que no se pudo iniciar dbus.

Pero aparte de todo, necesito hacer backup de los Bookmarks y de Evolution y todavía no sé cómo se hace.

Gracias por tu aviso.

saludos

---

### Post by Hei Ku on 2007-10-14
Lo que salió es el Release Candidate 1. O sea, es una versión que podría convertirse en la versión final si no se encuentran errores o graves, o podrían salir nuevas versiones de Release Candidate hasta que finalmente una sea la versión final.

El proceso es así, mas o menos:
Primero salen versiones Alpha: muy crudas, con muchos errores, principalmente para uso interno.
Versiones Beta: crudas, pero en general son usables, recomendadas solo para desarrolladores
Release Candidate: casi, casi lista. recomendadas para usuarios avanzados. La última de estas release candidate generalmente es la que se convierte en versión final.

En este momento estamos en Release Candidate 1, RC1. Probablemente haya al menos un release más antes del final.

---

### Post by Vero1 on 2007-10-14
Hola Hei Ku,

Se parece a las versiones que saca Microsoft.

Gracias por la aclaración.

Disculpen los ubunteros por la comparación:)

---

### Post by Montsegur87 on 2007-10-14
**NO** lo instalen todavia , tiene el bugazo de tzdata + linux-utils con locale. 

Esperen al 18 , es al **** todavia.

---

### Post by Hei Ku on 2007-10-15
> **Vero1 said:**
> Hola Hei Ku,

Se parece a las versiones que saca Microsoft.

Gracias por la aclaración.

Disculpen los ubunteros por la comparación:)

Es que es algo standard dentro del desarrollo de software. Ni Microsoft ni Ubuntu inventaron nada acá, y eso está muy bien, porque como es standard, todos nos podemos entender mejor.  ;)

---

### Post by Vero1 on 2007-10-15
No lo sabía. Todos los días se aprende algo nuevo no?:popcorn:

---

### Post by Vero1 on 2007-10-15
> **Montsegur87 said:**
> **NO** lo instalen todavia , tiene el bugazo de tzdata + linux-utils con locale. 

Esperen al 18 , es al **** todavia.

Yo por mi parte y haciendo caso de un comentario de Hei Ku, esperaré para instalar por lo menos dos semanas despues que salga.

saludos:)

---

### Post by Montsegur87 on 2007-10-15
> **Vero1 said:**
> Yo por mi parte y haciendo caso de un comentario de Hei Ku, esperaré para instalar por lo menos dos semanas despues que salga.

saludos:)

Yo termine de instalar el 7.10 RC y no encontre cambios aparentes. Entre Feisty y Gutsy no cambio nada importante.

---

### Post by rojojuan on 2007-10-15
> **Montsegur87 said:**
> Yo termine de instalar el 7.10 RC y no encontre cambios aparentes. Entre Feisty y Gutsy no cambio nada importante.

Probaste la de 64?

---

### Post by Montsegur87 on 2007-10-15
> **rojojuan said:**
> Probaste la de 64?
No , aunque tengo un Athlon 64 no leo buen feedback de migrar a 64 bits. Tanto tiempo libre no tengo.

---

### Post by rojojuan on 2007-10-16
> **Montsegur87 said:**
> No , aunque tengo un Athlon 64 no leo buen feedback de migrar a 64 bits. Tanto tiempo libre no tengo.

Bueno, veremos los comentarios que vayan surgiendo...

---

### Post by tzulberti on 2007-10-16
Yo tengo un amd64 y tambien instale el RC este viernes...
La verdad es que funciona bien... Para mi dos de los mayores problemas se solucionaron:
-> Flash: ahora es muy simple de instalar
-> Codecs de videos: con la nueva version del mplayer no me fue necesario instalar ningun paquete de codecs extra (w32codecs).

Fuera de eso, no note ninguna mejora con feisty de 64.

Saludos,
TZ

---

