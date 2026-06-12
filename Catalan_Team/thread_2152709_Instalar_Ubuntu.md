---
title: "Instalar Ubuntu"
date: 2013-06-08
forum: Catalan Team
---

### Post by jorditu on 2013-06-08
no puc instal-lar Ubuntu
Tinc el Windows 7 instalat i per molt que carregui el cd de Ubuntu al final no em surt per enlloc em diu que reinici l'ordenador i quan arranca no em surt, he intentat instal.lar per la Bios i em passa igual . Que puc fer

---

### Post by wgarcia on 2013-06-10
Coses a comprovar:

1) L'ordre de arrencada està configurat perquè comenci primer al CD i no al disc dur. Això es fa al menú de configuració de la BIOS quan arrenques l'ordinador i abans que arrenqui qualsevol sistema operatiu

2) El CD està ben gravat, no està defectuós

3) La unitat de CD no està defectuosa

També pots crear un USB arrencable i intentar arrencar des del port USB

---

### Post by ernestux on 2013-06-13
Fa poc vaig comprar un portàtil amb windows 8 (quin remei !) i a més tenia el sistema d'arrencada anomenat UEFI,  una espècie de BIOS.   Aquest sistema dificulta molt la convivència de qualsevol altra sistema operatiu amb el windows.
Primer també vaig tenir problemes per elegir l'arrancada pel CD/DVD, per poder fer córrer el dvd ubuntu.  Entre altres coses s'ha de desactivar en el "secure boot" del menu arrancada:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Després , també un cop instal·lat l'ubuntu no es podia accedir al windows.   Amb l'ajuda d'aquest tutorial he pogut tenir els 2 sistemes i elegir el que vull usar:

[http://tecnoubuntu.wordpress.com/2012/12/09/instalar-ubuntu-12-10-junto-a-windows-8/](http://tecnoubuntu.wordpress.com/2012/12/09/instalar-ubuntu-12-10-junto-a-windows-8/)

Conclusió:  si he de comprar un ordinador , que no tingui el sistema UEFI .

Sort,

Ernest

---

### Post by wgarcia on 2013-06-14
Segons tinc entès el problema que menciona ernestux sols el presenta Windows 8, però no Windows 7, però potser estic equivocat.

---

### Post by ernestux on 2013-06-17
Hola,

Pel que he pogut veure a la xarxa el sistema de fitxers EFI ja podia usar-se en ordinadors que tenien el windows 7, també.  
L'interfaç EFI -de Intel- comunica l'arrancada amb el MBR, però tamé amb el sistema GPT , menys limitat que el MBR.
Salut,
Ernest

---

