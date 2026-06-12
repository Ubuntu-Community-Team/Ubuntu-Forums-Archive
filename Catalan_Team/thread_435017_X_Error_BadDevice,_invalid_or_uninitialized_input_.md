---
title: "X Error: BadDevice, invalid or uninitialized input device 154"
date: 2007-05-06
forum: Catalan Team
---

### Post by Syzygia on 2007-05-06
Hola. Sóc usuari de l'Ubuntu 6.06. Estic fent un programa gràfic usant les llibreries de Qt 3. Puc compilar els arxius amb el codi font sense problemes, però a l'executar el programa em surt el següent error:

[COLOR="Red"][INDENT]X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
[/INDENT][/COLOR]

He provat d'executar-ho a un altre ordinador (amb Kubuntu) i no m'ha donat problemes. Sabeu com ho puc solucionar? Moltes gràcies

---

### Post by papapep on 2007-05-07
Té tota la pinta de que tinguis un problema amb la configuració de l'xorg.conf.
Fixa't que el missatge et diu, entre d'altres coses:

```
X Error: BadDevice, invalid or uninitialized input device 154
```

Amb el qual sembla que algun disposiu d'entrada, teclat, ratolí, tableta gràfica, etc.. t'estigui causant problemes. Ho hauries de revisar.

---

### Post by Nythain on 2007-05-07
comment out the wacom tablet pc only devices in your /etc/X11/xorg.conf... something like this
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

```

---

