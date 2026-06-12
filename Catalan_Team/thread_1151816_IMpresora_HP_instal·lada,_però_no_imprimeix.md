---
title: "IMpresora HP instal·lada, però no imprimeix"
date: 2009-05-07
forum: Catalan Team
---

### Post by Jayhawker on 2009-05-07
Hola, 

He connectat una HP Laserjet 1018 i immeditament s'han descarregat els drivers per a Linux. Tot semblava anar de primera. Però un cop m'ha demanat d'imprimir una pàgina de prova, se'm diu que l'ordre està en procés i uns segons després s'obre un cartellet dient que s'ha fet la feina, però la impressora s'ha quedat igual, sense oferir cap foli imprès. He intentat d'imprimir d'altres coses i no hi ha hagut manera; passa el mateix. Sisplau, hi ha alguna manera de solucionar això?

merci  :(

---

### Post by Jayhawker on 2009-05-07
Cap suggeriment? Com ho feu perquè les impressores funcionin amb Linux?:confused:

---

### Post by mcako on 2009-05-07
A mi això em va passar aquesta setmana mateix, li donava a imprimir i em deia que ho havia imprès quan realment no havia fet res. 
Lo únic que vaig fer va ser eliminar la impressora i tornar-la a instal·lar i ja em va funcionar.
Crec que el problema ve de que vaig desendollar la impressora perquè no tenia prous ports USB i la vaig endollar en un altre port USB que no era el mateix d'abans. Vols dir que a tu no et va passar el mateix? no l'has canviat de port? potser no és això i només és una paranoia meva..
Prova de fer això, elimina la impressora i torna-la a instal·lar!

---

### Post by Jayhawker on 2009-05-07
> **mcako said:**
> A mi això em va passar aquesta setmana mateix, li donava a imprimir i em deia que ho havia imprès quan realment no havia fet res. 
Lo únic que vaig fer va ser eliminar la impressora i tornar-la a instal·lar i ja em va funcionar.
Crec que el problema ve de que vaig desendollar la impressora perquè no tenia prous ports USB i la vaig endollar en un altre port USB que no era el mateix d'abans. Vols dir que a tu no et va passar el mateix? no l'has canviat de port? potser no és això i només és una paranoia meva..
Prova de fer això, elimina la impressora i torna-la a instal·lar!

Merci per l'atenció. Ja he canviat d'USB, però res. Com hauria de fer per desintal·lar i tornar a instal·lar?

---

### Post by mcako on 2009-05-07
Simplement has d'anar a Sistema > Administració > Impressores.
Veuràs que hi han totes les impressores que tens instal·lades. Prem botó dret sobre de la impressora i Eliminar.
Un cop eliminada, pitja el botó que posa "Nou" i teòricament ja et detectarà les impressores que tens connectades, només cal seguir els passos que et va dient.

---

### Post by Jayhawker on 2009-05-07
> **mcako said:**
> Simplement has d'anar a Sistema > Administració > Impressores.
Veuràs que hi han totes les impressores que tens instal·lades. Prem botó dret sobre de la impressora i Eliminar.
Un cop eliminada, pitja el botó que posa "Nou" i teòricament ja et detectarà les impressores que tens connectades, només cal seguir els passos que et va dient.

Moltes mercès, però això ja ho he fet diversos cops. Potser me n'oblido de fer alguna cosa. LA qüestió és que segueix dient-me que imprimeix i després no fa res.

---

### Post by mcako on 2009-05-07
Revisant altres pàgines he llegit els drivers que venen amb Ubuntu pel teu model no són gaire bons i és probable que no funcionin. Hi ha una alternativa, que és instal·lar un driver compatible amb la teva impressora que segons he llegit pot solucionar-te el problema. Nomes has de seguir la guia del link següent: 
[http://www.guia-ubuntu.org/index.php?title=Foo2zjs](http://www.guia-ubuntu.org/index.php?title=Foo2zjs)
Has de desinstal·lar la impressora primer.
No et puc assegurar que funcioni ja que no he provat mai aquest driver i possiblement et sigui una mica complicat d'instal·lar.

---

### Post by Jayhawker on 2009-05-07
> **mcako said:**
> Revisant altres pàgines he llegit els drivers que venen amb Ubuntu pel teu model no són gaire bons i és probable que no funcionin. Hi ha una alternativa, que és instal·lar un driver compatible amb la teva impressora que segons he llegit pot solucionar-te el problema. Nomes has de seguir la guia del link següent: 
[http://www.guia-ubuntu.org/index.php?title=Foo2zjs](http://www.guia-ubuntu.org/index.php?title=Foo2zjs)
Has de desinstal·lar la impressora primer.
No et puc assegurar que funcioni ja que no he provat mai aquest driver i possiblement et sigui una mica complicat d'instal·lar.

T'estic molt agraït. M'ha funcionat! Creia que no seria possible. 

Salutacions cordials  :)

---

### Post by mcako on 2009-05-08
Jo tampoc creia que et funcionés, però mira per on, ha funcionat! xD
Salut!!

---

### Post by CarlesOriol on 2009-05-11
Aquesta serie d'impresores hp 1018, 1020... tenen una caracteri'stica diabòlica i és que el programa que controla la impresora (el firmware) s'ha de descarregar de l'ordinador quan es connecta.

La càrrga d'aquest programa (que evidentment és privatiu ja que no es pot adaptar ni  millorar) fa que no puguis usar la impresora en punts d'accés ethernet-usb, i en l'ubuntu calgui un programa que càrregui aquesta informacio' un cp es connecti el port usb (o d'inici).

Jo sempre he tingut problemes amb aquest tipus d'impresores. N'hi ha d'hp que van fantàsticament bè però aquestes, pufff.

---

