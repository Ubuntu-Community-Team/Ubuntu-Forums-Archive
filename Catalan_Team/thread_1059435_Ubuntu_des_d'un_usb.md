---
title: "Ubuntu des d'un usb"
date: 2009-02-03
forum: Catalan Team
---

### Post by lFossil on 2009-02-03
Bones!

Fa temps que intento instal·lar l'ubuntu de nou però no em carrega el LiveCd i he comprovat que estigui tot com ha d'estar i no sembla que hi falti res, la qüestió és que no el carrega, ni amb Ubuntu ni amb WXP.
Els 2 cds estan ben grabats i en perfecte estat ja que els he utilitzat els 2 varies voltes.
A partir d'aquí, com que no me n'he sortit voldria fer-ho des d'un usb a veure si tinc menys problemes.
He estat buscant i he trobat que m'he de descarregar el unetbootin d'aquí [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) però quan l'intento obrir em surt que no hi ha cap aplicació instal·lada per a obrir-lo.
Algú sap que passa? D'on me'l puc descarregar i els passos a seguir per instal·lar l'ubuntu al pen?

Moltes gràcies!

---

### Post by Jordi B on 2009-02-04
Si el LiveCD no et carrega (t'arrenca?) deu ser que la BIOS no la tens configurada pera que el dispositiu d'arrencada provi d'arrencar primer el CD que el disc dur (però si dius que tampoc te'l pot llegir un finestres és possible que tinguis un problema de maquinari. Si fos un problema de maquinari no et llegiria cap CD. Si aquest és el cas, prova, amb l'ordinador completament apagat, de desconnectar els busos d'alimentació i IDE o SATA del lectors de CDs i torna'ls a connectar). Des de qualsevol ordinador que puguis arrencar amb el LiveCD pots fer-te una memòria USB d'arrencada anant a Sistema -> Administració -> Create a USB startup disk (a l'Ubuntu 8.10). Després, per poder arrencar des d'USB també et caldrà configurar la BIOS per a prioritzar l'arrencada (en molts ordinadors, prement F8, F9, F11 o tecla especial en alguns portàtils surt un menú per a escollir amb quin dispositiu arrencar l'ordinador). Molta sort.

---

### Post by Tomàs M. on 2009-02-04
> **lFossil said:**
> 
He estat buscant i he trobat que m'he de descarregar el unetbootin d'aquí [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) però quan l'intento obrir em surt que no hi ha cap aplicació instal·lada per a obrir-lo.
Algú sap que passa? D'on me'l puc descarregar i els passos a seguir per instal·lar l'ubuntu al pen?

Moltes gràcies!
Quina versió, per a Linux o Hasefroch? A mi em funciona perfectament...

---

### Post by lFossil on 2009-02-04
Doncs tinc ben configurada la BIOS i crec que deu ser un problema del maquinari ja que des de l'última actualització (ubuntu 8.10) que fa coses rares i em dona problemes, per exemple just abans d'aparèixer la finestra d'entrada quan l'engego, em surten unes quantes notificacions informàtiques amb anglès de les quals no entenc res, però com que a part d'això tampoc m'ha complicat la vida, doncs no li he donat importància, però crec que deu estar relacionat.

Suposo que et deus referir que ho desconnecti en un pc de taula, perquè jo tinc un portàtil i no sí si es pot fer això.

No sé que podria fer, per carregar el live cd, perquè si ho vull fer amb el usb es perquè no m'ensurto amb el cd.
Potser tindría que canviar de fil de moment fins a resoldre el tema de carregar el live cd no?

Merci!

---

### Post by marteljorge on 2009-02-05
Bé, doncs [aixó]("http://kent.dl.sourceforge.net/sourceforge/unetbootin/unetbootin-linux-313") es un executable. tens que desar-ho, donar-li permís d'execució i executar-ho dins un terminal

---

### Post by lFossil on 2009-02-05
I a això com li diuen?:D

---

### Post by Jordi B on 2009-02-06
Si el problema està en el maquinari, mira d'aconseguir-te un lector de CDs extern, configura la BIOS i instal·la-ho. Si no t'és possible, fes-te el llapis USB arrencable des d'un altre ordinador arrencat amb el CD de l'Ubuntu 8.10 i, connectant la teva memòria USB, ves a Sistema -> Administració -> Create a USB startup disk. Un cop fet el llapis USB arrenca'l des del teu portàtil. Sort !

---

### Post by lFossil on 2009-02-10
D'acord, gràcies ja ho provaré.
De totes formes amb el unetbootin estic igual, no me l'executa

---

### Post by marteljorge on 2009-02-12
Que li tens que donar permís d'execució!!

> **lFossil said:**
> D'acord, gràcies ja ho provaré.
De totes formes amb el unetbootin estic igual, no me l'executa

---

### Post by lFossil on 2009-02-14
I com es fa això??

---

### Post by papapep on 2009-02-14
Dues maneres:

```
sudo chmod +x nom_del_fitxer
```

o

Botó de la dreta sobre el fitxer, "Propietats", pestanya "Permisos", marcar "Permetre execució" (o com es digui la opció, però parla d'executar).

---

### Post by lFossil on 2009-02-16
He preparat el usb amb el menú Sistema> Administració> Create a USB startup disc.

El problema és que a l'hora de reiniciar l'ordenador no me'l carrega i està configurada la BIOS per a que mel carregui primer (removable device).

Què passa?

---

### Post by SiscoGarcia on 2009-02-16
Hola |Fossi|, jo també he tingut molts problemes amb el "Create a USB startup disc", fins que vaig fer 2 coses que no tenia gaire en compte. Una d'elles és inexplicable però certa, es tracta de deixar el màxim espai de disc per desar-hi dades (és a dir, com si aquesta aplicació només deixés fer claus USB persistents), i l'altra cosa és desmuntar la clau USB un cop creada la unitat arrencable, és a dir, un cop acabada l'operació amb l'aplicació "Create a USB startup disc". Espero que te'n surtis.

---

### Post by lFossil on 2009-02-17
Ja ho he anconseguit, a la enèssima vegada que he reiniciat l'ordinador m'ha funcionat i he pogut instal·lar-lo moltes gràcies a tots!!!

Per cert com es posa SOLVED? No ho he sabut mai XD

---

### Post by SiscoGarcia on 2009-02-17
> **lFossil said:**
> Ja ho he anconseguit, a la enèssima vegada que he reiniciat l'ordinador m'ha funcionat i he pogut instal·lar-lo moltes gràcies a tots!!!

Explica'ns com ho has aconseguit i així servirà per qui vingui al darrere ;)

> **lFossil said:**
> Per cert com es posa SOLVED? No ho he sabut mai XD

Jo és ara que no ho sé, perquè abans es feia des de "Thread Tools" i un cop allà triaves l'opció "Mark This Thread As Solved", però ara sembla ser que això no és possible... de moment (mira't l'entrada #7 d'[aquest fil]("http://ubuntuforums.org/showthread.php?t=1059995")).

---

### Post by lFossil on 2009-02-18
Doncs això, el vaig reiniciar unes quantes vegades i a no sé quina de totes em va carregar el usb i vaig realitzar la instal·lació.
Coses de l'informàtica!;)

---

