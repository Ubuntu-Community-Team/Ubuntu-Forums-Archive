---
title: "Conectar portàtil al televisor"
date: 2011-04-26
forum: Catalan Team
---

### Post by Funk'u on 2011-04-26
Hola a tot-hom!, doncs resulta que intento connectar el portàtil al televisor i després de seleccionar si "[COLOR=Sienna]TwinView[/COLOR]" o "[COLOR=Sienna]Separate[/COLOR]", al clicar sobre "[COLOR=Sienna]Apply[/COLOR]" em diu que:

"[COLOR=Sienna]The current settings cannot be completely applied due to one or more of the following rasons:
[/COLOR] 
[LIST]
[*][COLOR=Sienna]The location of an X screen has changed.[/COLOR]
[*][COLOR=Sienna]The location type of an X screen has changed.[/COLOR]
[*][COLOR=Sienna]The color depth of an X screen has changed.[/COLOR]
[*][COLOR=Sienna]An X screen has been added or removed.[/COLOR]
[*][COLOR=Sienna]Xinerama is being enabled/disabled.[/COLOR]
[/LIST]
[COLOR=Sienna]For all the requested setting to take effect, you must save the configuration to the X config file and restart the X server[/COLOR]."

Un altre error que m'ha sortit tot intentant-ho; "[COLOR=Sienna]Failed to parse existing X config file '/etc/X11/xorg.conf'![/COLOR]"

I un altre:
"[COLOR=Sienna]Your current changes to the X server display configuration may no longer be applied due to changes made to the running X server.

You may either reload the current X server settings and lose any configuration setup in this page, or select "Cancel" and save your changes to the X configuration file (requires restarting X to take effect.)[/COLOR] [COLOR=Sienna]

If you select "Cancel", you will only be allowed to apply settings once you have reset the configuration.[/COLOR] "

He esborrat el controlador, he reiniciat l'ordinador i l'he tornat a instal·lar. Val a dir que tinc el fitxer xorg.conf. El controlador em va molt bé, funcionen els efectes 3d, bona calitat d'matge,etc... , l'únic problema és aquest de la connexió al tv. Amb el netbook no hi tinc problema, ossigui que no es el tv.

Sistema [COLOR=Sienna]Ubuntu 10.10 64bit[/COLOR]
Tarja [COLOR=Sienna]nVidia GF GT 320M 1GB[/COLOR]

Potser algú amb nVidia em pot posar el seu xorg.conf per comparar?

Moltes gràcies!

Com es fa per posar text o codi a una finestreta amb la barra lateral perquè es pugui veure directament sense haver de descarregar l'adjunt?

---

### Post by wgarcia on 2011-04-27
Pel que expliques sembla que utilitzes el controlador propietari de la targeta gràfica, i no el lliure "nouveau". 

Possiblement no et deixa desar el fitxer xorg.conf des de l'eina de configuració de NVIDIA perquè aquest fitxer està protegit. Pots provar de córrer l'eina de configuració amb "sudo" des d'una terminal:

sudo nvidia-settings

configurar els monitors (en el meu surt a Xserver Display Configuration) i aquí tens una opció de desar l'xorg.conf.

---

### Post by Funk'u on 2011-04-27
Tant sense "sudo" com amb "sudo nvidia-settings" em dona el mateix error, i si intento guardar em diu "[COLOR=Sienna]Failed to parse existing X config file '/etc/X11/xorg.conf'![/COLOR]".

Una pista que no havia comentat; al terminal em surt aquest error, que abans de potinejar comento:

[COLOR=Sienna]joma@joadma:~$ sudo nvidia-settings
[sudo] password for joma: 

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".
[/COLOR]

La veritat és que el controlador va molt bé, hi ha bona calitat d'imatge i bona acceleració, no sé si el "nouveau" que comentes va igual de bé o més, el cas és que si desconnecto el controlador si que és veu per la tele, amb els controladors per defecte, però clar em queda una configuració molt dolenta i sense acceleració, m'interessava precisament poder aprofitar la tarja.

He posat la configuració original que tenia al xorg.conf.backup, però no em funciona, el curiós del cas és que el meu oncle amb la mateixa configuració li funciona perfectament, tot i que crec que utilitza el Ubuntu 10.04 i no el 10.10:

[COLOR=Sienna]Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"[/COLOR] [COLOR=Sienna]
    Load    "glx"
EndSection

Section "Device"[/COLOR] [COLOR=Sienna]
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
[/COLOR] 

Tant sols hi ha això, vaig provant alternatives.


Salut!

---

### Post by Funk'u on 2011-04-29
Per casualitat algú utilitza l'Ubuntu 10.10 amb tarja nVidia i li va bé la conexió amb el televisor?, és per veure si podem comparar el xorg.conf, o algún arxiu referent al tema.

