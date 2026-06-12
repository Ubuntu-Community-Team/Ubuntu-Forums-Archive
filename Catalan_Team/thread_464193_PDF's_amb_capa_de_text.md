---
title: "PDF's amb capa de text"
date: 2007-06-04
forum: Catalan Team
---

### Post by ilion1250 on 2007-06-04
Algú em podria dir com fer PDF's amb dues capes, es a dir la gràfica i la de text ?. És important perquè si el PDF conserva la capa de text es poden fer cerques de paraules.
He creat una impressora virtual PDF, com a driver l' hi he posat el fitxer ghostpdf.ppd, em fa uns PDF fantàstics però només amb la capa gràfica.
He mirat els manuals de postscript y ghostscript i no he sabut troba la instrucció que permet fer-ho. Se que es pot fer perque si imprimeixo a l' escriptori KDE no ho ha problema, els PDF em surten amb dues capes però com el navegador que prefereixo que és l' Iceweasel agafa les impressores que hi ha al Gnome i no les del KDE i m' estic tornant boig intentant veure quina es la diferència que fa que el PDF surti d' una manera o d' un altra.
Utilitzo un Debian 4.0, si algú em pot donar un cop de ma li agrairia.

Gràcies

---

### Post by orestesmas on 2007-06-04
Aquests programes de gnome no me'ls conec massa, però hi ha un truc que pots usar amb l'iceweasel: Obre'l i posa "about:config" a la barra de la URL. Llavors tira avall fins que trobis la cadena

"print.postscript.print_command"

(pots buscar-la a la caixa de text on posa "filtre")

Situa't sobre la cadena i clica-hi al damunt amb el botó DRET del ratolí. Escull "modifica" i canvia el valor que posa allí per "kprinter" (sense cometes). Això el que fa és especificar l'ordre concreta que ha d'executar quan ha d'imprimir per una determinada impressora.

Ara quan imprimeixis, si esculls la impressora "PostScript" el que farà és cridar-te el kprinter, que és el gestor d'impressió del KDE, i allí ja podràs dir-li que imprimeixi a PDF amb les capes de text que tu vols.

No pateixis per canviar això. Sempre pots tornar a editar la cadena i restaurar el seu valor original.

A veure si això et funciona.

---

### Post by CarlesOriol on 2007-06-05
Orestes.

Ahir desppres de veure aquest missatge d'ilion vaig estar provant-ho un munt de coses per veure si funcionava i no me'n vaig sortir.

Avui he vist el teu missatge i l'he provat directament dins de gnome i tampoc que no em fa les recerques. Tampoc no m'ho fa el konqueror imprimint a postscript.

És més, la generació d'un ps (ja que alguns filtres pdf s'executen com una segona passada sobre la impressió postscript) tampoc no ho fa.

El mètode que he usat per provar-ho ha estat imprimir el web d'ubuntu i després amb un visualitzador postscript (evince en gnome i kpdf en kde) intento cercar la paraula ubuntu sense èxit.

A la tarda provaré d'engegar en kde per veure com funciona això que expliques dins d'aquest entorn a veure si veig com fer-ho rutllar en gnome.

---

### Post by ilion1250 on 2007-06-05
Moltes gràcies per la informació, ho he probat però de moment no surt, ho seguiré intentant però t' estic molt agraït m' has obert una via cap a una possible solució i que a més segur que em servirà per altres coses.
Només fa quinze dies que tinc el linux i t' asseguro que  he aprés tant en quinze dies com en els anterior quinze anys, dono per bones les hores que m' estic intentant posar-ho tot a punt per migrar de l' XP al linux definitivament.
De moment per solucionar el problema dels PDF he trobat una solució provisional, quan estic navegant amb el Iceweasel i trobo una pàgina que vull guardar amb PDF copio l' adreça de la barra de navegació amb el ratoli, després premo ALT+F2, s' obre una petita caixa de diàleg anomenada executa ordre, amb el ratolí enganxo l' adreça que he copiat de la barra d' adreces i premo intro i s' em obre el Konqueror a la pàgina que vull guardar, aleshores des d'el Konqueror no hi ha problema imprimeixo i em genera un PDF de doble capa (text i gràfic), no obstant algunes vegades depenent d' alguns tipus de font especials ho ha algun problema però en general funciona.
Fa una mica de ràbia no trobar l' explicació d' aquest curiós enigma però ho seguiré intentant, de moment intentaré veure si amb el Konqueror hi ha quecom semblant al about:config per veure quina configuració hi ha. Quan hagi adquirit mes coneixements miraré de fer rutllar una sèrie de scripts per treballar amb PDF però quan domini una mica més la consola.
Una vegada més moltes gràcies, no dubteu que si trobo la solució la penjaré al forum.

---

### Post by ilion1250 on 2007-07-01
Benvolguts Ubuntaires, com que vàreu ser els primers i els únics de tots els fòrums a contestar el meu dubte sobre els PDF voldria notificar-vos que de moment la meva recerca del "PDF de doble capa perdut" ha finalitzat.
Crec que us pot interessar a la gent que veu servir GNOME.
Reformulo el problema, des d' aplicacions Gnome es poden fer PDF's amb una impressora virtual però aquests PDF's només tenen una capa gràfica, es a dir que com a document no deixen de ser gaire diferents que un JPEG o un TIFF.
Amb el KDE hi ha el Kprinter que solucionaba en part el problema ja que fa PDF's amb doble capa de text i de gráfic es a dir que el contingut del document es cercable però a vegades depenent del tipus de font d' entrada crea un document amb unes fonts de sortida no gaire nítides i es perd la funció de cerca.

La solució es la següent:

La solució està al repositori de Debian i es diu **HTMLDOC,** es tracta d' un programa que converteix pàgines web en fantàstics PDF de doble capa ( o PS si voleu), les possibilitats de configuració son moltes i encara les estic provant totes.
Podeu convertir fitxers HTML baixats previament o en línia copiant i enganxant una URL i ja està.
Si la pàgina és molt complexa canvia una mica el format i la distribució però el que importa ho ha molt bé i allà on el kprinter falla HTMLDOC no.
Cal baixar-se dos paquets
* htmldoc
* htmldoc-common
Hi ha un manual en PDF a [http://www.easysw.com/htmldoc/documentation.php](http://www.easysw.com/htmldoc/documentation.php)
El programa s' executa via consola o amb un petit i util GUI més que suficient per no necessitar la consola
No es tracta d' un programa específic de cap escriptori, jo el faig servir amb el KDE però no hi ha cap raó perque no funcioni al GNOME

---

