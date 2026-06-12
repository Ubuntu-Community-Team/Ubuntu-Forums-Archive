---
title: "[SOLVED] repositoris"
date: 2007-10-23
forum: Catalan Team
---

### Post by muleta on 2007-10-23
Tinc la carpeta /etc/apt/sources.list buida.

Què he de fer per activar els repositoris?.

---

### Post by patrickfromspain on 2007-10-23
/etc/apt/sources.list no es una carpeta. Estas segur de que ho tens buit? En un terminal gksudo gedit /etc/apt/sources.list

Per a gutsy:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse

Per a feisty (7.04) cambia gutsy per feisty i ja esta.

salut

---

### Post by RainCT on 2007-10-23
Si no necessites descarregar el codi font dels paquets per res (cosa que dubto que et faci falta), tens prou amb les següents línies:

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse


Les que comencen amb deb-src, que són per al codi font, només fan perdre ample de banda i alenteixen la comprovació d'actualitzacions noves si no es fan servir (encara que tampoc passa res greu si les deixes, però això, no fan falta).

---

### Post by CarlesOriol on 2007-10-24
Directament al synaptic a:

paràmetres > repositoris > 

a Programari ubuntu actives totes les fonts (codi font si el requereixes)

i 

a Actualitzacions . Marca com a mínim les dues primeres.

---

### Post by muleta on 2007-10-24
Ja ho tenia bé. Gràcies.

---

