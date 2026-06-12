---
title: "Problemas con ubuntu y su configuracion de graficos y efectos."
date: 2008-03-18
forum: Argentina Team
---

### Post by lucasordonez on 2008-03-18
Buenas:
vi en algun que otro post algo parecido con el titulo, pero mi problema corre por otro lado, 
sucede que ayer me pase a windows por primera vez despues de instalar ubuntu (lo instale hace 3 dias), necesitaba cargar un par de dvds con programas y otras cosas. 
el problema fue hoy, cuando inicie ubuntu. en primer lugar se me cambio la resolucion, de 1280x1024 a 640x800, se me cambio la conf del teclado, en un principio los efectos andaban, pero como veia casi la mitad de la pantalla y todo se habia amontonado no podia cambiar la resolucion desde sistema>pantalla y graficos entonces borre la hora para que me haga lugar.
intente cambiar la resolucion y no permitia, despues si, y me decia que tenia que cerrar todas las sesiones de usuarios,
cerre sesion volvi a iniciar y nada ...
entonces me fije en la opcion de tarjeta grafica, y tenia puesta otra, no me acuerdo el nombre, entonces puse la mia (GeForce7300) y no recuerdo bien si despues que cambie la resolucion de entrada en administracion de arranque fue que tuve la resolucion que quiero, 1280x1024,    
el problema es que no me ejecuta ningun efectos, ni uno, y todos estan marcados como si tuvieran que funcionar, ni la ventana gelatinosa, nada de nada.
no tengo idea como resolverlo.
cabe destacar que anoche cerre la sesion de windows con actualizaciones de windows, nose si influye, pero lo comento.
este es mi primer post, espero respuesta.
gracias.

---

### Post by faktorqm on 2008-03-18
hola, bienvenido al foro. 

al igual que en windows para tener aceleracion grafica necesitas instalar los drivers de la placa de video. lo hiciste? los efectos corren sobre eso. si no lo hiciste, busca "envy" en google, es un script automatico para instalar drivers de video SOLO de nvidia o ati, si tenes alguna de esas dos placas, bajatelo e instalalo, es de confianza ese script. Salu2!!

---

### Post by lucasordonez on 2008-03-18
lo baje y lei algo de eso, supuestamente era ejecutarlo y escribir esto $ sudo apt-get install nombre_de_version.deb (fue lo que hice), pero me aparece esto E: No se pudo encontrar el paquete nombre_de_version.deb y lo extrano es que anoche me andaba todo a la perfeccion, grrr, fue hasta que volvi a windows, antes tenia instalada la placa y todo, igual muchas gracias, a mi siempre me pasan cosas raras.

---

### Post by lucasordonez on 2008-03-18
listo! lo que paso es que se perdio mi configuracion no se porque.
y despues me fijaba en los efectos y estaban marcados, pero yo tenia el lanzador directo a advance desktop effect settings y no tenia marcada la opcion personalizada ..
tuve que reiniciar y ya funcan todos los efectos con la barra mac tmb.
si pudiera hacer algo para ayudar con mi poco conocimiento, por favor decirlo.
gracias.

---

### Post by Hei Ku on 2008-03-18
la proxima, para instalar un paquete deb el comando correcto es:

sudo dpkg -i paquete.deb

---

### Post by sajnox on 2008-03-18
> **Hei Ku said:**
> la proxima, para instalar un paquete deb el comando correcto es:

sudo dpkg -i paquete.deb

No te olvides que tambien podes simplemente hacer doble click sobre el archivo, si bien es cierto que la consola no muerde, el mouse tampoco transmite enfermedades....

---

### Post by vk-cdg on 2008-03-19
> **sajnox said:**
> ... si bien es cierto que la consola no muerde, el mouse tampoco transmite enfermedades....

Juaaaaaa, muy buena frase. Todavía me estoy riendo!!!!
Pido permiso publicamente para usarla!

---

### Post by sajnox on 2008-03-19
> **vk-cdg said:**
> J
Pido permiso publicamente para usarla!

Es GPL

---

### Post by Hei Ku on 2008-03-19
> **sajnox said:**
> ... la consola no muerde, el mouse tampoco transmite enfermedades....

Depende de cada cuánto laves el mouse!! :lolflag:

Muy buena frase!!

---

