---
title: "Problemes amb GTK+ al instal.lar AMAYA"
date: 2009-06-05
forum: Catalan Team
---

### Post by xangai on 2009-06-05
Detallo versió d'Ubuntu i Kernel:

     Ubuntu 9.04 Jaunty Jackalope
     Kernel: Ubuntu 8.10, kernel 2.6.27-11-generic (no em vaig aclarir
             quan vaig actualitzar a la 9.04 i a la pregunta sobre
             modificar el menu.lst del GRUB li vaig dir que no 
             l'actualitzés)

No he instal.lat mai compil.lant. Sempre ho faig "automàticament" a través del Synaptic, i no sé ben bé com funciona la qüestió. Estic instal.lant l'editor de pàgines web Amaya i segueixo les instruccions següents que he trobat en una pàgina web:

       $ tar zxvf amaya-sources-11.1.tgz 
       $ cd Amaya10.0/Amaya
       $ mkdir LINUX-ELF
       $ cd LINUX-ELF
       $ ../configure 

Tot ha anat bé fins que executo la instrucció "../configure". Comença bé però arriba un punt on s'atura i dóna aquests missatges:
 
[FONT="Comic Sans MS"]checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error:
The development files for GTK+ were not found. For GTK+ 2, please
ensure that pkg-config is in the path and that gtk+-2.0.pc is
installed. For GTK+ 1.2 please check that gtk-config is in the path,
and that the version is 1.2.3 or above. Also check that the
libraries returned by 'pkg-config gtk+-2.0 --libs' or 'gtk-config
--libs' are in the LD_LIBRARY_PATH or equivalent.
                            
configure: error: A problem occurs durring wxWidgets library configuration. Please fix the problem and try again.[/FONT]

Vaig a Synaptic i hem diu que tinc instal.lat:

     [FONT="Comic Sans MS"]gtk2-engines   versió: 1:2.18.1-0ubuntu1
     gtk2-engines-murrine   versió: 0.90.3-1ubuntu1
     gtk2-engines-pixbuf   versió: 2.16.1-0ubuntu2
[/FONT]

Tingueu en compte que no conec massa els "entrellats" del sistema operatiu Ubuntu. Tot just estic iniciant-me.

Gràcies pel vostre ajut.

Vicenç.

---

### Post by CarlesOriol on 2009-06-05
Pots baixar els deb pre-compilats a :

[http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)

---

### Post by xangai on 2009-06-05
Moltes gràcies Carles. Ja estic baixant el paquet .deb. No obstant això de que no troba aquest programa GTK+ ... ¿com puc instal.lar-lo? Aquests GTK2 que están instal.lats ¿que són?. Suposo que aquest GTK+ deu ser una eina necessària per instal.lar programes sense compil.lar ¿oi?. ¿Tindré els mateixos problemes si més endavant vull instal.lar programes no compil.lats?

Gràcies de nou.

Vicenç

---

### Post by quitus on 2009-06-05
El gtk+2.0 es una llibreria per poder crear la interfície gràfica, quan instal·lis el paquet deb instal·larà les dependències necessàries. Al compilar el programa, et donava error perquè li faltaven aquestes llibreries, i per tant no podia finalitzar la compilació.

mes o menys crec que va per aquí la cosa.

salut.

---

### Post by xangai on 2009-06-05
Gràcies Marc. 

Ja us informaré si tinc problemes en futures compil.lacions.

Adéu.

Vicenç

---

