---
title: "la ç al conky"
date: 2012-03-18
forum: Catalan Team
---

### Post by Lalaith on 2012-03-18
Hola!

ja fa uns mesos de trastejo amb l'Ubuntu amunt i avall, i fa uns dies m'he posat a treballar en un petit conky que hauria de mostrar-se a l'escriptori.

Quan li demano que em mostri el mes (març), enlloc d'esriure la ç em surten símbols que no sé ni reproduir aquí =p
el tipus de lletra que utilitzo, però, he comprovat que conté la ç i la pot escriure en un document del libreoffice.

Podríeu dir-me on està l'error o orientar-me sobre com trobar una solució a aquest problema? no sé ni per on començar :s

Gràcies!

---

### Post by kimet on 2012-03-18
Es en el calendari, cal, gcal...?
Son fonts xft? Prova a posar 'use_xft no' a .conkyrc.

Tindríes que posar el .conkyrc aquí per el puguem veure.

---

### Post by Lalaith on 2012-03-18
He provat a posar "use_xft no" i m'han desaparegut la majoria de tipus de lletra que estava utilitzant, així que dedueixo que sí que són xft.

la part de configuració del .conkyrc és:

```
# Conky configuration

background yes
use_xft yes
xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
update_interval 5.0
total_run_times 0
own_window no
own_window_type desktop
own_window_transparent yes
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
border_margin 2
border_width 1
default_color white
default_shade_color black
default_outline_color black
alignment middle_right
gap_x 12
gap_y 0
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 1024
color1 white
color2 6892C6
color3 E77320
color4 78BF39
color5 3B3B3B

```i la línia que em dona problemes (on surt "març"), és:

```

${voffset -70}${font Ubuntu:size=14}${color1}${time %A}, ${time %d %B %Y}
```si cal posar tot el .conkyrc el puc posar, però pot ser més pesat i no crec que sigui útil 

gràcies! =)

---

### Post by kimet on 2012-03-18
El tipus de lletra aquest ${font Ubuntu:size=14} no te la 'ç'. Prova a canviar-la. P.ex ${font Sans:size=14}, o simplement esborres aquesta referència per que prengui la lletra per defecte.

Salut.

---

### Post by Lalaith on 2012-03-19
al libreoffice sí que puc escriure ç's amb la lletra Ubuntu. 
A més, he provat a canviar la lletra del .conkyrc a la sans i em continuen sortint els simbolets enlloc de la ç. :shock:

---

### Post by Lalaith on 2012-03-19
al FAQ del conky hi surt aquesta qüestió: 

A: This is a Problem of character encoding and possibly a  bug. Until it has been fixed, there exists a workaround when Conky was  built with iconv support. Having a system defaulting to UTF-8, the  following could do the trick:        ```
${iconv_start UTF-8 ISO_8859-1}° ${iconv_stop}
```no sé si aplica pel cas present, però quan tingui temps m'ho miraré amb més calma.

---

### Post by kimet on 2012-03-19
No la veig aquí: [http://font.ubuntu.com/](http://font.ubuntu.com/)
Normalment quan una lletra no es troba en un tipus es subtituida per la lletra del tipus per defecte, el mateix passa amb els accents. per això libreoffice si escriu la lletra ç.
 Per altra banda, jo si puc veure les ç al conky, pot ser com dius, un bug a la versió.

---

### Post by Lalaith on 2012-03-19
a la web que has posat pots escriure-hi text per veure com queda amb la lletra Ubuntu, i si hi escrius la ç et surt (també he provat altres caràcters estranys com la ß i també surten).
Per tant, descarto que sigui culpa del tipus de lletra :(

---

