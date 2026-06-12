---
title: "Com canviar la resolució de pantalla?"
date: 2007-05-26
forum: Catalan Team
---

### Post by albello on 2007-05-26
Hola,

A preferències>resolució de pantalla només apareixen resolucions fins 1024x768, i la que jo vull és de 1280x1024. La meva gràfica és una ATI X600.
He instal·lat els drivers ("sudo apt-get install xorg-driver-fglrx") i després he provat d'editar la nova resolució manualment a l'arxiu "/etc/X11/xorg.conf", que és el que he llegit que s'havia de fer, però no puc desar els canvis perquè "No tinc el permís necessari"...

Algú em pot donar un cop de mà?

Gràcies.

---

### Post by lluisanunez on 2007-05-26
obre un terminal:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.vell
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by papapep on 2007-05-26
Al fitxer /etc/X11/xorg.conf tens definides les resolucions de pantalla que vols tenir per als diferents nivells de profunditat. Hauries de tenir alguna cosa semblant, entre moltes altres, a això:

```
              
Section "Screen"
        Identifier      "Default Screen"
        Device          "Targeta de video generica"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

Si no et surt el mode  "1280x1024", afegeix-lo i, en principi, ja t'hauria de sortir al selector de resolucions un cop hagis reiniciat el servidor X (ctrl+alt+backspace).

---

### Post by albello on 2007-05-26
He fet el que m'heu dit i ara l'arxiu /etc/X11/xorg.conf té la resolució que busque:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480" "256x256"
	EndSubSection
EndSection

```

Però al selector de resolució de pantalla segueixen apareguent només les tres resolucions de sempre: 1024x768, 800x600 i 640x480. No sé quina tecla és el blackspace per a reiniciar el serivdor X, així que he reiniciat l'ordinador. Supose que no serà eixe el problema.

Gràcies per les respostes.

---

### Post by JosanRF on 2007-05-26
Hola a tothom,
només un comentari: la tecla "backspace" és la de borrar (a sobre del INTRO).
És el meu primer post, m'acabo de registrar fa uns minuts! :p
Espero utilitzar-ho força.
Salut!:)

---

### Post by lluisanunez on 2007-05-26
Sí que ho és, però per parlar d'un altre tema havies d'obrir un nou fil de conversa. D'això que has fet se'n diu "segrestar un fil".

---

### Post by albello on 2007-05-26
Ara que ja sé quina és la tecla blackspace puc dir-vos que no era eixe el problema, ja que el selector de resolucions de pantalla continua igual (només mostra 1024x768, 800x600 i 640x480) després d'haver modificat l'arxiu /etc/X11/xorg.conf i reiniciat el servidor X.

A JosanRF: Enhorabona. Aviat dominarem el món.
A Lluisa: Qui dius que ha segrestat el fil?

Gràcies per l'ajuda.

---

### Post by lluisanunez on 2007-05-26
A veure, 
aquesta conversa anava de com canviar la resolució de pantalla, ve un altre i pregunta com si res que quina és la tecla Backspace, ara vens tu i et penses que la tecla Backspace és per a solventar el teu problema de pantalla. 
Li podem dir segrestar el fil, o si voleu El Joc dels Disbarats :guitar:

---

### Post by Cows on 2007-05-26
Ustedes estan ablando espanol? porque yo lo puedo entender .. ( no tengo los accentos installados en mi compu ). tambien si no es espanol este lenguage se parese como espanol y francais mixclado.

---

### Post by lluisanunez on 2007-05-26
:D

