---
title: "Virtual Box i tema d'USB"
date: 2007-05-18
forum: Catalan Team
---

### Post by bikerbaixcamp on 2007-05-18
He instal·lat el Virtual Box, i ja he posat l'XP. Doncs ara el que no me'n surto és amb el tema de l'USB. I és el que més necessito.

Mireu que el em diu: (fer gran veure imatge voto dret)

[IMG]http://webs.racocatala.cat/bikerbaixcamp/virtual_error.png[/IMG]

---

### Post by patrickfromspain on 2007-05-18
hem sembla que et podra servir aixo:

[http://ubuntuforums.org/showthread.php?t=393582&highlight=usb+vmware+%2Fetc%2Ffstab](http://ubuntuforums.org/showthread.php?t=393582&highlight=usb+vmware+%2Fetc%2Ffstab)

Alla hi surt aixo:

 Re: USB problem with VirtualBox
I am not sure how to activate a usb device in Edgy, but I can tell you how I did it in Feisty.

First, it had nothing to do with fstab.

This solution worked for me :

Edit (as root) /etc/udev/rules.d/40-permissions.rules (I use vim, you can use nano, gedit or whatever)

Change this line :

SUBSYSTEM=="usb_device", MODE="0664"

To :

SUBSYSTEM=="usb_device", MODE="0666"


For further advice see : [http://www.virtualbox.org/download/UserManual.pdf](http://www.virtualbox.org/download/UserManual.pdf)

See section 10 "Troubleshooting" there is a section on USB devices.

FYI : I am working on a Virtual Box How-to for Ubuntu here : [http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

Feel free to give feedback
__________________

EDIT: consti que no ho he probat eh? ;)

---

### Post by bikerbaixcamp on 2007-05-18
> **patrickfromspain said:**
> hem sembla que et podra servir aixo:

[...............

EDIT: consti que no ho he probat eh? ;)

[IMG]http://www.racocatala.cat/smileys/flipa.gif[/IMG]

uff que complicat.. Això pot afectar a l'ubuntu (de manera negativa, clar)? Esperaré a veure si trobo alguna cosa menys perillosa i comprovada...

Hauria de fer això?:

Edit (as root) /etc/udev/rules.d/40-permissions.rules (I use vim, you can use nano, gedit or whatever)

Change this line :

SUBSYSTEM=="usb_device", MODE="0664"

To :

SUBSYSTEM=="usb_device", MODE="0666"


;-)

---

### Post by patrickfromspain on 2007-05-19
si, hauries de fer allo. A la gent li ha funcionat. proba-ho, reinicia i si no et va, ho desfas i llestos.

---

### Post by bikerbaixcamp on 2007-05-19
També dir que he provat el Vmware i es no trobo les opcions pel usb, i com que de costum tampoc va. També dir-vos que tinc un ordinador nou.

Bé, doncs he modificat això del numeret aquest i amb l'Ubuntu correcte, i amb el VirtualBox, mig mig. M'explico, doncs l'he engegat i allà em posava que detectava un USB device i tot això. I bé, s'ha posat a descarregar els drivers perquè anés. El Windows em deia que no eren segurs el seu funcionament, però jo li he dit que endavant.. Bé, llavors després de tot això he comprovat dues coses: El concentrador USB tampoc m'anava (és un 1) i després la sortida USB directa de l'ordinador (2.0 clar) si que ha anat (però no alhora amb l'Ubuntu, però amb això cap problema). I res, el que passa es que he tancat el VirtualBox i no m'anava el teclat a l'Ubuntu!! (tinc un teclat USB). He tornat a entrar al VirtualBox de diveres maneres, desactivant USB i tota la pesca i res. La solució es que he hagut d'anar a desendollar l'USB del teclat de darrera l'ordinador i tornar-lo a posar. I llavors tornava a funcionar. Però entro al VirtualBox de diverses maneres i res.. si està desactivitat l'USB res de res (evidentment) i activat feia el sorollet de connectar però res més, no s'obria res.

Que n'opineu?

PD: De l'USB em surten dues coses:
- ALCOR generic USB Hub [0312]
- Unknown device 0566:3004 [0100]

;)

---

### Post by bikerbaixcamp on 2007-05-19
Aaaaa, novetat....

Necessitava el Windows per fer funcionar el Picture Project, i només per aquest programa, en principi..

Doncs ara resulta que amb aquest canvi que he fet el Digikam em detecta la càmera digital!!! I ja puc fer les coses que necessito!

Així que mantindré el VirtualBox, i intentaré que vagi tot, però en principi ja no necessito per res massa cosa més!

Visca el programari lliure!

---

### Post by smoker on 2007-05-20
thanks for this, biker,  one simple edit and all is well,

have bookmarked your tutorial as well (just have to remember to unmount the usb drive before opening vbox!)

cheers:-)

---

