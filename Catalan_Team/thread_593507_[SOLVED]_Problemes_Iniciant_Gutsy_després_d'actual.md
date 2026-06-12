---
title: "[SOLVED] Problemes Iniciant Gutsy després d'actualitzar"
date: 2007-10-27
forum: Catalan Team
---

### Post by guillemsola on 2007-10-27
Obro aques post especificament per un problema que tinc a l'arrencar el Gutsy. 

Després d'actualitzar-lo desde la 7.04 ja no arrenca gairebé mai. Es queda penjat més o menys on diu "Iniciant Gnome" això que hi ha cops que arriva a posar OK. Total que d'aquí no passo, però vaig probant i probant i algun cop arrenca bé. És dir no em passa sempre.

He probat a fer un dpkg-reconfigure xserver-xorg per allò de treure els drivers de la nvidia però sembla que passa del tema.

salut!

---

### Post by CarlesOriol on 2007-10-27
abans o despres del so?

---

### Post by guillemsola on 2007-10-27
Tot m'ha passat a l'actualitzar però aquest problema és mes greu perquè el pc s'engega quant ell vol (que no és gaire sovint). La resta de vegades es sol queda penjat i no sempre al mateix punt. Algún cop s'ha reiniciat sol durant l'arrencada. He pensat doncs que son problemes diferents i es mereixen posts separats.

A proba d'errors s'acostuma a engegar bé encara que fins hi tot un cop es va quedar sense engegar.

Allò que deieu de tenir la partició home a part per poder instalar desde 0, podria fer-ho ara? és a dir crear una partició nova i copiar el contingut de la home i després actualitzar? És que aquest error em fa molt difícil de fer servir l'ubuntu

salut!

---

### Post by guillemsola on 2007-10-28
Provant, provant he aconseguit que ara el Gutsy arrenqui molt més sovint. Diguem que si abans arrencaba 1 cop de cada 5 ara no arrenca 1 cop de cada 5. No és perfecte però ja és quelcom.

El que he fet ha estat ha estat canviar el tipus de monitor a un de plug'n'play. Quant es penjava em vaig adonar que feia aquell so que fa un monitor de CRT quant canvia de mode. El fet és que no canviava de mode, es quedava en mode texte i penjat.

Crec que només puc fer arribar el monitor a 1024x768 a 50Hz. Tot i que algun cop 'ubuntu l'ha posat a 60Hz penso que pot ser per això que es pengi.

Tot i així hi ha cops en que encara es queda penjat. Potser si pogués dir-li que només fes servir aquest mode aleshores ja no es penjaria.

No se de que deu ser culpa que no ho detecti bé, La meva tarja és una nvidia GeForce2 i el montior un CRT que ja té un temps. No és dels que aguanti taxes de refresc molt altes però tampoc havia tingut tants problemes amb ell.

Salut!

---

### Post by papapep on 2007-10-28
Podries fer un cop d'ull al fitxer /etc/usplash.conf a veure quina resolució té definida.

També podries provar fent el següent. Fes una còpia de seguretat del fitxer /boot/grub/menu.lst:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Un cop assegurada la vida ;-) edita'l:

```
sudo nano /boot/grub/menu.lst
```

Busca (amb Ctrl+W) la línia que comença per "# defoptions=quiet splash", Un cop l'hagis trobat, afegeix-hi una d'aquestes opcions, en funció de quina resolució vols al inici del sistema:

vga=785  Per tenir 640x480
vga=788 Per tenir 800x600
vga=791 Per tenir 1024x768
vga=794 Per tenir 1280x1024 

Amb el qual, suposant que vols 1024x768, la línia quedarà de la segúent manera:

```
# defoptions=quiet splash vga=791
```

Un cop estiguis, prement Ctrl+x desaràs els canvis.

Ara cal actualitzar el grub per a que agafi les modificacions d'aquí endavant:

```
sudo update-grub
```

I ara prova a reiniciar a veure què fa.

---

