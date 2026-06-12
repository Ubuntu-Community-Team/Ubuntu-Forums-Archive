---
title: "Asus M2N-MX y un sonido espantoso."
date: 2007-06-01
forum: Argentina Team
---

### Post by valucha on 2007-06-01
[COLOR="DarkOrchid"]Bueno, instalé Ubuntu en mi nueva compu :) y tengo un problema con el sonido.
Tengo una Placa M2N-MX la cual trae la placa de sonido integrada. Pero cuando enchufo el parlante me suena un pitido asqueroso... Como cuando acercás el micrófono y se acopla.
El micrófono no lo tengo enchufado y el ruido no me aparecía con WIndows. 
¿Alguien tiene ese problema o sabe de qué hablo?... Gracias.[/COLOR]

---

### Post by valucha on 2007-06-01
[COLOR="DarkOrchid"]Ahh, antes con mi vieja compu y estos parlantes tampoco se escuchaba el ruido feo ese.[/COLOR]

---

### Post by MeduZa on 2007-06-01
hola, yo tambien tenia unos problemas medios raros con la placa de sonido integrada (era otra y el problema era otro) pero haciendo pruevas y buscando informacion en internet, me di cuenta q la mayoria de las placas integradas son una tremenda %#@#, asi que yo tenia una sound blaster liver 5.1 (esas q salen 20 a 30 dolares ) tirada por ahi, q pensaba q era peor o igual q la que traia on-board el mother, y me asombro, no solo porque andaba perfecto sino porque todo lo que hacia lo hacia por hardware y no por emulacion por software (que come microprocesador)
Para darte un ejemplo, la mescla de diferentes sonidos en una placa q no tiene esa opcion por hardware, los tiene q hacer el procesador, lo msimo con las entradas, y los efectos 3D y todo eso!

Asi que desde ese dia tengo la SB andando perfectamente con mejor calidad de audio ( se noto un aumento en el volumen)

Yo te recomiendo una de estas dos cosas:

1 vas a la pagina de alsa y buscas tu placa de sonido para encontrar informacion extra, ademas de buscar en los fotos de linux sobre esa placa
2 te compras una placa de esas SB varatas q andan de maravilla y no dan problemas

Saludos

---

### Post by valucha on 2007-06-01
[COLOR="DarkOrchid"]Meduza pero quiero solucionarlo con mi placa :(. Gasté 2000 pesos en mi compu y no quiero gastar 100 más en una placa de sonido :(.
Espero a ver si alguien lo solucionó... sino tomo tu consejo. gracias [/COLOR]

---

### Post by beuno on 2007-06-01
¿Podras ubicar que chipset tiene?

Asi lo googleamo' un poco y vemos.

---

### Post by valucha on 2007-06-01
[COLOR="DarkOrchid"]http://www.asus.com/products4.aspx?l1=3&l2=101&l3=343&model=1338&modelmenu=1

esas son las especificaciones de mi mother...
Igualmente encontré un driver para Linux en la página de ASUS...
Alguien sabe cómo instalarlos?

mil mil gracias[/COLOR]

---

### Post by valucha on 2007-06-02
[COLOR="DarkOrchid"]Buscando en internet logré avanzar algo...
le hice un ./configure y  me saltó un error de que faltaba un archivo install.sh o algo así, el cual me lo pasó un chico por msn y funcionó, pero ahora me dice [/COLOR]

> error: cannot find input file: version.in

[COLOR="DarkOrchid"]alguien sabe?[/COLOR]

---

### Post by valucha on 2007-06-02
[COLOR="DarkOrchid"]Logré terminar de compilarlo...
Me salió todo ok.
Pero el problema es que el sonido sigue funcionando mal...
Me dijeron que tngo que configurar los modules con el alsaconf
logré tener el alsaconf...
ahora no sé qué configurar.

me dice que tengo:
hda-intel nvidia corporation MCP61 High Definition Audio (rev a2)
legacy  Probe legacy ISA (non-pnp) chips

[/COLOR]

---

### Post by valucha on 2007-06-04
[COLOR="DarkOrchid"]Bueno, la real solución para este problema la encontré de casualidad en un foro...
Y la posteo por si alguien tiene el mismo problema:[/COLOR]

> [COLOR="DarkOrchid"]sudo gedit modules.conf[/COLOR] 
[COLOR="DarkOrchid"]Y agregar esta linea:

**options snd-hda-intel position_fix=1 model=3stack**

Listo, después de eso mágicamente se soluciona.[/COLOR]

---

