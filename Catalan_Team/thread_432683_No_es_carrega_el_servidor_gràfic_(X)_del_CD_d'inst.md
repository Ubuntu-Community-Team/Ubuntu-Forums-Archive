---
title: "No es carrega el servidor gràfic (X) del CD d'instal·lació"
date: 2007-05-04
forum: Catalan Team
---

### Post by jmaspons on 2007-05-04
Hola a tots,
Estic intentant instal·lar Ubuntu 7.04 en un portàtil amd64 però no se'm carrega el servidor gràfic. Concretament estic provant la versió catalanitzada que hi ha a [caliu.cat]("http://caliu.cat/blog/2007/04/20/la-ubuntu-704-feisty-en-catala-al-servidor-de-caliu/"). El cd funciona correctament en altres ordinadors.

Tenia entès que és possible instal·lar la versió per i386 en un amd64. De fet en el mateix ordinador ja havia instal·lat la versió Dapper per i386 i no havia tingut problemes. Pot ser que sigui això el què falla?

---

### Post by CarlesOriol on 2007-05-04
No per això no pot ser.

Pots baixar la versió no-catalanitzada etiquetada ALTERNATE dels servidors oficials. Instal·lar-lo en mode text i un cop muntat descarregar els paquets d'idioma language-pack-ca.

La insta&#320;lació serà en anglès però jo ja m'hi he trobat en algun amd64 amb una nvdia integrada a placa base que  fa el ruc insta&#320;lant.

L'altra opció es provar de fer la insta&#320;lació en mode gràfic segur.

---

### Post by papapep on 2007-05-04
A mi no m'ha passat, però tinc un amic, que també té AMD64 i tarja Nvidia, al qual li va passar i ho va solventar amb l'alternate, tal i com diu en Carles.

---

### Post by eselma on 2007-05-04
Justament ahir vaig enviar una nota a la llista manifestant que ni al meu ordinador ni al de la meva dona arrencava el CD d'instal·lació de kubuntu 7.04 en català. "Casualment" els dos són AMD, el meu de 64 bit amb xipset nVidia, i el de la meva dona AMD XP de 32. El mateix CD arrenca bé en un portàtil amb Pentium M i al de la feina (un altre intel).

Per curiositat, abans d'usar la versió* alternate*, podries provar-ho amb el CD en original; a mi aquest em funcionava (això si, en mode gràfic VESA, doncs tinc una tarja nVidia 6600 LE al que el xorg li aplica per defecte al cotrolador lliure nv, que no funciona amb aquesta tarja. Després li aplico el privatiu i va tot bé. Potser sigui aquest el teu problema. 

Quina tarja gràfica tens?

---

### Post by Compact on 2007-05-04
A mi al actualitzar al Feisty em va petar el servidor X i també tinc un AMD64 (sempron) amb una targeta de vídeo integrada Nvidia.

---

### Post by CarlesOriol on 2007-05-05
Si tenies els controladors gràfics oficials d'nvidia a l'actualitzar la versió del nucli cal corretgir-ho a maneta. Reinstalant-los. 

Si simplement es van desconfigurar, sols cal fer un sudo dpkg-reconfigure xserver-xorg

(aquesta comanda tinc la sensassió d'haver-la escrit en mil posts abans!)

En cap cas és res greu.

---

### Post by jmaspons on 2007-05-11
Hola i gràcies a tots,
He provat d'instal·lar amb el cd Alternate però el problema no se soluciona. Suposo que deu ser problema de la targeta gràfica, una ATI Mobility Radeon X1300. A la [documentació ]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")he trobat una possible solució. 
El què m'extranya és que amb la versió 6.10 no havia tingut cap problema però en actualitzar a la 7.04 el servidor gràfic ja no funcionava... suposo que es pot considerar un bug.

Ja informaré de com em va.
Salut!

---

### Post by jmaspons on 2007-05-19
Efectivament era un problema dels drivers de la targeta gràfica.
He instal·lat els drivers restringits i ara ja em funciona, amb compiz i tot!

Visca!

---

