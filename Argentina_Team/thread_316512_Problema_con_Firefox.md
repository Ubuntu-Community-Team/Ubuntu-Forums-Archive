---
title: "Problema con Firefox"
date: 2006-12-10
forum: Argentina Team
---

### Post by Nemesis Teufel on 2006-12-10
Me pasa que usando el firefox.. haga lo que haga.. es como que cada 20 segundos se tilda.. carga n las pantallas que tienen q cargar pero yo no veo ningun cambio y no puedo hacer ninguno y eso durante.. otros 20 segundos... me pasaba algo similar en dapper pero le hecchaba la culpa a bcompiz.. pero ahora no lo tengo instalado.
Yo uso el firefox que me vino directamente en edgy.. yo habia leido que en dapper era conveniente instalar firefox desde los repositorios ya que era diferente al que venia por defeecto.. pero en edgy es la 2.0 
saben que hacer? xq es inutilizable.. lo raro es que aparecio de la noche a la mañana.. no instale NADA nuevo

---

### Post by felipelerena on 2006-12-10
Lo que haria yo:
[LIST=1]
[*]desinstalar firefox
[*]borrar todas las extensiones, de hecho borraria el perfil
[*]install firefox[/LIST]si no funciona y sigue pasando instala firefox vanilla
vanilla = el que dan en firefox.com

saludos.

---

### Post by beuno on 2006-12-11
> **Nemesis Teufel said:**
> Me pasa que usando el firefox.. haga lo que haga.. es como que cada 20 segundos se tilda.. carga n las pantallas que tienen q cargar pero yo no veo ningun cambio y no puedo hacer ninguno y eso durante.. otros 20 segundos... me pasaba algo similar en dapper pero le hecchaba la culpa a bcompiz.. pero ahora no lo tengo instalado.
Yo uso el firefox que me vino directamente en edgy.. yo habia leido que en dapper era conveniente instalar firefox desde los repositorios ya que era diferente al que venia por defeecto.. pero en edgy es la 2.0 
saben que hacer? xq es inutilizable.. lo raro es que aparecio de la noche a la mañana.. no instale NADA nuevo

Yo tuve ese problema con las versiones alpha, y despues con el plugin del flash.
Me suena que esta en alguna version "bon echo" del firefox.

Si es asi, volala y bajate otra urgente.

---

### Post by Nemesis Teufel on 2006-12-11
Probe borrandolo del synaptic y volviendo a instalar.. sabia que iba a tener mucha suerte si funcionaba pero bue.. estoy con poco time y sucedio lo obvio.
Con borrar al perfil te referis con borrar la carpeta .mozilla que cree en el home? la de .macromedia tmb la borro o no hace falta?
o q hago?

---

### Post by jpmorelli on 2006-12-11
A mi me pasaba algo parecido cuando habria alguna pantalla con flash y encontrè el comando misterioso, que tambien use en Flock y sirvio.

For Firefox:
sudo gedit /etc/firefox/firefoxrc

export XLIB_SKIP_ARGB_VISUALS=1

For Flock:
If you've got Flock installed in /opt/flock, as I have, you can do the following, I think:

Code:

sudo gedit /opt/flock/flock

Find the line that says..
Code:

export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR

..and change it to..
Code:

export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR XLIB_SKIP_ARGB_VISUALS=1

---

### Post by Nemesis Teufel on 2006-12-12
jajaja!!:p :p :D 

Me funciona! agregue esto: export XLIB_SKIP_ARGB_VISUALS= como dijo el amigo morelli y todo bien. 
tambien me decia sobre un bug y q vaya a esta pagina: [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760)

Pero ni la lei xq ya me funciona perfecto y sin borrar nada.

Gracias

---

### Post by jpmorelli on 2006-12-15
josha !!! :)

---

### Post by Nemesis Teufel on 2006-12-15
Lo unico es que el flash cuando veo videos me funca un poco mal: dps de unos.. 20 o 30 segundos aprox.. se tilda 4 segundos el audio y video pero dps vuelve. No es la muerte de nadie, pero uno aspira a tener lo mejor. =)

---

### Post by jpmorelli on 2006-12-15
> **Nemesis Teufel said:**
> Lo unico es que el flash cuando veo videos me funca un poco mal: dps de unos.. 20 o 30 segundos aprox.. se tilda 4 segundos el audio y video pero dps vuelve. No es la muerte de nadie, pero uno aspira a tener lo mejor. =)

si lo que tenes es un retardo te comento que yo tambien lo tenía , instalé la version 9 beta del flash que anda por este foro el link, y partir de ahi, todo bien !

---

### Post by daniminas on 2006-12-15
aproposito, esta bueno está el FF 2.. :D..

bah, no se que diferencias habrá.. (tecnicas).. pero que le hayan puesto el boton cerrar a cada pestaña (a lo Opera :P) es lo mejor :)

---

### Post by Nemesis Teufel on 2006-12-15
Si, la verdad que es mucho mejor FF2 sobre todo en Ubuntu. Hay mucha diferencia, es mas rápido y mucho mas estable.
Con lo del cierre a la pestaña, es mejor usar el tab mix plus como plugin:
[https://addons.mozilla.org/firefox/1122/](https://addons.mozilla.org/firefox/1122/)

Mejor BASTANTE la navegación por pestañas, es imprescindible.

---

### Post by DuckMan on 2006-12-15
buenaaaa, aguante el zorro

---

### Post by Nemesis Teufel on 2006-12-16
Instale el flash 9 y va para la miercole. Lo instale dos veces y anda peor que nunca, solo con videos. Se traba el sonido y el video cada 5 segundos.

Creo que el flash 7 iba mejor :(

Alguna forma de volver?

---

### Post by ubuntu27 on 2006-12-17
> **Nemesis Teufel said:**
> Instale el flash 9 y va para la miercole. Lo instale dos veces y anda peor que nunca, solo con videos. Se traba el sonido y el video cada 5 segundos.

Creo que el flash 7 iba mejor :(

Alguna forma de volver?


ANYBODY KNOW THE ANSWER TO HIS QUESTION ABOUT "HOW TO UNINSTALL FALSH9 AND INSTALL FLASH7?"


No se como desinstallar Flash9 que viene de Adobe.com
pero, por mientras (esperando que alguien te responda)

que tal si pruebas el navegador epiphany?

Epiphay es ligera (no te consume mucha memoria), es nativo de GNOME (se comporta y actua tal como cualquier gnome app), y tien algunas caracteristicas similares a de firefox talez como pestaña.

```
sudo aptitude install epiphany-browser
```

talvez te guste. :) Intentalo.

Si no te gusta simplemente remuevelo con
```

sudo aptitude remove epiphany-browser
```

---

### Post by Nemesis Teufel on 2006-12-17
> que tal si pruebas el navegador epiphany?
Si, lo he probado cuando el FF andaba en problemas. Me encanta, ya que es ligerisimo y anda muy bien. Pero bueno, la contra que tiene son los plugins y algunas mañas que tiene el FF.
Como navegador auxiliar me parece perfecto, para un usuario que le gustan los chiches y botoncitos con todo y para todo.. no.

---

### Post by jpmorelli on 2006-12-18
Para desisntalar el Flash PLayer 9 tenes que sacar la libreria libflashplayer.so ya sea en:

/home/usuario/.mozilla/plugins

o en la carpeta /usr/lib/mozilla/plugins

o en la carpeta /usr/lib/firefox/plugins

segun como lo hayas instalado. Igual te comento que yo lo estoy usando y me anda perfecto pero bue, cada sistema es un mundo aparte.

---

