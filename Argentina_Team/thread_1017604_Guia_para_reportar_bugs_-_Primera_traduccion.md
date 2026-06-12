---
title: "Guia para reportar bugs - Primera traduccion"
date: 2008-12-21
forum: Argentina Team
---

### Post by sajnox on 2008-12-21
Hola a todos, 

Hace rato que me interesa el tema de reportar bugs, ya que muchas veces nos preocupamos mas por solucionar un problema particular de alguien pero no contribuimos como comunidad en reportar bugs. Haciendo esto ultimo contribuimos en forma mas certera y precisa a la comunidad de Ubuntu en general y no a los que participan del foro o que eventualmente pueden encontrar informacion a travez de buscadores.

Buscando informacion de como reportar bugs (es algo que hice una sola vez y mal !!) encontre esta [0] guia que me parecio muy clara y simple. Como esta en ingles hice una primera traduccion y quiero invitar a todos los que sepan Ingles y tengan unos minutos para que revisen la traduccion y sugieran los cambios necesarios.

Una vez que tengamos la traduccion pulida podriamos abrir un thread para asistir a la gente que quiera reportar bugs, ya sea con la traduccion de su problema (en caso que quien tenga el problema tenga un conocimiento basico del Ingles) o para ayudar a identificar el mismo.

A continuacion dejo la traduccion que hice.

[0] [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

**_[COLOR=Blue]Guia para reportar bugs[/COLOR]_**

Ok alto!! Si bien parece que hay mucho para leer mas abajo, te puedo prometer que [COLOR=DarkRed]reportar bugs no es tan complicado[/COLOR]. Este post tiene la intencion de mostar la forma de hacer buenos reportes de bugs usando la herramienta de Ubuntu para esta tarea llamada Launchpad, la seccion de Launchpad para reportar bugs se la puede encontrar en [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

Debido al gran volumen de bugs reportados, es importante que cuando se reporten se lo haga de manera correcta con la mayor cantidad de informacion posible. Podemos asegurar que mejorara significativamente las posibilidades de que el bug sea revisado y reparado en el corto plazo.

**_[COLOR=Navy][COLOR=Blue]Una breve reseña sobre los bugs:[/COLOR][/COLOR]_**

[COLOR=Blue]_Que es un bug?_[/COLOR]

Hay un bug cuando un programa hace algo que no se esperaba que pase, usualmente causando problemas al usuario. Algunos ejemplos de Bugs son:

 * Cierre anormal o cuelgue abrupto de un programa
 * La falta (simple) de una opcion aplicación
 * Errores inesperados, usualmente impiden que se siga usando normalmente la aplicación
 * Otros comportamientos inesperados

[COLOR=Blue][U]Lo que no es un bug
[/U][/COLOR]
Un pedido de soporte (usen los foros !!)
La falta de una aplicacion (requiere mucho trabajo el implementarlo)
Configuracion incorrecta del hard

_[COLOR=Blue]Como se si es un bug?[/COLOR]_

Para los recien llegados a Ubuntu y/o Linux en general antes de reportar el bug es aconsejable que consulten en los foros. Muchas veces se esta ante problemas que no son realmente bugs, y muchos problemas comunes que son bugs ya han sido reportados (Podes revisarlo vos mismo)

Los usuarios con mas experiencia pueden ofrecerte ayuda para poder opinar si tu problema es un bug y si el mismo debe ser reportado.

[COLOR=Blue]_Antes de reportar un bug_[/COLOR]

 * Estar seguro de tener la cuenta en Launchpad &#8211; No se pueden reportar bugs sin tener una cuenta en Launchpad. Si no tienes una cuenta en Launchpad la puedes abrir en [https://launchpad.net/](https://launchpad.net/), click en &#8220;register&#8221; y seguir las instrucciones.

Buscar en los bugs de Launchpad ([https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)) que no haya sido reportado, si hay uno abierto  por favor agrega tu problema en el mismo y si ti es posible cambia el status de &#8220;New&#8221; (nuevo) a &#8220;Confirmed&#8221; (confirmado). Importante: Esto solo debes hacerlo si estas un 100% seguro que es exactamente el mismo problema. Si el bug se refiere a una pieza de hardware que tienes, debes tener la misma parte o al menos una muy parecida, en caso que este no sea tu situacion por favor abre un nuevo reporte y menciona el que ya hayas encontrado, un triager podra ayudarte a determinar si tu problema corresponde ser incluido en el mismo reporte o debe ser incluido en uno nuevo.

[COLOR=Blue]_Pasos para reportar un bug_[/COLOR]

1)En [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) haz click en &#8220;Report a Bug&#8221;
2)Describe tu bug en forma breve y concisa y haz click en &#8220;Continue&#8221;
3)Una lista de los bugs que pueden ser similares acorde a tu descripcion aparecera , si piensas que tu problema no esta incluido en ese listado haz click en &#8220;No, I'd like to report a new a bug&#8221;
4)Es importante (por lo menos que lo intentes) de reportar el bug en el paquete correcto, una lista de busqueda aparecera en la pantalla cuando hagas click en  &#8220;Choose&#8221; para ayudarte con la busqueda. 
5)Aquí puedes describir tu bug con mas detalle, incluir los pasos para reproducir el bug y que has hecho para intentar solucionarlo
6)Por favor incluye en el reporte la salida de los siguientes comandos

    lsb_release -rd
    uname -a
    apt-cache policy &#8220;nombre del paquete&#8221; (&#8220;nombre del paquete&#8221; es el paquete     al que asocias tu reporte en el punto 4.
