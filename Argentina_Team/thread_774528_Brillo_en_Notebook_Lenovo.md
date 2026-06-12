---
title: "Brillo en Notebook Lenovo"
date: 2008-04-29
forum: Argentina Team
---

### Post by Idus on 2008-04-29
Hola, les comento que hace unos días hice una instalación limpia de Hardy en mi Lenovo 3000 c200. Ya hace un tiempo la venía utilizando con Gusty sin ningun problema.
El problema que encuentro es que cuando botea ya baja el brillo al mínimo y a pesar de que luego lo configuro a mi gusto con el teclado o con el applet del panel, no logra mantener esta configuración y cada vez que reinicio tengo que hacer todo de nuevo.
En Gusty ajustaba los parámetros en Preferencias>Gestión de Energía y mantenía los mismos sin problema.
En Hardy este camino no me sirve porque no ofrece la posibilidad de establecer el porcentaje de brillo y solo mantiene algunas pocas opciones específicas.
Lo raro es que si reinicio y elijo la opción Windows xp en el Grub, también este último aparece con poco brillo y tengo que ajustarlo con el teclado. En todos los casos estoy hablando de utilizar la notebook con el cable de alimentación, no con batería.
Alguien conoce alguna solución para este problemita?

---

### Post by faktorqm on 2008-04-30
Hola! vamos a ver que podemos hacer.

Vamos por partes, primero vamos a probar que configuracion se ajusta mejor a tu requerimiento de brillo poniendo en una consola el comando xgamma: (con esta herramienta, se puede hallar el ajuste exacto que se necesita en el "xorg.conf")

Abri la consola y ejecutá:
```

xgamma -gamma 1.0    (este comando limpia cualquier ajuste anterior)
xgamma -gamma 1.1    (subimos el brillo...)
xgamma -gamma 1.2    (subimos más el brillo...)
xgamma -gamma 0.9    (reducimos el brillo...)

```

No pongas el valor 0, ya que se te quedaría la pantalla totalmente en negro....

Supongamos que el valor 1.3 es el que va entonces lo ponemos en "/etc/X11/xorg.conf" en la sección monitor.

haces ```
sudo gedit /etc/X11/xorg.conf
``` y buscas la seccion monitor y le agregas la linea de gamma. Te tiene que quedar asi mas o menos:

```

Section "Monitor"
    Identifier    "Configured Monitor"
    Gamma 1.3
EndSection

```

Cuando reinicies, deberia guardarte esa configuracion, si esto no pasa, y la seccion te figura con la opcion DPMS, desactivala, para eso le ponemos un # adelante, y te tendria que quedar asi:

```

Section "Monitor"
    Identifier    "Configured Monitor"
#   Option        "DPMS"
    Gamma 1.3
EndSection

```

Ahora bien, si con esta configuracion aun no funciona, ahora si anda al panel o a donde debas ir para configurar eso y cuando reinicias supuestamente te lo tiene que tomar. Si no te lo toma, espero tu post y lo revisamos. 
Espero que te haya servido. Salu2!!

---

### Post by Idus on 2008-05-01
Hola, gracias por la ayuda; pero debo decirte que no funcionó.
Es rarísimo, pero directamente no funciona el comando xgamma, no produce ningún cambio en la pantalla.
De igual manera puse un valor (1.2) reinicié y el problema seguía (no guardaba la configuración). Vuelvo a revisar el "xorg.conf" y estaba tal cual lo había dejado sin la opcion DPMS.

---

### Post by spg76 on 2008-05-01
Yo tengo el mismo problema y, por lo que estuve investigando en el foro, es bastante común aunque no encontré ninguna solución.
Tengo la sospecha de que algo tiene que ver el kernel de Hardy, porque creo recordar que ni bien actualicé, si iniciaba el sistema con la versión más vieja del kernel que venía trayendo de Gutsy esto funcionaba bien. Lamentablemente ya borré esa versión y no puedo volver a probar mi teoría.

---

