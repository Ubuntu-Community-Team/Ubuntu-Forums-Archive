---
title: "Olympus x-10, no soporrtado por gthumb."
date: 2008-01-09
forum: Argentina Team
---

### Post by valucha on 2008-01-09
[COLOR="DarkOrchid"]Hola chicos, ando con un nuevo problema...
Me compré una cámara digital OLYMPUS X-10 Y no la puedo hacer funcionar :(.
La conecto, me la reconoce como cámara. Se abre el gthumb para importar las fotos y primero que me da cualquier modelo de cámara que no es el mio... y segundo que dice que no hay fotos cuando si las hay (tanto en la memoria interna de la cámara como en la tarjeta de memoria).
Hay algunaforma de hacerla funcionar... al menos ue pasos debería seguir... que info necesitan, etc...
Espero que puedan ayudarme... gracias :)[/COLOR]

---

### Post by faktorqm on 2008-01-09
hola, primero que version de gthumb estas usando? en la page oficial esta la 2.10.8 mientras que la que yo tengo instalada por ejemplo esta en la 2.10.2.
segundo, anda al gthumb, hace click en archivo -> importar fotos... y ahi te abre una ventana. Hace click sobre el boton de la izquierda, (a mi me aparece como "no ha seleccionado ninguna camara" y el icono es una camara tachada) arriba de la ayuda, es cuadrado. ahi t abre otra ventana y te dice: modelo: no se ha seleccionado. Ahi apretas la casilla de opcion que dice "seleccione del catalogo" y ahi te aparece una lista de camaras con modelos. Naturalmente, tu modelo no esta, pero podes elegir la Olympus X-100, X-250 y X-450 y probar a ver sin con alguna de las 3 "agarra viaje".
Espero q t haya servido. Salu2!

---

### Post by valucha on 2008-01-09
[COLOR="DarkOrchid"]Con algunas me dice 
"Se ha producido un error en la biblioteca de entrada-salida ('Parámetros incorrectos'): No se pudo encontrar el dispositivo USB (fabricante 0x7b4, producto 0x114). Debe asegurarse que este dispositivo está conectado a la computadora."
y con otras me dice que no hay imágenes...

Por ahora encontré una solución provisoria de cul*, despues de que me aparezca el cuadro de diálogo preguntandome que quiero hacer con las fotos, si sigo esperando me aparece ootro cuadro de diálogo en el que hay una nueva opción con respecto al anterior "abrir carpeta". Por ahora espero y lo abro como disco y bajo las fotos.

Igualmente me gustaría que el gthumb me la reconozca,,,


Ah ah ah, acabo de abrir el gthumb, luego de decirle a la compu que monte la camara como un disco (eligiendo la opción "abrir carpeta ") y ahora sí me reconoce la cámara como "mass storage cam" y puedo bajar exitosamente las fotos.

Así que parece ser que si lo monto en /media/disk-2 me la reconoce...[/COLOR]

---

### Post by faktorqm on 2008-01-10
aaaahhhhhhhh ok, parece que es asi, primero monta la camara en alguna ubicacion como si fuera un disco extraible (que de hecho lo es), una vez montado recien ahi reconoce las fotos, o al menos intenta organizarlas desde ahi. Si le pedis que lo haga pero no esta montada la cam, no puede leer los archivos, y eso es un error de entrada-salida. 
Buenisimo si al menos se resolvio parte del problema. salu2!!

---

### Post by valucha on 2008-01-10
[COLOR="DarkOrchid"]Necesito una ayudita de novata...
Existela posibilidad de configurarlo de forma tal que siempre que la conecte me la monte como disco extraible y yo abra manualmente el gthumb y baje mis fotos???

Mil gracias por la ayuda :)[/COLOR]

---

### Post by faktorqm on 2008-01-10
de nada! :D
Igual, supuestamente siempre te la monta como disco extraible. Los mp3's, las camaras digitales, los pendrives, los celulares, todo es una memoria flash, solo que cada uno reconoce distintos tipos de archivos, el mp3 reconoce solo mp3, wma y wav, la camara te reconoce jpg y algun formato de video, etc.
Capaz no entendi lo que preguntaste, decime cualquier cosa. salu2!

---

### Post by sajnox on 2008-01-10
> **valucha said:**
> [COLOR="DarkOrchid"]Necesito una ayudita de novata...
Existela posibilidad de configurarlo de forma tal que siempre que la conecte me la monte como disco extraible y yo abra manualmente el gthumb y baje mis fotos???

Mil gracias por la ayuda :)[/COLOR]

Si se puede, seguramente cuando conectas la maquina al puerto USB te aparece en el escritorio un acceso a la nueva unidad montada, si no lo hizo anda a /media/ y ahi tenes que tener una carpeta en la que monto el disco, generalmente /media/disk

Desde ahi podes hacer copiar y pegar como con cualquier carpeta de archivos.

Ojo, que si borras las fotos con nautilus en la raiz de la memoria de la camara genera una carpeta oculta .trash-username en la que guarda todo lo que borraste. Borra el contenido de esa carpeta por que sino es como si no hubieras borrado nada

---

