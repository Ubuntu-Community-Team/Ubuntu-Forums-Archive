---
title: "Purgar archivos antiguos de la papelera de reciclaje"
date: 2008-03-21
forum: Argentina Team
---

### Post by newtonfn on 2008-03-21
Hace un tiempo busqué en este foro y en otros, como hacer para que los archivos más antiguos de la papelera de reciclaje se fueran borrando automáticamente.

Encontré varios topics relacionados al tema, pero en ninguno la solución. (siempre que se proponía una solución, se le encontraba algún error serio.. básicamente borrar más de lo que debería)

En fin, dejo aquí, como attachment, para ustedes el script solución que yo planteé para la evaluación de todos y el aprovechamiento de los necesitados. Su uso es simplemente ejecutarlo pasándole el path de la papelera de reciclaje y definir cuantos días como máximo pueden tener los archivo.

**Ejemplo**. delete_old_files.sh ~/.Trash 7

Con ese comando todos los archivos de más de 7 días de la papelera de reciclaje serán eliminados. Para que sea automático y no tenga que recordar ejecutarlo cada vez, lo puse en un crontab que se ejecuta, en mi caso cada una hora.

Mi solución obviamente tiene algunas limitaciones. Algunas salvables fácilmente, otras no tanto. Pero a mi me está resultando muy útil.

Les dejo _[COLOR="Blue"][en mi blog la explicación del funcionamiento]("http://blog.soluciones3f.com.ar/2008/03/21/eliminar-los-archivos-antiguos-de-la-papelera-de-reciclaje-de-gnome/")[/COLOR]_  para aquellos que la necesiten (aunque el código creo que esta comentado) y detalles sobre las limitaciones que tiene.

Demás esta decir que si lo usan tenga cuidado ya que borra archivos de manera que no pueden ser recuperados y que obviamente no garantizo que a todos les ande bien y no me hago responsable por la perdida o daño de cualquier índole que este script pueda generar.

Espero igualmente, que a muchos les sea útil, y si necesitan alguna customización para que sea más útil, o tienen alguna sugerencia para mejorarlo, no duden en avisarme que si en la medida de mis posibilidades, intentaré ayudar.

Saludos
Fernando

---

### Post by marianom on 2008-03-21
Muchs gracias por el aporte.
Yo siempre uso este comando:
```
find -mtime +xx -exec rm '{}' ';'
```
pero se ve que lo tuyo es mucho más elaborado.

---

### Post by newtonfn on 2008-03-21
No te creas que lo mio es más elaborado. Es básicamente la misma idea. Pero el problema para aplicarlo a la papelera de reciclaje, que es especificamente el problema que yo planteaba, es que cuando borras un archivo (al igual que cuando lo mueves usando mv, que es lo que internamente hace gnome realmente) el mtime no se modifica. En consecuencia no sirve para determinarla fecha en que fue borrado, sino la fecha en que fue modificado (los datos del archivo) por última vez que es casi invariablemente anterior.

Como explico en el post que hice en el blog (aunque en manera gratuitamente complicada) hago un find usando ctime y no permitiendo la búsqueda dentro de directorios. ;)

---

### Post by marianom on 2008-03-21
Si, había notado eso de la fecha en tu script. 
Pregunta: ¿conoces el módulo inotify del kernel? Por ahí tiene algo para dar.

---

### Post by newtonfn on 2008-03-22
Hum.. creo que te refieres a una funcionalidad de notificacion de cambios de archivos. Con respecto a inotify, honestamente no la conocía, lo que si conocía aunque nunca usé es FAM que por una mini investigacion que hice es casi lo mismo pero mas antiguo.

Realmente mi idea era hacer algo muy simple, que no fuera más que un script, y por eso lo hice en Bash. Para usar alguna funcionalidad al estilo FAM o inotify o la que sea seguramente necesitaría de algun lenguaje más poderoso, que pueda interaccionar mejor con librerías externas.

Finalmente, si bien no lo investigué ni concideré mucho tiempo, no veo la necesidad de algo más sofisticado (al menos para mis necesidades, si se te ocurre algun caso mas complejo se puede analizar) que justifique pasar a un lenguaje un poco más serio y convertir la aplicación en un demonio. Pero nuevamente, es probable que no logre ver la imagen completa debido a mi ignorancia.

Gracias por el interes y la sugerencia. Son muy gratificantes. :)
Fernando

---

### Post by marianom on 2008-03-22
Ahora que lo pienso de nuevo, mi sugerencia no sirve de nada ya que tenes que suscribirte para saber cuando sucede un cambio en un archivo con inotify y claro, uno no sabe que va a enviar un archivo a la papelera hasta que efectivamente lo hace :)
Nevermind, el feriado me está afectando.

Nuevamente gracias por el script, estoy seguro que muchos lo encontrarán de utilidad.

---

### Post by newtonfn on 2008-03-22
jaja.. mejor que te afecte el feriado, aún tenemos 3 dias para quedar bien bien afectados... debo confesar tambien me afecta a mi.

Con respecto a tu sugrencia, podría servir si me subscribo a los directorios .Trash a donde van a parar los archivos, pero sigo sin encontrarle la vuelta... simplemente no veo la utilidad por ahora. (que repito puede tenerla, y si a alguien se le ocurre me encantaría escucharla)

Saludos,
Feliz Pascuas.
Y buen fin de semana extra-largo

---

