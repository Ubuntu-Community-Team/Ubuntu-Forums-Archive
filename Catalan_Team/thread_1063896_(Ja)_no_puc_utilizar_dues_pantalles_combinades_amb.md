---
title: "(Ja) no puc utilizar dues pantalles combinades amb Xfce"
date: 2009-02-08
forum: Catalan Team
---

### Post by giorgiograppa on 2009-02-08
Salutacions, companys,

Ahir vaig migrar de Hardy a Intrèpid aprofitant que havia canviat el disc dur del portàtil (un HP Compaq nx6110 amb gràfica Mobile 915GM/GMS/910GML Express Graphics Controller).

El cas és que, fins ahir mateix, i suposo que gràcies a un simpàtic fitxer xorf.conf (que no sé ben bé com vaig generar, penso que va ser de casualitat des del Kde 3.5, i que miraré d'adjuntar-vos (crec que ho he fet)), podia combinar fàcilment la pantalla del portàtil (15") amb la vella Princeton (17"): gairebé feia goigs treballar-hi!
I la cosa més curiosa era que em funcionava igual tant si treballava amb Gnome, amb Xfce o amb Kde 3.5.

Ara, amb l'Intrepid, només puc combinar les dues pantalles amb Gnome (amb l'eina gràfica que apareix a Sistema/Preferències/Resolució de pantalla, i que m'ho posa molt fàcil; però no reflecteix cap canvi al /etc/X11/xorg.conf); amb Xfce, no passo de la simple duplicació (i això de veure la feina per partida doble, dóna mal karma); amb Kde 4.1, però, he aconseguit posar la imatge de la Princeton cap per avall, en pla malabarista :o.

He cercat informació pel nostre fòrum, pel nostre correu, per sant Google, però la major part de les descripcions que hi trobo parlen de les utilitats gràfiques de la targeta Envídia, o Endívia, i si diuen alguna cosa sobre configurar xorg.conf a mà, sembla un galimaties.

He provat amb les ordres:

dpkg-reconfigure xserver-xorg
dpkg-reconfigure -phigh xserver-xorg

i l'única cosa que fan és deixar-me una configuració amb les dues pantalles iguals (la resolució de la més gran es rebaixa a la més petita).

També he provat a copiar-hi el xorg.conf que em funcionava a la Hardy, però, en reiniciar les X, em diu que és de sa tia i que no la vol vendre (pantalles d'error sobre les X espatllades; reconfiguració fins tornar al punt de partida).

Cercant i cercant, he arribat a [aquesta pàgina]("http://unidadlocal.com/Dos_monitores_dual-head_con_xrandr_en_Linux") (explicació per a Debian, no per a Ubuntu), on he aconseguit un èxit parcial emprant xrandr: he apagat el monitor secundari, l'he tornat a engegar (però no m'admet la configuració màxima, 1280x768) com a clon del del portàtil.
Quan he volgut fer-los treballar combinats (sempre amb ordres xrandr), m'ha dit que la pantalla total era massa gran; he configurat la Princeton molt petita (800x600) i aquesta volta sí que les he fet anar una com a continuació de l'altra (ara mateix, sota Fluxbox). Però no estic aprofitant la màxima resolució de Princeton :(.



He arribat a la conclusió que la configuració de les ditxoses pantalles ja no té res a veure amb el fitxer /etc/X11/xorg.cong, i que, a més, cada entorn d'escriptori es busca la vida com pot.

Algú té alguna pista?

(M'he deixat alguna cosa per explicar?)

Gràcies per la paciència.

---

### Post by papapep on 2009-02-08
Si no ho has fet ja, provaria a comparar els anteriors xorg.conf que tindràs dins el mateix directori, amb un suffix numèric, amb el que actualment està fent servir, a veure com configura el Xinerama. Igual per aquí trobes pistes. Un altra tema seria si el controlador no és el mateix i té unes funcionalitats diferents, tema que no sé. Però, vaja, jo començaria la caça per aquí. ;-)

---

### Post by papapep on 2009-02-08
Per cert, aquí: 

[http://ubuntuforums.org/showthread.php?p=1773624](http://ubuntuforums.org/showthread.php?p=1773624)

tens un fil que igual et va bé.

---

### Post by giorgiograppa on 2009-02-08
Això em referia quan deia "galimaties", Papapep :D . Bé, no a aquest fil concretament, però sí a d'altres de semblants.


Me l'he llegit fins on m'ha durat la neurona (a partir d'aquí, me l'he mirat, ho confesso). Crec que el resultat final és molt semblant al fitxer que havia "heretat" de la Hardy, amb tot dos monitors ben definits i, fins i tot, amb la referència final activant el Xinerama. Les diferències, si les hi ha, no les podré trobar amb la neurona cansada.

Ups.... Com puc saber si tinc el Xinerama instal·lat i ben instal·lat? aptitude show no em diu res (ni per xinerama ni per Xinerama), ni el whereis ni el man ni res de res.

I, a més, el Xinerama no havia estat substituït pel XRandr?

Buf, em sembla que continuaré mirant-ho un altre dia: avui no puc més.

Gràcies, i ja continuaré un altre dia (que porto des d'ahir amb el tema...).

---

### Post by giorgiograppa on 2009-02-08
No sé ben bé com ho he fet, però sembla que ja ho tinc. Tanmateix, sospito que, en apagar i reiniciar, perdré la configuració i ho hauré de repetir. Bé, de moment, millor és això que una pedrada en un ull.


Cansat de veure que desxifrar llargs paràgrafs tècnics [SIZE="1"]en llatí[/SIZE] en anglès amb la neurona de vacances no és el meu fort, he acabat de mirar les pàgines que tenia obertes i m'he donat de nassos amb un programeta gràfic (sí, gràfic, què passa?) anomenat Grandr (ups! ara no en trobo l'enllaç; bé, ja sabeu: "sudo apt-get install grandr" i "grandr") i dissenyat per a les biblioteques Gtk. He pensat que potser treballaria, també, sota el Xfce i m'hi he posat.

Després d'unes quantes provatures, he descobert que no totes les línies del Princeton on deia "1280x1024@60MHz" havien de ser iguals, perquè una d'elles (l'última, com de costum) m'ha permet veure el monitor en tot l'esplendor de les seves 17" (sí, ja sé, tots teniu un monitor de vint-i-catorze-mil-polsades-i-dos-pams...), treballant en paral·lel al monitor del portàtil.

Després de cantar un *Te Deum*, he anotat tots els passos (és a dir, provar amb totes les configuracions possibles per al Princeton de la gama que en qüestió) i per afegir les línies:
	SubSection "Display"
		Virtual	2314 1034
	EndSubSection
dins de la Section "Screen" del meu brevíssim /etc/X11/xorg.conf . Cosa rara, no m'ha llançat per terra aquest canvi. Tampoc tinc molt clar si és rellevant.

Apa, gràcies per la paciència.

-----

PS: En efecte, la solució és provisional: en reiniciar les X i tornar a entrar al mateix usuari, sempre amb Xfce, m'he tornat a trobar les pantallades clonades. Per sort, ara ha estat molt ràpida la configuració, i ja miraré la forma de fer-la permanent (probablement, experimentant amb l'xorg.conf, com deia en Papapep).

---

### Post by giorgiograppa on 2009-02-08
SOLUCIÓ DEFINITIVA
==================

(O gairebé...)

Després d'haver aconseguit, amb Grandr, configurar els dos monitors sota Xfce, he vist que podia aconseguir informació detallada d'aquella configuració amb [FONT="Courier New"]xrandr -q[/FONT] :

[FONT="Courier New"]professor@asterix:~$ xrandr -q
Screen 0: minimum 320 x 200, current 2304 x 1024, maximum 2314 x 1034
VGA connected 1280x1024+1024+0 (normal left inverted right x axis y axis) 384mm x 306mm
   1280x1024      56.3 +   60.0*    60.0
   1600x1024      60.2
   1440x900       59.9
   1280x960       60.0     60.0
   1360x768       59.8
   1152x864       75.0     75.0     75.0     70.0     60.0
   1024x768       75.1     75.0     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        75.0     72.8     72.8     75.0     66.7     60.0     59.9
   720x400        70.1
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 300mm x 220mm
   1024x768       60.0*+
   800x600        60.3
   640x480        59.9
professor@asterix:~$
[/FONT]

Mirant on estaven els asteriscos (les configuracions actives) i llegint el man del xrandr, he arribat a la conclusió que l'ordre que jo necessitava (i que havia executat a través de la interfície gràfica) era:

[FONT="Courier New"]xrandr --output VGA --mode 1280x1024 --rate 60 --right-of LVDS[/FONT]

Com que l'Xfce també es tornava una mica boig en executar-la, he creat l'script [FONT="Courier New"]dospant.sh[/FONT] amb un parell d'ordres més:

[FONT="Courier New"]
#!/bin/bash
# dospant.sh
# Coordinar les dues pantalles 15 i 17 des de Xfce

xrandr --output VGA --mode 1280x1024 --rate 60 --right-of LVDS
xfce-setting-show
xfce4-panel[/FONT]


Després, l'he afegit a les aplicacions que s'executen en entrar a l'Xfce i... *voilà*!

D'acord, d'acord, ja sé que no és molt elegant... Però, almenys, funciona! (o gairebé)

---

### Post by giorgiograppa on 2009-02-09
He he he he! Funciona! Funciona! L'script funciona!

I em deixa l'Xfce a punt per treballar.

Potser també funcionaria amb algun gestor de finestres; ho hauré de provar.

:D

---

### Post by papapep on 2009-02-09
Dae, egreggio dottore! ti é un crack!!!! :-D

---

### Post by giorgiograppa on 2009-02-09
Gràcies, Papapep! Venint de tu, qualsevol *eulogi* és com un medalla al mèrit pingüinil :guitar:

La llàstima és que no em funciona amb tots els usuaris: serà qüestió de continuar investigant.

---

### Post by papapep on 2009-02-09
Crec que ja has arribat a una de les classes importants a un sistema Unix-Gnu/Linux, els scripts d'arrencada i aturada:

```
man update-rc.d
```

;-)

---

### Post by papapep on 2009-02-09
Per cert, aquí:

[http://cv.uoc.es/cdocent/F6X1E4P8EKE7HHA007BG.pdf](http://cv.uoc.es/cdocent/F6X1E4P8EKE7HHA007BG.pdf)

pots (podeu) trobar un bon document que parla, entre d'altres coses, de l'arrencada del sistema, els seus nivells i els scripts que s'executen.

Aprofito per recomanar-vos la documentació que va alliberar l'UOC del seu Màster de programari lliure, del qual forma part l'anterior document. És prou bona, amplia i, increïble, en català! :-D:

[http://ocw.uoc.edu/informatica-tecnologia-i-multimedia/](http://ocw.uoc.edu/informatica-tecnologia-i-multimedia/)

---

### Post by giorgiograppa on 2009-02-09
Ah! Sembla que tornen a funcionar els fòrums!

Gràcies, Papapep, m'ho miraré.

I, sí, el material del màster aquell és formidable. I en català!

---