7)Si necesitas adjuntar algun/os archivo/s (pueden ser screenshots) ve a la opcion de &#8220;include an attachment&#8221; Solo se puede subir un archivo por cada reporte, por lo que si tiene mas archivos debes añadirlos en tus comentarios despues de haber reportado el bug.
8 ) Debido a que los bugs deben ser reportados en Ingles lo siguiente sera de mucha utilidad:
   Transformar el mensaje de error en ingles: 
   Ejemplo:

```
miguel@miguel-desktop:~$ rmdir /boot
rmdir: No se pudo eliminar «/boot»: Permiso denegado
miguel@miguel-desktop:~$ ls /foo
ls: no se puede acceder a /foo: No existe el fichero ó directorio
miguel@miguel-desktop:~$ LANG= ls /foo
ls: cannot access /foo: No such file or directory
```9)Cuando creas que has agregado informacion suficiente haz click en &#8220;Submit bug report&#8221;

[COLOR=Blue]_Despues de reportar el bug_[/COLOR]

Puedes agregar comentarios extra adjuntar mas archivos, para esto haz click en &#8220;Add comment/attachment&#8221; al final del reporte del bug
Recibiras emails relativos a los cambios y respuestas al bug que hayas reportado. El seguimiento del bug no puede ser completado hasta que hayas suministrado toda la informacion requerida. Agrega el reporte a tus favoritos e intenta hacer un seguimiento del mismo
Los bugs triager o los desarrolladores pueden preguntar por mas informacion en caso de considerarlo necesario. Si te quieres adelantar algunos puedes ver las &#8220;Generic bug responses&#8221; ([https://wiki.ubuntu.com/Bugs/Responses](https://wiki.ubuntu.com/Bugs/Responses)) en la wiki de Ubuntu. Ahi encontraras links con informatiocn para completar algunos tipos especificos de reportes de bugs, como ser con el hardware o con el kernel
Tambien puede ser que te soliciten que reportes un bug en el upstream &#8211; esto significa que hagas algo similar a lo que ya hiciste pero en un sitio fuera de Launchpad &#8211; aquí encontraras mas informacion ([https://wiki.ubuntu.com/Bugs/Upstream](https://wiki.ubuntu.com/Bugs/Upstream))
Tambien puede ser que te soliciten que revises este mismo error en la version en desarrollo de ubuntu, esto lo podras hacer con un LiveCd de la version en desarrollo




