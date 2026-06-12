---
title: "k3b en català"
date: 2007-08-23
forum: Catalan Team
---

### Post by farig on 2007-08-23
Anteriorment havia instal·lat el programa k3b des del meu afegeix/elimina programes i se m'havia instal·lat en català i ara per més que ho intento no ho puc fer, algú sap el truquillo per que s'instal·li en català?
é que l'anglès, la veritat, no se'm dóna gaire bé!
Faraig

---

### Post by papapep on 2007-08-23
Ostres...és curiós...i la resta de programari la tens en català???

Prova a tornar a anar a Sistema > Administració > Suport d'idioma i verifica que el català estigui marcat i sigui l'idioma per defecte.

---

### Post by guillemsola on 2007-08-23
A mi em passa el mateix, el k3b està en anglès. Vaig provar a instal·lar des de synaptic un paquet de k3b que no estava instal·lat.

> Internationalized (i18n) files for k3b 
This package contains the translations for k3b.

K3b is a GUI frontend to the cd recording programs cdrdao and cdrecord.  Its
aim is to provide a very user friendly interface to all the tasks that come
with cd recording.

però sense èxit.

salut!

---

### Post by CarlesOriol on 2007-08-23
sudo apt-get install kde-i18n-ca

---

### Post by patrickfromspain on 2007-08-23
sudo apt-get install kde-i18n-ca k3b-i18n

salut

---

### Post by pserra on 2007-08-23
Deus tenir alguna cosa mal configurada,jp ho vaig fer a través de Aplicacions->afegeix/elimina i perfecte i en català a la primera.
UNA PEGUNTA....... algun dia hi ha hagut algun programa que potser se m'ha instal·lat a mitges....o  sigui que no el tinc instal·lat del tot....  hi ha alguna manera o
programa de fer neteja? no he trobat rés per enlloc....O es que l?ubuntu ja ho fa sol?
Perquè vaig una mica 'justet d'espai'....
A reveure..

---

### Post by farig on 2007-08-23
M'ha funcionat això que m'ha dit el sudo apt-get install libk3b2 libk3b2-mp3 k3b-i18n del  patrickfromspain . Moltes gràcies.Ara ja em funciona en català

---

### Post by pespin on 2007-08-23
> hi ha alguna manera o programa de fer neteja?

per a netejar paquets descarregats tens
$ sudo aptitude clean
$ sudo aptitude autoclean

també hi ha una aplicació anomenada KleanSweep, però m sembla que per al Gnome n'hi havia una semblant més adequada

[Edit] aqui hi ha la pàgina d'on vaig treure la info del KleanSweep i tots aquests: [http://www.microteknologias.cl/linux_herramientasdisco.html](http://www.microteknologias.cl/linux_herramientasdisco.html)

---

### Post by muleta on 2007-08-23
Pere,

mira què em diu en Papapep: "Jo personalment no te'n recomano cap, perquè no cal. Si fas servir el sistema d'Ubuntu d'instal·lació de paquets ell mateix s'encarrega de mantenir el sistema net i polit.
Quan instal·les un paquet ell controla què i on ho posa, i si ho esborres amb les comandes adeqüades o des d'el Synaptic ell s'encarrega de fer dissabte i deixar-te el sistema en ordre."

---

### Post by pserra on 2007-08-23
Merci,
deu ser que el Synaptic em mante l'ubuntu net perquè he executat les 2 comandes i el resultat ha estat neteja.:0 KB
Merci companys..

---

### Post by muleta on 2007-08-23
El KleanSweet està en els repositoris d'Ubuntu però, si l'instal·les, l'hauràs d'executar com a Root.

---

### Post by guillemsola on 2007-08-24
Pot ser que el k3b s'instal·li en anglès per defecte pq és una aplicació KDE i l'ubuntu porta gnome?

Ho dic pq en instal·lar el  *kde-i18n-ca* també m'instal·la 30Mg amb 

[I]language-pack-kde-ca language-pack-kde-ca-base
[/I]
això deuen ser els paquets de català sencers per a KDE no?

gràcies.

---

### Post by CarlesOriol on 2007-08-24
També tens la opció autoremove per eliminar aquells paquets que s'han installat per dependencies i que ja no son necesaris.

---

### Post by CarlesOriol on 2007-08-24
reservori	;) Genial!! 

La proposo com a paraula del mes.

---

### Post by SiscoGarcia on 2007-12-06
Jo també m'he trobat amb aquest problema del K3b en català i ho he fet com expliqueu al fil. El que ho entenc és com fer l'autoremove que proposes Carles.

---

### Post by CarlesOriol on 2007-12-07
sudo apt-get autoremove

i per fer neteja de les descarregues:

sudo apt-get autoclean

---

### Post by albert-I on 2007-12-07
Parlant que jo tinc Xubuntu, pero aquest es molt similar amb el programari amb ubuntu, el xubuntu porta xfburn aixi com el K3b es una aplicació de kde

> **angrychai said:**
> Pot ser que el k3b s'instal·li en anglès per defecte pq és una aplicació KDE i l'ubuntu porta gnome?

Ho dic pq en instal·lar el  *kde-i18n-ca* també m'instal·la 30Mg amb 

[I]language-pack-kde-ca language-pack-kde-ca-base
[/I]
això deuen ser els paquets de català sencers per a KDE no?

gràcies.

---

