---
title: "COMO: Nvidia TV OUT en Ubuntu!"
date: 2007-10-05
forum: Argentina Team
---

### Post by User21 on 2007-10-05
**COMO: TvOut para Nvidia**

Con este COMO para tarjetas gráficas NVIDIA, puedes ver X simultáneamente en tu monitor y en tu TV (Twinview).
Ideal para todos aquellos que nos gusta ver peliculas de la PC, pero en LA TV! Si, es para vos, que lo miras por TV! xD 

(Este COMO requiere tener corriendo tu placa gráfica NVIDIA con los controladores restringidos, y por ende, el cable apropiado para conectar la placa gráfica con el TV. Yo lo probe asi, no lo he testeado con los controladores libres. )

Antes que nada, hagamos un backup de tu archivo xorg.conf. En un terminal:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```Edita el archivo xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```Lo siguiente es para una pantalla de 1400x900; configuralo a la resolución que creas más cómoda.

Los "..." indican que allí hay ciertos comandos que debes dejar tal como estaban. En las opciones "meta modes", indicamos que no estamos esperando TV usando NULL (?). Modifica la sección "Device" de tu archivo xorg.conf de esta forma:

```
Section "Screen"
    ...
    Option         "TwinView"
    Option         "TVOutFormat" "Tipo de Cable"
    Option         "TVStandard" "Norma de TV"
    Option         "MetaModes" "1440x900,640x480; 1440x900,NULL; 1024x768,NULL; 800x600,NULL; 640x480,NULL"
    SubSection     "Display"
        ...
        Modes      "1440x900" "1280x1024" "1024x768" "720x450" "640x480"
    EndSubSection
EndSection
```Donde "TVOutFormat" puede ser SVIDEO o COMPOSITE de acuerdo al tipo de cable que utilices, y la salida de tu tarjeta.
Donde "TVStandard" depende de la norma de TV que uses (en Argentina, PAL-NC).
Las demás opciones dependen de los tamaños de escritorios que desees adoptar, y creas apropiadas para tu TV.

Nota: Algunas placas gráficas requieren se agregue lo siguiente a la sección "Device", para funcionar apropiadamente:

```
Option "ConnectedMonitor" "CRT,TV"
```Además, puedes setear saltearte el logo de Nvidia, en la sección "Device" con:

 Option  "NoLogo"        "true"


Una vez guardado tu xorg.conf, solo reinicia las X con Ctrl + ALt +Backspace. TVOUT funcionando...

** NOTA:** el modo TwinView extiende el tamaño horizontal de tu escritorio al TV, por lo que el papel tapiz, se estira, logrando un efecto indeseable! Como solucionarlo? NO SE! Solo quite el papel tapiz! :P

Si deseas aun mas control, puedes instalarte el paquete **nvidia-settings** (si ya no lo tienes instalado), y ejecutarlo mediante terminal o crearte un lanzador en un panel o escritorio. nvidia-settings es una interfase gráfica que permite setear el tamaño de los escritorios, su disposición, color, saturación,  zoom en el TV, entre otras cositas. Con el, podras cómodamente configurar todo a tu gusto hasta alcanzar el aspecto visual apropiado para tus películas o vídeos y guardar tu xorg.conf ideal.

Espero hayas logrado extender tu escritorio al TV, y disfrutes del CINE EN UBUNTU ;) 

Saludos, adictos al cine! :)
[B]
Este COMO esta basado en [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)[/B]

---

