---
title: "Dubte amb les particions"
date: 2009-11-16
forum: Catalan Team
---

### Post by Leirdalag on 2009-11-16
Hola a tots!

Per començar voldria demanar disculpes, segur que el tema està explicat per algun lloc, però sóc un poc inútil i no m'en surto amb la informació que trobo.

La situació es la següent:
En un principi tenia el meu PC, amb dos discs durs de 500G, unitat C: amb Windows Vista; unitat E: buida; y una petita unitat D: (FACTORY IMAGE) que no tinc ni idea del que es.

Vaig voler instal·lar l'ubuntu, que havia estat provant amb el Wubi i aquí es quan la vaig liar.
A l'intal·lar l'ubuntu vaig optar per conservar Windows i crec que se m'ha intalat en la unitat E:
Fins aqui correcte, tinc tots dos sistemes operatius i he passat els arxius importants que tenia a Windows a la unitat E: i els he copiat a l'escriptori de l'ubuntu, que encara no entenc les rutes dels arxius i no se on tenir-los.
Ara simplement voldria esborrar Windows i disposar de tot el PC per a l'ubuntu.
Algú em podria ajudar? he descarregat l'eina Gparted però no m'en surto.

Simplement vull tenir l'ordinador com si vingues de fàbrica amb l'ubuntu, però conservant els documents que acabo de passar a l'escriptori de l'ubuntu.

---

### Post by papapep on 2009-11-16
Abans de res, assegura't de tenir una còpia dels teus documents fora dels discs durs, per si "les eventualitats"...

> que encara no entenc les rutes dels arxius i no se on tenir-los

Això és prou normal en fer "el salt". Ja hauràs vist que aquí de C: (i similars) rien de rien.
Tens diversos directoris (carpetes a l'entorn gràfic) a /home/elteusuari, que són per desar els teus documents, imatges, música, etc. Allà és el lloc correcte.
Després hi pots accedir de manera simple anant a Llocs al menú de la barra superior.

Respecte el teu tema dels discs: jo optaria, considerant que pel que tu mateix dius ets novell, i sempre un cop tinguis les teves dades ben conservades en còpia de seguretat a banda, per una instal·lació neta des de 0, liquidant tot el que hi ha actualment al disc dur primari (el teu C:). Podries fer invents i canviar un disc dur per altre, refer el grub, o moure les dades d'un lloc a l'altra...però tot plegat se't farà molt coll amunt (crec jo).

Per cert, assegura't de crear una partició a banda pel teu /home, així t'estalviaràs feina en posteriors instal·lacions.

> una petita unitat D: (FACTORY IMAGE) que no tinc ni idea del que es

Aquesta deu contenir la imatge comprimida de "l'altre" sistema operatiu per restaurar-la de manera automàtica al teu disc dur en cas de necessitat (Factory image --> Imatge de fàbrica).

Benvingut al fòrum, Leirdalag.

---

### Post by Leirdalag on 2009-11-16
Gràcies per la resposta papapep. Crec que optaré per fer com dius, salvaré totes les dades importants i començaré de 0.

Pero ara em surgeix un nou dubte respecte al que dius (ok, acabo de descubrir que tampoc se fer "quotes" ¬¬' que frustrant xD) 

Et semble un bon procediment, que desde "l'altre S.O" formategi la unitat E on ara tinc l'ubuntu i després amb el CD de l'ubuntu formategi la unitat C? que faig de la unitat D (factory image) l'elimino,oi? Es que no vull fer un desastre.

Estic fet un mar de dubtes ^^

---

### Post by papapep on 2009-11-16
> Et semble un bon procediment, que desde "l'altre S.O" formategi la unitat E on ara tinc l'ubuntu

Jo ja passaria olímpicament de "l'altre" :D

Instal·la l'Ubuntu al disc primari, recorda fer la partició /home a banda, i un cop el tinguis instal·lat ja marranejarem el disc secundari. 
L'important és que tinguis ben desadetes les dades, la resta és molt simple.

> acabo de descubrir que tampoc se fer "quotes"

Tens dues opcions: o fas clic a l'icona que és com una bafarada de còmica al damunt de l'editor dels posts, o fiques el text que vols citar entre les etiquetes 
**QUOTE** i **/QUOTE** (has de ficar-ho entre [], però si ho faig ara no ho podràs veure).

---

### Post by Leirdalag on 2009-11-16
Ok! Faré el que em dius!

> recorda fer la partició /home a banda

Abans de donar el tema per resolt, em podries explicar això si us plau?
Gràcies per les respostes i perdó per la meva ignorància :oops:

---

### Post by papapep on 2009-11-16
> perdó per la meva ignorància

Ningú ha nascut ensenyat, no pateixis pas. Qui s'ha d'avergonyir és qui no vol aprendre, no qui no sap alguna cosa i la pregunta ;)

Així doncs, a l'hora de particionar el disc, has de triar particionat manual, i crear, com a mínim, una partició de uns 20-30 Gb per al directori arrel (d'on pengen la resta de directoris) i la resta per al /home, que serà on desaràs tots els teus documents i fitxers de configuració de programes. Es poden fer més filigranes, però crec que amb això ja tens prou per començar.
Amb això el que aconsegueixes, és que si has de reinstal·lar el sistema, deixes la partició /home sense tocar i no has de patir per tots els fitxers que hi tens, instal·les el sistema operatiu a / i ja està.
No sé si m'he sapigut explicar. En tot cas, no dubtis en preguntar.

Per cert, potser t'ajudaria a entendre una mica l'estructura de directoris del Gnu/Linux llegir [aquest article]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#Organitzaci%C3%B3%20del%20sistema%20de%20fitxers") que tenim al wiki de l'equip.

---

### Post by Leirdalag on 2009-11-16
Ok! Ara si!
Moltes gràcies!
Declaro el fil solucionat!
Estic llegint l'enllaç que m'has passat i tinc ganes d'aprendre a utilitzar bé l'ubuntu així com entendre millor tot el que envolta al programari lliure, així que segur que ens seguim veient pel fòrum!

---

