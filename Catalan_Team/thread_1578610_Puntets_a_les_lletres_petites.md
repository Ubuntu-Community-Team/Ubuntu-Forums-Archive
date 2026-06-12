---
title: "Puntets a les lletres petites"
date: 2010-09-20
forum: Catalan Team
---

### Post by Flocdemer on 2010-09-20
Tinc un ubuntu 10.04 i n'estic molt content! No he tingut cap problema per configurar els perifèrics que faig servir i la majoria m'ho han configurat al disc d'ubuntu.

Però quan estic a un navegador o a l'openoffice treballant amb lletres petites llavors veig puntets de color clar que em difuminen el traç i és incòmode.

Algú s'hi ha trobat i ho ha pogut solucionar?

---

### Post by wgarcia on 2010-09-21
És estrany, que podries fer una captura de pantalla i adjuntar-la per veure exactament què està passant?

---

### Post by Flocdemer on 2010-09-21
T'adjunto una foto d'una fulla de càlcul.  Fíxa't en Teià, vinya,...

---

### Post by lluisanunez on 2010-09-23
Prova anant a Sistema > Preferències > Aparença > Fonts i jugant amb les opcions de configuració que apareixen a sota, i també clicant a "Detalls"

---

### Post by andymorton on 2010-09-23
andy no entiende :(

---

### Post by SiscoGarcia on 2010-09-23
> **andymorton said:**
> andy no entiende :(

Maybe because this is the [catalan language]("http://en.wikipedia.org/wiki/Catalan_language") subforum, and here this is the language we use.

---

### Post by CarlesOriol on 2010-09-25
Comprova a 
Sistema > Preferències > Aparença > Tipus de lletra
Que tinguis marcat
Suavitzar de subpixels

>> i a Detalls:
Marca:
Subpixel 
LCD, 
Complet
RGB

Sempre que no tinguis KDE que allà la cosa va diferent.

---

### Post by Flocdemer on 2010-09-25
Hola Macos,

ja he provat el que m'heu dit  però no hi ha manera. Només aconseguia que els puntets es belluguessin.

No se us acudeix res més?

---

### Post by wgarcia on 2010-09-26
Pots provar de crear un altre usuari i veure si el problema es reprodueix per a aquest altre usuari?

Si al nou usuari es veu bé, entra a l'escriptori del teu usuari original i fes:

1) Entrar a l'escriptori
2) CTRL-ALT-F1 per accedir a una consola de text fora del sistema gràfic
3) entra:
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
i prem intro
4) CTRL-ALT-F7  per tornar a l'escriptori

Les carpetes que esborres en el pas 3) es recreen en tornar a entrar a l'escriptori.

---

### Post by Flocdemer on 2010-10-04
Ja ho he provat i sembla i fa el mateix. 

No sé què més fer.

---

### Post by papapep on 2010-10-04
I si arrenques amb un CD en viu o amb un pendrive USB amb l'Ubuntu, et passa el mateix? que no sigui el monitor o la placa gràfica.

Quina gràfica tens? Posant a l'intérpret d'ordres "lspci |grep VGA", sense les cometes mostrarà el model i marca concret. Enganxa-ho aquí després.

Quin controlador de la gràfica tens funcionant? Fent, un altre cop a l'intérpret d'ordres, "lsmod |grep video", veurem el que tens carregat. Enganxa-ho aquí també.

Salut.

---

### Post by Flocdemer on 2010-10-13
Em sembla que ja he solucionat el tema de les lletres amb puntets. Acabo d'instal.lar el control.lador de maquinari que ubuntu em recomenava per l'nvidia. I ja no tinc els problemes que tenia:
-se'm veia puntets de color del fons a qualsevol tipus de lletra, però sobretot molestava més quan més petita era.
-quan escrivia en un quadre, les lletres de la mateixa línia es bellugàven.

Moltes gràcies a tots.

---

