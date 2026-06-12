---
title: "[SOLVED] Conflicte amb algun programa al voler instal·lar amule"
date: 2008-12-26
forum: Catalan Team
---

### Post by josepss on 2008-12-26
hola amics, soc nou amb aixo de l'ubuntu 8.10, tinc un problema que en vull baixar el amule i em diu que hi ha un conflicte amb un altre programa, que baji al gestor de paquets synaptic, vaig desistalar el programa transmission que venia per defecte amb el cd, per si era aixo, pero següeix igual,e buscat per tot arreu i no dono amb la solució,si elgu em pot indicar com puc trobar aquet programa que don conflicte,parlant d'altre cosa si algu en pot dir si aura alguna trobada mes per explicar l'instal·lació i funcionament de l'ubuntu,ja que quant es va celebrar el d'amer jo encara no estava ficat amb aixo.

gracies per andavant.

---

### Post by josepss on 2008-12-26
> **josepss said:**
> hola amics, soc nou amb aixo de l'ubuntu 8.10, tinc un problema que en vull baixar el amule i em diu que hi ha un conflicte amb un altre programa, que baji al gestor de paquets synaptic, vaig desistalar el programa transmission que venia per defecte amb el cd, per si era aixo, pero següeix igual,e buscat per tot arreu i no dono amb la solució,si elgu em pot indicar com puc trobar aquet programa que don conflicte,parlant d'altre cosa si algu en pot dir si aura alguna trobada mes per explicar l'instal·lació i funcionament de l'ubuntu,ja que quant es va celebrar el d'amer jo encara no estava ficat amb aixo.

gracies per andavant.

nota: no tinc cap coneixament d'angles.

---

### Post by oriolsbd on 2008-12-26
Adjunta'ns el missatge que et dóna. Acostumen a ser força aclaridors, i et podrem ajudar millor.

---

### Post by papapep on 2008-12-26
Benvingut al fòrum, Josep.

Quan tinguis un moment no estaria de més que fessis una bona llegida al fil pels nouvinguts:

[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

i tampoc estaria malament que ens fessis cinc cèntims de qui et/què fas al de benvinguda:

[http://ubuntuforums.org/showthread.php?t=562776](http://ubuntuforums.org/showthread.php?t=562776)

---

### Post by josepss on 2008-12-26
be, oriolsbd, al anar a afageix/elimina aplicacions i marcar amule en surt el següent quadre que diu:senyal de prohibició i el text seguent : no es pot instal·lar <<Amule>>, aquesta aplicació té un conflicte amb un altre programa instal·lat, que heu d'eliminar si voleu instal·lar <<Amule>>
utilitzeu el gestor de paquets Synaptic per solucionar aquest conflicte.
ara bé, com es pot trobar aquest programa que don conflicte amb el synaptic?

gracies.

---

### Post by papapep on 2008-12-26
A un terminal fes:

```
sudo aptitude update
```

quan acabi, que no hauria de trigar gaire, fas:

```
sudo aptitude safe-upgrade
```

i quan acabi, fas:

```
sudo aptitude install amule
```

si et mostra algun missatge d'error en algun dels passos, enganxa'l aquí tal i com et surti.

---

### Post by oriolsbd on 2008-12-26
Quan diu instal·lar des de Synaptics, vol dir fer-ho des del menú "Sistema\Administració\Gestor de paquets Synaptic". Intenta instal·lar l'amule des d'allà.

Les instruccions que t'ha passat el Papapep també són correctes, simplement fetes des de terminal, en comptes de fetes des d'un programa gràfic (realment el Synaptic t'acaba executant, sense que ho vegis, les instruccions que ell t'ha passat). Pots fer el que prefereixis. Des de tots dos llocs et mostrarà els mateixos missatges.

---

### Post by josepss on 2008-12-26
hola, gracies per andavant a oriolsbd i en pepapep per la seva comprensió i les instruccions,en aquets primers passos amb l'ubuntu, ja he instal·lat el amule 2.2.2 via synaptic, ara be acostumat amb l'emule que visitava un portal de descarregues, triava el que volia baixar i clicava el enllaç amb el simbol
de la mula i ja quedava baixat al emule, amb l'amule faig el mateix i a l'hora de clicar el enllaç, amb surt la següent llegenda: avis, el firefox no ha sabut com obrir aquesta adreça, perquè el protocol ( ed2k) no esta associat amb cap programa, i sut una finestreta per clicar d'acord,com es pot resoldre ?, per properes ocasions procurare asabentar-me sobre els meus dubtes, antes de plantejar preguntes al forum, pero era la primera vegada i li tenia panic a fer una destroça.

agrait a tots.

---

### Post by oriolsbd on 2008-12-27
Em sembla que per tal que t'agafi els links d'ed2k has d'instal·lar el paquet "amule-utils".

---

### Post by Quepotser on 2008-12-27
Hola. Jo vaig tenir el mateix problema i el vaig sol.lucionar de la següent manera:

1. Al Firefox ves al desplegable **Edita** i cliques "Preferències". Se t'obrirà una finestra amb una sèrie de pestanyes, clica la que posa "Aplicacions" i all`veuràs dues columnes. A la de l'esquerra hi trobaràs una aplicació que es diu "ed2k" i en la mateixa fila però a la columna de la dreta hi ha una pestanya que diu: "utilitza ed2k (per defecte)", doncs bé cliques a sobre i s'et desplegaran dues o tres opcions i una d'elles diu "altres". Sel.lecciones aquesta i t'apareixerà una finestra,un cop allà tries "Sistema de fitxers" i se t'obrirà una altra finestra. Sel.leciona "usr" i a la finestra que t'apareixerà tries "bin" i encara et sortirà una altra finestra, un cop aquí sel.leciones "ed2k" i cliques a sobre de "Afegeix".

2.A la caixa d'adreces del Firefox escrius: "about:config" apareix un avís terrorific del que has de fer un cas relatiu i tires endavant i a la pantalla que t'apareixarà cliques amb el botò dret, a qualsevol lloc, i sel.lecciones "Nou" i "Logic" i allà escrius:
**network.protocol-handler.external.ed2k** i li donem el valor "true".
Un cop fet això tornes a clicar amb el botò dret a sobre de la pantalla i aquesta vegada sel.leciones: "nou" i "cadena" i escrivim:
**network.protocol-handler.app.ed2k** i li donem el valor: (ho hem d'escriure) "usr/bin/ed2k".

Reinicies el Firefox i ja està. Quan cliquis un fitxer ed2k a qualsevol pàgina enviarà el codi al amule.

Espero no haver-me equivocat en res i que et funcioni.

---

### Post by josepss on 2008-12-28
be, he provat el que m'ha dit (oriolsbd), pero no a funcionat, llavors he fet el deia (quepotser)fins a aplicacions, i alla tant a la colum·na esquerra com dreta no hi ha el que ell diu(e2k), aixi que he borrat amule i he instal·lat transmission 1.34(6778), si en baixo coses de the pirate bay,si que funciona, si me les baixo de una web de torrenst,no funciona i em diu el següent error, no s'ha pogut obrir (fixer), perque l'aplicació de l'ajudant associat no existeix.canvieu l'associació a les vostres preferencies.algu sap com solucionar-lo? 

gracies a tots.

---

