---
title: "Uso de RAM muy alto"
date: 2007-04-11
forum: Argentina Team
---

### Post by damcito on 2007-04-11
hola gente, suelo leer el foro pero no posteo mucho, a veces pq hago lectura rapida otras porque no tuve tiempo, prometo ponerme mas al dia

tengo el siguiente problema, vengo usando Kubuntu hace 1 año maso, desde hace unos dias estoy teniendo un consumo exagerado de ram, tengo 1.25gb de los cuales apenas inicio me quedan 100mb o hasta 50mb libres! (en este momento 57)

en la lista de procesos no veo nada raro, solo que muchos procesos ocupan 30mb o mas, es muy raro, lo unico nuevo que tengo es el driver nvidia 97.55

el kernel sigo usando el mismo de antes 2.6.17-686

alguna idea de que puedo chequear o hacer?

saludos y gracias

---

### Post by Tinchio on 2007-04-11
no tengo la explicacion "oficial" ni soy ningun experto, pero segun tengo entendido (x eso no lo tomes tan en serio) la administracion de memoria en GNU/Linux es distinta a Windows, creo que (y aca mas que nunca "creo") la idea es que "llena" toda la memoria de una y esa memora la reparte entre las aplicaciones ya cargada y una especie de memoria cache,la verdad no recuerdo bien como era, asi que para no seguir diciendo cualquiera nada mas digo que es distinto como para no alarmarse; Igual que un experto lo aclare asi yo tmb  me lo aprendo bien  :mrgreen:

---

### Post by damcito on 2007-04-11
ta bien, pero esto me lo hace desde hace unos dias, siempre iniciaba y no pasaba los 100 150mb de consumo inicial

raro

---

### Post by jpmorelli on 2007-04-11
COmo dice Tinchio, la memoria cachea programas hasta lo más que puede. igualmente si tenés 1.25Gb y aplicaciones de 30Mb que te la llenan, cuantos programas abre tu compu al principio ??? :confused: 
No estaría mal que tires un reporte bajo consola con el comando "top" y lo postees o que te fijes con el comando"ps -aux" y te fijes cuantos procesos tenés corriendo en la máquina, a ver si podemos ayudarte un poco más con el tema. 
Yo por ejemplo en este momento tengo 245Mb en uso de 1Gb de memoria total, asi que algo le pasa a tu sistema.
Suerte !

---

### Post by DuckMan on 2007-04-11
tengo la experiencia personal de q el administrador de tareas de kde me fruteaba la ram en uso, y siempre era distinta a la del gnome, igual son delirios mios pero ..

la pc te va lenta o simplemente ves q es medio raro? si te va lenta bueno, preocupate, si no, debe ser q cachea *como dicen los chicos*

---

### Post by kowal on 2007-04-11
Adhiero a jmorelli. Posteá el resultado de ps -aux y vemos que puede ser.

Otra cosa, KDE tiene una opción de "Guardar la sesión previa" y quizás pueda dejar algunos procesos corriendo de fondo. La podés desactivar desde Configuración del Sistema -> Avanzada -> Administrador de sesiones -> Comenzar una sesión nueva

---

### Post by marianom on 2007-04-11
Si está pasando desde hace un par de días y -creyente del determinismo como soy- tiene que ser algo que instalaste recientemente. 
Con un reporte top como te sugiere jmorelli sería la forma correcta de identificarlo.

---

### Post by damcito on 2007-04-11
mmm, en el inicio solo tengo beryl, superkaramba, kmix, kclipper, lo basico

[PHP]top - 00:22:00 up  1:45,  1 user,  load average: 0.92, 0.66, 0.59
Tasks:  92 total,   1 running,  91 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.0%us,  3.7%sy,  0.0%ni, 80.7%id,  0.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1295764k total,   947040k used,   348724k free,    38544k buffers
Swap:  2048276k total,        0k used,  2048276k free,   495868k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 9205 damian    15   0 33260  15m  12m S 12.3  1.3   0:03.72 konsole
 4422 root      15   0  146m  82m 7168 S  4.3  6.5   7:15.63 Xorg
 5000 damian    15   0  113m  55m 6180 S  0.7  4.4   1:55.92 beryl
 8384 damian    15   0  353m  78m  33m S  0.7  6.2   0:14.42 java
    1 root      16   0  1636  496  420 S  0.0  0.0   0:01.19 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.16 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  131 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  164 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  165 root      15   0     0    0    0 S  0.0  0.0   0:00.02 pdflush
[/PHP]

ah, la maquina en si la siento igual, ahora tengo 300mb libres (que para el andar general de linux sobra)

---

### Post by gepatino on 2007-04-12
> **damcito said:**
> mmm, en el inicio solo tengo beryl, superkaramba, kmix, kclipper, lo basico

[PHP]top - 00:22:00 up  1:45,  1 user,  load average: 0.92, 0.66, 0.59
Tasks:  92 total,   1 running,  91 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.0%us,  3.7%sy,  0.0%ni, 80.7%id,  0.3%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   1295764k total,   947040k used,   348724k free,    38544k buffers
Swap:  2048276k total,        0k used,  2048276k free,   495868k cached
[/PHP]




Fijate la linea que comienza con 'Swap:', al final te dice que tenes 495 megas de cache. 
Esto puede ser medio confuso en el top, porque en realidad ese cache no se refiere al swap sino a la ram. En una de esas estuviste usando archivos grandes (imagenes isos, peliculas, etc) y quedaron en memoria como cache. 
Tener la memoria ocupada por cache es lo mas normal, de esta forma se acelera el acceso a disco. Cuando tu sistema necesite usar mas memoria para procesos, no te preocupes que el mismo kernel va a limpiar el cache según necesite.

---

### Post by clasificado on 2007-04-12
otra forma es verlo con el comando **free -m** (para megabytes)
```

             total       used       free     shared    buffers     cached
Mem:           376        371          4          0          6        132
-/+ buffers/cache:        232        144
Swap:         1098        136        961

```

en la linea **-/+ buffers/cache:** se ve el numero ya resuelto (con ese tema del caché descontado y todo). 

por ejemplo, yo tengo 232mb ocupados y 144mb libres (tengo todo abierto)

clasificado.

---

