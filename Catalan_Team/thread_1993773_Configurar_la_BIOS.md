---
title: "Configurar la BIOS"
date: 2012-06-02
forum: Catalan Team
---

### Post by joaquimrubio on 2012-06-02
Voldria instal·lar la versió 12.04  LTS a un portàtil Asus sèrie A53S amb processador i.7 i BIOS de American Megatrends. 
Ja he gravat un DVD amb la imatge del programa descarregat des del lloc web Caliu.
El portàtil no engega per defecte des del DVD i voldria configurar la BIOS per tal que ho fes. A l'arrencar pressiono F2 i accedeixo a la BIOS. Amb les fletxes em canvio de MAIN a BOOT. Allí em surt:
BOOT CONFIGURATION:
UEFI BOOT
PXE ROM

Boot option. Priorities:
Boot option #1            Disabled in BBS order
Boot option #2            [PO: Hitachi HTS 547...]

Hard Drive BBS Priorities:
CD/DVD ROM Drive BBS Priorities
Delete Boot Option

I quan arribo aquí ja no sé que més he de fer...
Algú em pot ajudar?

---

### Post by kimet on 2012-06-03
Prova canviar 'boot option #1' i deixa-ho en 'enabled'.

Salut.

---

### Post by joaquimrubio on 2012-06-03
No existeix aquesta opció. 
Si el selecciono, apareixen 2 opcions: 
1.- Disabled
2.- La que està selecionada: Disabled in BBS order.

Gràcies.

---

### Post by joaquimrubio on 2012-06-15
Reitero la consulta. Com ho haig de fer per a modificar la BIOS?

---

### Post by Jautenim on 2012-06-16
La segona entrada té tota la pinta de ser el teu disc dur principal (Els Hitachi HTS són una gamma de discs durs). Prova canviant aquella entrada per una altra. Estic segur que si al Boot Option #2 poses la lectora de DVDs t'arrencarà des del disc. (Sobretot a l'acabar recorda tornar a canviar l'entrada per Hitachi HTS... o potser no podràs arrencar l'ordinador).


D'altra banda, per una altra vegada que hagis de fer una instalació com aquesta et recomano que utilitzis una memoria USB en comptes de gastar cèntims cremant un disc. Fent servir algun programet per Windows com l'Universal USB Installer* només li has d'indicar quina és la lletra de la unitat on tens conectada la memòria i quina .iso vols fer servir i ja t'ho prepara automàticament (vigila no hi tinguis res important guardat que un cop ho tenen tot llest el primer que fan aquests programes és formatejar la memòria...)


* [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by wgarcia on 2012-06-17
Des d'Ubuntu amb el creador de disc d'arrencada també permet crear una memòria USB amb la imatge de l'Ubuntu "autònoma", és a dir que es pot arrencar. Però la BIOS també hauria de tenir una opció per dir-li que arrenqui des del port USB. Normalment les BIOS el que fan és decidir l'ordre, i posant abans l'USB o el CD/DVD ja és suficient, si no hi ha res aquí automàticament passa a arrencar des del disc dur.

---

### Post by joaquimrubio on 2012-06-17
Gràcies Jautenim i Wgarcia, aviat ho tornaré a intentar.

Un dubte que m'ha sorgit llegint el tema de l'USB, si configuro la BIOS per començar per CD/DVD, això també inclou els ports USB? 

(Justament no utilitzo la possibilitat de Ubuntu de gravar en memòries USB el nou Ubuntu ja que no sé com configurar la BIOS per tal que comenci des del port USB).

Joaquim

---

### Post by wgarcia on 2012-06-18
Normalment l'arrencada des del port USB apareix com una opció separada, almenys als BIOS que he vist recentment

---

### Post by joaquimrubio on 2012-06-18
Gràcies.

Ara ja tinc el DVD gravat, però ho provaré la propera vegada.

---

### Post by joaquimrubio on 2012-06-30
Ja he pogut configurar la BIOS, primer s'ha de posar en disabled la segona opció, que és el disc dur com molt bé va suposar Jautenim, aleshores es pot posar com a primera opció el DVD. Un cop posat com a primera opció el DVD he posat com a segona el disc dur. així no calia tornar-ho a canviar. F10 per desar els canvis i Save & Exit. I al tornar a engegar ja ho fa des del DVD. Ubuntu 12.04 instal·lat sense més entrebancs.

---

