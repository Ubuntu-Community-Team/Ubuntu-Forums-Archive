---
title: "Un cuc a l'Ubuntú?"
date: 2007-03-22
forum: Catalan Team
---

### Post by saballars on 2007-03-22
Hola!

Sóc molt novato en tot aquest món i per això hauria de ser més prudent... El cas és que no sé què he fet que em sembla que se m'ha petat el sistema per culpa d'un cuc. Ara l'Ubuntú ja no arrenca com abans, amb el logo, la barra de procés, sinó directament amb els Ok de no sé què (no sé si m'explico). I després d'escriure el nom d'usuari i la contrasenya em surt un mena de programa amb el dibuix d'una espècie d'escarbat (o això m'ha semblat a mi) que si no recordo malament en el nom tenia la paraula grub. Li vaig dient endavant, sense entendre res del que em diu, i al final em demana un correu electrònic que, per a més inri, no me'l reconeix quan li escric. Total, que em sembla que hauré de tornar a instal·lar tot l'Ubuntú (el tinc particionat amb Windows), però no m'importaria perquè no hi tinc cap arxiu, fa quatre dies que me'l vaig instal·lar.
Què m'aconselleu? Puc tornar a instal·lar l'Ubuntú? Com ho haig de fer perquè no faci més particions del disc dur?
Gràcies per endavant!!!

Saballars

---

### Post by RainCT on 2007-03-22
Hola,

Dubto molt que pugui ser un virus.

Pel que expliques diria que els deus haver espatllat d'alguna manera de forma o bé has desactivat la pantalla splash d'arrancada. La finestra aquesta amb l'escarbat que comentes és la eina d'informa d'errades.

Segurament no serà necessari reinstal·lar-lo, si ens dónes més detalls segur que algú dels que volten per aquí et pot ajudar, tot i que potser si què és ho més ràpid si encara no hi tens res.

---

### Post by saballars on 2007-03-22
Perdoneu que abans no us hagi donat més dades, però és que des d'on estava no em podia connectar al meu ordinador. Ara sí que ho he pogut fer. Us n'explico els detalls.
Quan arrenca tot és ok excepte el "sembling RAID arrays". Després de posar el nom d'usuari i la contrassenya em surt aquest missatge: "S'ha produit un error en arrencar el GNOME setting Deamon. Algunes coses com els temes, el so o la configuració del fons podrien no funcionar correctament." I afegeix: "L'últim missatge d'error va ser: The name org.gnome.SettingsDaemon was not provided by any service files"
I al mateix temps se m'obre aquell programa que comentava abans i que en realitat es diu: Bug Buddy. No entenc res del que em diu, o em sembla entendre que haig d'explicar quin problema tinc (i fer-ho en anglès!!!).
A veure si algú sap què puc fer, i si em puc evitar reiinstal·lar-ho tot, millor, perquè si no encara em carregaré més coses...
Salut!

saballars

---

### Post by saballars on 2007-03-22
Abans m'he oblidat de dir que puc entrar a totes les aplicacions i al sistema, i dels Llocs no puc entrar ni a Escriptori ni a carpeta d'inici, ni Ordinador... en definiva, enlloc.

---

### Post by jomateix on 2007-03-23
Hola!

No sé que li deu haver passat al teu ubuntu... sembla com si tinguessis algun paquet trencat. Pots provar d'executar:

```
sudo dpkg --configure -a
```

en una consola (prem "CTRL + ALT + F1" si no et funciona el gnome-terminal, despres "ALT + F7" per tornar al gnome). Aquesta comanda et configurarà de nou tots els paquets que tinguis instal·lats. Et farà un munt de preguntes... si no saps el que et demana, accepta l'opció per defecte.

Si això no funcionés, jo instal·laria de nou :| ... total, tampoc no triga tant...

---

### Post by saballars on 2007-03-24
Hola!

No estava segur que intal·lant de nou l'Ubuntú no em carregués res més, però al final m'he decidit i m'ha sortit bé. Així, doncs, torno a tenir l'Ubuntú. Problema solucionat.
Gràcies.

---

