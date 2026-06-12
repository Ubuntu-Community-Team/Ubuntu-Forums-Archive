---
title: "Error actualització 9.10 no s'inicia"
date: 2010-08-23
forum: Catalan Team
---

### Post by diablessamariken on 2010-08-23
Hola ubuntaires

després d'esperar-me bastant per cangueli, he acabat actualitzant la meva versió de l'ubuntu a la 9.10. Ho he fet aprofitant el gestor d'actualitzacions. 

Tot anava bé fins que ha dit que havia de reiniciar l'ordinador. Li he dit que ho fes i ja no ha tornat a entrar a Ubuntu de cap de les maneres!
Diu STARTING (en modo MSDOS) però després ja no es carrega la pantalla d'inici on et demana el nom d'usuari i la contrasenya. Només tinc una pantalla negra! i què faig???

He provat d'entrar amb el Recovery Mode i m'apareix una fila de textos, em demana la contrasenya i diria que hi accedeix, però sense perdre el format MSDOS.
De moment ho estic provant des de: UBUNTU 9.10, Kernel 2.6.31-22-generic

Ara bé, quan provo d'entrar-hi com UBUNTU 9.10, Kernel 2.6.31-19-generic tampoc funciona.

Alguna idea?? 

Moltes gràcies!

---

### Post by trinkus on 2010-08-23
Aixi doncs, t'apareix el menu del GRUB?

Has provat d'iniciar amb un LiveCD?

---

### Post by diablessamariken on 2010-08-23
No tinc cap LiveCD!

I no sé què és el menú del GRUB, et refereixes a la pàgina on et deixa triar des de quin sistema operatiu o kernel vols iniciar?
Si és això, sí que m'apareix.

---

### Post by diablessamariken on 2010-08-23
Després de llegir molts posts en diversos fòrums veig que la gent ha tingut problemes amb la targeta ATI, jo també en tinc una: 

ati mobility radeon x1300

no sé si això hi pot tenir alguna cosa a veure...

Sinó, em conformaria amb poder tornar a la versió anterior amb la que sí que podia treballar!

Gràcies

---

### Post by quitus on 2010-08-23
Hola, quan apareixia la pantalla negre, et devia sortir alguna cosa, o era només negre.

salut

---

### Post by diablessamariken on 2010-08-25
Gràcies a un company ho hem pogut solucionar.

Les entrades del grub que apuntaven a un UUID s'han canviat a mà per la ruta de dispositiu de la partició

root- /dev/sda5

Ara funciona.

---

