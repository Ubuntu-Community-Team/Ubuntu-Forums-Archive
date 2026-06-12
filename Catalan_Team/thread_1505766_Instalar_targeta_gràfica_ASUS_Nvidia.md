---
title: "Instalar targeta gràfica ASUS Nvidia"
date: 2010-06-09
forum: Catalan Team
---

### Post by RamPaS27 on 2010-06-09
Hola molt bones,

soc un iniciat en el camp de Ubuntu, i tinc un petit problema el qual he  estat buscant però no he sigut capaç de trobar solució, us explico:

abans tenia una targeta gràfica ASUS i tinc el NVIDIA X Server Settings,  sense cap tipus de problema. El problema ha aparegut quan m'he canviat  la gràfica a una altra ASUS Nvidia (ENGT 220) y el NVIDIA X Server  Settings hem diu que he de escriure 
$sudo nvidia-xconfig
i reiniciar les X.
però segueix igual.

Si algú sap com arreglar-ho, em faria un gran favor. 
Moltes gràcies.

---

### Post by RamPaS27 on 2010-06-10
hola! he pogut instalar la gràfica, però ara tinc un altre problema, no es guarda la configuració, per tant, cada cop que reinicio he de tornar a isntalar-ho.
He probat de borrar el xorg.cfg i reiniciar, de modificar-lo mitjançant el programa i tampoc.

Si algú té alguna solució li agrairia molt...

---

### Post by wgarcia on 2010-06-10
Mira en Sistema -> Preferències -> Aplicacions d'inici, i busca si tens NVIDIA X-SERVER SETTINGS, si ho tens prem "editar" i mira què posa a la segona línia (hauria de ser alguna cosa així com "comanda") i engantxa-ho aquí.

---

### Post by RamPaS27 on 2010-06-10
a la segona linia posa això:

sh -c '/usr/bin/nvidia-settings --load-config-only'

---

### Post by wgarcia on 2010-06-11
Mira a veure si et funcionen els suggeriments que poso aquí:

[http://ubuntuforums.org/showpost.php?p=9439876](http://ubuntuforums.org/showpost.php?p=9439876)

---

### Post by RamPaS27 on 2010-06-11
Bones,
he provat la solució 2 ja que no tenia l'arxiu, però tampoc funciona.

Tot i això, al iniciar el NVIDIA X Server Settings m'he fixat que a la consola apareix:

ERROR: Cannot open display 'alfredo1:0.0'.

ERROR: Unable to assign attribute CursorShadow specified on line 21 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute CursorShadowAlpha specified on line 22 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute CursorShadowRed specified on line 23 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute CursorShadowGreen specified on line 24 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute CursorShadowBlue specified on line 25 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute CursorShadowXOffset specified on line 26 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute CursorShadowYOffset specified on line 27 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute SyncToVBlank specified on line 28 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute LogAniso specified on line 29 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute FSAA specified on line 30 of configuration
       file '/home/alfredo/.nvidia-settings-rc' (no Display connection).

ERROR: Unable to assign attribute TextureSharpen specified on line 31 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute AllowFlipping specified on line 32 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute FSAAAppControlled specified on line 33 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 34 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute OpenGLImageSettings specified on line 35 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute FSAAAppEnhanced specified on line 36 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute RedBrightness specified on line 37 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute GreenBrightness specified on line 38 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute BlueBrightness specified on line 39 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute RedContrast specified on line 40 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute GreenContrast specified on line 41 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute BlueContrast specified on line 42 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute RedGamma specified on line 43 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute GreenGamma specified on line 44 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute BlueGamma specified on line 45 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute DigitalVibrance specified on line 46 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute OverscanCompensation specified on line 47 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute XVideoTextureBrightness specified on line 48
       of configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute XVideoTextureContrast specified on line 49 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute XVideoTextureHue specified on line 50 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute XVideoTextureSaturation specified on line 51
       of configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       52 of configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 53 of
       configuration file '/home/alfredo/.nvidia-settings-rc' (no Display
       connection).

he mirat l'arxiu:
#
# /home/alfredo/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Fri Jun 11 14:11:25 2010
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = Yes
ShowQuitDialog = No
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

alfredo1:0.0/CursorShadow=0
alfredo1:0.0/CursorShadowAlpha=64
alfredo1:0.0/CursorShadowRed=0
alfredo1:0.0/CursorShadowGreen=0
alfredo1:0.0/CursorShadowBlue=0
alfredo1:0.0/CursorShadowXOffset=4
alfredo1:0.0/CursorShadowYOffset=2
alfredo1:0.0/SyncToVBlank=0
alfredo1:0.0/LogAniso=0
alfredo1:0.0/FSAA=0
alfredo1:0.0/TextureSharpen=0
alfredo1:0.0/AllowFlipping=1
alfredo1:0.0/FSAAAppControlled=1
alfredo1:0.0/LogAnisoAppControlled=1
alfredo1:0.0/OpenGLImageSettings=1
alfredo1:0.0/FSAAAppEnhanced=0
alfredo1:0.0/RedBrightness=0.000000
alfredo1:0.0/GreenBrightness=0.000000
alfredo1:0.0/BlueBrightness=0.000000
alfredo1:0.0/RedContrast=0.000000
alfredo1:0.0/GreenContrast=0.000000
alfredo1:0.0/BlueContrast=0.000000
alfredo1:0.0/RedGamma=1.000000
alfredo1:0.0/GreenGamma=1.000000
alfredo1:0.0/BlueGamma=1.000000
alfredo1:0.0/DigitalVibrance[CRT-1]=0
alfredo1:0.0/OverscanCompensation[CRT-1]=0
alfredo1:0.0/XVideoTextureBrightness=0
alfredo1:0.0/XVideoTextureContrast=0
alfredo1:0.0/XVideoTextureHue=0
alfredo1:0.0/XVideoTextureSaturation=0
alfredo1:0.0/XVideoTextureSyncToVBlank=1
alfredo1:0.0/XVideoSyncToDisplay=2

no sé si pot influir, però ja no sé que més mirar.

---

### Post by wgarcia on 2010-06-11
Quan els resultats que vols mostrar son tan llargs, els hauries d'adjuntar en un fitxer. 

Quan dius que et surt això en executar NVDIA X Server Settings, què vols dir? Com l'executes, des de la línia de comandes? I amb quina instrucció?

---

### Post by RamPaS27 on 2010-06-11
ho sento no ho sabía. La cosa es que quant executo des de la terminal la comanda
$sudo nvidia-settingsel que he escrit és el que posa a la terminal oberta.

---

### Post by PatrickVogeli on 2010-06-11
mm quina versió del driver d'nvidia tens? Es compatible amb la grafica nova?

Podries provar a fer una cerca al synaptic per nvidia i desinstalar-ho tot, reiniciar i llavors vas a sistema -> administracio -> control·ladors de maquinari i t'instal·les el driver mes nou que hi ha.

Salut

---

### Post by wgarcia on 2010-06-11
I la solució 1) la vas provar? En quan al suggeriment de PatrickVogeli, jo crec que aquí no estem parlant que no s'iniciï el sistema gràfic, o sí?

---

### Post by RamPaS27 on 2010-06-11
per la solució 1) no tinc l'arxiu que posa, per tant directament vaig passar a la 2. Porbaré per si decàs la solució proposada, ja us informaré.

---

### Post by RamPaS27 on 2010-06-12
Curiosament la solució de borrar-ho tot i tornar a instalar funciona a mitges.
La resolució i tot va bé, l'únic que no puc canviar la configuració de res. Com a opció provisional per no deixar-me la vista va bé jeje

---