He provat de connectar-ho tant en RGB com en HDMI, i em dona els mateixos resultats.




Moltes gràcies, salut!

---

### Post by snoopo71 on 2011-05-03
Bones, aviam, pel que crec no et deixa guardar el xorg.conf per una qüestió de permisos, però és igual, hi ha una solució!!

-Obre el "nvidia-settings"
-Fes els canvis que creguis necessaris i clica a "save x to configuration file".
-Et sortirà l'error en qüestió.
-Clica a "show preview", t'apareixerà la configuració que vols.
-Copia.
-Al terminal: "sudo gedit /etc/X11/xorg.conf" .
-Enganxa el que has copiat i desa.
-Reinicia les X o surt i torna a entrar.

Ja ho tens.

Aviam si t'ho soluciona!:D

---

### Post by Funk'u on 2011-05-04
Bones snoopo71!, gràcies per a contestar, provant el que m'has dit el primer cop em diu:

[COLOR=Sienna]Your current changes to the X server display configuration may no longer be applied due to changes made to the running X server.

You may either reload the current X server settings and lose any configuration setup in this page, or select "Cancel" and save your changes to the X configuration file (requires restarting X to take effect.)

If you select "Cancel", you will only be allowed to apply settings once you have reset the configuration.
[/COLOR]
Llavors sembla que m'ho ha deixat fer, sembla perquè no n'hi ha hagut prou i ha seguit sense funcionar, llavors al nvidia-settings he volgut posar separate X screen i al aplicar em diu:

[COLOR=Sienna]Failed to set MetaMode (1) 'DFP-0: nvidia-auto-select @1366x768 +0+0, DFP-1: nvidia-auto-select @1920x1080 +1366+0' (Mode 3286x1080, id: 51) on X screen 0.[/COLOR]

La resolució de pantalles estava en mode automàtic, he provat d'ajustar[COLOR=Black] la tele al monitor[/COLOR]:

[COLOR=Sienna]Failed to set MetaMode (1) 'DFP-0: nvidia-auto-select @1366x768 +0+0, DFP-1: 1360x768 @1360x768 +1366+0' (Mode 2726x768, id: 50) on X screen 0.[/COLOR]

I per últim ajustar als mateixos valors:

[COLOR=Sienna]Failed to set MetaMode (1) 'DFP-0: 1024x768 @1024x768 +0+0, DFP-1: 1024x768 @1024x768 +1024+0' (Mode 2048x768, id: 51) on X screen 0.

[COLOR=Black]Ara bé, tot s'ha de dir, ara ja envia senyal al televisor, però sembla una pantalla apart, només el punter hi va, no hi pots dur una finestra oberta per exemple, hi ha la imatge de fons i s'obre el menú secundari clicant amb el ratolí o touchpad, peró nio pots fer com una extensió de la pantalla, ni que surti la mateixa.

Gràcies per l'atenció rebuda, seguiré provant. Salut! ;-)
[/COLOR][/COLOR]

---

### Post by snoopo71 on 2011-05-05
Aviam, com connectes a la tele per hdmi o vga?
La tele i la pantalla tenen la mateixa resolució(1080p)?
Com tens el xinerama?
Envia una copia del teu xorg i una captura de pantalla de la pestanya "X server display configuration", si us plau.

---

### Post by Funk'u on 2011-05-06
Hola snoopo71!!,

A veure, ho he provat tant amb hdmi com en vga amb exactament els mateixos resultats, la resolució em surt aixó:

```
joma@joadma:~$ xrandr -q | grep -w Screen
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1366 x 768, maximum 1366 x 768

```

El Xinerama tant activat com desactivat també em dona el mateix resultat.

El xorg actual l'he posat com estava per defecte:

```
joma@joadma:~$ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

I el del "X server display configuration" l'he guardat com a "backup"

```
joma@joadma:~$ cat /etc/X11/xorg.conf.backup 
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "LG Electronics LG TV"
    HorizSync       30.0 - 83.0
    VertRefresh     58.0 - 62.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 320M"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 320M"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-1: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```


Gràcies per l'atenció snoopo71!! :smile:

---

### Post by roquet on 2011-05-08
és estrany, perquè les teles noves amb entrada vga no donen problemes, almenys a mi. Prova de mirar si la versió live et va, així com anar amb els drivers no-privatius, jo vaig tenir problemes amb els drivers privatius amb una sortida s-video fa uns anys.

---

### Post by albert-I on 2011-06-22
Jo ho trobo una mica estrany, ja que connecto el meu netbook de 10" sense problemes amb VGA amb una televisió Pannasonic de 42 i es veu molt be. I no tinc més que triar el canal d'auxiliars de la TV

---