### Post by guillemsola on 2007-10-28
Gràcies per la resposta XD

Això és el que diu al meu uspash.conf

> # Usplash configuration file
xres=1024
yres=768


He provat el que m'has amb 800x600 i 1024x768. Suposo que aquest canvi al grub deu ser per canviar la resolució de la barra de càrrega. El que passa és que quant ho he fet, al premer ALT+F1 no podia veure els missatges d'arrencada.

De totes formes fins ara la barra de càrrega no m'ha donat problemes (això penso) i com ja he dit acostumo a fer ALT+F1, sobretot ara que es penjava a l'arrencada.

De moment la "solució" que he trobat ha estat canviar el tipus de monitor i sembla que ara quasi sempre "s'enten" amb el pc a l'hora d'escollir la frequencia amb la resolució i arrenco satisfactoriament.

El que penso que podria ser interessant seria "baixar" la resolució de la pantalla de log al gnome. He mira't i no veig que ho hagi una entrada específica al xorg.conf. No se si així seria menys proper a fallar.

Salut!

---

### Post by papapep on 2007-10-28
Tot el rotllo que t'he deixat anar abans era per posar la resolució que tu vulguis a l'arrencada. 
Prova posant-la a 800x600 (vga=788) a veure si ja et funciona correctament.

---

### Post by guillemsola on 2007-10-29
Ja he provat a posar l'arrencada a 800x600 però quant es penja és al iniciar el gnome. Jo per si un cas ho deixo posat.

De totes formes des que li vaig canviar el tipus de monitor estic arrencant correctament (toco fusta!!)

gràcies

---

### Post by papapep on 2007-10-29
Enganxa'ns el teu /etc/X11/xorg.conf, si us plau.

---

### Post by guillemsola on 2007-10-29
Doctor, doctor, és greu?

Obri la boca i digui xoooorg XD

> 
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "es"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
        Boardname       "vesa"
        Busid           "PCI:2:0:0"
        Driver          "nvidia"
        Screen  0
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1024    768
                Modes           "1024x768@60"   "1024x768@43"   "832x624@75"   "800x600@60"     "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"   "640x480@85"     "640x480@75"    "640x480@72"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection
Section "device" #  
        Identifier      "device1"
        Boardname       "vesa"
        Busid           "PCI:2:0:0"
        Driver          "vesa"
        Screen  1
EndSection
Section "screen" #  
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
EndSection
Section "monitor" #  
        Identifier      "monitor1"
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection


Salut!

---

### Post by papapep on 2007-10-29
A veure, ajupi's, que agafo el pot de vaselina  :-P

Jo el que faria és eliminar totes les referències a resolucions i/o freqüències que el meu monitor no sapigués interpretar (en el meu cas tot el que superi els 60 Hz) d'aquestes seccions:

> Section "Monitor"
Identifier "Generic Monitor"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
modeline "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
modeline "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
modeline "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
modeline "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1024 768
Modes "1024x768@60" "1024x768@43" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
EndSubSection
EndSection

També baixaria el paràmetre Virtual a 800 600 a veure què tal. (RECORDA FER-NE UNA CÒPIA DE SEGURETAT ABANS!!!)

---

### Post by guillemsola on 2007-10-30
Bueno, bueno, bueno... em penso que això ja està solucionat :):):):)

La cosa ha quedat que puc arribar a fer servir el meu monitor fins a 1024x768 però amb la tassa de refresc a 50Hz en comptes del 60 habituals. No és que no funcioni a 60 però és en aquest mode que a vegades no "enganxa" la resolució així que millor obviar-lo.

Tots els altres modes "no vàlids" els he tret de xorg.conf per evitar que l'ubuntu caigui en la temptació de carregar-los.

Estic content perquè no ho veia clar de lliurar-me de reinstal·lar l'ubuntu ara que tot anava com una seda. :guitar:

SAlut!!

---

### Post by papapep on 2007-10-30
M'alegro de que te n'hagis sortit :-D

Au, posa el "solved" ;-)

---

