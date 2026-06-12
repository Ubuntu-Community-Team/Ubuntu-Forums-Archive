---
title: "Idioma de teclado se reinicia"
date: 2008-04-29
forum: Argentina Team
---

### Post by smrdelj on 2008-04-29
Hola, buenas noches. Tengo este otro problemita extraño: cada vez que reinicio, el teclado se resetea, activando el idioma ingles. Entonces, cada vez q reinicio la pc, tengo q molestarme en volver a setearlo en español. Lo raro es que tengo español como distribucion predeterminada, e incluso removí "US" de la lista. Ademas, para setear el español, no me hace falta reconfigurarlo como idioma, sino q con tan solo, por ejemplo, cambiar el teclado (osea, ponerle que uso por ejemplo el teclado Genius XX##) ya es suficiente.

Me resulta bastante raro esto..alguien sabe qué pasa? Me imagino que existe forma de setear esto por consola, editando algun archivo q obligue a cargar por defecto al español como idioma/distribucion del teclado.

Espero su ayuda, muchas gracias

---

### Post by atatiducken on 2008-04-30
ok, si lo q digo a continuacion esta mal, que alguien me corrija :), primero hace un backup tu archivo xorg.conf por seguridad :), escribi en una terminal
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
ahora editamos el xorg, escribi en una terminal
```
sudo gedit /etc/X11/xorg.conf
```
 mi Xorg dice esto

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
```

fijate el tuyo  en la linea
**Option		"XkbLayout"	"es"**   
deberia decir "es" para q sea español, guarda los cambios y despues reinicia para probar si funciona
Cualquier cosa pregunta, si no funca avisa 
saludos

---

### Post by sajnox on 2008-04-30
Un unico comentario de mi parte, no hace falta que reinicies el equipo, con reiniciar las X alcanza ctrl + alt + backspace

---

### Post by smrdelj on 2008-04-30
Hola q tal, muchas gracias por responder. 

atatiducken, habia leido exactamente esto que me respondiste en otro foro, pero cuando abrí el xorg.conf no tenia ninguna linea como esta: ```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
``` Entonces lo que habia hecho fue simplemente agregarla al archivo y guardar. Pero no me habia dado resultado. Ahora lo que hice fue simplemente colocar la linea "Option		"XkbLayout"	"es"" en lo que a mi me aparecia al cargar el xorg.conf

Es decir que, en vez de quedarme como vos dijiste, lo q en mi ubuntu queda sería lo siguiente: ```
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option		"XkbLayout"	"es"
EndSection
```

Saludos muchas gracias!

---

### Post by atatiducken on 2008-04-30
gracias sajnox, tenes razon es mas rapido reiniciando las X
smrdelj te funciono o sigue igual?

---

### Post by smrdelj on 2008-04-30
Hola q tal. 

Sí, funcionó.

Como dije en el post anterior, la unica diferencia fue que al abrir el xorg.conf me encontré con un "esquema" diferente, asi q agregué la linea ahi y listo. Esta bien grafico en mi otro post para q cualquiera q le pase lo mismo q a mi lo pueda entender.

Saludos

---

