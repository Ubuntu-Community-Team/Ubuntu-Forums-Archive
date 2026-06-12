---
title: "Socors!!! no sé instal·lar res!!"
date: 2007-09-25
forum: Catalan Team
---

### Post by MarMar3 on 2007-09-25
Hola, sóc nova i no en tinc ni idea de Linux, no sé com fer-ho per a instal·lar programes, ja que he intentat fer lo de: $ passwd root i em diu q el comma not find:
Crec q ho faig bé: vaig a Terminal i introdueixo aq codi i enter, però em diu q no ha trobat el comanament. Co ho puc fer instal·lar programes ???' moltes gràc

---

### Post by orestesmas on 2007-09-25
Qui t'ha explicat aquestes coses tan lletges?

Per instal·lar programes hi ha una utilitat que es diu synaptic. Si el teu escriptori és el KDE llavors la utilitat es diu "adept" i és al menú "Sistema"

---

### Post by papapep on 2007-09-26
Hola Mar! 

Tal i com t'ha comentat l'Orestes no vas ben orientada per a instal·lar programes, com a mínim si no vols tenir problemes.
A més, donada la teva inexperiència, no et recomano entrar com a root a fer res, no et cal.

Per a trobar el Synaptic, ves a Sistema > Administració > Gestor de paquets Synaptic.

Si tens dubtes al respecte, tot i que és bastant intuitiu, pregunta el que et calgui.

Per cert, t'han comentat que tens algun problema amb el teclat que fa que escriguis certes paraules a mitges? :-P

---

### Post by Satboy on 2007-09-26
Hola,
 **MarMar3 ** sigues benvinguda al "club"!!

 Siau! ;-)

---

### Post by kukat on 2007-09-26
Benvinguda!!

Si vols instalar programes, el millor es anar a la consola, i escriure: sudo (per a tindre permisos d'administrador) apt-get install + el paquet que vulguis instalar. 

per exemple, per instalar  K3b (com el Nero per a lInux), tendries que escriure el seguent:

sudo apt-get install k3b

i així amb qualsevol programa. Però per instalar es pot fer de moltes diveres formes. Aquesta hem pareix de lo més fàcil... això si, ves en compte amb les majúscules i minúscules, ja que linux fa distinció!!.

---

### Post by marcoil on 2007-09-26
Benvinguda!

Al menú d'aplicacions hi ha una entrada "Afegeix...". És la manera més senzilla d'instal·lar aplicacions, sense línea de comandes.

---

### Post by MarMar3 on 2007-09-27
Ostres!!!! MOLTES GRÀCIES A TOTS!!! però... ara quan vaig al Synaptic hem diu aixó: E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Qué he de fer???

---

### Post by papapep on 2007-09-27
Doncs el que diu :-D

Fes a un terminal:

```
sudo dpkg --configure -a
```

---

### Post by MarMar3 on 2007-09-27
Papapep!! gràcies gràcies! però ho faig i em demana un password (q suposo q és el meu) però no em deixa escriure res més, "el teclat no m'esciriu la meva password ni res " (jejeje, ho sento sóc tan nova amb el tema...)

1000 gràcies!!!

---

### Post by patrickfromspain on 2007-09-27
encara que ho vegis, si que estas escrivint el teu password ;)

---

### Post by papapep on 2007-09-27
gnu/Linux és un sistema operatiu amb una clara vocació de seguretat (entre d'altres), i un petit exemple n'és el fet de que no es vegin les contrassenyes mentre les tecleges a fi de que no tinguis ningú mirant per damunt la teva espatlla. ;-)

Com diu en Patrick, només cal que t'asseguris de que la tecleges correctament, l'ordinador ja farà la resta.

---

### Post by MarMar3 on 2007-09-27
Val ara crec q si, moltes mercès!
Seguiré preguntant...

---

### Post by muleta on 2007-09-27
> **MarMar3 said:**
> ho sento sóc tan nova amb el tema...)!

Mar, en aquest forum la gent en sap moltíssim i són molt gentils posant-se a la disposició dels que no en tenim ni idea.

Jo estava pitjor que tu. En Papapep, que és un sant varó i un sac de paciència, va ser qui em va fer saber que existeix el terminal.

Tots es desviuen per ajudar-nos però el seu nivell és massa alt per a nosaltres i no podem pas dependre absolutament de que ens portin de la maneta. He trobat molta ajuda més elemental en el Google. Si escrius "linux bàsic" hi trobaràs cursos d'iniciació i pautes per a començar a sentir-te menys perduda.

Jo també "estoy en ello". SORT.

---

### Post by MarMar3 on 2007-09-27
doncs moltes gràcies per tot i sobretot per això del linux bàsic!!!!
sempre hi ha un inici de tot!!!!

---

### Post by MarMar3 on 2007-09-27
Només una última pregunta, en aques fòrum puc preguntar quin és l'equivalent del Guitar Pro per a Linux? o Només és per a qüestions de programació?

Merci.

---

### Post by papapep on 2007-09-28
Com diu aquell, contra el vici de preguntar, la virtud de no contestar...o no era així??? :-D

Tu pregunta el que vulguis, tot i que això no vol dir que algú t'ho contesti, no ho sabem pas tot (tant de bó). Així mateix, si el tema no és l'adeqüat, segur que algú et farà algun comentari "constructiu" ;-)

---

### Post by CarlesOriol on 2007-09-28
El **kguitar** és el més complet i pots carregar els arxius de **guitarpro**. 

Per **afinar** la guitarra el **lingo** és el que va millor. 

Per escriure **tabulat** ràpidament el **songwrite**.

Per escriure partitures tipus **finale** tens el **noteedit.**

Si el que vols és un multipista tipus **cubase** tens el **ardour2** amb una quantitat d'efectes indecent. També tens el **muse** i el **rosegarden**. 

Com a **caixa de ritmes** tens l'**hydrogen**. (et caldrà el **sintetitzador** **timidity** si no tens un dispositiu midi)

El **jack** podriem dir que fa les funcions d'homogenització del **asio**.

A més tens una **versió específica de l'ubuntu per tractament de multimèdia** anomenada** ubuntu-studio.**

Com ja saps tots aquest programes son lliures. ;-)


Benvingut

---

### Post by papapep on 2007-09-28
Per que no digueu que sóc un barroer movent posts (cosa que fareu igualment...:-P), he copiat els tres últims posts a un nou fil per si algú busqués el tema.

---

### Post by RainCT on 2007-09-28
Benvinguda!

*[missatge esborrat, no havia vist que aquest fil ja té 2 pàgines]*

---

