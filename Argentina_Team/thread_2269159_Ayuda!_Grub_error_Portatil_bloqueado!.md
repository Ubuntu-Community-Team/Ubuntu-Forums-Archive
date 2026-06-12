---
title: "Ayuda! Grub error Portatil bloqueado!"
date: 2015-03-13
forum: Argentina Team
---

### Post by jamesal777 on 2015-03-13
[COLOR=#333333][FONT=Ubuntu]Saludos comunidad, soy nuevo en Ubuntu y tengo un problema que tiene inutilizable mi computador.
Particioné el disco para utilizar por aparte windows y ubuntu sin tener ciudado.
Dentro de windows borre la particion de ubuntu y cuando reinicie el pc me aparecio una pantalla negra[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]error: no such partition
Entering rescue mode...
grub rescue>[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]He dedicado mucho tiempo a esto, he booteado una usb con ubuntu para reinstalar y cuando quiero abrir "instalar ubuntu" me aparece lo siguiente: [http://i.4cdn.org/g/1426285668773.jpg](http://i.4cdn.org/g/1426285668773.jpg)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Y tampoco puede abrir ubuntu sin instalar. Estas lineas despues se quedan quitas sin hacer nada, aparentemente.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Probé instalando windows 7 y windows 10 con usb y con dvd, pero ambos se quedan quietos y no me aparece la típica ventanita donde se eligen los idiomas del teclado y el sistema.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Luego revise en otros sitios y videos y observé que en el grub rescue escribian:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]grub rescue> ls[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]y luego me aparecen, creo yo, las particiones:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu](hd0), (hd0,msdos5), (hd0,msdos1)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]en cada una escribo:
grub rescue> ls (hd0)
grub rescue> ls (hd0,msdos5)
grub rescue> ls (hd0,msdos1)
y me aparece algo como file system unknown o algo asi.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]No se que mas hacer, no puedo entrar a ningun sistema operativo, no puedo usar el terminal de ubuntu ni por casualidad y windows mucho menos. No se si sea correcto esperar muchas horas para que arranquen los setup tanto de windows como de ubuntu.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]No me importa borrar o formatear todo lo que tenia con tal de que me deje instalar algun sistema operativo. Mi portatil es Toshiba Satelite.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Cuento con otro computador donde tengo las imagenes iso y las quemo a dvd o booteo, es lo único que puedo hacer o escribir en el grub rescue. Tengo completamente bloqueado el portatil, y cualquier solución a este problema se los agradeceria infinitamente.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]A ustedes gracias por atender mi duda.
Feliz dia.
Saludos![/FONT][/COLOR]

---

