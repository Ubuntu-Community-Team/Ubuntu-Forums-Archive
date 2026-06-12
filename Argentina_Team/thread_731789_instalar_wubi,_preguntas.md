---
title: "instalar wubi, preguntas"
date: 2008-03-22
forum: Argentina Team
---

### Post by joseluis on 2008-03-22
Amigos,
pido disculpas si no estoy en el ítem correspondiente. Uso Ubuntu en mi PC de escritorio y necesito probar Ubuntu en mi Notbook.

Por eso quiero probar wubi y necesito  ayuda.

Cuando comienza instalarse (luego de darle los parámetros iniciales como idioma, cantidad de espacio en disco, etc...) va diciendo algunas preguntas. Me quedo frenado en dos momentos , a saber:

1- pide de dónde instalar el CD???? es decir, busca el cd de instalacion. Le doy que ignore y sigue...

2. Aca viene lo complicado, en este punto: Me pide en un momento seleccionar la partición, como si se tratara de una instalación normal con sus opciones: a) todo el disco duro; b) redimensionar la partición; c) hacerlo manualmente (o algo parecido.)  Alli es donde me paro porque me da un terror de que reviente el disco y me parta el windows (lo necesito asi como está).

 La pregunta sera si cuando intenta instalar el ubuntu este wubi al pedir el espacio del disco se está refiriendo justamente al espacio que le he asignado al comenzar todo (por ejemplo 5 gigas).

bueno, gracias por leer esto y espero vuestra ayuda

---

### Post by Mafber on 2008-03-23
Hola Joseluis. Vos le asignaste 5 gigas en tu rigido? ya tenes esa partición (unidad) ???
Acordate que Ubuntu usa por lo menos dos unidades, una es ext3 y otra en swap. (yo uso 3 unidades donde una es la swap y dos estan en ext3, "/" y home) 
Si no estas mas o menos familiarizado con este tema de las particiones, te recomendaría que leas algunos tutoriales (no es un tema dificil, de hecho es relativamente sencillo) 
te paso este [link]("http://www.cesarius.net/preparativos-para-instalar-gnulinux/"), tal vez te sirva (fijate de la mitad en adelante) es para que tomes un poco de idea del tema... no te salva de buscar en google :)
Suerte!!!

---

### Post by joseluis on 2008-03-23
hola mafer...
Si..eso lo entiendo, pero wubi no necesita preparar esas particiones por lo que tengo entendido. Utiliza un archivo que instala dentro de la particion de windows. Por eso es lo que me extraña.

---

### Post by Mafber on 2008-03-23
proba con poner "c) hacerlo manualmente" total te va a mostrar las unidades que ve. no hace nada en forma automática en esa opción (como por ej. formatear sin preguntar) fijate, tal vez te muestre las unidades que esta creando (virtuales).
y como te dije, no te va a formatear nada hasta que vos decidas hacerlo.
Por las dudas, me parece exagerado pero por las dudas..., hace un backup de aquellos elementos que sean irreemplazables (por ej "mis documentos", "el solitario", el archivo  log de los errores de windows.. ) ;)

---

### Post by joseluis on 2008-03-23
ok-- voy a probar eso..gracias

---

