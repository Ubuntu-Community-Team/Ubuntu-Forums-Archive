---
title: "No vull estalviar energia! (així no)"
date: 2010-03-21
forum: Catalan Team
---

### Post by lpargemi on 2010-03-21
Hola, 

Tinc un ordinador nou de sobretaula, i li he instal·lat un Ubuntu Karmic. Tot xuta amb normalitat, però em passa una cosa: Quan entra l'estalvi d'energia es queda engegat a mig gas, amb la pantalla apagada i no sé com tornar-lo a posar actiu. No fa cas a res. He provat amb el teclat, amb el botó d'engegar -(el resultat de la darrera prova és que es para, clar...), amb el ratolí a cegues...

La solució -morta la cuca, mort el verí- és des de *Sistema-> preferències-> gestor d'energia* dir-li que no hi entri mai. Però això cal definir-ho per cada usuari... i a més segur que hi ha una sortida prevista al tema. Sabeu què hauria de fer per sortir de l'estalvi d'energia?

Agraït

Lluís

---

### Post by pelai21 on 2010-03-21
Normalment, quan s'activa l'estalvi d'energia, tocant lleugerament el botó d'encendre n'hi ha prou per tornar-lo a posar en marxa. Potser l'apretes massa estona, i per això es para.

---

### Post by orestesmas on 2010-03-21
Això sona a bug. Debugar això acostuma a ser molt complicat, perquè no saps massa si és de l'ACPI, de les X o de l'entorn d'escriptori. No sóc massa expert en aquests temes. A veure si algú altre et sap donar alguna indicació. Si no, ja veurem.

Però ajudaria disposar de la informació típica: Model de placa base, targeta de vídeo i monitor, entorn d'escriptori, etc...

---

### Post by lpargemi on 2010-03-21
> Model de placa base, targeta de vídeo i monitor, entorn d'escriptori, etc... 

Un resum tret amb l'aplicació Hardinfo (a veure si queda llegible)

No, no hi queda, demà amb més temps miro de fer un resum amb cara i ulls

---

### Post by lpargemi on 2010-03-22
> **lpargemi said:**
> Un resum tret amb l'aplicació Hardinfo (a veure si queda llegible)

No, no hi queda, demà amb més temps miro de fer un resum amb cara i ulls

La placa base que tinc és una Gigabyte GA-G41M-ES2L

La CPU és un Intel EM64T E5300  

La tarja de video és la que ve integrada amb la placa base

Vendor		: Tungsten Graphics, Inc
Renderer		: Mesa DRI Intel(R) G41 GEM 20090712 2009Q2 RC3 
Version		: 2.1 Mesa 7.6
Direct Rendering		: Yes


Pel què fa a les X:

-Display-
Resolution		: 1280x1024 pixels
Vendor		: The X.Org Foundation
Version		: 1.6.4
-Monitors-
Monitor 0		: 1280x1024 pixels

L'operatiu

-Version-
Kernel		: Linux 2.6.31-20-generic (x86_64)
Compiled		: #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010
C Library		: GNU C Library version 2.10.1 (stable)
Default C Compiler		: GNU C Compiler version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
Distribution		: Ubuntu 9.10

Salut

Lluís

---

### Post by wgarcia on 2010-03-23
Dos coses fàcils per provar, si no ho has fet ja i per descartar que no siguin configuracions de l'escriptori, són:
1) si no tens desactivats els "efectes visuals", anar a "Preferences -> Aparença" i desactivar els efectes visuals extra
2) crear un altre usuari i veure si també li passa a aquest altre usuari

---

### Post by lpargemi on 2010-03-23
> **wgarcia said:**
> Dos coses fàcils per provar, si no ho has fet ja i per descartar que no siguin configuracions de l'escriptori, són:
1) si no tens desactivats els "efectes visuals", anar a "Preferences -> Aparença" i desactivar els efectes visuals extra
2) crear un altre usuari i veure si també li passa a aquest altre usuari

Provaré això de l'escriptori - si és això ja serà mala sort, perquè hagués estat la primera vegada que els podia tenir activats.

La segona està confirmada: em passa a tots els usuaris.

Lluís

---

### Post by wgarcia on 2010-03-24
Estic d'acord amb l'Orestes que sembla un problema d'acpi (sistema de gestió d'energia). Una possibilitat, fins que no arribi alguna actualització que ho arregli, és posar "acpi=off" a la línia de comandes que arrenca el nucli al grub. 

Si no saps com fer això indica quina versió de grub tens, que pots veure amb:

update-grub -v

des d'una terminal.

---

### Post by farigola on 2010-03-24
Hola Lluís,
Tens el compiz instal·lat? Altres temes fes un canvi de resolució de pantalla 800 x 600 i fes una nova prova. 

El bruixot petador de linux nº 1
Jordi

---

### Post by CarlesOriol on 2010-03-26
Pot ser a:

/etc/default/acpi-support 

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

passar-lo a false?

tot i que al file hi diu
#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

---

