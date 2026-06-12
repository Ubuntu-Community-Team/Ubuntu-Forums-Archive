---
title: "Gestió de disc dur"
date: 2007-02-21
forum: Catalan Team
---

### Post by sergix on 2007-02-21
hola,
Soc un nou usuari de GNU i no en se gaire, espere que em pogueu ajudar...

Tinc un disc dur de 60 gb (57 reals). Actualment el tinc al 90% en ús , però la carpeta Home te menys de 10gb, i no sóc capaç de trovar amb que coi estic gastant la resta de memoria.
A les carpetes amagades he trovat uns gigas més..però m'hen falten un munt!!
La meva pregunta seria: Hi ha alguna aplicació per gestionar el disc dur , que hem permetés veure totes les carpetes i els seus tamanys?
                gracies

---

### Post by benjami on 2007-02-21
Gràfic, el filelight: [http://en.wikipedia.org/wiki/Filelight](http://en.wikipedia.org/wiki/Filelight)

No gràfic, du.  Exemple:

$ sudo du -h --max-depth=1 /etc
68K     /etc/network
164K    /etc/default
16K     /etc/skel
[...]
14M     /etc

---

### Post by patrickfromspain on 2007-02-21
podries mira la carpeta /var y podries fer un sudo apt-get clean

---

### Post by marcoil on 2007-02-23
La darrera versió d'Ubuntu ve amb el Bonsai, una molt bona aplicació per fer exactament això. La trobaràs al menú d'Aplicacions, dins Accessoris, com a "Analitzador de l'ús dels discs".

Per analitzar-ho tot (compte! poc tardar bastant) pitja a "Sistema de fitxers", o si vols analitzar una carpeta en concret, pitja a "Carpeta" i selecciona-la.

Esper que t'hagi servit!

---

### Post by CarlesOriol on 2007-02-26
És diu **baobab**

> **marcoil said:**
> La darrera versió d'Ubuntu ve amb el Bonsai, una molt bona aplicació per fer exactament això. La trobaràs al menú d'Aplicacions, dins Accessoris, com a "Analitzador de l'ús dels discs".

Per analitzar-ho tot (compte! poc tardar bastant) pitja a "Sistema de fitxers", o si vols analitzar una carpeta en concret, pitja a "Carpeta" i selecciona-la.

Esper que t'hagi servit!

---

### Post by marcoil on 2007-02-26
> **CarlesOriol said:**
> És diu **baobab**

Tens tota la raó, perdonau :)

---

### Post by CarlesOriol on 2007-02-28
Una altra manera també ben xula és si tens instal·lat kde amb el **konqueror** un cop ets dins d'una carpeta anar a [FONT="Courier New"] Visualitza > Mode de vista > Vista de mides de fitxers[/FONT].

---

