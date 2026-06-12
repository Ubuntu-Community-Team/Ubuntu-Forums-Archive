---
title: "se cuelga el mouse"
date: 2008-02-18
forum: Argentina Team
---

### Post by sebaxxxtian on 2008-02-18
mi problema es q de vez en cuando se cuelga mi mouse ps/2. probe de iniciar mi maq en mi windows 98 para descaratr q sea el mouse, pero anda bien en eindows

q puede ser q falle en gutsy?

---

### Post by Mauro22 on 2008-02-19
Te pasa solo en linux?'


El xorg.conf que dice:??


El mio es asi:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection
```

---

### Post by sebaxxxtian on 2008-02-19
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by User21 on 2008-02-19
El mio dice:
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```
Tengo un mouse genius optico de los mas baratos.Si me funcionan los 3 botones, de todas formas..
La pregunta es: SOLO TE SUCEDE en UBUNTU ? Lo probas en otras distros o win y funciona sin problemas ?? 
Revisaste la aceleración y la sensibilidad del mouse, en Sistema > Preferencias > Ratón ?
Esperamos tu respuesta!!!

---

### Post by sebaxxxtian on 2008-02-19
solo me pasa en ubuntu. ahora estoy en win98. revise tambien las config del mouse y no habia nada extraño (de hecho estaba en los valores de default)

---

### Post by User21 on 2008-02-20
Ahora que sabes hacer backups del xorg.conf, podrías intentar con un **sudo dpkg-reconfigure xserver-xorg** para chequear los parámetros de configuración del mouse... 
NO OLVIDES HACER UN BACKUP del mismo, en caso que necesites volver a la config previa!
Cómo hacer un backup? pues, copialo con otro nombre, añadiéndole la fecha (y hora, si lo deseas) del momento del backup, o ponle el nombre que te plazca!
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.ddmmaa
```A ver que sucede!

---

### Post by sebaxxxtian on 2008-02-20
hola

gracias por la mano, ya backpee el xorg.conf.
y de paso tambien arregle lo del mouse: en vez de setear el device como "ImPS/2) lo setee como "Psaux". ayer no se colgo.

asi q lo unico q me falta es poder editar el titulo de los threads con [solved], pq veo q no lo tomo al cambio.

---

