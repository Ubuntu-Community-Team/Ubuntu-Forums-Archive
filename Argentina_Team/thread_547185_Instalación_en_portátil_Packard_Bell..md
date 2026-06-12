---
title: "Instalación en portátil Packard Bell."
date: 2007-09-09
forum: Argentina Team
---

### Post by hernan blau on 2007-09-09
Amigos: Hoy me decidí e instalé Ubuntu Feisty. Les cuento que en el representante técnico de P.B. en Argentina dice que no suministran los drivers por un convenio con el monopolio y que la pc debe usarse con vista. De más está decir que nada dicen de eso cuando uno compra la pc. Instalé y no tenía sonido. Tengo una placa Realtek High Definition Audio. Luego de buscar en la red encontré la solución y es la siguiente: 
Por consola:
sudo gedit /etc/modprobe.d/alsa-base

y agregar al final la linea: 

options snd-hda-intel model=3stack

Grabar las modificaciones.
Al reiniciar hay sonido.  
El link de donde lo saqué: [http://www.ubuntu-es.org/index.php?q=node/59147](http://www.ubuntu-es.org/index.php?q=node/59147)

Les cuento que acabo de instalar. Hasta ahora me tomó el touchpad, el mouse, la internet por puerto usb, el sonido arreglado como dije arriba,  Me falta aún ver qué pasa con el wi-fi, tengo problemas de red.  Ya volveré. Cordialmente, Hernán Blau.

---

### Post by FlyerDie on 2007-09-10
y la pregunta del millon....si conectas los auriculares, se te anulan los parlantes? o te suena todo a la vez?

---

### Post by faktorqm on 2007-09-10
hola, fijate que yo respondi por ahi un post identico al tuyo, la unica diferencia es que uno tenia audio y cuando enchufaba los auriculares no se le cortaban los parlantes. y aparecian ahi muchas guias y links. salu2!

---

### Post by hernan blau on 2007-09-10
Como les prometí acá van los avances:

1) Respecto del audio -que pregunta el compañero ubuntista- se escucha por parlantes. Cuando se enchufan los auriculares se corta el sonido de los parlantes pero no se escucha por auriculares.  ¿Qué será?

2) Respecto de la wi-fi acabo de hacerla andar mediante configuración manual con mi red. Aún no pude tomar redes de otros o públicas ni hacerla andar como "itinerante".

3) Logré copiar el driver de la impresora Epson Stylus desde el otro lado. Parece que quedó configurada pero no logro sacarle ni impresión de prueba ni de un archivo O.O. Seguiré intentando.

Les cuento que me gano la vida en actividades que no tienen ninguna relación con la computación, por lo que me cuesta.
Saludos a todos. Cordialmente, Hernán Blau

---

### Post by faktorqm on 2007-09-12
[SIZE="4"]1) YA RESPONDI ESO EN OTRO POST!!!![/SIZE] buscalo.
2) no ves digamos, la red propiamente o te conectas pero no tenes internet? por que no es el mismo problema.
3) postea marca y modelo, y si es usb o paralelo.
salu2!

---

### Post by hernan blau on 2007-09-12
Amigos: Ahora quiero afinar la instalación en mi nueva portátil. Ya tengo funcionando una impresora Epson Stylus cx4700 con Ubuntu en mi pc de escritorio. INstalo en la portátil siguiendo las instrucciones de la guía Ubuntu. No la detecta. Elijo "impresora de red" y en puerto pongo "USB". En el paso 2 elijo la impresora y modelo que tengo. En controlador sólo hay dos opciones y pongo "Imagen de alta calidad (Gutenprints CUPS) (expert). En el paso 3 pongo "aplicar" y listo. Dice que ya está en condiciones de ser usada. Trato de imprimir cualquier cosa y no pasa nada. Me coloco en el ícono de la impresora instalada, pulso "propiedades" y en la pestaña "general" , en "Estado", aparece la siguiente leyenda: "Imprimiendo: Unable to lookup host 'USB' - Unknown host" La impresora está conectada por puerto USB. Lo que hice fue duplicar lo que ya tengo en la pc de escritorio pero no anda. Por favor, si se les ocurre algo avisen. Gracias, Cordialmente, H. B.

---

### Post by rojojuan on 2007-09-12
> **hernan blau said:**
> Amigos: Ahora quiero afinar la instalación en mi nueva portátil. Ya tengo funcionando una impresora Epson Stylus cx4700 con Ubuntu en mi pc de escritorio. INstalo en la portátil siguiendo las instrucciones de la guía Ubuntu. No la detecta. Elijo "impresora de red" y en puerto pongo "USB". En el paso 2 elijo la impresora y modelo que tengo. En controlador sólo hay dos opciones y pongo "Imagen de alta calidad (Gutenprints CUPS) (expert). En el paso 3 pongo "aplicar" y listo. Dice que ya está en condiciones de ser usada. Trato de imprimir cualquier cosa y no pasa nada. Me coloco en el ícono de la impresora instalada, pulso "propiedades" y en la pestaña "general" , en "Estado", aparece la siguiente leyenda: "Imprimiendo: Unable to lookup host 'USB' - Unknown host" La impresora está conectada por puerto USB. Lo que hice fue duplicar lo que ya tengo en la pc de escritorio pero no anda. Por favor, si se les ocurre algo avisen. Gracias, Cordialmente, H. B.

