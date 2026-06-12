---
title: "Com configureu impressions pagines parelles/senars"
date: 2007-09-03
forum: Catalan Team
---

### Post by pserra on 2007-09-03
Hola companys,
sóc bastant 'novell' en entorn ubuntu i aquests dies  hauré d'imprimir bastants arxius...... i  una pregunta    bàsica.....  Hi ha alguna manera de poder escollir qualitat d'impressions i escollir pàgines parelles i senars???  quan cliko imprimir
em surt una finestreta molt bàsica... amb poques opcions...
A rhttp://ubuntuforums.org/images/smilies/smiley-faces-75.gifeveuire

---

### Post by papapep on 2007-09-03
Això depèn de l'impressora que tinguis i, conseqüentment, del controlador que tinguis instal·lat. 
En tot cas, pots accedir a la configuració d'impressores de dues maneres:

1.- Obrint el navegador d'internet i posant a la barra d'adreces:

```
localhost:631
```

i 

2.- Anant a Sistema > Administració > Impressió

---

### Post by orestesmas on 2007-09-08
Com diu el papapep, el tema de la qualitat d'impressió depèn de cada impressora... però definitivament el fet de poder imprimir les pàgines parells o senars no té res a veure amb això, sinó amb la programació del teu escriptori. 

Ara se'm menjaran viu, però diria que això és culpa del Gnome, que no té la gentilesa d'oferir-te aquestes opcions, perquè els seus programadors deuen creure que els usuaris mai no voldran fer coses tan *estranyes* com això de voler imprimir només les pàgines senars. On s'ha vist!!

Si vols, pots provar amb el sistema d'impressió del KDE, que sembla que és una mica més "gentil" en aquests aspectes. No cal que instal·lis tot el KDE si no vols, només cal el paquet "kdeprint" (el qual també instal·larà automàticament unes quantes llibreries de KDE)

En acabat fes "kprinter nom_del_fitxer_a_imprimir" El fitxer pot ser un PostScript, PDF o qualsevol altre format imprimible. Si vols imprimir directament des de l'OpenOffice, o el Firefox primer hauries de ensenyar-los a usar el kprinter enlloc del sistema d'impressió del Gnome...

Pot ser que se t'instal·lin unes quantes llibreries extra, però la comoditat s'ho val.

---

### Post by papapep on 2007-09-08
Aisssss, bon intent Orestes!!! 

A Gnome es pot fer servir **[gtklp]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=gtklp&searchon=names&subword=1&version=all&release=all")**, que també proporciona una bona interfície per a "coses rares" d'impressió, sense haver d'instal·lar llibreries de KDE.

Tot i això, i en favor del "fair play", haig de dir que kdeprint no és un mal sistema ;-)

---

### Post by orestesmas on 2007-09-10
Bé, home! No voldràs que estigui al dia de totes les coses que van sortint per Gnome, oi? Altra feina tinc...

Potser algun dia que ens veiem et sol·licitaré un curset accelerat per posar-me al dia. Com que Gnome és tan senzill, net i precís, suposo que amb 5 minuts en tindrem prou.

P.D.: Clarament haig d'elevar els meus nivells de "fair play"; prometo esmenar-me en el futur... :-)

---

