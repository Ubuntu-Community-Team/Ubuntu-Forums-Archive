---
title: "Como instalar gutsy sin perder /home???"
date: 2007-12-18
forum: Argentina Team
---

### Post by niko_3100 on 2007-12-18
Bueno gente les comento tengo feisty y cuando lo instale particione el /home ahora quiero instalar gutsy como tendria que hacer para no pisar esa /home?? Solo indico una particion /  o sea el sistema de archivos y la swap?? No quiero perder todos los datos de mi carpeta porque no termino de cargarlos mas jejejeje!!!! No pido La explicaciones o sencilla para guiarme un poquito. Muchas gracias.

---

### Post by odiseo77 on 2007-12-18
Hola, si ya tienes otra partición /home, debes especificarla durante el proceso de instalación para que Ubuntu la reconozca, **pero**, eso sí, diciendole al instalador de Ubuntu que **NO** la formatee (de lo contrario, perderás los datos que tengas en /home). No recuerdo exactamente cómo se hace esto en el instalador del live-cd porque hace tiempo que no lo uso (uso el disco de instalación alterno), pero quizás alguien que lo use podría darte una explicación más detallada al respecto.

Saludos.

EDIT: se me está refrescando un poco la memoria :D en la lista de particiones que aparece después de particionar seleccionas la partición que estás usando como /home, le asignas el punto de montaje /home y te fijas bien que no esté marcada para formatear.

---

### Post by madrod on 2007-12-18
Para utilizar una partición existente, en este caso (/home), lo que tienes que hacer es decirle al instalador del livecd que vas a usar un particionamiento personalizado.
Una vez que seleccionaste esa opción, te mostrara una lista con las diferentes particiones de tu(s) disco(s).
Para decirle al instalador que partición sera tu home o cual sera tu / simplemente modifica el punto de montaje de la partición :popcorn:
NOTA: OJO, CUANDO MODIFIQUES EL PUNTO DE MONTAJE DE TU HOME, VERIFICA QUE ESTE DESHABILITADA LA OPCIÓN DE FORMAT, PORQUE DE LO CONTRARIO PERDERAS TODOS TUS DATOS.
No obstante, hace backup, por si las moscas.
Saludos.

---

### Post by niko_3100 on 2007-12-18
AAh buenisimo no parece ser taan comlpicado solo estar atento. Lo hare asi, muchas gracias.

---

### Post by valucha on 2007-12-19
[COLOR="DarkOrchid"]Hago una pregunta al respecto.
Es recomendable borar antes todas las configuraciones guardadas en el /home?.
Porque una vez me mande una macana con ubuntu y andaba todo re mal, reinstale usando la misma /home y seguia todo mal :(.[/COLOR]

---

### Post by Moonlit Knight on 2007-12-19
Yo instalé gutsy manteniendo el /home y no tuve inconvenientes, por ahí sería remonedable borrar los directorios .gconf y los que tengan que ver con la  configuración de algunos programas. 

Creo que eso por sentido común que instalás nuevas versiones de los paquetes y algunas configuraciones no son compatibles.

---

### Post by hernan blau on 2007-12-21
Una recomendación conocida pero que nunca está de más: hacete una copia de respaldo de tu /home antes de lanzarte a reinstalar. Entre otros el k3b es muy bueno. Suerte.

---

