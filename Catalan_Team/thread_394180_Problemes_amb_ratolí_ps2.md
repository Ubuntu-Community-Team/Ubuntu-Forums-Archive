---
title: "Problemes amb ratolí ps/2"
date: 2007-03-26
forum: Catalan Team
---

### Post by jraulbc on 2007-03-26
Hola,

Tenia un teclat inalàmbric Genius que m'anava perfectament amb l'Ubuntu 10.7. El ratolí estava prou cascat i finalment va deixar d'anar. Aleshores vaig endollar un ratolí de reserva (òptic, genèric i al port ps/2), mentre que continuava usant el teclat inalàmbric. Aquest ratolí no m'ha funcionat bé. He provat totes les combinacions possibles, canviant també el teclat inalàmbric per un USB, per un ps/2. He fet igual amb el ratolí. Els teclats m'han funcionat perfectament, però el ratolí no. He buscat per ahí a vore si trobava alguna solució, però no n'he trobat cap. El més a prop que he trobat és [_aquesta_]("http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html") informació, que diu que cal instal·lar drivers ATI (això és una targeta gràfica, no?). Però jo tinc Nvidia. No he provat res, per si de cas. Teniu coneixement d'aquest tipus d'error i com es pot solucionar? Hem recomaneu que faça el que he trobat?

Gràcies per endavant,

jraulbc

PD: l'altre dia em vaig trobar algú que no li agradava que li donaren les gràcies per endavant en els correus electrònics. Espero no trobar-me en aquesta situació a aquest fòrum! :-)

---

### Post by orestesmas on 2007-03-26
Potser el ratolí espatllat tenia rodeta i el nou no en té (o viceversa)?

Normalment utilitzen protocols de comunicació diferents, i per això no funciona.

La solució està en editar (sudo gedit) el fitxer /etc/X11/xorg.conf i cercar quelcom com ara:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
EndSection

Canvies "ImPS/2" per "PS/2" (o viceversa), salves, reinicies el servidor X i llestos.

A veure si l'encerto!

---

### Post by jraulbc on 2007-03-27
Hola,

He provat el que m'has dit. Al editar el fitxer /etc/X11/xorg.conf he trobat la secció amb el següent text:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Com pots vore, apareix "ExplorerPS/2" en lloc de "ImPS/2" o "PS/2" com m'havies dit. Què vol dir això? He provat a canviar-ho per "ImPS/2" i "PS/2", però no he trobat cap canvi (a part de quedar-me sense rodeta en el segon cas :-))

Algun suggeriment més? Gràcies!

---

### Post by orestesmas on 2007-03-27
A veure:

1) ExplorerPS/2 no el coneixia però deu ser el mateix que ImPS/2.

Crec que ja veig què et passa: Segons el teu fitxer estas usant el dispositiu /dev/input/mice, que indica, si no m'erro, que el ratolí és USB. En canvi repassant el teu missatge m'adono que tu deies que el ratolí de reserva està connectat al port PS/2 (vaja, que no és USB). 

Els ratolins PS/2 usen un port diferent. Prova de canviar la línia 

Option "Device" "/dev/input/mice"

per 

Option "Device" "/dev/psaux"

salva, reinicia les X i a veure què tal.

---

### Post by jraulbc on 2007-03-31
Hola de nou,

He canviat el que em proposaves, i després he salvat l'arxiu i he reiniciat l'ordinador (lo de "renicia les X" no sabia com fer-ho... :oops:  ). Però continuo tenint el mateix problema. El ratolí no em funciona correctament.

Algun consell més? Gràcies!

jraulbc

---

### Post by orestesmas on 2007-03-31
> **jraulbc said:**
> Hola de nou,

He canviat el que em proposaves, i després he salvat l'arxiu i he reiniciat l'ordinador (lo de "renicia les X" no sabia com fer-ho... :oops:  ). Però continuo tenint el mateix problema. El ratolí no em funciona correctament.

Algun consell més? Gràcies!

jraulbc

Per reiniciar les X cal fer (en un terminal)

"sudo /etc/init.d/gdm stop" 

Si segueix sense anar, potser és útil mirar els LOGS que escriuen les X quan arrenquen. És un fitxer llarg però molt informatiu. El trobaràs a 

/var/log/Xorg.0.log

Sense més detalls ja no se m'acut res més.

---

### Post by jraulbc on 2007-04-03
He mirat l'arxiu Xorg.0.log i en un moment determinat trobo el següent fragment:


[INDENT](**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/psaux"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"[/INDENT]

per la qual cosa penso que la configuració del ratolí és correcta.

Em queda com alternativa provar un ratolí USB i canviar la configuració com m'havies dit més amunt. Però això no ho podré fer fins passades les vacances. 

Gràcies de nou i ja et contaré com acaba la cosa.

jraulbc

---

### Post by jraulbc on 2007-04-03
> **jraulbc said:**
> He mirat l'arxiu Xorg.0.log i en un moment determinat trobo el següent fragment:


[INDENT](**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/psaux"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"[/INDENT]

per la qual cosa penso que la configuració del ratolí és correcta.

Em queda com alternativa provar un ratolí USB i canviar la configuració com m'havies dit més amunt. Però això no ho podré fer fins passades les vacances. 

Gràcies de nou i ja et contaré com acaba la cosa.

jraulbc

RECTIFICACIÓ!

Al final de l'arxiu Xorg.0.log apareix el següent text

[INDENT](**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list![/INDENT]


No se si és important, per que sembla algun tipus d'error que no se interpretar.

jraulbc

---

