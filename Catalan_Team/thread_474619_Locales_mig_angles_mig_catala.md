---
title: "Locales mig angles mig catala"
date: 2007-06-15
forum: Catalan Team
---

### Post by crazyserver on 2007-06-15
Bona tarda!
A veure si algu em pot donar un cop de mà...
Se m'han desconfigurat els locales, o això suposo...

Faig servir els paquets del repositori:
[http://people.ubuntu.com/~pitti/langpacks/daily/feisty-updates]("http://people.ubuntu.com/%7Epitti/langpacks/daily/feisty-updates")
que s'actualitzen quasi cada dia... en principi creia que era això i tot i que no he provat de tornar enrere, es segueixen actualitzant sense millores...

Només tinc el Locale Català instal·lat al sistema
I en canvi de fa un temps (fara dues setmanes aprox) hi ha moltes coses que em surten en angles, Synaptic, Gaim, Terminal, Rhythmbox, gimp
I altres en català: Firefox, OpenOffice, gedit, geany, menu principal del gnome (tot i que algunes coses en angles)

He provat:  sudo dpkg-reconfigure locales
I no m'ha areglat el problema però us poso la sortida:
```
 Generating locales...
  ca_AD.UTF-8... up-to-date
  ca_ES.UTF-8... up-to-date
  ca_ES.UTF-8@valencia... up-to-date
  ca_FR.UTF-8... up-to-date
  ca_IT.UTF-8... up-to-date
  en_US.UTF-8... up-to-date
Generation complete.
```Més sortides: en fer locale:
```
 LANG=ca_ES.UTF-8
LANGUAGE=ca_ES:ca:en_GB:en
LC_CTYPE="ca_ES.UTF-8"
LC_NUMERIC="ca_ES.UTF-8"
LC_TIME="ca_ES.UTF-8"
LC_COLLATE="ca_ES.UTF-8"
LC_MONETARY="ca_ES.UTF-8"
LC_MESSAGES="ca_ES.UTF-8"
LC_PAPER="ca_ES.UTF-8"
LC_NAME="ca_ES.UTF-8"
LC_ADDRESS="ca_ES.UTF-8"
LC_TELEPHONE="ca_ES.UTF-8"
LC_MEASUREMENT="ca_ES.UTF-8"
LC_IDENTIFICATION="ca_ES.UTF-8"
LC_ALL=
```i en fer locale -a
```
 C
ca_AD.utf8
ca_ES.utf8
ca_ES.utf8@valencia
ca_FR.utf8
ca_IT.utf8
en_US.utf8
POSIX
```Que creieu que pot ser?
A algú més li passa?

---

### Post by AlexMuntada on 2007-06-16
> **crazyserver said:**
> Faig servir els paquets del repositori:
[http://people.ubuntu.com/~pitti/langpacks/daily/feisty-updates]("http://people.ubuntu.com/%7Epitti/langpacks/daily/feisty-updates")
que s'actualitzen quasi cada dia... en principi creia que era això i tot i que no he provat de tornar enrere, es segueixen actualitzant sense millores...

D'entrada no tinc gens clar que sigui una bona idea utilitzar aquest repositori, a menys que estiguis participant activament en la traducció.  Si més no, jo no recomanaria ningú que l'usés perquè no és oficial.

D'altra banda, cal que tinguis en compte que les traduccions comporten molta feina i costa mantenir-les al dia, sobretot quan es produeixen actualitzacions de seguretat o actualitzacions a l'origen (*upstream*) que no s'han incorporat.  D'aquí que et surtin en anglès algunes coses.

Finalment, cal dir que s'estan incorporant noves millores al producte Rosetta del Launchpad, que és el que s'utilitza per a coordinar les traduccions que s'importen de Debian amb les que es fan només a ca l'Ubuntu.  La traducció és una feina complexa i sovint desagraïda perquè hom només se'n recorda quan és incompleta o dolenta ;)

Jo miraria de contactar amb l'equip de traducció al català:
[https://launchpad.net/~ubuntu-l10n-ca](https://launchpad.net/~ubuntu-l10n-ca)
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-l10n-ca](https://lists.ubuntu.com/mailman/listinfo/ubuntu-l10n-ca)

---

### Post by rajoar on 2007-06-16
A veure..., no se si aquesta sol·lució et pot servir... A mi, també em surtia part del programari en anglès i ho vaig sol·lucionar repassant els repositoris ca, -ca, -ca- i ca-. Es veu que, no se ben bé perquè se m'havien desinstal·lat alguns... Tornar-los a instal·lar i... tot a la normalitat!...
Vinga, que tinguis sort!

---

### Post by crazyserver on 2007-06-16
Gràcies per contestar!

D'una banda he desinstalat els paquets dels repositoris aquets, i això no ha solucionat el problema, d'altre he provat d'instalr els que en rajoar em deia, no m'en faltava cap de cap programa que usés però de tota manera n'he instalat algun i segueix igual...

Seguirem provant!

---

### Post by crazyserver on 2007-06-19
Bona tarda,
segueixo tenint el locales a mig terme entre el català i l'anglés i no se que més fer.. m'he desenpallegat de la configuració d'usuari i en un altre usuari nou, tot segueix igual... vaja.. cosa de sistema.. si algu te alguna proposta... jo seguire investigant...

---

### Post by crazyserver on 2007-06-19
Semblo un spammer del foro ara mateix...
Ho he solucionat!
Reinstal·lant tots els paquets d'idioma del català:
He buscat al Synaptic per lang Catalan i els he reinstalat tots
Sembla ser que els fitxers mo d'alguns programes estaven defectuosos...

Moltes gràcies a tothom!

---

