---
title: "Resolucion del monitor"
date: 2007-03-24
forum: Argentina Team
---

### Post by gustavoefe on 2007-03-24
Hola,
Tengo muy poca experiencia en linux y no se cómo aumentar la resolución del monitor.
Tengo una notebook "Dell Inspiron 1300" que tiene una placa de video Intel 915 y su resolución máxima es de 1280x800.
Instale Ubuntu 6.10 y solo me acepta una resolución de 1024x768.

Agradeceré si alguno sabe cómo lo puedo arreglar.

Saludos

---

### Post by marianom on 2007-03-24
Gustavo, confirmame por favor.
Cuando vas a Sistema->Preferencias->Resolución de la pantalla, ¿la única opción que tenés en el primer desplegable es 1024x768? ¿o tenes varias opciones pero solo te toma 1024x768 no importa lo que elijas?

---

### Post by gustavoefe on 2007-03-24
Mariano,
La única opción que aparece es 1024x768. A la derecha aparecen las flechas para desplegar las opciones y cuando hago clic ahí no aparece ninguna. 
Gracias por responder.

---

### Post by marianom on 2007-03-24
Habría que analizar tu xorg.file para detectar cualquier problema.
Te sugiero lo siguiente: fijate si podes seguir este [howto]("http://www.ubuntuforums.org/showthread.php?t=83973") para asegurarte que los pasos básicos están cumplidos o existe alguna opción que puedas modificar.

[COLOR="Red"]Fair warning[/COLOR]: es posible que, al modificar tu xorg.conf y si da un error, termines en la linea de comandos (no vas a poder usar el modo gráfico) y hasta que no lo arregles no vas a poder volver a modo gráfico. No te preocupes porque no es un problema serio.

Segui estas ideas si te llega a pasar:
siempre antes de modifiquar el xorg.conf, hace una copia de tu versión en funcionamiento:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
```
Si algo sale mal y quedas en modo de línea de comandos, solo:
```
sudo mv /etc/X11/xorg.conf.bkp /etc/X11/xorg.conf 
```
luego Control+Alt+Backspace y estarás de nuevo operativo como si nada.

Cualquier otro problema estamos a tu disposición.

Fijate el howto que te sugiero y cualquier cosa nos avisas.

---

### Post by gustavoefe on 2007-03-24
Corregime si me equivoco, pero pude observar que las especificaciones de la placa de video están bien. Sin embargo el controlador de la placa corresponde a otra (i810). Puede ser?
Eso se puede arreglar?
Te adjunto el archivo si no te molesta.

---

### Post by spg76 on 2007-03-24
> **gustavoefe said:**
> Corregime si me equivoco, pero pude observar que las especificaciones de la placa de video están bien. Sin embargo el controlador de la placa corresponde a otra (i810). Puede ser?
Eso se puede arreglar?
Te adjunto el archivo si no te molesta.

Gustavo, el nombre del controlador es correcto (aunque no sé si tu placa funcionaría mejor con otro).
Lo que podes hacer es colocar la resolución que queres usar en la parte que dice:

```
SubSection "Display"
		Depth		24
		Modes		[COLOR="Red"]"1280x1024" "1024x768" "800x600"[/COLOR]
```
(En rojo está lo que agregue yo)

Yo tenia un problema similar (con otra placa de Intel) y lo solucione así.
Antes de tocar el archivo xorg.conf, tené en cuenta las recomendaciones de Mariano.

---

### Post by gustavoefe on 2007-03-24
En la página **[http://doc.ubuntu-fr.org/materiel/portable/inspiron_1300](http://doc.ubuntu-fr.org/materiel/portable/inspiron_1300)** dan una solución, entre otras, que es:

**sudo apt-get install 915resolution**

Luego reinicie el equipo y tomó la máxima resolución (1280x800) como esperaba.

Igualmente, agradezco a cada uno por su aporte.

---

