---
title: "Problema amb GNUCAP"
date: 2007-03-11
forum: Catalan Team
---

### Post by GNUinU on 2007-03-11
Hola a tothom.
Jo sempre he sigut usuari de Windows, pero aquest quatrimestre a la universitat hem començat a utilitzar GNUCAP (el quatrimestre passat utilitzàvem PSPICE per Windows), i vaig decidir a probar Ubuntu 6.10.

Bé, m'he baixat la següent versió de GNUCAP: gnucap-2007-02-21
I he seguit per l'instalació aquests passos: 

tar xzvf gnucap-2006-05-06.tar.gz
cd gnucap-2006-05-06
./configure
make
make install

Doncs bé, el problema que trobo es que a la Universitat podem editar-ho tot amb Kate, però aquí, per utilitzar el programa he de cridar el Terminal, i escriure gnucap, i a partir d'aquí fer-ho tot a través del terminal.

Com puc tenir-ho com a la Universitat?


Merci. :)

---

### Post by RainCT on 2007-03-11
Hola,

No et calia compilar el GNUCAP, podies haver-lo instal·lat des de Sistema -> Administració -> Gestor de paquets Synaptic i allà haver sel·lecionat gnucap per a instal·lar i apretant a "Aplicar" se't hauria descarregat i instal·lat tot sol. Així també tindries actualitzacions automàtiques. Pots instal·lar Kate de la mateixa manera.

---

### Post by GNUinU on 2007-03-12
Gràcies.
Ara ja ho tinc, pero sorgeixen dos "problemes" nous.
El primer es que arranqui el Kate com l'arranqui, no em funciona el "terminal" que porta incorporat. Hi click-ho pero no apareix res, no puc escriure.

I l'altre és el grace.
Per exemple aquest circuit:

> 
Prova per xmgrace
Vvar 1 0 DC 0V
R1 1 2 10K
R2 2 0 4.7K
.print dc V(R2)
.dc Vvar 0 220 10 > graf.dat
.end


Després, al terminal, escric:

> xmgrace -nxy graf.dat

I no funciona, em diu el següent:

> bash: xmgrace: orden no encontrada

I això que he instal·lat primer grace6 desde el Sinaptics, i després m'he baixat i he compilat el grace normal.

Alguna idea?


Gràcies.

---

### Post by orestesmas on 2007-03-13
Sobre això del Kate i el terminal, faig una hipòtesi:

Tu deus tenir Ubuntu a seques, amb l'escriptori Gnome. Kate és una aplicació KDE (i molt flexible), cosa que em fa suposar que el "terminal" que hi ha a la pestanya és el terminal del KDE (que es diu konsole), i tu no el deus tenir instal·lat.

És necessari que sigui així perquè les aplicacions KDE fan ús intensiu de la tecnologia KPARTS, que et permet incrustar unes aplicacions dins d'unes altres i així no anar reinventant la roda constantment.

Algunes suggerències, doncs, per tal d'arreglar això:

1) Si tant te fa un escriptori com l'altre, instal·la't KDE i treballa amb ell (paquet "kubuntu-desktop")

2) Si prefereixes seguir amb Gnome, instal·la't només el konsole.

Sobre el GRACE:

El paquet que t'has d'instal·lar és el "grace", no el "grace6". Vaja, suposo que et pots instal·lar el "grace6", però aleshores el fitxer executable ja no es dirà "xmgrace" sinó potser "xmgrace6".

Espera... hi ha una manera de saber-ho sense instal·lar-lo, via apt-file. A veure un moment...

orestes@tintin:~$ apt-file show grace6
grace6: usr/bin/grace6
grace6: usr/bin/grace6-thumbnailer
grace6: usr/bin/gracebat6
grace6: usr/bin/xmgrace6

Com veus, porta els executables "xmgrace6" i "grace6" que potser és un enllaç a l'anterior.

A banda d'això, veig que tens una certa tendència a la compilació compulsiva. No està malament, perquè compilant programes s'aprèn molt, però si debian (o ubuntu) tenen disponibles les fonts d'un programa, el més probable és que ja estigui compilat, cosa que t'estalvia temps i feina.

---

### Post by GNUinU on 2007-03-13
Gracies Orestes. 
Probaré a instal·lar el konsole a veure què tal.
I amb el Grace teníes raó, posant 'xmgrace6 -nxy arxiu.dat' tot solucionat.

Gràcies! :)

---

### Post by GNUinU on 2007-03-13
Tenies raó Orestes, ja funciona perfectament. :)

Gràcies!

---

