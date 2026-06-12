---
title: "Problemes amb el LibreOffice &quot;--/---/---/ no existeix&quot;"
date: 2013-04-03
forum: Catalan Team
---

### Post by Anxolot on 2013-04-03
Hola a Tothom :)

No se si ja em vaig presentar, però aprofito per fer-ho :). Porte ja uns quasi 4 anys amb Ubuntu's i estic encantat de la vida amb aquest s.o., i he resolt bastant problemes mirant aquest foro, o preguntant a la gent del xat :) i sempre he trobat solucions. 

 Actualment utilitzo Lubuntu 12.04, i tinc un problemilla amb el LibreOffice: Quan guardo arxius, i els torno a obrir, em surt una finestra que em diu sempre cosses com "/media/Xlot/4t any/2on Semestre/Història d'Àsia Imperis i Nacions/1er Examen, Temes 1 al 6/Tema 2. Àsia. Marc històric/atlas_imperios_campus.ppt no existeix." i el mateix moltes vegades quan treballo amb cosses directament a l'ordinador (perquè l'exemple posat, és d'un usb). La qüestió esque moltes vegades, sols fa falta cambiar el nom de l'arxiu per tornar a poder obrirlo... són cosses molt rares, i ja estic fart. Sembla que ho fa com aleatoriament tant al usb com al pc i des de fa molt de temps. He treballat amb el AbyWord per solventar el problema, però ara necessito fer altres tasques més complexes. 

A pesar de portar anys amb aquest s.o., és la primera vegada que em passa una cosa semblant. 

Què creieu que potser?

Espere que podeu ajudar-me. 

Salutacions a tothom

---

### Post by wgarcia on 2013-04-04
Té pinta de ser algun problema amb la codificació del nom del fitxer o de les carpetes o subcarpetes on el deses. Pots identificar si passa particularment quan el fitxer té caràcters tipus accents o d'altres, o les subcarpetes tenen aquests caràcters, o espais en els noms o les subcarpetes? Tot això no hauria de ser un problema per a LibreOffice, però identificant millor el problema potser ajuda a solucionar-ho.

---

### Post by Anxolot on 2013-04-04
La cosa es més extranya del que em pensava. He aconseguit copiar fitxers dels que no podia obrir al l'usb, a una carpeta de l'escriptori, i em surt el mateix error, "---/---/---/ no existeix". Pot ser sigui alguna cosa relacionada amb l'ús dels permisos, o algo aixi? Anant a propietats de l'arxiu, inclós ficant drets de lectura i escriptura a tots, i continua fent el mateix...

He tret tots els accents de les carpetes i altres signes als noms de les carpetes i de l'arxiu, fins a arribar a on es l'arxiu, i continua amb el mateix problema. 

Me instal·lat l'escriptori de gnome i he formatejat l'usb, i encara continua amb els mateixos problemes: Baixò un ppt al meu pc -> s'obre, el copio a un usb -> "l'arxiu no existeix"... Copio el mateix arxiu que no es pot obrir a l'usb, el pego al pc, i si que s'obre.  També he vist que, a dins de l'usb, anant a propietats i intentant ficar permisos d'escriptura i lectura per a grup, a banda de propietari, es torna a ficar en "nomes lectura" automaticament.

A banda d'això, la cosa es més bizarra encara: Guardant diferents arxius odt amb el libreoffice, a un em surt el missatge d'error, i després, sense tocar res, edito un altre, el guardo, i me deixa sense cap problemes. Aquesta vegada, a l'arxiu que ha guardat però que no puc obrir, m'han sortit 3 finestres dient nomenant la direcció a on es guarda l'arxiu i dient que no existeix, i una tercera, en la que diu algo nou: 
"Error en desar el document Sense nom1:
No hi ha accés a l'objecte.
No es pot accedir a l'objecte
per falta de drets d'usuari."

I justament provant a guardar un altre, si que va. Es una tocada molt gran d'ous que m'està fent anar més lent en els meus estudis. 

Què pot ser?

---

### Post by wgarcia on 2013-04-04
Pots provar amb un altre usuari al mateix sistema? Per exemple amb l'usuari "visitant" si el tens definit? Potser sigui un problema del teu perfil d'usuari que no afecti altres perfils d'usuari.

---

### Post by Anxolot on 2013-04-04
Hola wgarcia,

Acabo de probar i res. Els mateixos simptomes. Què pot ser??

---

### Post by wgarcia on 2013-04-05
Pots obrir una terminal, i des de la terminal entrar

```
libreoffice --impress "/media/Xlot/4t any/2on Semestre/Història d'Àsia Imperis i Nacions/1er Examen, Temes 1 al 6/Tema 2. Àsia. Marc històric/atlas_imperios_campus.ppt"
```

mirar quins missatges s'imprimeixen a la terminal i enganxar-los aquí?

---

### Post by Anxolot on 2013-04-05
I18N: X Window System doesn't support locale "ca_ES.UTF-8@valencia"
I18N: Operating system doesn't support locale "en_US"

Això surt. Vaja. Sembla que es algun conflicte amb el idioma... però de a on? del idioma que té configurat LibreOffice o el meu pc?

---

### Post by wgarcia on 2013-04-06
Pots mirar al menú Eines de Sistema -> Suport d'idioma si està tot marcat, i en particular, si està marcat que s'apliqui la llengua que has escollit a "tot el sistema"?

Mira també 

[https://help.ubuntu.com/community/Lubuntu/Documentation/LanguageSupport](https://help.ubuntu.com/community/Lubuntu/Documentation/LanguageSupport)

per si et pot ser d'utilitat.

---

### Post by Anxolot on 2013-04-07
Ja està el problema solucionat! He anat probant amb les configuracions de llenguatges i de configuració local, i allà estava le problema: A l'apartat de Formats regionals, tenia ficat "català;valencià", i el problema s'ha resolt canviant-ho a Español;Castellano (España).

He estat provant els diversos arxius als mateixos llocs des de a on sortia aquest problema, i els executa tots sense problemes.

Moltíssimes gràcies wgarcia

Salutacions per a tot l'equip d'ubuntu.cat

---

### Post by wgarcia on 2013-04-07
Però això sembla un error, oi? "català;valencià" hauria de funcionar a "formats regionals" també. Bé, estaré atent a veure si puc reproduir aquest error per poder reportar-ho. De moment si cas posa "Solved" al fil per si algú altre té el mateix problema així sap que aquí hi ha una solució, tot i que sigui temporal. Per posar solved has d'editar el teu primer missatge, escollir "Advanced" a baix, i clicar sobre "Prefix" on una de les opcions és "Solved".

---

