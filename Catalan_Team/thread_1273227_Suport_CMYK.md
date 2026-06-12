---
title: "Suport CMYK"
date: 2009-09-23
forum: Catalan Team
---

### Post by LitusMayol on 2009-09-23
Bon dia familia,

per temes de feina he de fer uns cartells. Fins ara sempre ho havia fet casolanament i els imprimia jo i per tan havia anat bé amb el RGB. Però ara la cosa és una mica més seria i és una altra persona qui s'encarrega de portar els cartells a impremta i tot plegat. Jo només en faig el disseny. En el món de la impremta es treballa amb CMYK. Jo no me n'havia preocupat mai pel que ja he esmentat abans, que era una mica *Juan Palomo: "yo me lo guiso, yo me lo como"*.

He estat trastejant per internet però no he trobat res satisfactori. Pel que sembla existeix el [Separate]("http://www.blackfiveservices.co.uk/separate.shtml") que és un *plug-in* experimental per al GIMP que permet certes operacions amb CMYK (una d'elles la més bàsica, que és la que necessito jo, que és transformar fitxers amb color RGB a un fitxer de capes CMYK). Però he seguint [aquest manual]("http://wiki.archlinux.org/index.php/CMYK_support_in_The_GIMP") no me n'he sortit a l'hora d'instal·lar-lo. 

Aleshores cercant pel fòrum he trobat [un post]("http://ubuntuforums.org/showthread.php?t=968027&highlight=cmyk") que parla d'un programa que es diu Krita. És massa senzill pel que vull fer. Però suporta CMYK. He pensat que potser obrint un arxiu creat amb el GIMP o l'Inkscape i després passar-lo a CMYK. El Krita suporta JPG i PNG, per tan puc importar arxius desde qualsevol dels dos. Però el problema és que un cop oberts amb el Krita no sé com desar-los amb colors CMYK.

Algú em pot ajudar?

Gràcieees!

---

### Post by kimet on 2009-09-23
Hi ha un plugin per GIMP que es diu Separate que et permet fer-ho.

Pots instalar un paquet, gimp-plugin-registry si es que es trova als repositoris...

Per convertir les imatges desde GIMP  has de clicar a la barra de gimp  Imatges>separate. 

Salut

---

### Post by kimet on 2009-09-23
Vaja... hauria d'acabar de llegir abans de contestar:oops::oops::oops:

Bé el que et deia, el plugin Separate s'inclou al paquet gimp-plugin-registry [http://packages.ubuntu.com/search?keywords=gimp-plugin-registry&searchon=names&suite=jaunty&section=all]("http://packages.ubuntu.com/search?keywords=gimp-plugin-registry&searchon=names&suite=jaunty&section=all") 

Salut.

---

### Post by orestesmas on 2009-09-23
> **LitusMayol said:**
> 
Aleshores cercant pel fòrum he trobat [un post]("http://ubuntuforums.org/showthread.php?t=968027&highlight=cmyk") que parla d'un programa que es diu Krita. És massa senzill pel que vull fer. Però suporta CMYK. He pensat que potser obrint un arxiu creat amb el GIMP o l'Inkscape i després passar-lo a CMYK. El Krita suporta JPG i PNG, per tan puc importar arxius desde qualsevol dels dos. Però el problema és que un cop oberts amb el Krita no sé com desar-los amb colors CMYK.

Algú em pot ajudar?


Si,

D'entrada, permet-me que discrepi sobre l'afirmació que el Krita és "massa senzill". De fet, està al nivell del GIMP i en algunes coses fins i tot el supera (com en el CMYK, per exemple). Potser en d'altres encara no hi arriba, però poc li falta. T'aconsello la lectura de [les seves especificacions]("http://www.koffice.org/krita/krita-features/").

Per desar un fitxer en CMYK has d'anar al menú Imatge -> Propietats i convertir la imatge de RGB a CMYK. despés ja la pots desar.

Tot això ho dic sobre la versió 2.0 del Krita, que és una "Release candidate" i que funciona sobre KDE 4. No sé si tu tens aquesta o l'anterior estable (la 1.6) però en totes es deu fer de forma similar.


Apali, adéu.

---

### Post by LitusMayol on 2009-09-23
> **orestesmas said:**
> Si,

D'entrada, permet-me que discrepi sobre l'afirmació que el Krita és "massa senzill". De fet, està al nivell del GIMP i en algunes coses fins i tot el supera (com en el CMYK, per exemple). Potser en d'altres encara no hi arriba, però poc li falta. T'aconsello la lectura de [les seves especificacions]("http://www.koffice.org/krita/krita-features/").

Per desar un fitxer en CMYK has d'anar al menú Imatge -> Propietats i convertir la imatge de RGB a CMYK. despés ja la pots desar.

Tot això ho dic sobre la versió 2.0 del Krita, que és una "Release candidate" i que funciona sobre KDE 4. No sé si tu tens aquesta o l'anterior estable (la 1.6) però en totes es deu fer de forma similar.


Apali, adéu.


Orestes, deixa'm que EM DISCREPI. No és massa senzill. NO EL SÉ USAR AMB SOLTURA. Porto tot el dia trastejant amb el KRITA i és un bon pepinot de programa. Potent, ràpid. Estic molt més avesat al GIMP, però no es tenen res que envejar l'un a l'altre. Hi ha mancances d'un que l'altre no les té i al revés. 

Gràcies Orestes de nou!

Kimet, mercid e totes maneres, perquè jo coneixia el Separate, però no el paquet que m'esmentes. L'he instal·lat i té funcions relament útils!


GRÀCIES DE NOU!

---

