---
title: "Feisty se cuelga al reproducir videos - ATI Raedon 9250"
date: 2007-06-26
forum: Argentina Team
---

### Post by ivanrengo on 2007-06-26
Hola a todos!!

Desde hace un tiempito me pase casi definitivamente a Ubuntu Feisty y digo casi porque estoy experimentando unos problemas multimedia que no me permiten desprenderme de mi Window$...

Al reproducir videos con los reproductores, kaffeine, VLC, MPlayer, etc, al cabo de aproximadamente 15 minuos se me cuelga completamente la PC. Les cuento que tengo una ATI Radeon 9250 y me parece que aquí está el problema...

Me fijé en el Xorg.0.conf y me tira estos errores los cuales me gustaría que alguien me los explique:

$ cat /var/log/Xorg.0.log | grep WW
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(WW) RADEON(0): No valid DDCType is given for DDC2, try vbe probing ...
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0): MC_FB_LOCATION was: 0xd7ffd000 is: 0xd7ffd000
(WW) RADEON(0): MC_AGP_LOCATION was: 0xffffffc0 is: 0xc07fc000
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32

Además quisiera saber que tengo que hacer para saber que drivers de ATI tengo instalados (si son los propietarios o no).

Les agradezco cualquier tipo de ayuda que me puedan dar.

Saludos!!

---

### Post by Al_maverick on 2007-06-26
no deberias tener problemas. Yo tengo una 9200 SE y no tengo ningun inconveniente, con Compiz funcionando a full.

Postea tu xorg.conf, para ver que drivers tenes instalados. Esta en /etc/X11

---

### Post by ivanrengo on 2007-06-27
Muchas gracias por contestar Al_maverick!!

Este es contenido de mi xorg.conf:

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "latam"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "T710SH"
        Option          "DPMS"
        HorizSync       30-71
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Monitor         "T710SH"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by Al_maverick on 2007-06-28
Por la placa que tenes, muy similar a la mia, y soportada full por el driver opensource, yo cambiaria el que tenes ahora. recordas como lo instalaste?

Te paso el link a la wiki sobre los drivers de radeon.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ivanrengo on 2007-06-29
Mil gracias por las respuestas!!

Te cuento que al final llegué a detectar el problema. De entrada cuando instalé el ubuntu le puse los drivers de ntfs-3g para poder escribir en la partición ntfs y los videos los tenía en esta unidad, así que después de probar mil cosas me acordé de esto, lo desinstalé y santo remedio!!!

Hace una hora estoy viendo una peli y parece que al fin me voy a deshacer del Window$ ;) (excepto por los juegos, jeje)

Es una lástima lo del ntfs-3g porque creía que era estable, pero bue, seguiré esperando que mejore

Espero q a alguien le sea de ayuda

Saludos!!

---

### Post by Al_maverick on 2007-06-29
> **ivanrengo said:**
> Mil gracias por las respuestas!!

Te cuento que al final llegué a detectar el problema. De entrada cuando instalé el ubuntu le puse los drivers de ntfs-3g para poder escribir en la partición ntfs y los videos los tenía en esta unidad, así que después de probar mil cosas me acordé de esto, lo desinstalé y santo remedio!!!

Hace una hora estoy viendo una peli y parece que al fin me voy a deshacer del Window$ ;) (excepto por los juegos, jeje)

Es una lástima lo del ntfs-3g porque creía que era estable, pero bue, seguiré esperando que mejore

Espero q a alguien le sea de ayuda

Saludos!!

Los drivers de ntfs-3g no son los de lectura-escritura de ntfs? Eso te arruinaba el video?
O era q los videos los estabas leyendo desde la particion ntfs?

---

### Post by ivanrengo on 2007-06-30
> **Al_maverick said:**
> Los drivers de ntfs-3g no son los de lectura-escritura de ntfs? Eso te arruinaba el video?
O era q los videos los estabas leyendo desde la particion ntfs?

Si, los drivers ntfs-3g son los de escritura de ntfs y era lo que me generaba conflictos al reproducir los videos que estaban en una partición de un HDD SATA 1 con ese file system.

Ayer me vi una peli de 1.30Hs de esa partición después de volver al ntfs común y no se me colgó en ningún momento. :D

---

