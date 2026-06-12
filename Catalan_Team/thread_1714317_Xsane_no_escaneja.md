---
title: "Xsane no escaneja"
date: 2011-03-25
forum: Catalan Team
---

### Post by Funk'u on 2011-03-25
Hola a tot-hom, a veure si algú s'hi ha trobat:

Al Xsane (he tornat a reinstal·lar tot el referent a  Xsane) em surt un error que al tancar-lo és torna a obrir tres vegades  abans no s'obre el programa, quan s'obre s'enfosqueixen les finestres  del programa mig segon, i només puc pre-visualitzar, al escanejar no  surt cap imatge, abans no ho feia i m'anava molt bé, tot i que escaneja  bé amb el Simple Scan.

L'error que em dona és el següent:

[COLOR=DarkRed]S'ha produït un error en la conversió CMS: No s'ha pogut obrir Perfil ICM de l'escàner.[/COLOR]


Moltes gràcies, salut!

---

### Post by wgarcia on 2011-03-25
Sembla que se t'han desconfigurat les opcions de gestió de color. Des de l'Xsane em sembla que ho pots fer des de 

Preferències->Configuració->Gestió de Color

A aquesta pàgina expliquen com s'ha de veure:

[http://www.xsane.org/doc/sane-xsane-setup-color-management-doc.html](http://www.xsane.org/doc/sane-xsane-setup-color-management-doc.html)

---

### Post by Funk'u on 2011-03-29
Hola wgarcia!, gràcies per respondre tant ràpid, perdona, però he estat desconnectat uns dies.

He estat mirant partint del que m'has comentat, a la carpeta [COLOR=DarkRed].color/icc/[/COLOR] no hi ha res, és buida, per tant tinc els camps de la gestió de color buits.

He llegit que s'havia d'instal·lar el paquet [COLOR=DarkRed]icc-profiles[/COLOR] i copiar el resultat a [COLOR=DarkRed].color/icc/[/COLOR], però no sé veure a on ha anat o el què s'ha de copiar.

També he instal·lat el [COLOR=DarkRed]xicc[/COLOR] que diuen que és necessari per fer perfils ¿?

Tanmateix segueixo la recerca, moltes gràcies per l'interès. ;-)


Salut!

---

### Post by wgarcia on 2011-03-30
Estic tocant una mica d'oïda, però en aquest fil:

[http://ubuntuforums.org/showthread.php?t=870424](http://ubuntuforums.org/showthread.php?t=870424)

diuen que pots trobar un perfil a

/usr/share/ImageMagick-6.4.5/config/sRGB.icm

i que si l'entres en el cinc llocs on demana el perfil a la pantalla d'xsane el problema s'arregla.

---

### Post by Funk'u on 2011-03-30
Caram crack!, l'has clavada!, ja funciona :lolflag:




Moltes gràcies wgarcia, salut!

---

