---
title: "Cambiar tamaño de fuentes de aplicaciones de KDE"
date: 2007-11-25
forum: Argentina Team
---

### Post by lordpuppet on 2007-11-25
Buenas, tengo un problema con las fuentes de las aplicaciones de KDE  en ubuntu. De un día para otro aumentaron de tamaño y no tengo idea como modificarlo.

Que necesito para editar el tamaño de las fuentes de las aplicaciones de KDE?

---

### Post by Hernán-Amaya on 2007-11-25
entra en preferencia del sistema / apariencia / tipos de letra y ahí elegí el tamaño que te guste

suerte!

---

### Post by lordpuppet on 2007-11-25
No,

Fui muy claro al especificar las fuentes de las aplicaciones KDE, no las de GTK.

---

### Post by Hernán-Amaya on 2007-11-25
perdón pensé que usabas kubuntu. Suerte

---

### Post by Hei Ku on 2007-11-25
> **lordpuppet said:**
> No,

Fui muy claro al especificar las fuentes de las aplicaciones KDE, no las de GTK.

Es que ahi es donde se cambian para KDE. Probado en un Kubuntu Gutsy.

Menu de KDE, Preferencias del sistema, Apariencia, Tipos de letra. Ahi elegis el tipo y tamaño de letra para las distintas posibilidades que hay,

Salvo que estes usando Ubuntu, y quieras cambiar el tamaño para las aplicaciones KDE, que en ese caso supongo que será distinto.

---

### Post by kowal on 2007-11-26
La forma sencilla sería instalar **kcontrol** y de ahí cambiar las opciones de las aplicaciones de KDE.

Si no querés instalarlo entonces creá/modificá el archivo **~/.kde/share/config/kdeglobals** 
Y en la sección General tenés las opciones de las fuentes..

[General]
XftSubPixel=rgb
alternateBackground=242,242,242
background=242,242,242=false
buttonBackground=242,242,242
fixed=Monospace,10,-1,5,50,0,0,0,0,0
font=Bitstream Vera Sans,10,-1,5,50,0,0,0,0,0
linkColor=0,0,192
menuFont=Bitstream Vera Sans,10,-1,5,50,0,0,0,0,0
selectForeground=255,255,255
taskbarFont=Bitstream Vera Sans,10,-1,5,50,0,0,0,0,0
toolBarFont=Bitstream Vera Sans,10,-1,5,50,0,0,0,0,0
visitedLinkColor=128,0,128

Saludos

---

### Post by kowal on 2007-11-26
Ah, el primer número después del nombre de la fuente y la coma es el tamaño (en mi caso es 10)

---

