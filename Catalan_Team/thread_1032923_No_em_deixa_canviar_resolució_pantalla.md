---
title: "No em deixa canviar resolució pantalla"
date: 2009-01-06
forum: Catalan Team
---

### Post by Dr.Rwh on 2009-01-06
Hola, tornem a ser aquí espero no donar gaire la tabarra :)

El cas és que ahir vaig estar jugant amb el "cedega" al Age of mitology , per jugar al correr tot al mínim de gràfics, el cas es que el joc es va penjar, em va retornar al escritori, i ara tinc una resolució que les carpetes son gegants, les lletres també gegants, i he provat varies coses per solventar-ho, i no ho aconsegueixo, a veure si algú em pot donar un cop de mà .

-Ja he provat de anar a Sistema - preferències - resolució de pantalla = la poso al 1024x786 , que és la que faig servir normalment, clico aplica i tancar. Reinicio el PC per veure si s'ha de reiniciar perque es vegi bé, però al tornar a iniciar, vinga les carpetes gengants i les lletres imenses...

-He desinstalat completament el Age of mitology, i el problema persisteix.


Gràcies per una mica del vostre temps!


Salut

---

### Post by Dr.Rwh on 2009-01-07
No sé perque no em deixa editar el missatge, bueno agrego nova informació.

He aconseguit posar la resolució de pantalla al 1024x860 , la bona, però per fer-ho vaig desinstalar els Drivers de la pantalla, així em va deixar posar la resolució de la pantalla, però ara al intentar tornar a activar els drivers, es queda penjat, deixo una captura, es queda al 0% i no fa res més.

[http://img522.imageshack.us/img522/5631/capturavn5.png](http://img522.imageshack.us/img522/5631/capturavn5.png)

He intentat buscar el driver e instalar-ho per comandes, però em dona error 

"  ERROR: You appear to be running an X server; please exit X before installing. "


P.D. Veient la firma del papep , tinc ubuntu 8.10

---

### Post by RainCT on 2009-01-08
Si executes el **jockey-gtk** des d'una terminal et diu alguna cosa?

---

### Post by catjosep on 2009-01-22
Hola bona nit a tothom jo em trobo amb el mateix problema. Només tinc unes quantes resolucions de pantalla predeterminades fins a la 800x600. I la veritat es que es veu molt malament.

Es tracta d'un ordinador ja un xic vell, però em serveix per fer les primeres passes amb l'Ubuntu. Les dades són:

PIII 600

Això és el que em surt com a informació de la versió:

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy

I la targeta és mot vella, però era bastant bona:

 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)

Haviam si em podeu donar un cop de mà, ja que la gran majoria de menús em surten retallats a ser massa gran. Només demano que m'ho expliqueu pas per pas,ja que no en tinc ni idea podríem dir.

Moltes gràcies.

---

### Post by SiscoGarcia on 2009-01-22
Hola catjosep, benvingut al fòrum!

Sento no poder servir-te d'ajuda pel problema que planteges, però almenys espero ajudar-te una mica en temes formals, que podríem anomenar d'etiqueta, [netiquette]("https://wiki.ubuntu.com/CatalanTeam/UbuntucatNetiquette") per a nosaltres: ja t'has mirat el [fil per principiants]("http://ubuntuforums.org/showthread.php?t=599965")? Allà hi trobaràs passes a donar abans de fer la consulta, de manera que potser podràs trobar-hi la solució tot sol, o si més no, ens podràs explicar amb més detall que és el que ja has provat.

Per cert, googlejant introduint-hi el model de tarja que trobes? Dóna'ns la major informació possible sobre la màquina i la tarja.

Fins aviat!

---

### Post by oriolsbd on 2009-01-23
Què et retorna aquesta comanda?
```
lspci
```

Salut!

---

### Post by catjosep on 2009-01-23
Perdó tens raó no m'he llegit massa bé la guia per a principiant, si que vaig estar buscant per internet però es que em parla de coses que ara mateix no se que són ni on anar-les a buscar.

En quan a la comanda em retorna això:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0e.0 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:0e.1 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:0e.2 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:0e.3 USB Controller: Agere Systems USS-344S USB Controller (rev 11)
00:0f.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
00:0f.1 Input device controller: Creative Labs SB Live! Game Port (rev 06)
01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo 3 (rev 01)

Ara mateix sento no pode acabar d'explicar els passos que he fet, quan torni al migdia.

Gràcies i salut!

---

