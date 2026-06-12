---
title: "Sense accents a l'Ubuntu 16.04"
date: 2016-05-07
forum: Catalan Team
---

### Post by oriolberga-e on 2016-05-07
Hola.

S´oc un ubuntaire novell que vaig instal·lar en un ordinador reciclat el 15.10 i acte seguit vaig actualitzar-lo al 16.04. Quan el faig c´orrer amb Gnome la vista cl`assica de sempre (posant botons de tancar, minimitzar i maximitzar a la dreta) els accents surten com veieu en aquest text. Aix`o no passa a l'escriptori per defecte. Sabeu a qu`e pot ser degut?

Moltes gr`acies!!

---

### Post by wgarcia on 2016-05-07
Saps exactament quin escriptori estàs fent servir? El MATE?, o el Gnome amb el "mode clàssic", o quin?

---

### Post by oriolberga-e on 2016-05-07
Quan surto de la sessi´o per canviar l'escriptori tinc les opcions:

Gnome Flashback (Compiz)
Gnome Flashback (Metacity)
Ubuntu (per defecte)

Entenc que ´es un Gnome en mode cl`assic (?)

L'error dels accents passa en les dues opcions flashback, per`o no a la que ve per defecte.

---

### Post by wgarcia on 2016-05-07
A "Paràmetres del sistema" -> "Suport d'idioma", fixat si tens actualitzat el paquet d'idioma que estiguis fent servir (català suposo). 

A "Paràmetres del sistema" -> "Entrada de text", al panell de l'esquerra (Fonts d'entrada a utilitzar) mira si hi ha "Espanyol" i si està en primer lloc.

---

### Post by oriolberga-e on 2016-05-07
Està tot tal qual dius. He provat a ->Entrada de text->Fonts d'entrada a utilitzar, posar tant l'espanyol com el català a dalt de tot i el resultat es el mateix.

També he assegurat que no faltessin actualitzacions i està tot al dia. Allò curiós es que el corrector funciona i corregeix amb els caràcters accentuats correctament. Finalment he revisat tambe les dues pestanyes dels paràmetres d'escriptura i dreceres del teclat pero no sembla haver-hi res estrany.

---

### Post by wgarcia on 2016-05-09
La manca d'accents és a tot arreu o a alguna aplicació en concret? Per exemple, si obres una "terminal" (buscant "terminal" al menú "Eines del sistema") si escrius a la terminal tampoc no hi ha accents?

---

### Post by oriolberga-e on 2016-05-09
Es a tot arreu. Fins i tot al terminal. Si es prem la tecla de l'accent, aquest apareix sense poder afegir-hi cap lletra: ` ´

---

### Post by wgarcia on 2016-05-10
Pots provar donar l'ordre següent des d'una terminal?:

```
sudo setxkbmap -layout 'es,es' -model pc105
```

---

### Post by oriolberga-e on 2016-05-10
Provat. M'ha demanat la contrassenya i fa el mateix
`a´a`

---

### Post by wgarcia on 2016-05-11
Una altra possibilitat és intentar reconfigurar el teclat. Suposo que tens un teclat amb els accents, ç, ñ, etc. Es pot entrar la següent ordre a una terminal:
```
sudo dpkg-reconfigure keyboard-configuration
```
i veure si el que està escollit és "Generic 105-key (Intl) PC", si no està escollit, escollir aquest teclat.

---

### Post by oriolberga-e on 2016-05-14
Tampoc. He provat tant aquest teclat genèric com l'específic de l'ordinador que sortia també al menú (Thinkpad T61).
Res. De moment torno a l'escriptori per defecte.

Gràcies de totes formes.

---

### Post by oriolberga-e on 2016-05-15
Arreglat el tema. Amb el Mate no hi ha pegues d'accents.

Merci a tots.

---

### Post by jinglada on 2016-08-20
Despr´es de l'actualitzaci´o d'ahir em passa el mateix. En canvi en la sessi´o de convidat escriu b´e els accents. No s´e quin escriptori faig servir. El S.O. ´es l'Ubuntu 16.04 LTS. Tampoc ser com es fa per canviar d'escriptori. 

Porto tota la tarda sense poder escriure res. Agrairia molt la vostra ajuda.

---

### Post by jinglada on 2016-08-20
Les "imatges" instal·lades:

~$ ls /boot
abi-3.15.0-031500rc2-generic     efi                                  memtest86+.elf                       vmlinuz-4.4.0-31-generic
abi-4.4.0-31-generic             grub                                 memtest86+_multiboot.bin             vmlinuz-4.4.0-31-generic.efi.signed
abi-4.4.0-34-generic             initrd.img-3.15.0-031500rc2-generic  System.map-3.15.0-031500rc2-generic  vmlinuz-4.4.0-34-generic
config-3.15.0-031500rc2-generic  initrd.img-4.4.0-31-generic          System.map-4.4.0-31-generic          vmlinuz-4.4.0-34-generic.efi.signed
config-4.4.0-31-generic          initrd.img-4.4.0-34-generic          System.map-4.4.0-34-generic
config-4.4.0-34-generic          memtest86+.bin                       vmlinuz-3.15.0-031500rc2-generic

He provat la 4.4.0-31 i tampoc ha funcionat. Ara se m'ha acudit provar la 3.15.0-031500rc2-generic i ara ja puc escriure amb accents: àáèéìíòóùú &#365;&#265;&#285;&#293;&#309;&#349;. Què hauria de fer per a què funcionés la 4.4.0-34?

Gràcies a la bestreta!

---

### Post by jinglada on 2016-08-21
Acabo d'engegar amb 4.4.0-34 i funciona bé àèìòùáéíóú &#365;&#259;&#277;&#301;&#335;&#365;&#265;&#285;&#293;&#309;&#349;
$ uname -a
Linux joan-Aspire-E1-572 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

---