[COLOR=Blue][U]Ciclo habitual del reporte de un bug
[/U][/COLOR]
El usuario experimenta un problema y reporta el bug
Si tiene suerte alguien mas confirmara su problema (No confirmes tu propio problema!!)
Un Triager mira e reporte. Si es necesaria mas informacion el Triager la solicitara, la persona que reporto el bug debe responder. Este proceso se repite las veces que sea necesario.
Cuando el Triager esta satisfecho con la informacion recolectada el bug sera marcado como &#8220;Confirmed&#8221; (o aun mejor y sera marcado como &#8220;Triaged&#8221;), el Triager indicara la importancia del bug y posiblemente asignarlo al desarrollador o a un equipo
Un desarrollador mira el reporte &#8211; ellos tambien puede pedir mas informacion, arregla el bug o lo rechaza (ya sea por que no es un bug o por que no la pena arreglarlo)
El reporte se cierra con el status de &#8220;Fix Released&#8221; (Arreglo propuesto para actualizacion), &#8220;Won't fix&#8221; (no sera arreglado), o &#8220;Invalid&#8221; (Invalido)
Cuando el arreglo es propuesto para actualizacion generalmete no es hecho para la version estable (salvo que sea un tema de seguridad o que reuna los criterios para la version estable). Generalmente los arreglos se ponen en la version en desarrollo (inestable)

_[COLOR=Blue]Y que es Apport?[/COLOR]_

Apport es una herramienta integrada a Ubuntu que es usada (en algunos casos) para reportar bugs en forma automatica. Usualmente abre una ventana luego de que un programa termina anormalmente y pregunta si quieres reportar el problema. Les pedimos encarecidamente que asi lo hagan, es muy simple para los usuarios y de mucha utilidad para los desarrolladores.

En muchos programas de Ubuntu puedes ir a Ayuda &#8594; Reportar un problema o en Ayuda &#8594; Reportar un Bug y en ambos casos Apport juntara la informacion y te redirigira al site para que puedas reportar el bug en Launchpad

[COLOR=Blue]_Algunos Links de interes_[/COLOR]

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
[http://www.chiark.greenend.org.uk/~sgtatham/bugs.html]("http://www.chiark.greenend.org.uk/%7Esgtatham/bugs.html")
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
[https://wiki.ubuntu.com/Bugs/Responses](https://wiki.ubuntu.com/Bugs/Responses)

---

### Post by ubuntu27 on 2009-05-30
Este thread deberia de ser un Sticky no lo creen?

---

### Post by sajnox on 2009-05-30
En algun momento lo deje como sticky pero la verdad que no hubo mucho exito y ya tenemos muchos stickys.

Tendria que darle una actualizacion ya que algunas cosas cambiaron respecto al reporte de bugs

Tengo planeado volver a la humanidad dentro de poco tiempo, no seria mala idea para retomar

Saludos

---

### Post by jandry on 2009-08-29
Gracias Saj, en un momento me parecia que era mas facil atravezar un foso de cocodrilos que reportar un bug:( ahora probare con esta guia para reportar un bug recurrente en el plasma de KDE, despues les cuento. Abrazo Ubuntero

---

### Post by jandry on 2009-09-01
Bug reportado con exito!!!! :D

---

### Post by ubuntu27 on 2009-09-01
> **jandry said:**
> Bug reportado con exito!!!! :D

Link al BUg Report? ;)

---

### Post by jandry on 2009-09-01
Me enviaron dos mail pidiendo mas informacion sobre el bug, lo cual fue muy complejo debido a mi escaso ingles (entiendo lo que me piden pero no se como explicarlo) entonces tengo que recurrir a mis hijos para que me ayuden con el proceso, previa burla de ellos ("asi que linux tiene estos errores...") pude darmas informacion y estoy a la espera de alguna confirmacion. Ni bien sepa algo aviso.
Abrazo Ubuntero

---

