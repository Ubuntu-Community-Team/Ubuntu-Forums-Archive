---
title: "Sonido..."
date: 2007-03-22
forum: Argentina Team
---

### Post by valucha on 2007-03-22
[COLOR="DarkOrchid"]Ya sé que habrá mil threads sobre "no tengo sonido" pero este es diferente.

Abstenganse de putearme y eso porque ya bastante tengo conmigo misma, y sí, me mandé una cagada muy grande por "chusma".

La cosa es que andaba buscando "sonidos" para bajarme y ponerlos como de defecto de ubuntu, para las alertas digamos...
Andaba tooodo perfecto hasat que encontré[ esta pág]("http://www.lugmen.org.ar/pipermail/lug-novatos/2005-August/005270.html")
Resulta que en mi atolondramiento e ingenuidad pensando que tendría los sonidos "mal configurados" por eso es que no los tenía, hice lo que me decía de hacer en la terminal. En el medio al ver que no me daba  lo que me decía (porque claro, yo tengo otra versión de ubuntu :S) aborte todo y salí sin guardar... Pero igual ahora no tengo sonido...

Si tienen una solución que no sea reinstalar ubuntu se los agradecería, y no me puteen ya aprendí que no tengo que andar tocando cosas así porque sí, es que "la curiosidad mató al gato" vieron... 
(aunque ahora fue más que curiosidad :( )[/COLOR]

---

### Post by jayflower on 2007-03-22
si hiciste este paso seguramente tenes un backup de ese archivo.

```
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup

```
restauralo:

```
sudo rename -f /etc/esound/esd.conf_backup /etc/esound/esd.conf
```


capaz lo recuperas...:confused:consejo de otra nueva en esto.

---

### Post by valucha on 2007-03-22
```
Bareword found where operator expected at (eval 1) line 1, near "/etc/esound"
        (Missing operator before esound?)
syntax error at (eval 1) line 1, near "/etc/esound"

```
[COLOR="DarkOrchid"]Me sale eso, gracias por la ayuda :)[/COLOR]

---

### Post by strugart on 2007-03-23
Mira te voy a ser sincero hay que ser........... para decirte que hay re instalar todo ubuntu de nuevo por un sonido y lo que vi es fácil darlo vuelta, claro si pones ganas y esfuerzo todo sale...
Otra cosa desde que tengo memorias hago cagadas (aun hoy viste)(tengo ya 16 y me dedico a esto desde los 5 asi que imaginete mi historial). Asi que la frase la cuiriosidad mato al gato te la devuelvo pero con otra: "la practica es fundamental".
Primero lo primero (todo en terminal)(supongo un fin logico mas o menos la mitad de la guia)(avisa si le pifie):
en ubuntu gnome trae el sonido mal configurado o algo así, para
configurarlo hace desde una consola :

sudo killall esd (aca mataste el sonido)
sudo cp /etc/esound/esd.conf /etc/esound/esd.conf_backup (aca tenes el backup, copia y pega todo listo pero...cualquier cosa):
sudo pico /etc/esound/esd.conf (aca tenes el archivo que puede estar ...):
y donde dice :
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5

lo cambias por esto: 

auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default

(Dos cosas acá tenes lo que tenes que cambiar, y no creo que hayas instalado alsa, o si??)

---

### Post by valucha on 2007-03-23
[COLOR="DarkOrchid"]Igualmente, el archivo no lo cambié, porque digamos que me arrepentí ahi justo y puse que se guardara sin cambios...

Lo tengo así:
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
[/COLOR]

---

### Post by valucha on 2007-03-23
[COLOR="DarkOrchid"]Y si pongo " sudo apt-get install alsa " me dice que lo tengo instalado en su versión más reciente.[/COLOR]

---

### Post by beuno on 2007-03-23
> **valucha said:**
> [COLOR="DarkOrchid"]Y si pongo " sudo apt-get install alsa " me dice que lo tengo instalado en su versión más reciente.[/COLOR]

```
sudo aptitude remove alsa --purge
sudo aptitude install alsa
```

(con --purge borra todos los archivos de configuracion existentes)

---

### Post by valucha on 2007-03-23
> **beuno said:**
> ```
sudo aptitude remove alsa --purge
sudo aptitude install alsa
```

(con --purge borra todos los archivos de configuracion existentes)[COLOR="DarkOrchid"]

Lo hice, pero sigo sin sonido...[/COLOR]

---

### Post by strugart on 2007-03-23
Te reconoce la placa? Porque puede ser que no. Proba, si es dedicada a cambiar de slot (osea si esta ubicada en el slot (pci isa o lo que sea) x pasalo al slot mas cercano que tengas del mismo tipo. Se me entiende?

---

### Post by valucha on 2007-03-23
> **strugart said:**
> Te reconoce la placa? Porque puede ser que no. Proba, si es dedicada a cambiar de slot (osea si esta ubicada en el slot (pci isa o lo que sea) x pasalo al slot mas cercano que tengas del mismo tipo. Se me entiende?
[COLOR="DarkOrchid"]
Tengo placa integrada a la mother.[/COLOR]

---

### Post by TattooedFish on 2007-03-24
Si quedaste sin sonido, aunque aparentemente salieras sin guardar, si estuviste en la terminal, algo se cambió. Me refiero a algún(os) archivo(s) de configuración que ha(n) cambiado; sino, no estarías sin sonido.
¿La solución? Todo depende... a veces te lleva un par de días o más, encontrar la respuesta correcta, aun si tenés una persona que te ayude. En cambio, una nueva instalación limpia te toma algo más de media hora (podá variar de acuerdo a la PC, pero no mucho), a lo sumo agregale unas horas más de instalar programas y poner todo como lo querés.

En casos como éstos, a menos que tengas cerca a alguien que sepa en seguida qué fue lo que se cambió y pueda revertirlo, la más fácil, limpia y rápida es reinstalar; no tomen la reinstalación siempre como algo tan sufrido, porque no lo es.

---

### Post by strugart on 2007-03-24
Dos cosas: 
Reinstalar todo el sistema operativo por un sonido? Estas bien? Me parece que no es necesario tanto.
Otra cosa si me decis que es onboard, pero no la calidad del integrado (me refiero si es AC'97 o o el de 8 canales mas actual). A mi personalmente se me murio el sonido del integrado y tuve que comprar una placa de sonido nueva de baja calidad para pasar el rato, dsp volvio solo (gracias a linux en parte).
Hace lo que quieras o te paresca bien.

---

### Post by valucha on 2007-03-25
[COLOR="DarkOrchid"]Agradezco su ayuda, pero reinstalé todo de nuevo. Porque necesitaba tener el sonido y  no hacía mucho que lo había instalado, nisiquiera había bajado los archivos que tengo en DVD's así que fue lo mismo, el tema era que quería aprender como hacerlo.

Si quieren cierren esto, o dejenlo por si hay otra persona que lo necesite. 
Gracias :)[/COLOR]

---

