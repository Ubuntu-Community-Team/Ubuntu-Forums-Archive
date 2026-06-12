---
title: "Wine no me funciona"
date: 2007-11-03
forum: Argentina Team
---

### Post by Mataca on 2007-11-03
Hola gente!!

Les cuento que hace un tiempo el wine 0.9.48 me andaba de diez, pero no me hacia funcionar el warcraft 2.

Recordé que con la versión 0.9.41 funcionaba todo de 10 e intente instalarla desde el codigo de fuente. Resultado: no pude :( segui las instrucciones y nada... estoy muy enojado con esto.
Ahora quise instalar desde sinaptic nuevamente la 0.9.48 y no hay drama, pero no funciona! les muestro los errores que tira la consola cuando trato de ejecutar el wow que antes andaba de 10.

```
env WINEPREFIX="/home/mataca/.wine" wine "C:\Archivos de programa\World of Warcraft\wow.exe"
err:module:import_dll Library OPENGL32.dll (which is needed by L"C:\\Archivos de programa\\World of Warcraft\\wow.exe") not found
err:module:import_dll Library wined3d.dll (which is needed by L"c:\\windows\\system32\\d3d9.dll") not found
err:module:import_dll Library d3d9.dll (which is needed by L"C:\\Archivos de programa\\World of Warcraft\\wow.exe") not found
err:module:import_dll Library d3d9.dll (which is needed by L"C:\\Archivos de programa\\World of Warcraft\\wow.exe") not found
```

Y cuando quiero ejecutar el config de wine
```
mataca@wika:~$ winecfg
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!
Application tried to create a window, but no driver could be loaded.
The X11 driver is missing.  Check your build!

```

Me gustaria que me digan, si pueden,  como instalar desde el codigo de fuente la 0.9.41 y si no que me digan como puedo solucionar esto.
Abrazo de pingüino

---

### Post by Alan Stancliff on 2007-11-03
Hola,

Disculpe mi letra pero estoy usando me computadora de trabajo y no tengo tecladora de espanol en este momento.

No tengo familiaridad con este juego, y soy principiante. Ademas toda mi software es en ingles. 

Quizas se pueda sacar ayuda en [[COLOR="RoyalBlue"]***_este foro para los ubantistas_***[/COLOR]]("http://www.ubuntu-es.org/index.php?q=forum") de habla espanol. Que tenga exito con wine.

---

### Post by por100pre1 on 2007-11-03
Verifica los permisos de opengl32.dll.so:

```
cd /usr/lib/wine
```

```
ls -al
```

[Aquí]("http://appdb.winehq.org/commentview.php?iAppId=1922&iVersionId=5109&iThreadId=14174") dice que los permisos deben ser **-rwxr-xr-x**.

Hazme saber si esto te ayuda. :-k

---

### Post by Alan Stancliff on 2007-11-04
Hola por100pre1,

Esta vincula que nos daba es en inglés, y es posible no que la enterdería Manteca. 

Manteca, lo que dice es que es preciso usar el comando "chmod" para que cambie los permisos de este fichero: /usr/local/lib/wine/opengl32.dll. Se puede buscar seminarios que trata con el uso del comando chmod [color=blue]***[aquí](http://www.google.com/search?hl=en&q=ubuntu+chmod+permisos+seminario&btnG=Google+Search)***[/color]. Espero que este le ayude.

[size=5]APÉNDICE:[/size]

Para otro vínculo muy utíl, haz clic **[[color=blue]aquí[/color]](http://www.guia-ubuntu.org/index.php?title=Sistema_de_ficheros)**. Qué busque "Cambio de permisos".

---

### Post by por100pre1 on 2007-11-04
> **Alan Stancliff said:**
> Hola por100pre1,

Esta vincula que nos daba es en inglés, y es posible no que la enterdería Manteca. 

Manteca, lo que dice es que es preciso usar el comando "chmod" para que cambie los permisos de este fichero: /usr/local/lib/wine/opengl32.dll. Se puede buscar seminarios que trata con el uso del comando chmod [color=blue]***[aquí](http://www.google.com/search?hl=en&q=ubuntu+chmod+permisos+seminario&btnG=Google+Search)***[/color]. Espero que este le ayude.

[size=5]APÉNDICE:[/size]

Para otro vínculo muy utíl, haz clic **[[color=blue]aquí[/color]](http://www.guia-ubuntu.org/index.php?title=Sistema_de_ficheros)**. Qué busque "Cambio de permisos".

Si, debí haber aclarado eso. :( Mataca, prueba con este comando:

```
sudo chmod 755 /usr/lib/wine/opengl32.dll.so
```

---

### Post by Mauro22 on 2007-11-04
Hola, para mi tendrias que borrar todo lo de wine usando 'purge'

y agregar los repos de wine HQ, y bajar ese:

```
*wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -*
``````
*sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list*
``````
sudo apt-get update
``````
**sudo apt-get install wine**
```Y en esta pagina de Wine, explica como hacer una regresión ("Antes funcionaba ahora no, porque?")
[http://www.winehq.org/site/docs/winedev-guide/x1344](http://www.winehq.org/site/docs/winedev-guide/x1344)

---

### Post by Mataca on 2007-11-04
Mauro22 me decis como sería el comando usando purge?

No estoy familiarizado todavia con la consola
gracias

---

### Post by por100pre1 on 2007-11-04
> **Mataca said:**
> Mauro22 me decis como sería el comando usando purge?

No estoy familiarizado todavia con la consola
gracias

```
sudo apt-get remove --purge wine
```

---

### Post by Mataca on 2007-11-04
Gracias por100pre  pero no lo purga. Dice lo siguiente

```
mataca@wika:~$ sudo apt-get remove --purge wine
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete wine no esta instalado, no se eliminará
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.

```
Alguna otra idea? Tengo permisos para escribir en la carpeta que me dijeron. La verdad que no tengo idea

---

### Post by Mauro22 on 2007-11-04
mmm....


Yo nunca use el --purge :(


Proba:

```
sudo apt-get purge wine
```

---

### Post by por100pre1 on 2007-11-04
> **Mauro22 said:**
> mmm....


Yo nunca use el --purge :(


Proba:

```
sudo apt-get purge wine
```

Evidentemente el paquete ya había sido removido en el manual de apt-get puedes leer sobre la opción --purge

```
man apt-get
```

purge como commando también funciona.

---

### Post by Mauro22 on 2007-11-04
Si lo estuve leyendo, evidentemente, se aprende algo todos los dias.

---

### Post by por100pre1 on 2007-11-04
> **Mauro22 said:**
> Si lo estuve leyendo, evidentemente, se aprende algo todos los dias.

Eso es lo bueno de esta comunidad. No sólo fomentamos el software libre, también aprendemos nuevos trucos. :)

---

### Post by Mataca on 2007-11-04
Ya lo hice de las dos formas y no funciona.
O sea lo remueve pero  cuando lo instalo de nuevo sigue tirando el mismo error.
No se como solucionarlo

---

### Post by Mauro22 on 2007-11-04
Trata de borra la carpeta .wine desde tu home

```
rm -r .wine/*
```

:guitar:

---

### Post by Alan Stancliff on 2007-11-05
> **por100pre1 said:**
> Eso es lo bueno de esta comunidad. No sólo fomentamos el software libre, también aprendemos nuevos trucos. :)
¡Por cierto!

---