Hello Cows
Welcome to Catalan Team Forum / Benvingut al Fòrum del Catalan Team
This is Catalan (the language of Catalonia) and yes, like French and Spanish, it comes from Latin 
[http://en.wikipedia.org/wiki/Catalan_language]("http://en.wikipedia.org/wiki/Catalan_language")

---

### Post by albello on 2007-05-26
Per resoldre el meu problema m'han dit, entre d'altres coses, que havia de fer crl+alt+blackspace, i JO he dit que com no sabia quina era eixa tecla el que he fet és reiniciar l'ordinador. JosanRF m'ha comentat quina tecla era, i jo he contestat que després de fer la combinació, el problema seguia igual (lògicament, ja que ja havia reiniciat l'ordinador). PUNT. Ningú ha preguntat quina és la tecla Blackspace ni jo m'he pensat que prement-la resoldria els meus problemes amb la resolució. 
Potser hauries de llegir bé els comentaris abans de parlar de segrestos i disbarats...

I continuant amb el meu dubte, a preferències>resolució de pantalla continua sense aparéixer la resolució de 1280x1024, a pesar d'haver-la introduit a l'arxiu "/etc/X11/xorg.conf", on abans no estava. Algú sap què passa?

Gràcies.

---

### Post by lluisanunez on 2007-05-26
Disculpa. Això és el que havia entès

---

### Post by patrickfromspain on 2007-05-26
hauries de probar a posar les frecuencies de refresc horitzontar i vertical del teu monitor a l'xorg.conf. Ara mateix no se les comandes, igual les pots buscar.

---

### Post by kukat on 2007-05-26
Perdoneu que no aporte res, simplement m'ha fet gracia el que deia que la nostra llengua era pareguda al espanyol i el francés i no s'havia quina era!! jajajaj. Es un poc fort que als temps que corren un espanyol no conega la nostra llengua....:( Bo!! i a veure si et solucionen el problema. Perdó per no poder aportar res.

---

### Post by CarlesOriol on 2007-05-26
Quin poti poti de fil... sols faltava el guiri preguntant on ha aterrat!!

---

### Post by patrickfromspain on 2007-05-26
> **kukat said:**
> Perdoneu que no aporte res, simplement m'ha fet gracia el que deia que la nostra llengua era pareguda al espanyol i el francés i no s'havia quina era!! jajajaj. Es un poc fort que als temps que corren un espanyol no conega la nostra llengua....:( Bo!! i a veure si et solucionen el problema. Perdó per no poder aportar res.
be, alguns ens fara gracia que escriguis s'havia en ves de sabia ;) i ho mires be, veuras que: Location: Brooklyn, NY

salut

---

### Post by kukat on 2007-05-27
Les meves disculpes... no havia vist que el xic era de Brooklyn!! Saluts!! jejejeje:D

---

### Post by albello on 2007-05-27
A la pantalla de selecció de resolució també hi ha la velocitat de refresc, i només està la de 60 Hz. Esta velocitat es canvia editant a l'arxiu xorg.conf. Exemple:
"1280x1024_75"
"1024x768_60"
etc.
He provat a posar una velocitat de 75 Hz. a la resolució de 1280x1024 i a la de 1024x768, i el que ha passat és que després de reiniciar el servidor X (ja sabeu, amb el blackspace i tal) és que la resolució de 1280x1024 ha continuat sense aparéixer i la de 1024x768 m'ha desaparegut...
¿Per què he fet el que he fet i quines conclusions n'he tret? Ni idea, però açò de la resolució de pantalla comença a posar-se massa abstracte.

Ale me'n vaig a votar.

---

### Post by patrickfromspain on 2007-05-27
El que hauries de fer es mirar la documentacio del teu monitor, i mirar quins valors de refresc horitzontal i vertical té. LLavors, en una consola: sudo dpkg-reconfigure xserver-xorg i vas responent el que et pregunta; hi ha un moment que podras posar les resolucions i un altre moment en pots posar els valors de refresc del monitor.

---

### Post by orestesmas on 2007-05-27
Ara seré _molt_ dolent: això també és segrestar un fil :-D

---

### Post by orestesmas on 2007-05-27
No acabo de tenir clar el teu entorn: Què utilitzes, Gnome o KDE? En KDE hi ha una utilitat amagadeta però a la qual s'hi pot accedir a través d'un terminal. L'utilitat es diu "krandrtray", i quan la crides posa una icona a la barra de tasques que et permet canviar la resolució de pantalla a qualsevol dels valors llistats al fitxer xorg.conf i, naturalment, que suporti la tarja.

Només en 2 ocasions m'he trobat que no puc triar totes les resolucions suportades:

1) Si connecto un monitor extern (en el meu cas un retroprojector) que no arriba a la resolució de la pantalla principal. En aquest cas, després de reiniciar les X no puc activar en el PC cap resolució per damunt de les que suporta el projector.

2) Si, per algun motiu, el fitxer xorg.conf està malament i conté resolucions més grans que les que la tarja pot suportar.

A més de tot això, t'han comentat que hauries de cercar els paràmetres del teu monitor (freqüències de refresc, etc.) i posar-les al fitxer xorg.conf. Certament, com dius, això és una mica (o molt) abstracte i, per acabar-ho d'adobar, no té la mateixa importància en un monitor "normal" que en un LCD/TFT.

A vegades el programa "xvidtune" (accessible per l'inia d'ordres) ajuda a batallar amb els casos recalcitrants, però si bé no passa res per executar-la i mirar una mica els valors que dóna, modificar aquests valors s'ha de fer amb prudència, especialment si tenim un monitor de raigs catòdics (la teoria diu que una freqüència de refresc poc adient podria espatllar el monitor)

---

### Post by albello on 2007-05-28
Quin desastre. M'he carregat el sistema. Al xorg.conf, a la secció "Screen", on posava "Generic Monitor" he posat el nom del meu monitor, i de sobte ha pegat un pet i ara em diu que no es pot iniciar el Servidor X perquè no està ben configurat.
Diu, entre d'altres perles: "Data incomplete in file /etc/X11/xorg.conf" o "Fatal server error: no screen found". I apareix una consola tipus la que utilitze normalment, però en blanc i negre. Intente fer "gksudo gedit /etc/X11/xorg.conf", però diu que no es pot mostrar.
Què puc fer? N'hi ha alguna combinació màgica que ho puga restaurar? És l'hora de tirar-me a la beguda?

---

### Post by CarlesOriol on 2007-05-28
sudo dpkg-reconfigure xserver-xorg

(comptador: 29.438.739 )

---

### Post by orestesmas on 2007-05-28
Bé, no t'espantis. a tots ens ha passat alguna vegada això. Cal que siguis conscient que NO t'has "carregat el sistema", perquè en GNU/Linux l'entorn gràfic és una aplicació més del sistema, no és en absolut una part imprescindible d'ell, com passa en windows.

Simplement el sistema gràfic no pot arrencar, per algun motiu o altre. Per tant, et deixa una consola de text perquè facis coses (bé, més d'una en realitat; pots accedir a les altres amb Ctrl+Alt+2, Ctrl+Alt+3, etc...).

Bàsicament has d'entrar com a usuari a la consola i, un cop registrat, has de cridar un programa per reconfigurar les X. és el que diu el carles més avall, tot i que de manera poc explícita per un que comença.
L'ordre és "sudo dpkg-reconfigure xserver-xorg". La majoria de les preguntes les pots passar prement "intro", acceptant els valors per omissió.

Un cop reconfigurat, mira de "ressucitar" les X fent:

"sudo /etc/init.d/gdm restart"

Si no funcionen, digues quins missatges d'error et surten per pantalla o envia el resultat d'executar l'ordre següent (que obté els errors i els "warnings" del fitxer de log):

grep "(WW)\|(EE)" /var/log/Xorg.0.log

Apa, a veure si hi ha sort

---

### Post by albello on 2007-05-31
Uff! Tot ha tornat a la normalitat. Gràcies!

Us done les últimes noves. Literalment. Primer de tot, no tinc ni idea de si utilitze Gnome o KDE.  No sabia que existiren diversos "entorns" dins de l'Ubuntu. He provat amb el Krandrtray que em dius, però primer em diu que no el tinc instal·lat i que per fer-ho he de fer "sudo apt-get install kcontrol", i quan ho faig em diu que eixe paquet no té versió disponible però que no patisca perquè està el "kdebase-bin kdelibs4c2a" que el substitueix, però una vegada instal·lat l'intente fer anar i m'ix "command not found"... En fi, tot un poc com sempre.

Després de reconfigurar les X la resolució torna a estar a 1024x768, a pesar d'haver marcat a la reconfiguració la resolució de 1280x1024, i a més la freqüència de refresc ha passat de 60Hz (que és l'òptim del monitor, ho he mirat) a 76Hz. Sense sentit. 

Per altra banda, l'arxiu xorg.conf torna a no tindre la resolució de 1280x1024. L'edite de nou introduint la nova resolució i reinicie el servidor X, com havia fet tantes altres vegades... Quasi plore de l'alegria quan a la pantalla de registre he vist que tenia la resolució de 1280x1024 però, mi gozo en un pozo, una vegada introduiexes usuari i contrassenya a la pantalla apareixen amb una espècie de ratlles en diagonal i no es veu res. A reconfigurar de nou i  tot com sempre.

"Si alguna cosa he aprendido repetidas veces en la vida es a reconocer cuándo he sido derrotado".
Crec que després d'aquest warning que m'ha donat l'Ubuntu el que vaig a fer és deixar el temeta aparcat unes setmanetes i quan el conega un poc més doncs ja tornar amb redoblades forces.

Gràcies per l'ajuda.

---

