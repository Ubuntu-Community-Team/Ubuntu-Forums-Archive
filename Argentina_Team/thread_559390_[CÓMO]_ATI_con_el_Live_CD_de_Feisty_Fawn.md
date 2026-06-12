---
title: "[CÓMO] ATI con el Live CD de Feisty Fawn"
date: 2007-09-25
forum: Argentina Team
---

### Post by leo_rockway on 2007-09-25
Algunas placas de video de ATI* no permiten cargar X (la interface gráfica) usando el Live CD de Feisy Fawn (Si no me equivoco el error es "no screens found"). No sé cómo será para Gutsy Gibbon porque aún no probé el Live CD.

Hay que hacer un par de cosas para que funcionen estas placas, pero es bien sencillo.

Apretando Control+Alt+F1 escribimos lo siguiente en la terminal:

```
sudo nano /etc/X11/xorg.conf
```

En Lignux "X11" es distinto de "x11", así que hay que tener cuidado con eso. Una buena idea es usar la tecla Tab para autocompletar las direcciones.

Es necesario agregar lo siguiente al final del archivo abierto:

```
Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "ServerFlags"
Option "AIGLX" "off"
EndSection 

```

Guardamos con Control+o y salimos con Control+x


Luego escribimos lo siguiente:

```
sudo apt-get update
```

```
sudo apt-get install xorg-driver-fglrx
```

```
sudo depmod -a
```

Este mismo paquete se encuentra disponible online ([http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx](http://packages.ubuntu.com/feisty/misc/xorg-driver-fglrx))


Una vez instalado xorg-driver-fglrx escribimos:

```
sudo aticonfig --initial
```

y

```
sudo aticonfig --overlay-type=Xv
```

Luego sólo bastará con escribir lo siguiente para cargar X:
```
startx
```

--
* Esta es una lista de placas para las que sirve xorg-driver-fglrx

FireGL: V7350, V7300, V7200, V7100, V5200, V5100, V5000, V3400, V3300, V3200, V3100, X3-256, X3, X2-256, Z1-128, T2-128, X1-128, X1-256p
FireMV: 2200 (Single card PCI-e configuration)
Mobility FireGL: V5000, T2
Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300, 9800, 9600, 9550, 9500
Radeon Xpress: 200M series, 1250 IGP, 200 series
Radeon: X1900, X1800, X1600, X1300, X850, X800, X700, X600, X550, X300, 9800, 9700, 9600, 9550, 9500

---

