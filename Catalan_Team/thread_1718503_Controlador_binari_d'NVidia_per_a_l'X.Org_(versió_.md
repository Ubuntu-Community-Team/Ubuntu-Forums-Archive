---
title: "Controlador binari d'NVidia per a l'X.Org (versió 185)"
date: 2011-03-31
forum: Catalan Team
---

### Post by dariusill on 2011-03-31
Hola a tots i totes,

Quan miro un video a youtube o qualsevol altre plataforma de streaming i intento maximitzar la imatge, aquesta es queda congelada o senzillament el vídeo no funciona. 

He pensat que potser és la targeta gràfica crec que és NVIDIA .... així que m'he instal·lat la última versió des de el gestor de programari UBUNTU.:


[LIST]
[*]Controlador binari d'NVidia per a l'X.Org (versió 185)
[/LIST]
Com poso en marxa aquest programari? Es per la manca de NVIDa que no podia veure els videos en format GRAN? NVIDIa té relació amb el html5  ?


Gràcies.

Dàrius Ill

---

### Post by wgarcia on 2011-03-31
Primer assegurat que realment la targeta gràfica que hi ha al teu ordinador és una NVIDIA. Això ho pots fer obrint una terminal (Aplicacions -> Terminal) i entrant la següent instrucció:

lspci | grep -i vga

A veure si et diu que la targeta és NVIDIA.

---

### Post by dariusill on 2011-04-01
Ei hola, 

~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Crec que no sóc Nvidia...

---

