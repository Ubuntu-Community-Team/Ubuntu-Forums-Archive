---
title: "Crear un &quot;xorg.conf&quot; per al nou monitor"
date: 2010-08-09
forum: Catalan Team
---

### Post by pageset on 2010-08-09
Bones,
 aquesta es la primera vegada que formulo una pregunta en un fòrum, 
 sempre havia aconseguit resoldre els dubtes només llegint els existents, 
 aquest cop crec que necessito una mica d'ajuda activa...

Aviat farà un any que remeno el gnu-linux, i de moment nomes he provat l'ubuntu.

doncs el tema es que em van passar un monitor de tub 21" 
[www.monitorcenter.hu/108035_belinea.pdf]("http://www.monitorcenter.hu/108035_belinea.pdf")

al connectar-lo i encendre l'ordinador m'emociono, arrenca be, passa  el grub, tot be, i després de la pantalla negre amb l'icona de l'ubuntu  al centre,,,
apareix una[SIZE=4] pantalla gris amb barres blaves[/SIZE] i res mes , aquí es queda penjat fins que l'apago.

el cas es que el monitor funciona, si l'encenc amb la partició de winXP, no dona problemes.

encara mes rebuscat es que si l'encenc i al grub trio la segona opció (recovery mode),  puc iniciar el mode consola despres de logejar-me, i tot seguit iniciar les x amb "startx"cosa que funciona i puc accedir a l'escriptori. (1)

També el fai funcionar si encenc la PC amb el monitor apagat i després d'un minut l'encenc. (2)
i també funciona si l'arranco amb la pantalla antiga i després canvio el cable. (3)

cap d'aquestes maneres es gaire còmoda....

una cosa que em preocupa es que si intento arrancar-lo des del CDlive també apareixen les barres blaves...:confused:
(tinc  ganes de provar d'instal·lar l'ubuntu de nou en un altre disc dur amb  la mateixa tarja gràfica i el monitor nou), (a veure que passa)...


Buscant, buscant, he vist que el problema pot venir del servidor X.
i he intentat buscat l'arxiu " /etc/X11/xorg.conf " però no hi era, 
després he buscat informació per crear-lo de nou, però aquí es on m'he empantanegat.


........................................
Doncs crec que aquesta hauria de ser  la meva pregunta, 
[SIZE=4]Com puc crear un xorg.conf adequat per a la meva pantalla?[/SIZE]
........................................


a partir d'aquí afegeixo alguna informació que m'he anat trobant pel camí de la resolució, (espero que sigui útil...)

 la tarja gràfica es una: Savage 4 16MB

$ lspci | grep VGA
 VGA compatible controller: nVidia co NV6 [Vanta/Vanta LT] (rev 15)

 

al xat em van preguntar a quina resolució s'inicia l'entorn gràfic, 

si encenc la PC amb el monitor apagat.(2)  l'xrandr em retorna això: 

$  xrandr
   Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
   default connected 800x600+0+0 0mm x 0mm
      800x600        60.0*    56.0  
      640x480        60.0  
       400x300        60.0     56.0  
      320x240        60.0  

si l'encenc amb l'antic monitor connectat, i després el canvio,(3)
 l'xrandr em retorna això:
$  xrandr
   Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
    default connected 1024x768+0+0 0mm x 0mm
      1024x768       60.0*    43.0  
       800x600        75.0     72.0     60.0     56.0  
       640x480        75.0     73.0     60.0  
       720x400        70.0  
       680x384        60.0  
       640x350        70.0  
       512x384        60.0  
       400x300        75.0     72.0     60.0     56.0  
       320x240        75.0     73.0     60.0  



i encara si l'encenc amb el monitor connectat, però al grub escolleixo l'opció 2 (recovery mode )
i tot seguit, després de loguejar-me, executo [SIZE=6]startx[/SIZE]. cosa que inicia l'entorn gràfic sense problemes. (1)
 en aquest cas l'xrandr em retorna:

