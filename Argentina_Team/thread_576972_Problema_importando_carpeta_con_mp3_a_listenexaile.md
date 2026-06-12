---
title: "Problema importando carpeta con mp3 a listen/exaile"
date: 2007-10-15
forum: Argentina Team
---

### Post by matog on 2007-10-15
Muchachos, tengo un problima con unos mp3. Primero pensé en postearlo en algún foro sobre el programa específico, pero como      veo que pasa con varios, por ahí es locura de mi Feisty AMD64.

Quiero armar mi biblioteca de mp3. En cualquier programa (probé con Exaile 0.2.10 o Listen de los repositorios) y me importa todo perfecto. Salvo una carpeta con mp3 de Café Tacuba (no es que a la maquina no le guste Cafe Tacuba porque otros discos los importó perfecto). Directamente me lo ignora. Incluso importando solo esa carpeta, no me da bola. La lista de temas es esta:
> 
01 - Seguir Siendo.mp3      
07 - Vamonos.mp3         
13 - Quiero Ver.mp3
02 - Tengo Todo.mp3         
08 - Cierto O Falso.mp3  
14 - Agua.mp3
03 - 53100.mp3              
09 - Esta Vez.mp3        
15 - Gracias.mp3
04 - El Outsider.mp3        
10 - De Acuerdo.mp3      
Cafe Tacuba - Si No.m3u
05 - Volver A Comenzar.mp3  
11 - Abandonado.mp3
06 - Arrullo.mp3            
12 - Y Es Que.mp3


Primero pensé que era por algún caracter medio extraño, pero no hay nada...que corno pasa?

Nota: Si importo sólo un mp3 de ese disco, no veo las tags (que los tiene..)

Gracias!

---

### Post by por100pre1 on 2007-10-16
Extraño. Prueba utilizar Audio Tag Tool:

```
sudo apt-get install tagtool
```

Con ese programa puedes renombrar los mp3, puede ser un problema de caracteres en los ID tags. Tambien puedes crear una nueva lista de reproducción m3u con ese programa. Si eso no es suficiente el siguiente paso seria convertir las carpetas nuevamente a mp3 o a ogg. No todos los codificadores de mp3 son iguales y algunos pueden ser problematicos.

EDIT: Olvidé mencionar que debes verificar los permisos de esa carpeta. ;)

---

### Post by Montsegur87 on 2007-10-16
Otra alternativa 

```
sudo apt-get install easytag
```

---

### Post by matog on 2007-10-17
Los permisos están ok. Están igual que el resto de la carpeta que tiene miles de subcarpetas con m3.
Todos están taggeados con el easytag, así que supongo que no será un problema de los tags...
Si abro el listen desde la consola, cuando importo la carpeta me dice:

```
Comprobando file:///media/sda3/Varios/mp3/mp3/Cafe%20Tacuba%20-%20Si%20No
14 songs loaded in  0.415579795837  seconds

```

Y con el Exaile, abierto desde la consola, se cuelga (la música sigue sonando, pero se pone la pantalla blanca por mas tiempo de lo que mi paciencia aguanta ;) ), y la consola no dice nada...

Que será? Tendrán mensajes satánicos? ;)

---

### Post by Montsegur87 on 2007-10-17
Proba compilando la version del bzr de Exaile , me parecion mas estable que la vieja.

Esta en la pagina de Exaile.

---

