---
title: "Compartir recursos Virtualbox-Jaunty.."
date: 2009-06-01
forum: Catalan Team
---

### Post by prostata on 2009-06-01
Algú em sabría explicar com comparteixe'n els recuros màquina entre VB y el mateix jaunty.???

Exemple: Jo tinc dues Gb de RAM i 256 de video, però quan obro sessió amb VB, aquest baixa moltìsim el rendiment en totes les aplicacions. A Vb tinc la configuració per defecte Memoria base 681 MB i de video 73 MB, si els vull modificar el mateix VB m'avisa que "es perillos"..suposo que deu ser perque entre l'anfitrió i el convidat deuen compartir els mateixos recursos totals...¿?, és dir no fan una gestió dinàmica dels recursos en funció de les necesitats de consum per cada "sesió" oberta, vull dir, si en un moment Juanty no en fa "res" i VB si treballa de valent, doncs a leshores que prengui recursos de Jaunty i el pasi a VB.

Un exemple: per fer HDR en VB triga més del doble de temps que quan el fei en wxp nadiu.. i qualsevol aplicació, O.O, per exemple també triga el doble.. he mirat per google però no veig res que em tregui del dubte...

Salutacions

---

### Post by akyra on 2009-06-01
Hola,

Una pregunta quin sistema estas virtualitzant? Aquest 256MB de tarja gràfica són compartits?

Si fos un WXP el que faria, a no ser que fos imprescindible, es baixar la memoria de la tarja gràfica a 8MBytes, y la memoria RAM a 512MB. En cas d'un W2003Server pujaria a com a mínim la RAM a 1GB, però sobretot depen del que tu tens de memòria física.

Normalment VB et dirà que és òptim per treballar amb la màquina virtual depenent de la teva màquina física. Si et pases donant recursos a la màquina virtual el rendiment de la física caurà i com a conseqüència també la virtual.

La màquina virtual, segons crec, agafa la memòria designada com seva per poder treballar i s'adapta al que li has designat, no va agafant més o menys memòria fins el màxim que li has deixat en funció de les seves necessitats, sino que agafa la que li dones.

El que si que fan les màquines virtuals es anar ocupant el disc dur de forma dinàmica a mida que ho necessiten en funció de si li has configurat així.

Salutacions

---

### Post by prostata on 2009-06-01
> **akyra said:**
> Hola,

Una pregunta quin sistema estas virtualitzant? Aquest 256MB de tarja gràfica són compartits?

Si fos un WXP el que faria, a no ser que fos imprescindible, es baixar la memoria de la tarja gràfica a 8MBytes, y la memoria RAM a 512MB. En cas d'un W2003Server pujaria a com a mínim la RAM a 1GB, però sobretot depen del que tu tens de memòria física.

Normalment VB et dirà que és òptim per treballar amb la màquina virtual depenent de la teva màquina física. Si et pases donant recursos a la màquina virtual el rendiment de la física caurà i com a conseqüència també la virtual.

La màquina virtual, segons crec, agafa la memòria designada com seva per poder treballar i s'adapta al que li has designat, no va agafant més o menys memòria fins el màxim que li has deixat en funció de les seves necessitats, sino que agafa la que li dones.

El que si que fan les màquines virtuals es anar ocupant el disc dur de forma dinàmica a mida que ho necessiten en funció de si li has configurat així.

Salutacions


Ok, gràcies era el que pensaba, però la teva opinió m'ho confirma, no es poden gestionar dinàmicament els recursos...

---

