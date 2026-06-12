---
title: "Bloquejar el Touchpad"
date: 2009-03-29
forum: Catalan Team
---

### Post by jinglada on 2009-03-29
En el [Packard Bell, EASYNOTE MT85-M-005SP]("http://support.packardbell.com/es/item/?m=home&pn=PC18E01904"), el teclat inclou sota la barra espaiadora hi ha un botó que anomena "[Bloquear Touchpad]("http://support.packardbell.com/es/item/index.php?i=instr_ic_touchpadlock_yamit_steele&ppn=PC18E01904")". I afegeix que: "El botón Bloquear Touchpad se encarga de activar o desactivar el touchpad para evitar los movimientos de cursor no deseados que se pueden producir a la hora de utilizar el teclado. Se trata de la opción más útil en caso de que tenga conectado un ratón al ordenador. El botón se enciende cuando el touchpad está bloqueado."

Qué hauria de fer per a activar el **Bloquear Touchpad**?

---

### Post by PatrickVogeli on 2009-03-30
Et dic el mateix que a l'altre fil, la solucio comença de manera igual:

[QUOTE=PatrickVogeli]
prem el boto varies vegades i despres fes un dmesg. Mira si a les ultimes linies hi apareix alguna cosa que hi diu setkeycode bla bla.

Un altra cosa que pots fer es obrir el programa acpi_listen i pitjar-lo, a veure si t'el reconeix.
[/QUOTE]

salut

---

### Post by Diegstroyer on 2009-03-30
No està activat de forma predeterminada? Has provat prémer Fn+"el botó que dius"?

Aquesta opció funciona igual (l'ubuntu ho configura) que si utilitzessis Windows.

Salutacions

---

### Post by jinglada on 2009-03-30
> **Diegstroyer said:**
> No està activat de forma predeterminada? Has provat prémer Fn+"el botó que dius"?
Aquesta opció funciona igual (l'ubuntu ho configura) que si utilitzessis Windows.

El touchpad està activat de forma predeterminada i el botó serveix per a desactivar-lo amb la finalitat d'evitar els moviments del cursor no desitjats que es puguin produir a l'hora d'utilitzar el teclat. Es tracta de l'opció més útil en el cas de que es tingui connectat un ratolí a l'ordinador. El botó s'encén quan el touchpad està bloquejat.
En Windows s'activa i es desactiva simplement prement el botó. En Ubuntu el botó no funciona i no s'encén al prémer-lo, ni amb Fn ni sense. He optat per la opció de desactivar els clics del touchpad a les preferències del ratolí:
 [IMG]http://ubuntuforums.org/picture.php?albumid=1000&pictureid=3592[/IMG]


> **PatrickVogeli said:**
> Et dic el mateix que a l'altre fil, la solucio comença de manera igual:

Prement el botó vàries vegades i fent un **dmesg** no apareix cap vegada la paraula **setkeycode** en les 446 línies mostrades pel Terminal.

En canvi l'**acpi_listen** dóna el següent:

joan@joan-laptop:~$ acpi_listen
hotkey ATKD 0000006b 00000011
hotkey ATKD 0000006b 00000012
hotkey ATKD 0000006b 00000013

Salut i gràcies a tots dos.

---

### Post by Razlo on 2010-05-02
ostres, jo tinc el mateix problema! No es pot associar el botó a l'opció "Habilita el ratolí tàctil" que surt a la captura?

---

### Post by jinglada on 2010-05-02
> **Razlo said:**
> ostres, jo tinc el mateix problema! No es pot associar el botó a l'opció "Habilita el ratolí tàctil" que surt a la captura?
Al cap de més d'un any, i havent migrat a l'Ubuntu 9.10 Karmic Koala, seguix tot igual pel que fa al botó, però a les preferències del ratolí hi ha variacions.
[IMG]http://ubuntuforums.org/picture.php?albumid=1000&pictureid=6040[/IMG]

---

### Post by Razlo on 2010-05-02
Doncs amb el lucid lynx les opcions són exactament les mateixes. El que preguntava, per això, és si no es podria programar botó físic del portàtil per (des)habilitar el tàctil.

Crec que em crearé un llançador a la barra que ho faci a través d'un script, però sempre és més còmode si ja tens el botó a la carcassa...

---

### Post by pelai21 on 2010-05-02
Jo tinc el mateix problema que vosaltres. I és molt molest, perquè el meu touchpad és molt sensible. El botó està permanentment encès i encara que el lucid inclou la pestanya de ratolí tàctil, no em fa cap efecte. També he provat algunes aplicacions que corren per internet, sense resultats. Pel que sembla hi ha moltes persones amb el mateix problema. Vaig trobar una solució que, teòricament, havia de funcionar:
[URL="http://ubuntuforums.org/showpost.php?p=8590673&postcount=9"]
 http://ubuntuforums.org/showpost.php?p=8590673&postcount=9[/URL]

però a mi no m'ha servit. Si trobeu una solució, feu-ho saber.

---

### Post by Razlo on 2010-05-02
'Device Enabled' equival a 121
$ID s'ha de canviar pel nom del touchpad
```
xinput set-int-prop $ID 121 8 0 #disables touchpad 
xinput set-int-prop $ID 121 8 1 #enables touchpad
```

Per saber la id del tàctil:
```
~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; **SynPS/2 Synaptics TouchPad**              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; HID 0a5c:4502                           	id=11	[slave  keyboard (3)]
    &#8627; Video WebCam                            	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]

```
Hauria de sortir algo així. Si no has canviat 'ImPS/2 Generic Wheel Mouse', que és el que surt al teu link, canvia-ho pel nom o per la id, més fàcil. Potser funciona :)

---

### Post by pelai21 on 2010-05-02
Razlo, demà ho provaré a veure què passa. No hi entenc massa, però em sembla que pot funcionar. De moment he trobat una solució provisional. He eliminat el paquet xserver-xorg-input-synaptics i em funciona molt millor. Ara el touchpad em funciona com un mouse normal i corrent, però almenys no em balla de forma descontrolada i puc utilitzar sense problemes un processador de textos.

---