$ xrandr
Screen 0: minimum 320 x 175, current 1360 x 768, maximum 1920 x 1440
default connected 1360x768+0+0 0mm x 0mm
   1920x1440      75.0     60.0  
   1856x1392      75.0     60.0  
    1792x1344      75.0     60.0  
   1600x1200      85.0     75.0     70.0     65.0     60.0  
   1680x1050      85.0     75.0     70.0     60.0  
   1400x1050      85.0     75.0     70.0     60.0  
   1280x1024      85.0     75.0     60.0  
    1440x900       60.0  
   1280x960       85.0     60.0  
   1360x768       60.0* 
   1152x864       75.0    100.0     85.0     70.0     60.0  
   1024x768       85.0     75.0     70.0     60.0     87.0  
    960x720        75.0     60.0  
   928x696        75.0     60.0  
   896x672        75.0     60.0  
   832x624        75.0  
   800x600        85.0     75.0     72.0     70.0     65.0     60.0     56.0  
    840x525        85.0     75.0     70.0     60.0  
   700x525        85.0     75.0     70.0     60.0  
   640x512        85.0     75.0     60.0  
   720x450        60.0  
   640x480        85.0     75.0     73.0     60.0  
    720x400        70.0     85.0  
   680x384        60.0  
   640x400        85.0  
   576x432       100.0     85.0     75.0     70.0     60.0  
   640x350        85.0  
   512x384        85.0     75.0     70.0     60.0     87.0  
    416x312        75.0  
   400x300        85.0     75.0     72.0     60.0     56.0  
   320x240        85.0     75.0     73.0     60.0  
   360x200        85.0  
   320x200        85.0  
   320x175        85.0  
 
el mes practic es la primera opció (2) però em quedo amb només 800x600
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Moltes gracies anticipades,
 estic segur que entre tots superarem aquest petit sotrac,,,

---

### Post by PatrickVogeli on 2010-08-10
Perdona, no havia llegit be el post...

salut

---

### Post by epileg on 2010-08-10
Bones,

Que no tinguis el fitxer /etc/X11/xorg.conf és del tot normal ja que la detecció de maquinari es fa automàticament. Però en cas de que aquesta detecció no funcionin correctament, com és el teu cas, es pot crear aquest fitxer per a configurar l'entorn gràfic manualment.

Per a crear el fitxer /etc/X11/xorg.conf entra a l'entorn gràfic com ho fas ara i fes això des d'un terminal:

```
$ sudo Xorg -configure
```

Això et crearà un fitxer base

en el meu sistema em crea aquest:

```
Section	"Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section	"Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

En el teu sistema canviarà lleugerament.

Ara afegeix això al final de la secció «Screen».
```
	SubSection "Display"
		Depth	24
		Modes	"1920x1440" "1600x1280" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection

```
Aquestes son totes les resolucions teòricament suportades pel teu monitor.

En el meu ordinador l'«xorg.conf» quedaria així:

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1920x1440" "1600x1280" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"fglrx"
EndSection

```

No facis «copia i enganxa» per a tot el fitxer ja que no et funcionaria. Fes-ho només per a la subsecció «Display».

Desa'l i reinicia l'ordinador.

Si al reiniciar et funciona, perfecte. Si no et funciona, reinicia i entra en mode text i edita el fitxer amb:
```
nano /etc/X11/xorg.conf
```
Ves a la subsecció «Display» i a la línia «Modes» esborra la primera entrada, en aquest cas «1920x1440». Desa el fitxer i reinicia.

Repeteix aquesta operació fins que et funcioni, i si no, torna a escriure per aquí.

Salut,

---

### Post by pageset on 2010-08-26
bones, 

En primer lloc, agraeixo l'atenció rebuda i perdoneu-me per trigar tant en donar senyals de vida...

tot seguit, mans a la feina,,,

[SIZE=3]**la recepta del Dr. epileg ha funcionat. **[/SIZE]

el cas es que vaig fer com em deies, però no funcionava...
i avui cansat de proves i proves, em decidia a tornar a demanar ajuda, i m'he donat compte d'un petit detall,, 
en alguna d'aquestes, borrant modes no suportats, em vaig menjar la paraula "Modes" del principi,,
resultat,
 l'ubuntu arrencava (desprès de preguntar-ho 2 cops) en mode low-grafics(1024x687)
 
com et dic, avui, desprès de restituir la paraula "Modes", guardar i reiniciar, 

arrenca directe en el mode desitjat, 1360x768 60Hz.

Moltes gracies   [SOLVED]

---

