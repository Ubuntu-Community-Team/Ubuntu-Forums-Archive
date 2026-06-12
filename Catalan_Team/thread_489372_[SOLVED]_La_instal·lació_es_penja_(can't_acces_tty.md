---
title: "[SOLVED] La instal·lació es penja (can't acces tty...)"
date: 2007-07-01
forum: Catalan Team
---

### Post by Drac_-_Ramon on 2007-07-01
Bon dia!
Tinc un Intel Pentium D a 3.0GHz muntat sobre una placa base Asus P5LD2-Deluxe, amb BIOS AMI v.705, chipset Intel i945P, 2 Gb de memòria RAM DDR-2 SDRAM, tarja gràfica NVIDIA GeForce 6600 amb 512 Mg de memòria, disc dur Maxtor DiamondMax10 model 6V300F0 de 300 Gb i un altre Seagate Barracuda 7200.10 model ST3320620AS de 320 Gb, regravadora de DVD GSA-H12N, regravadora de CD LG GCE-8400B, una "cutre-disquetera" de 1.44Mb de tota la vida i una pantalla Sony SDM-HX95 DVI.
M'he trobat que, en intentar arrencar el PC des d'un Live CD de Kubuntu 7.04, o bé se'm penja quan surt la barra de progressió després del menú inicial, o bé em surt l'error "/bin/sh: can't access tty; job control turned off (initram fs)". El mateix em passa amb la versió Kubuntu 6.06 i en els CD d'Ubuntu 7.04 i 6.06. Intentar arrencar el Live CD en mode gràfic segur tampoc no corregeix el problema.
He provat els CD en un altre PC i arrenquen Kubuntu sense cap problema...
Què passa? Com puc instal·lar-ho??
Agraïria que m'ajudessiu; són TOTALMENT novell amb Linux, i no me'n surto.

Gràcies!!!

---

### Post by CarlesOriol on 2007-07-01
Prova d'insta&#320;lar la versió ALTERNATE. 

Aquesta intentarà inta&#320;lar-se en mode text. Pot ser així et funcioni.

---

### Post by eselma on 2007-07-01
> **Drac_-_Ramon said:**
> Bon dia!
Tinc un Intel Pentium D a 3.0GHz m...tarja gràfica NVIDIA GeForce 6600 amb 512 Mg...


Jo també tinc una tarja gràfica nVidia 6600 (LE, en el meu cas...) Des de la versió 6.9 de les x.org, aquestes la detecten, efectivament, com una nVidia i l'hi apliquen el controlador lliure "nv". Amb un problema: aquesta tarja no el reconeix i no es disposa d'entorn gràfic en arrencar.

Si pots executar una consola (amb Ctrl + Al + F1, per exemple, i aconsegueixes canviar al fitxer /etc/X11/xorg.conf l'entrada:

[I]Section "Device"
 .            Identifier       "video card nvidia 6600##..."[/I]
  .           **Driver            "nv"**
........................

canviant el Driver de "nv" a "**vesa**" (com a administrador, *root*, amb l'editor *nano*, per exemple) hauries de poder arrencar fent

              startx

Si no arrenca, anota els missatges d'error.

Un cop instal·lat amb el controlador VESA (sense acceleració 3D) pots canviar el controlador pel privatiu nvidia amb Synaptic (Aptitude en Kubuntu); va com una seda.

Suposo que el teu problema és aquest; ja vaig manifestar aquesta inconsistència de x.org (en una altra distro) però veig que continua igual. No sé que hi deuen haver fer els de nVidia a aquest controlador.

Ja ens diràs com ha anat.

---

### Post by Drac_-_Ramon on 2007-07-02
> **eselma said:**
>  Si pots executar una consola (amb Ctrl + Al + F1, per exemple, i aconsegueixes canviar al fitxer /etc/X11/xorg.conf ...

Gràcies a tots 2 per contestar tan ràpid!! :)

Ja us he dit, però, que sóc totalment nou en tot això... Un cop arrenqui el PC amb el Live CD, quan he de prémer Ctrl + Alt + F1? Abans o després  del menú? I sobretot... on és i com puc accedir a aquest fitxer xorg.conf???

Gràcies altre cop!

---

### Post by eselma on 2007-07-02
> **Drac_-_Ramon said:**
> Gràcies a tots 2 per contestar tan ràpid!! :)

Ja us he dit, però, que sóc totalment nou en tot això... Un cop arrenqui el PC amb el Live CD, quan he de prémer Ctrl + Alt + F1? Abans o després  del menú? I sobretot... on és i com puc accedir a aquest fitxer xorg.conf???


El que probablement et falla és la visualització en mode gràfic (*x-window*, no confondre amb un mot semblant...). Una opció, com t'han dit, és descarregar la versió "alternate" i fer la instal·lació en mode text, que no depèn de les particularitats de la teva  tarja gràfica. Però si ja has gravat el CD* live * (que permet provar la distribució des del CD, i després instal·lar-la, si vols) pot fer una altra argúcia:

[LIST]
[*]Deixar que acabi de carregar-se el CD "a cegues" (ho notaràs perquè el llumet del lector de CDs roman sempre apagat
[*]llavors pots prémer Ctrl + Alt + F1 : T'ha d'aparèixer una pantalla en mode text
[*]et sortirà una pantalla en anglès que et recordarà que per actuar com a administrador, cal que marquis primer "sudo"
[*]recorda que encara tindràs el teclat "anglès", llevat que hagis arrencat amb el CD català; per tant, la barra inclinada la tens a la tecla "-"
[*]Ja  pots marcar "cd /etc/X11" (sense els guionets) (és a dir, aparentment "cd -etc-X11", fixa't que la "X" és majúscula)
[*]Això et situarà al directori adequat. Pots fer "ls" (i retorn de carro, per descomptat) per veure els fitxers que hi ha
[*]N'hi ha d'haver un anomenat xorg.conf. Cal que l'editis com t'hem dit abans.
[*]Crida l'editor en mode administrador amb "*sudo nano xorg.conf*"
[*]A sota del senzill editor (nano) t'indica com moure't; posa't sobre la línia on diu *Driver     "nv"*
[*]Canvia el "nv" per "vesa"
[*]Un cop estigui fet, desa el fitxer modificat amb Ctrl + O (sortir i desar), no pas amb Ctrl + X (sortir sense desar)
[*]llavors pots provar d'arrencar les "X" tot fent "*startx*" (sense les cometes, és clar)
[*]si tot ha anat bé, s'engegarà l'entorn gràfic
[*]Ja  pots instal·lar-ho al disc dur, si vols... però... compte! els canvis que has fet abans no es traslladen a la nova instal·lació
[*]Un cop hagis rearrencat, i engegat des del disc dur... (SENSE el CD-ROM...)
[*]Cal que tornis a repetir la operació, però ara ja et quedarà registrada a la nova instal·lació
[*]Llavors amb l'instal·lador Adept, pots instal·larte els mòduls:
[*]"*linux-restricted*" i "*nvidia*"
[*]Això, un cop rearrencat, hauria d'instal·lar-te els controladors privatius
[/LIST]

Si, malgrat tot, no arrenca amb els nous controladors (ho pots provar marcant des de la konsole "*glxgears*", hauries de veure tres rodes dentades girant), pots tornar a editar (amb sudo, es clar) el ja conegut fitxer /etc/X11/xorg.conf, fent primer una còpia de seguretat d'aquest:

*sudo cp /etc/X11/xorg.conf /etc/X11/xorg.vesa*

i després canviant el Driver de "*vesa*" a "*nvidia*"

Pots provar a reiniciar les "X" (no cal rearrencar, només cal aque facis Ctrl + Alt + Backspace (la tecla <-- que hi ha sobre de la de retorn de carro). Ara ja t'hauria d'anar bé.

Ànims, que, fent aquestes coses, s'agafa seguretat.

Ja ens diràs com va tot plegat.

---

### Post by Drac_-_Ramon on 2007-07-06
> **eselma said:**
> Ja ens diràs com va tot plegat.

Fatal...!!!  :(

Ni Ctrl+Alt+F1, ni Alternate, ni res de res! Se'm queda mort a mig carregar K/Ubuntu...
Ja no sé què més fer: he fet tots els canvis i combinacions possibles a la BIOS; he anat "desenxufant" tots els perifèrics, hubs, lectors i demés, fins a deixar el PC en la seva mínima expresió; he provat diferents versions... i res!

Penso que, o canvio de PC, o he de deixar córrer Ubuntu i seguir amb el maleït Windows  :(:(

Gràcies per l'interès, però.

---

### Post by papapep on 2007-07-06
Si estigués en el teu cas agafaria una tarja de video qualsevol que tingués tirada per casa i la ficaria a canvi de la GeForce 6600 a veure què tal funciona la instal·lació amb el canvi. Com a mínim sabria definitivament si és la placa de video o no.

---

### Post by Drac_-_Ramon on 2007-07-15
Hola a tothom.

He estat liat aquesta setmana, i no m'hi he pogut dedicar fins ara...
L'única tarja gràfica que tinc "tirada per casa" és una ATI AGP que no puc connectar a la meva placa base, o sigui que no puc fer la prova. De totes maneres, per tal i com se'm penja, i pels missatges que mostra la versió Alternate just abans de penjar-se, no crec que el problema estigui a la tarja gràfica...
Si algú té alguna altra idea o suggeriment serà moooooolt benvingut!!!

Gràcies!

---

### Post by CarlesOriol on 2007-07-16
Mira:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/48556](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/48556)

---

### Post by Filodoro on 2007-07-16
> **Drac_-_Ramon said:**
> Fatal...!!!  :(

Ni Ctrl+Alt+F1, ni Alternate, ni res de res! Se'm queda mort a mig carregar K/Ubuntu...
Ja no sé què més fer: he fet tots els canvis i combinacions possibles a la BIOS; he anat "desenxufant" tots els perifèrics, hubs, lectors i demés, fins a deixar el PC en la seva mínima expresió; he provat diferents versions... i res!

Penso que, o canvio de PC, o he de deixar córrer Ubuntu i seguir amb el maleït Windows  :(:(

Gràcies per l'interès, però.


Hola, yo tengo un equipo parecido y me pasaba lo mismo,, lo solucione sustituyendo el disco SATA por un ATA convencional de la misma capacidad,, ahora me arranca y funciona bien.

podrias probar con un disco normal y comentar como te va ?

pd:perdonad mi catalan

---

### Post by CarlesOriol on 2007-07-17
> **Filodoro said:**
> pd:perdonad mi catalan

Cap problema. Però tens bones eines com [www.internostrum.com](www.internostrum.com) per ajudar-te amb el català si vols.

---

### Post by Drac_-_Ramon on 2007-07-17
> ... lo solucione sustituyendo el disco SATA por un ATA convencional... 

Benvolguts companys i companyes.... ENS N'HEM SORTIT!!!

La clau estava en el post de Filodoro (gràcies!). 
He anat a la BIOS i he canviat la configuració dels discs a "Enhanced IDE", mode "S-ATA + P-ATA" (abans he fet còpia de seguretat de les dades importants, per si d'acàs... ;-)  ). I ara ja m'arrenca la tan i tan esperada instal·lació!!!!!!!!

Gràcies a tots els que heu intentat ajudar-me; no ho dubteu: seguiré consultant coses; segur!

Una abraçada,
Ramon.

---

