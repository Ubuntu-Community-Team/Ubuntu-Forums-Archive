---
title: "[SOLVED] M'he quedat sense so!"
date: 2007-09-15
forum: Catalan Team
---

### Post by crazyserver on 2007-09-15
Bon dia a tothom!

Us explico una història de Terror...
Tinc un disc dur SATA de 200Gb d'una coneguda marca de discos que comença per MAX i acaba de TOR, en una caixa extraïble que només utilitzo per dades (en un rack, doncs el disc de sistema està intern i es IDE). Doncs bé, es veu que les connexions de la caixa son molt dolentes i que de tant en tant fallen, i quan el buffer d'escriptura no es pot escriure a disc i està ple, el sistema falla i es penja. I direu... que té a veure amb el so això? Doncs poc a poc...

La cosa es que dimecres nit, en apagar l'ordinador plenament operatiu, durant l'apagat es va quedant a la fase de Desactivant la Swap, vaig pensar que seria un error del mateix sistema de disc dur i tal i vaig acabar apagant a la brava, doncs bé, divendres en encendre'l,  em va demanar manteniment (Control+D) Jo això ja sse que vol dir en el meu cas: encendre amb mode de recuperació i que faci els commits del Journaling. Dit i fet, engego el PC, i com si fos nou, obre l'ubuntu... PERO, no hi ha so. el control de volum està tot mutat i tot a 0, pujo els controls pero segueixo sense so.

RESUM:
tinc dues targetes de so, la VIA interna de moltes plaques, i una SBLive5.1 a la BIOS està deshabilitada la primera (tot i que mai he tingut problemes amb habilitar-la, doncs funcionava igualment bé) utilitzo sempre la segona. I en un altre sistema operatiu funciona perfectament.

Algú té alguna idea? He mirat els sistemes multimedia i de so, he mirat altres forums... i res.

Moltes gràcies!

---

### Post by CarlesOriol on 2007-09-15
Eps.!

has comprovat que tots els canals necesaris a la sb estan activades? Al mesclador: pcm, general i front.

Es possible que usis kde i hagis fet una incursió en gnome darrerament? El volum general d'ambdos escriptoris canvia (pcm vs front) i el mute també.

---

### Post by crazyserver on 2007-09-15
Doncs PCM mmm diria k no.. provaré, però no... no uso KDE ni penso usar-lo amb Gnome estic prou bé!

Llarga Vida a Gnome!!!

D'altra banda he provat diverses coses a la configuració del so i he aconseguit que la "Prova" faci piiip pels altaveus, tot i que no es a configuració amb la que abans funcionava i els programes segeuxisen sense sentir-se, en quant pugui provar lo del so, us explico el què!

Gràcies!

---

### Post by crazyserver on 2007-09-16
Ue ue ue!!! Doncs si CarlesOriol! Estaves en el cert... un volum que es diu Wave estava mutat també (i no es mostrava, clar...) ... ara ja tot està correcte, 

moltes gràcies!!

---

