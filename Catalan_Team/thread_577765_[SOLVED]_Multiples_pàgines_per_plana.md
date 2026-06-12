---
title: "[SOLVED] Multiples pàgines per plana"
date: 2007-10-16
forum: Catalan Team
---

### Post by anigwei on 2007-10-16
Hola!

A windows fagi servir asiduament el FinePrint, una aplicacioneta que permet imprimir treballs a dos,quatre,sis.. pagines per plana, o a doble cara (amb una làser és molt pràctic).
El Fineprint és una impressora virtual, els documents s'imprimeixen primer aquí, i d'aquí a la impressora física que vulguem.

Sabeu d'alguna cosa similar per a Linux?

Gràcies!!

---

### Post by CarlesOriol on 2007-10-16
El mateix menú d'impresió de les aplicacions en gnome t'ho permet fer i crec que el kde també.

---

### Post by orestesmas on 2007-10-16
Confirmo que el de KDE també. Més et diré: si fas sovint aquest tipus de tractaments has de saber que el sistema d'impressió de GNU/Linux empra nativament el format PostScript, i que ja fa molts anys que GNU/Linux disposa d'una colla d'utilitats per manipular PostScript abans d'imprimir-lo. Per exemple, pots reduir/ampliar les pàgines a voluntat, posar-ne tantes com vulguis en una pàgina, redistribuir les pàgines d'un document llarg en quaderns per tal de poder-los doblegar i enquadernar com es fa en els llibres professionals, etc.

---

### Post by guillemsola on 2007-10-16
Jo acostumo a imprimir un parella de fulles per pàgina. Hi que només des de OpenOffice no puc imprimir vàries fulles per pàgina. Aleshores el que faig és exportar primer el document a pdf i des de el visor de pdf l'imprimeixo.

Això què linux faci servir el postcript natiu i que permet fer tantes coses vol dir que hi ha algun lloc més on puc manipular la impressió a part del programa original?

salut!

---

### Post by orestesmas on 2007-10-16
I tant. Tanmateix, moltes d'aquestes utilitats són per línia d'ordres. Per exemple, hi ha algunes utilitats en el paquet "psutils". Qüestió d'instal·lar-lo i després fer servir el "man" per veure què fa cadascuna. Els noms dels programes continguts dins del paquet psutils són (he marcat les principals amb asterisc):

/usr/bin/fixscribeps
/usr/bin/psselect   *
/usr/bin/fixdlsrps
/usr/bin/fixmacps
/usr/bin/getafm
/usr/bin/epsffit
/usr/bin/psmerge   *
/usr/bin/fixtpps
/usr/bin/psresize   *
/usr/bin/fixwfwps
/usr/bin/fixpsditps
/usr/bin/fixwpps
/usr/bin/fixfmps
/usr/bin/includeres
/usr/bin/extractres
/usr/bin/fixpspps
/usr/bin/pstops   *
/usr/bin/fixwwps
/usr/bin/psbook   *
/usr/bin/psnup   *
/usr/bin/showchar

---

### Post by marcoil on 2007-10-17
> **anigwei said:**
> Hola!

Sabeu d'alguna cosa similar per a Linux?

Gràcies!!

Jo el que solia fer per imprimir amb dues pàgines era "clonar-me" la impressora a la mateixa pàgina de configuració del CUPS. Així en tenia 2, una normal i una altra de 2ppp (pàgines per pàgina :) ).

Ara mateix no tenc impressora, així que no ho puc comprovar, però crec que si vas al menú Sistema > Administració > Impressores i selecciones la que ja tens configurada, la pots copiar. Només et queda canviar la configuració de la copiada.

Esper que te funcioni!

---

### Post by anigwei on 2007-10-18
Hola!

L'únic que veig factible és el que comenta en Marcoil. Fins i tot dues impressores, una de 2 i una de 4 pàg. per cara, ja que a vegades les transparències.........

Salut!!

---