Cuando elegís el controlador, también tenés que indicarle que el puerto es usb, porque me parece que te la está colocando en otro puerto, fijate.
Saludos

---

### Post by hernan blau on 2007-09-12
Gracias. pero en el "paso 2" del instalador en el renglón "Controlador" aparecen las dos posibilidades de "Imagen de alta calidad...". Vos te referís seguramente  al primer paso del instalnga explicación por elador en donde allí te pide ese dato y yo lo coloco. Hatsa ahora no pasa nada, quizás tenga e ésen inglplicación por el lado de la leyenda que aparece en inglés que ya señalé y no sé a qué refiere.  Cordialmente, HB

---

### Post by rojojuan on 2007-09-12
> **hernan blau said:**
> Gracias. pero en el "paso 2" del instalador en el renglón "Controlador" aparecen las dos posibilidades de "Imagen de alta calidad...". Vos te referís seguramente  al primer paso del instalnga explicación por elador en donde allí te pide ese dato y yo lo coloco. Hatsa ahora no pasa nada, quizás tenga e ésen inglplicación por el lado de la leyenda que aparece en inglés que ya señalé y no sé a qué refiere.  Cordialmente, HB

Sí, me refería al primer paso, toda la cuestión debe estar allí. Qué puerto elegís?

---

### Post by niko_3100 on 2007-09-12
Intentaste instalar la impresora con los drivers de windows? Proba con el wine. Te comento mi problema tengo una lexmark x2250 y no puedo usarla... Es por esa razon que todavia tengo windows.... GRGRGR!!!

---

### Post by ubuntu27 on 2007-09-12
> **hernan blau said:**
> Amigos: Ahora quiero afinar la instalación en mi nueva portátil. Ya tengo funcionando una impresora Epson Stylus cx4700 con Ubuntu en mi pc de escritorio. 

Elijo "impresora de red" y en puerto pongo "USB".

"Imprimiendo: Unable to lookup host 'USB' - Unknown host" 

Saludis. En vez de poner USB, escribe el IP (Internet Protocol) de la maquina en el cual la impresora esta conectada.

---

### Post by hernan blau on 2007-09-13
Hola amigos: Sigo luchando con la instalación de la impresora. Por otra  parte, la red wi fi funciona sólo en forma manual. Esto es, si oprimo en el ícono de red de la barra arriba me detecta por ejemplo cuatro redes: Juan, Pedro, José y Pablo. Si hago doble click en una gira un rato la flecha sobre el ícono y cuando termina aparece la escalerita como si estuviera conectado a la red elegida, pero si trato de acceder a una página web con el firefox no lo logro. El único modo que encontré hasta ahora de usar la wi fi es cliquear en el ícono de red, elegir configuración manual, poner la clave de root, elegir conexión inalámbrica; allí marcar propiedades, quitar la pestaña itinerante, poner el nombre de la red inalámbrica a la que queremos conectarnos (obtenida de la lista detectada antes de empezar con esto) elegir configuración automática, cerrar y rebootear la pc. Ahora sí se podrá gozar de internet. Si se desea cambiar de red inalánbrica, hay que repetir el proceso. No será muy dúctil pero la red wi fi se puede usar. Cordialmente, HB.

---

### Post by hernan blau on 2007-09-13
Amigos: como les conté, no podía hacer instalar la impresora. Hasta , que entré aq Sistema-Preferencias-Unidades y soportes extraíbles, allí la pestaña impresoras y poner tilde en "Ejecutar un programa automáticamente cuando se conecte una impresora" y en la casilla "gnome-cups-add hal://%h". Luego conectar por puerto usb la impresora andando y listo. Claro que es una tontería luego que se la aprende pero antes..........................Cordialmente, HB

---

### Post by marianom on 2007-09-13
Yo creo que lo más criterioso sería juntar todos tus posts con respecto a la cuidadosa instalación que estás llevando a cabo en un solo thread.
Por ejemplo, el día de mañana una persona se encuentra en tu misma situación y en vez de tener que ver varios theads separados (que los tiene que buscar), va a tener toda la data en uno solo: práctico y al alcance.

Si a vos te parece bien, yo me encargo de juntarlos en uno solo.

---

### Post by hernan blau on 2007-09-13
Me parece bárbaro. Muchas gracias. Disculpen si no estoy familiarizado con la operatoria de la página. Mi idea es justamente transmitirle esto a los que compraron esta portátil que salió hace poco al mercado acá en Argentina. Cordialmente, HB

---

### Post by marianom on 2007-09-13
¡Hecho entonces! (Creo que quedó muy bien, paso por paso).

---

