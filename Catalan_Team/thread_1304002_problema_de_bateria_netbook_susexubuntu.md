---
title: "problema de bateria netbook suse/xubuntu"
date: 2009-10-28
forum: Catalan Team
---

### Post by kilian_cuerda on 2009-10-28
Hola a tothom, m'he comprat aquesta setmana un netbook Lenovo S9e, que venia amb Suse Linux Enterprise Desktop 10 preinstalat, i, com em resulta un poc confús en alguens coses (bé, un poc nou, m'aclare millor amb Ubuntu, que és el linux que he deprés), havia pensat en instalar-le Xubuntu 9.04.
Ara però, he preparat un pendrive per autoarrancar el xubuntu, i tot bé, però m'he percatat que mentre estava el pendrive amb xubuntu (mode provar sense instalar res) funcionant, tot bé però la bateria, en el moment de màxima càrrega, i començant a descarregar-se em donava una duració aproximada de 1 hora 50 minuts, quan amb el suse linux dona, en les mateixes condicions de càrrega total, 2 hores 34 minuts. Això perquè podria ser? si instalara Xubuntu, no hauria de ser la capacitat de càrrega de la bateria la mateixa, en teoria? Moltes gràcies per anticipat.

---

### Post by jaume69 on 2009-10-29
Podries provar amb un CD Live **Xubuntu.**
:o

---

### Post by kilian_cuerda on 2009-10-29
Ehmmm... el netbook no té lector de cd

---

### Post by jaume69 on 2009-10-29
Podries també mirar un **HD** extern..$..
Encara que tampoc hi ha tanta diferencia l´una amb l´altre distribució,44 minuts.
No sé..

---

### Post by PatrickVogeli on 2009-10-29
Jo el que tinc fet es un script per aplicar algunes opcions d'estalvi energetic que no venen activades per defecte: de la wifi, del sata, del pci-express, augmento el temps entre escritures del disc dur i alguna cosa més em sembla. 

A més, faig servir kernels baixats de kernel.org i els compilo amb el pedaç per poder baixar el voltatge del processador i que encara gasti menys.

Aqui hi pots trovar alguns consells útils per intentar augmentar l'autonomia: [https://wiki.ubuntu.com/CatalanTeam/Recursos/IncrementarAutonomiaPortatil](https://wiki.ubuntu.com/CatalanTeam/Recursos/IncrementarAutonomiaPortatil) Tingues en compte que el tema de baixar el voltatge s'ha provat en pc's amb un core 2 duo serie T, un Core 2 Solo SU3500 i un Pentium Dual Core SU4100, però no crec que et funcioni en un Atom.

Salutacions

---

### Post by jdk9 on 2009-10-29
Mira't aquest [post]("http://ubuntuforums.org/showthread.php?t=1278530"), potser et serveixi

A PatrikVogeli: He mirat el tutorial aquest que has enllaçat, i em trobo amb que quan faig lsmod | grep acpi_cpufreq no em retorna res, com ara quan vull saber si és el driver de la targeta de wifi que uso, tampoc em retorna res. Uso Ubuntu 9.10, i el processador és un Centrino duo T5470. A que deu ser degut? M'extranya la veritat, ja que el driver de la targeta de wifi, quan faig un lspci | grep network em diu que l'uso, i si "li faig dir expressament", no em retorna res. Potser és que no ho faig bé, o que no usa cap de les dos coses, però no deixa d'estrenyar-me.

---

### Post by PatrickVogeli on 2009-10-31
ah, si. Es veritat. Aquell tutorial esta escrit per a la 8.10, quan acpi_cpufreq era un modul. A partir de la 9.04 ho han canviat i ara esta integrat al kernel. A veure si algun m'aixeco amb ganes i refaig els articles que tinc al wiki.

Aqui en parlen: [http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67](http://www.linux-phc.org/forum/viewtopic.php?f=13&t=67)

Salut

---

### Post by kilian_cuerda on 2009-10-31
Hola, l'altre dia vaig preparar un pendrive amb, aquesta vegada, xubuntu 8.04. Bàsicament, m'he donat compte que les estimacions de temps de descàrrega, amb xubuntu (varis) i suse varien entre les 2 i les 2'50 hores, cosa que no està malament. Així, crec que instalaré de totes maneres xubuntu 8.04. Moltes gràcies per les vostres observacions i indicacions sobre l'estalvi energètic, prendré bona nota, no només per al netbook. Salut!

PD: Això, que com he dit: estimacions. Al situar el cursor sobre l'icona de bateria, donava 1h 50 min., i al punxar i entrar en bateria, 2h 50min. El temps real venia a ser unes dos hores i pico, variable.

---

### Post by pauelmaco on 2009-11-01
Una cosa que a mí hem fa estalviar molta bateria i que fa que hem duri 1 hora i 10 minuts més és la comanda "powersave". Aquesta comanda, s'encarrega de estalvial energia. Ja va incluïda en l'ubuntu, per activar-la només has d'escriure:

"pm-powersave True"

I després posar-la a les aplicacions d'inici perquè cada cop que arrenquis ja s'activi l'estalvi d'energia.

---

### Post by kilian_cuerda on 2009-11-01
HM! interessant, i pareix molt fàcil (ideal per a mi, vaja, que encara sent això de "compilar" i m'acollone front a allò desconegut). Prenc també bona nota. Gràcies!

---

### Post by pauelmaco on 2009-11-02
De res home!!

---

