---
title: "[SOLVED] pantalla borrosa"
date: 2008-12-10
forum: Catalan Team
---

### Post by bratac on 2008-12-10
Bones,

acabo de comprar-me una pantalla Samsung SyncMaster 923nw (de 19 polzades) per que la vella va morir. Un cop l'he instal·lada tot em surt allargassat i borrós. Com puc fer per a que no es vegi ni borrosa ni allargassada? 

gràcies,

---

### Post by tanreb20 on 2008-12-10
Suposu que es tonteria pero...

Has provat de canviar la resolucio?

---

### Post by bratac on 2008-12-10
Sí, ho he fet, el problema és que em marca la pantalla com a desconeguda i la resolució màxima que puc agafar és de 1280x1024, que ja m'està bé però si em passo a 1024x768 ho veig més gran, però no més clar. A velocitat de refresc de la pantalla hi posa 0hz. Potser el problema és de la targeta gràfica una intel 950 integrada a la placa base, però he mirat els connectors i els tinc instal·lats i actualitzats.

Una altra cosa, a la caixa diu que la resolució òptima de la pantalla és 1440x900. Com puc fer-ho per a canviar-la i veure si així ho soluciono?

gràcies

---

### Post by tanreb20 on 2008-12-10
Segons llegeixo en els forums en castella:

Hauries de editar el Xorg.conf:

```
sudo gedit /etc/X11/xorg.conf
```

I després buscar la seccio "**screen**" i anar al subdirectori Display (varius)
Busca el predeterminat (segurament será el 24, posa algo aixi com: default depth).

Afegeix la resolució  a **modes**.

Hauria de anar!

---

### Post by bratac on 2008-12-11
El fitxer xorg em diu el següent:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Res més,he intentat desar-hi el dept24 però no em deixava, em deia que no tinc permisos.


Acabo d'engegar l'ordinador amb el liveCD d'ubuntu 8.10 i em detecta la pantalla (marca, resolució...) Em podeu dir com ho puc fer per arreglar-ho a l'ordinador?

Gràcies!
Algú em pot ajudar?

---

### Post by tanreb20 on 2008-12-11
Uhm.. si l'ordiandor amb un LIvCD et detecta..

Podries mirar com esta configurat el xorg del livecd? I copiar-lo?

---

### Post by bratac on 2008-12-12
Tinc la configuració que m'ha donat xandr sobre la resolució de la pantalla que utilitza el liveCD d'ubuntu (que me la detecta a la primera) és la següent:

Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1600 x 1600
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 410mm x 257mm
   1440x900       59.9*+   75.0     59.9*    60.0  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      75.0     60.0     60.0  
   1280x960       60.0     60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9  
   720x400        70.1 

Com puc fer per posar-ho a l'ordinador per a poder canviar la resolució de la pantalla?

---

### Post by bratac on 2008-12-14
Moltes gràcies a tots ja he trobat la solució, és la següent:


sudo gedit /etc/X11/xorg.conf

i hi havia de treure el driver vesa, que era el que impedia que l'ordinador detectés totes les pantalles!

Gràcies Rain CT i endiku!

---

