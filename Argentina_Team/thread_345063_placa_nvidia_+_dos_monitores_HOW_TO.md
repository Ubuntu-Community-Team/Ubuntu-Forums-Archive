---
title: "placa nvidia + dos monitores HOW TO??"
date: 2007-01-23
forum: Argentina Team
---

### Post by jajajavi on 2007-01-23
hace tiempo que ando dando vueltas por foros ubuntu anglosajones e hispanos, y alegremente doy con este... me ando quemando la cabeza copiando todo tipo xorg.conf para hacer andar mi placa **nvidia geforce fx 5500** con dos monitores (catódicos de 19' y 15') como en 'escritorio extendido' tal como lo usaba en el ya olvidado winxp. si alguno tiene la posta, desde ya agradecido. tengo ubuntu dapper 6.06 en un amd 64. gracias, muchachos, gloria al loco team argentina!! su trabajo hará grande a la patria!!

---

### Post by beuno on 2007-01-23
Pegale una leida a esto:

[http://ubuntuforums.org/showthread.php?t=301946](http://ubuntuforums.org/showthread.php?t=301946)

---

### Post by jajajavi on 2007-01-23
ok, encontré por ahí cerca [http://www.ubuntuforums.org/showthread.php?p=1773544](http://www.ubuntuforums.org/showthread.php?p=1773544) voy a ver qué onda eso. muchas gracias!!

---

### Post by jajajavi on 2007-01-24
Finalmente logré hacer andar el BigDesktop..!! La única objeción es que ubuntu amplia el escritorio literalmente, es decir, cuando maximizamos una ventana esta ocupa los dos monitores, y dado que tengo dos monitores de diferente tamaño queda bastante choto, pero por el momento lo resuelvo restaurándolas manualmente. A continuación pego un fragmento de mi actual **xorg.conf**:

```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	Option		"TwinView"	"on"
	Option		"MetaModes"	"1280x1024, 1280x1024; 1024x768, 1024x768"
	Option		"SecondMonitorHorizSync"	"30-85"
	Option		"SecondMonitorVertRefresh"	"50-160"
	Option		"TwinViewOrientation"		"RightOf"
EndSection

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5500]"
	Monitor		"Monitor genérico"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection
```

Actualmente tengo un "escritorio chorizo" de **2048 x 768 pixeles**, para esto hay ir a *System>Preferencias>Resolución...* y elegir la resolución a utilizar (sin esto último, no pasa nada). Para ver películas en pantalla completa cambio a **1280 x 1024** anulado la extensión de escritorio. Al menos así funciona por ahora. 

LG 19' ---------> [IMG]http://www.pxweb.com.ar/sitio/files/images/Pantallazo.png[/IMG] <------ Samsung 17'

**Problemitas: **La resolución 2048 x 1024 me congela la pantalla, sólo anda el mouse y no puedo salir de X de ninguna manera combinando Alt + Ctrl + <-- o Supr, ni recurriendo a las consolas F1-F6. ¿Hay alguna forma menos traumática de salir de esto sin recurrir al botón Reset? ¿Se puede eliminar la opción 2048 x 1024 o bien arreglar algo para que no se me cague? ¿Puedo obtener configuraciones de escritorio extendido mayores a mis actuales 768 px de alto? ¿Es posible configurar el reposicionamiento de las ventanas, ya que lo hago manualmente cada vez que quedan entre los monitores? ¿El ave maría vuela?

Desde ya, muchas gracias. Y que la fuerza esté con todxs...

---

### Post by beuno on 2007-01-24
Yo tuve los escritorios como big screen, pero maximizando en un solo monitor.
Fijate que es cuestion de jugar con la configuracion.

---

### Post by jajajavi on 2007-01-24
Efectivamente, modificando los MetaCodes en la **Section "Device"**

[FONT="Courier New"]	Option		"MetaModes"	"[COLOR="Red"]1024x864, 1024x864[/COLOR]; 1024x768, 1024x768"[/FONT]

Donde antes decía 1280x1024, 1280x1024, y todo anda perfecto en mi escritorio de 2048 x 768. Recomiendo checkear [Configuración de TwinView en tarjetas NVIDIA]("http://www.linuca.org/body.phtml?nIdNoticia=186") y todos contentos... Aunque me quedo con la duda de cómo salir de un eventual *cuelgue* sin tener que resetear.

---

### Post by beuno on 2007-01-24
> **jajajavi said:**
> Efectivamente, modificando los MetaCodes en la **Section "Device"**

[FONT="Courier New"]	Option		"MetaModes"	"[COLOR="Red"]1024x864, 1024x864[/COLOR]; 1024x768, 1024x768"[/FONT]

Donde antes decía 1280x1024, 1280x1024, y todo anda perfecto en mi escritorio de 2048 x 768. Recomiendo checkear [Configuración de TwinView en tarjetas NVIDIA]("http://www.linuca.org/body.phtml?nIdNoticia=186") y todos contentos... Aunque me quedo con la duda de cómo salir de un eventual *cuelgue* sin tener que resetear.

Me alegro que lo hayas resuelto, y gracias por postear como lo solucionaste.

Podes resetear gnome con "control + alt+ backspace" si es eso a lo que te referis...

---

### Post by jajajavi on 2007-05-18
> **jajajavi said:**
> Efectivamente, modificando los MetaCodes en la **Section "Device"**

[FONT="Courier New"]	Option		"MetaModes"	"[COLOR="Red"]1024x864, 1024x864[/COLOR]; 1024x768, 1024x768"[/FONT]

Donde antes decía 1280x1024, 1280x1024, y todo anda perfecto en mi escritorio de 2048 x 768. Recomiendo checkear [Configuración de TwinView en tarjetas NVIDIA]("http://www.linuca.org/body.phtml?nIdNoticia=186") y todos contentos... Aunque me quedo con la duda de cómo salir de un eventual *cuelgue* sin tener que resetear.

La posta:
```
"MetaModes" "1280x1024, 1024x768; [COLOR="Red"]1024x768@1024x1024[/COLOR], 1024x768; 1280x1024, NULL"
```

Ahora sí funciona perfecto, me queda un escritorio de **2034x1024**, donde 1024x768@1024x1024 (paning domain) es el monitor chico de 1024x768 con un "area muerta" de 1024x256 pixeles en la parte inferior.

---

