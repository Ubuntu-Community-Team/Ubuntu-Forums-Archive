---
title: "ubuntu no engega en un amd athlon"
date: 2009-03-06
forum: Catalan Team
---

### Post by Josep-Sanz on 2009-03-06
Hola.

He baixat l'ubuntu 8.10 en el mateix ordinador on el volia instal·lar, l'he gravat en un CD, i l'he intentat instal·lar engegant-lo des de la mateixa unitat de DVD on l'he gravat, però s'atura. S'atura tant en mode instal·lació com en mode live CD. Arriba un moment en que el lector de DVD deixa de llegir i es queda el monitor amb el fons de pantalla de l'ubuntu paralitzat.
A més a més, he provat a engegar un portàtil intel centrino en mode live CD amb aquest mateix CD i funciona perfectament.

Algú em pot ajudar?
Em sona que en versions anteriors de l'ubuntu podies triar, a l'hora de baixar-te'l, si volies la versió per a intel o per a amd. Però en la versió 8.10 no he trobat aquesta opció. Sabeu si encara existeix?

Gràcies de bestreta.

---

### Post by oriolsbd on 2009-03-06
Hola, Josep.

A la [pàgina de descàrrega d'Ubuntu]("http://www.ubuntu.com/getubuntu/download"), a baix de tot, hi ha un selector per si et vols baixar la versió de 32 bits o la de 64 bits.

Salut!

---

### Post by albandy on 2009-03-06
exactament quin hw te aquesta màquina?
Model del processador
chipset
grafica 
....

---

### Post by PatrickVogeli on 2009-03-08
si el cd t'arriba a arrancar es que esta ben gravat i la versio es correcta. Tal com ho dius entenc que el sistema es comença a instal·lar i de sobte es para no? No sera algun problema amb el disc dur o el lector? De que igual ja no van fins, dic.

salut

---

### Post by Josep-Sanz on 2009-03-09
> **oriolsbd said:**
> Hola, Josep.

A la [pàgina de descàrrega d'Ubuntu]("http://www.ubuntu.com/getubuntu/download"), a baix de tot, hi ha un selector per si et vols baixar la versió de 32 bits o la de 64 bits.

Salut!

Hola.

Aquest selector l'he vist. M'he baixat la versió de 32 bits.
Amb aquesta no hauria de tenir problemes, no?

Gràcies.

---

### Post by Josep-Sanz on 2009-03-09
Bona pregunta.
Aquesta tarda ho miraré i et respondré.

Gràcies.

---

### Post by Josep-Sanz on 2009-03-09
> **PatrickVogeli said:**
> si el cd t'arriba a arrancar es que esta ben gravat i la versio es correcta. Tal com ho dius entenc que el sistema es comença a instal·lar i de sobte es para no? No sera algun problema amb el disc dur o el lector? De que igual ja no van fins, dic.

salut
Hola.

Home. Podria ser, però el CD el va gravar a la primera. I després, amb un portàtil amb un micro celeron, funciona perfectament: es va iniciar em mode liveCD sense problemes.

Gràcies.

---

### Post by papapep on 2009-03-09
Podries provar amb la versió "alternate":

[http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso](http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso)

a mi a vegades m'ha anat bé en màquines on el CD autònom no m'anava ni a patades.

També hi ha el típic recurs d'anar provant "noapic" i demés modificadors del nucli a l'arrencada.

---

### Post by socderafel on 2009-03-09
jo vaig tindre un problema similar i era el lector, que està un poc cascat...
la 8.10 no arrancava al meu portatil, i a un altre PC si que ho feia perfectament. sempre queda baixar-te la 8.04 i actualitzar a la 8.10, jo és el que vaig fer...

---

### Post by Josep-Sanz on 2009-03-10
> **papapep said:**
> Podries provar amb la versió "alternate":

[http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso](http://releases.ubuntu.com/intrepid/ubuntu-8.10-alternate-i386.iso)

a mi a vegades m'ha anat bé en màquines on el CD autònom no m'anava ni a patades.

També hi ha el típic recurs d'anar provant "noapic" i demés modificadors del nucli a l'arrencada.

Moltes gràcies.

Provaré amb la versió "alternate" i et diré com m'ha anat.
La segona part del teu missatge no l'entenc. Perdona la meua limitació en la coneixença de l'Ubuntu. No sé què és "noapic" ni els modificadors del nucli d'arrencada. Però m'interessa saber-ho. Si tinguessis l'amabilitat d'explicar-m'ho, t'estaria molt agraït.

Salut!

---

### Post by Josep-Sanz on 2009-03-10
> **socderafel said:**
> jo vaig tindre un problema similar i era el lector, que està un poc cascat...
la 8.10 no arrancava al meu portatil, i a un altre PC si que ho feia perfectament. sempre queda baixar-te la 8.04 i actualitzar a la 8.10, jo és el que vaig fer...

Moltes gràcies.

He provat amb el lector de DVD i amb el gravador posant-lo com a master. Amb els 2 em passa el mateix.
De tota manera, d'on puc baixar la versió 8.04? Ho dic perquè a la pàgina de descàrregues de l'Ubuntu només està la versió 8.10, no?

Salut!

---

### Post by Josep-Sanz on 2009-03-10
> **albandy said:**
> exactament quin hw te aquesta màquina?
Model del processador
chipset
grafica 
....

Hola.

La configuració hardware que he trobat del meu PC és la següent:
AMD Athlon(tm) 64 Processor 3000+
2 GHz, 448Mb de RAM
Targeta gràfica: VIA/S3G UniChrome Pro IGP
Chipset: American Megatrends v02.57
L1 cache: 128 Kb
L2 cache: 512 Kb
512 Mb with 64 Mb shared memory
DIMM1: 512Mb/166MHz (DDR333)

Espero que et serveixi.

Salut!

---

### Post by socderafel on 2009-03-10
> **Josep-Sanz said:**
> Moltes gràcies.

He provat amb el lector de DVD i amb el gravador posant-lo com a master. Amb els 2 em passa el mateix.
De tota manera, d'on puc baixar la versió 8.04? Ho dic perquè a la pàgina de descàrregues de l'Ubuntu només està la versió 8.10, no?

Salut!

Ahí va...

[http://releases.ubuntu.com/8.04.2/]("http://releases.ubuntu.com/8.04.2/")

---

### Post by albandy on 2009-03-10
te pinta de ser la gràfica que és molt rara. Prova amb l'alternate o passant-li un paràmetre al kernel del tipus vga=791

---

### Post by Josep-Sanz on 2009-03-10
> **socderafel said:**
> Ahí va...

[http://releases.ubuntu.com/8.04.2/]("http://releases.ubuntu.com/8.04.2/")

Gràcies.

Provaré primer amb la versió "alternate", i si no em funciona provaré amb la versió 8.04

Salut!

---

### Post by Josep-Sanz on 2009-03-10
> **albandy said:**
> te pinta de ser la gràfica que és molt rara. Prova amb l'alternate o passant-li un paràmetre al kernel del tipus vga=791

Gràcies.

Provaré amb la versió "alternate". També me la recomanada papapep. Ja us diré com m'ha anat.
Respecte a passar-li un paràmetre al kernel del tipus vga=791, no sé fer-ho. Perdona la meva ignorància. M'ho podries explicar? Què significa aquest 791? Què aconseguiríem amb això?

Salut!

---

### Post by albandy on 2009-03-11
vga=791 força la pantalla a 1024x768 a 16 bits
Simplement quan hagis seleccionat l'idioma al cd d'instal·lacio, prem F6, t'apareixera una linia que pots editar, treus els parametres "quiet splash" i poses vga=791 despres prems enter

---

### Post by Josep-Sanz on 2009-03-11
> **albandy said:**
> vga=791 força la pantalla a 1024x768 a 16 bits
Simplement quan hagis seleccionat l'idioma al cd d'instal·lacio, prem F6, t'apareixera una linia que pots editar, treus els parametres "quiet splash" i poses vga=791 despres prems enter

Moltes gràcies.

Si no em funciona la versió "alternate" provaré això.
Per a forçar una resolució més baixa, 800x600 a 16 bits, saps quin número cal posar?

Salut!

---

### Post by albandy on 2009-03-11
```


Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795




```

---

### Post by Josep-Sanz on 2009-03-12
> **albandy said:**
> ```


Color depth      | 640x480  800x600  1024x768 1280x1024
-----------------+-------------------------------------
256        (8bit)|  769      771       773      775
32000     (15bit)|  784      787       790      793
65000     (16bit)|  785      788       791      794
16.7 Mill.(24bit)|  786      789       792      795




```

Moltes gràcies.

La veritat és que amb col·laboradors com vosaltres un aprèn força.

Salut!

---

### Post by Josep-Sanz on 2009-03-12
Gràcies a tots.

Ja m'he pogut instal·lat l'Ubuntu amb la versió "alternate".
Ara tinc un altre problema: el grub no funciona.
Obro un nou tema en el fòrum per a que tothom el pugui veure sense necessitat d'arribar al final d'aquest.

Salut!

---

### Post by Josep-Sanz on 2009-04-06
Ja ho he solucionat.
El problema era, efectivament com algú m'havia dit, la targeta gràfica.
Feia servir la que estava integrada a la placa base.
Vaig posar una que tenia per ahí, connectada al port AGP i s'acabaren els problemes. Ara l'Ubuntu ja engega perfectament.
Gràcies a tots.

---

