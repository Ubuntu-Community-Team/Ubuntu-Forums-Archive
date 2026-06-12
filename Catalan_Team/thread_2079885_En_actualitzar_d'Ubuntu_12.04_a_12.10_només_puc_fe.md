---
title: "En actualitzar d'Ubuntu 12.04 a 12.10 només puc fer una &quot;actualització parcial&quot;"
date: 2012-11-02
forum: Catalan Team
---

### Post by 19preguntes on 2012-11-02
Hola,
inicio el procés d'actualització de l'Ubuntu 12.04 al 12.10, i al cap de poc apareix un avís, que podeu veure a la imatge adjunta, dient que només puc fer una actualització parcial. Abans de ficar la pota, he preferit cancel·lar el procés i preguntar.

Abans de fer l'actualització d'una versió a l'altra de l'Ubuntu, he fet una comprovació amb el gestor d'actualitzacions, o sigui que estic segur que l'Ubuntu 12.04 estava ben actualitzat abans d'iniciar el procés.

Què em recomaneu que faci?

Gràcies!

---

### Post by 19preguntes on 2012-11-02
Potser hauria de suprimir totes les PPAs externes, com diuen [aquí]("http://askubuntu.com/questions/203301/how-to-safely-upgrade-from-ubuntu-12-04-to-12-10")?

---

### Post by wgarcia on 2012-11-03
Sí, s'han de inhabilitar totes les fonts de programari de ppa i altres fonts externes o de tercers. Però en principi el gestor d'actualitzacions ja ho fa això, inhabilitar les fonts de tercers, així que pot ser hi hagi algun altre paquet que estigui fent la guixa. 

A mi aquest tipus d'actualitzacions se'm van completar iniciant-les, i quan  surt el missatge que dius instal·lant manualment els paquets retinguts (és a dir fent "sudo apt-get install <paquets retinguts>"), i usant aquestes comandes per completar:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install -f
```
```
sudo apt-get dist-upgrade
```
```
sudo apt-get autoremove
```

A vegades repetint aquestes instruccions diversos cops.

És un procés llarg fins que acaba de baixar i instal·lar tots els paquets, i com sempre sota la teva responsabilitat, a mi m'ha funcionat molts cops però si la instal·lació queda a mitges és molt probable que s'hagi de tornar reinstal·lar tot.

---

### Post by 19preguntes on 2012-11-04
Gràcies wgarcia!
això de que "pot ser hi hagi algun altre paquet que estigui fent la guixa" m'ha fet preguntar-me quin paquet podia ser, i l'he trobat
 :) Era el unity-dodge-windows, que vaig instal·lar-me just després d'actulitzar a Ubuntu 12.04 per millorar una mica el comportament de l'autohide de la barra lateral de Unity.

Eliminat aquest paquet, he pogut actualitzar a l'Ubuntu 12.10 sense problemes.

Salut!

---

