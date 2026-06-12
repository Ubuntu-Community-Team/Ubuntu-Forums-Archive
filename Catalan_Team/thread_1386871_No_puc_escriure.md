---
title: "No puc escriure"
date: 2010-01-21
forum: Catalan Team
---

### Post by farigola on 2010-01-21
Hola 
Problema: No puc escriure
Equip Pentium IV
4Mb Ram
Kunbuntu 9.10
Gràfica Ati 4670
Monitor hanns-g 19"

Fa cinc dies vaig escriure per un problema de configuració de la ATI doncs volia millorar la resolució i vaig petar les X, després de diferents intents vaig decidir treure la ATI per iniciar l'equip amb un Nvidia de la placa de l'equip, vaig recuperar imatge, però tenia un error de kwin i aquest no deixava escriure res, però si que tenia possibilitat d'obrir finestres, després de proves i més proves vaig tornar a instal·lar Kwin i ja no tenia error algun, però després d'escriure el login ja no tenia possibilitat d'escriure res més a la vegada cap dispositiu media que insereixi al sistema aquest no surt per les X, he de dir també que no tinc possibilitat de moure les finestres només funciona el sistema per el seu inici i tancament. He mira`t de trobar informació i cert que hi ha temes similars, però res igual, de ben segur que algú de vosaltres sap com resoldre aquest tema.
Gràcies

---

### Post by quitus on 2010-01-21
Hi ha un mode d'inici per reparar paquets trencats. Quan inicia el sistema en aparèixer el grub prems la tecla ESC, esculls l'opció d'iniciar en recovery mode i poc després dpkg reparar paquets trencats. Espero que et funcioni.

salut

---

### Post by farigola on 2010-01-25
Gràcies quitus per el teu consell, havia fet proves amb "dpkg". GUtilitzant aptitude  vaig eliminar "kwin" i al iniciar l'equip i recuperar les X ja podia escriure, però el comportament de les finestres va ser del tot negatiu doncs vaig obrir firefox i aquest va quedar minimitzat i a la vegada ja no podia escriure, vaig iniciar sessió un altre cop i llavors vaig procedir a utilitzar konqueror sense tenir cap problema, la meva idea llavors va ser eliminar KDE de l'equip i a la vegada firefox i el resultat va ser que al iniciar tenia possibilitat d'utilitzar openoffice i konqueror sense problemes. Vaig tornar a la carga per instal·lar KDE i vaig tornar a tenir els mateixos problemes.
Tot una experiència

---

### Post by farigola on 2010-02-11
Després de diferents proves vaig inserir una nova placa de vídeo i d'aquesta manera vaig tornar a tenir la possibilitat de recupera el sistema gràfic, un cop fet això vag tornar a inserir la placa original i ara les finestres les tinc sense possibilitat d'ampliar-les i reduir-les i a la vegada no tinc drets per. Copiar dades del meu home. He fet proves com crear un nou usuari per al iniciar tinc el mateic problema. Crec que la solució està en eliminar KDE del tot per després instal·lar Gnome, però no se com podria fer això per tal de fer net. La meva intenció es tornar a tenir KDE. Sabeu com podria fer aquesta operació, és a dir eliminar totalment KDE per instal·lar Gnome?
Gràcies

---

### Post by farigola on 2010-03-15
Hola,
Després de dedicar-hi hores i més hores vaig comprar un cable HDMI i la cosa va millorar, però no podia moure finestres ni fer canvis a les mateixes. D'altra banda vaig tornar a tenir problemes al cap de poques hores i ja no vaig tenir possibilitat ni recuperar l'inici doncs sembla ser que el kernel ha fet una petada total.
El tema està en voler fer ara una copia del meu home i fer una nova instal·lació. El problema el tinc que al iniciar amb un disc 8.10 el home del sistema no es deixa copiar, bé només les carpetes i no veig com fer un canvi de permisos al disc, he utilitzat chmod, però res de res.

Pregunta: La meva intenció és instal·lar un altre cop Kubuntu però desconec si el directori Home desapareix totalment al fer una nova instal·lació.

---

### Post by orestesmas on 2010-03-15
Jordi, ets un expert en descollonar sistemes :-D

1) Si no pots moure finestres (desapareix la barra de títol) és que t'ha petat el gestor de finestres.
   Prova d'obrir un terminal i teclejar "kwin" allí.
   Si això no xuta (a vegades s'obre però no agafa el focus i no accepta caràcters), mira de fer Alt-F2 i escriu "kwin" allí
   Si en executar el kwin peta sistemàticament, tens un problema amb les X. Mira de desactivar la composició (efectes d'escriptori) a veure si millora la cosa.

2) Si malgrat tot no aconsegueixes res de res, potser sí que tens el sistema tan petat que s'imposa una reinstal·lació. En aquest cas la conservació o no del directori /home serà més o menys senzilla en funció de si el tenies ubicat en una partició apart o no. En cas afirmatiu simplement li has de dir a l'instal·lador que aquella partició no la formategi. Pots dir-li que la munti com a nou /home, o pots dir que la deixi sense muntar. En aquest segon cas, hauràs de modificar posteriorment el /etc/fstab per indicar como i on vols que munti aquesta partició

Vigila bé no t'equivoquis de partició!! En qualsevol cas, fes còpia de seguretat de les dades.

---

### Post by farigola on 2010-03-22
Hola a tots,
Afirmatiu, tinc una habilitat brutal per tenir problemes.

He de dir que la cosa va millorar del tot al utilitzar un cable HDMI, però al utilitzar per exemple "firefox" el sistema quedava sense poder escriure una lletra, només tenia les funcionalitats del mouse i sense poder tancar ni obrir finestres existents, crec doncs que definitivament he de mirar de copiar el home *.* per tal de fer una nova instal·lació, de totes maneres, aquesta operativa també resulta un problema doncs al tenir el sistema amb el Kernel fora de servei només tinc la possibilitat d'iniciar amb DVD i veure como només tinc possibilitat de copiar les carpetes del home sense dades, potser caldrà fer un canvi de permisos chmod del home local, de fet només voldria copiar tres directoris ( no tinc partició de home.

Alegria!

---

