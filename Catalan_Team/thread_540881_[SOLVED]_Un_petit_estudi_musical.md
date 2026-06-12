---
title: "[SOLVED] Un petit estudi musical?"
date: 2007-09-02
forum: Catalan Team
---

### Post by lo gambusí on 2007-09-02
Salutacions!!

M'agradaria saber si algú té idea d'algun programeta per a poder modificar arxius d'àudio per pistes, rotllo estudi de so. Tinc, per exemple, una cançó, i vull treure-li la pista de veu i afegir-hi jo una altra.  Com ja deia abans, jo això ho he vist fer en estudis de so i tal, però no sé si existeix algun programa més accessible capaç de fer-ho.

Si no trobés res per Ubuntu, miraria d'aconseguir-ho en lo güindous...:(

Moltes gràcies a tots!:lolflag:

---

### Post by eselma on 2007-09-02
Un programa senzill, que en la versió actual està idicat per Gnome, és l'*Audacity*. Si vols una cosa més complerta, tens l'*Ardour*.

Per a fer muntatges només cal que tinguis una màquina amb la capacitat adequada; si vol enregistrar, et caldria canviar el nucli per un del tipus "l*owlatency*", també disponible per *Ubuntu.

Quan parles de "treure una pista de veu" se suposa que l'enregistrament original el tens en multipista, i no és un resultat de mescla.

Hi ha més programes, però aquest parell crec que són representatius de dos nivells diferents.

---

### Post by PellRoja on 2007-09-02
[http://www.somgnu.cat/linux-multimedia-studio/](http://www.somgnu.cat/linux-multimedia-studio/)

---

### Post by CarlesOriol on 2007-09-02
Per fer el que vols evidentment el programa és l'ardour que s'insta&#320;la predeterminadament en l'ubuntu studio i requereix el kernel lowlatency com ja t'han comentat.

Per eliminar l'audio d'una mescla existent - sempre sabent que la qualitat resultat estarà molt afectada- audacious i el seu pluggin voide removal.

---

### Post by CarlesOriol on 2007-09-02
El noatun al menú efectes també té aquest filtre

---

### Post by lo gambusí on 2007-09-02
Uf, moltes gràcies a tots, però crec que m'he embolicat molt. :P

Mireu, lo que vull fer exactament és agafar un arxiu d'àudio, una cançó, treure-li la veu i gravar per sobre amb un company, com es fa als estudis de gravació professionals.

De moment he posat a baixar l'ardour este, a vore si me servix. Això que dieu del kernel lowlatency què és? L'he d'instal·lar? Com?

Gràcies a tots,i disculpeu les molèsties...

---

### Post by CarlesOriol on 2007-09-03
A veure:

Als estudis "profesionals" no es des-mescla la música per treure la veu...senzillament s'elimina la pista on està aquesta i s'enregistra de nou.

El que tú vols fer és més "marrano".

El programa ardour et recomano que NO l'usis ja que en el teu cas et fotras en un merder de de por i no et servirà per res.

El nucli lowlatency serveix per que en programes d'enregisrament "professional" la màxima diferència de temps entre el que espera el programa i el que s'enregistri sigui tant baix com es pugui. (una tarjeta senzilla pot produir una diferencia de temps de fins a 750 ms - que en música és una eternitat- i una de molt bona entre 2 o 4 ms )... 
Però aquest com et deia abans no és el teu camí


Per fer-ho "més o menys" senzill hauries de fer uns passos similars a aquests (sempre que el teu maquinari t'ho permeti)

1. Instalar el noatun
2. Posar el mesclador per què enregistri el que sona a l'ordinador
3. carregar el audacity i posar a enregistrar
4. amb el noatum (i el filtre per treure la veu) reproduir la cançó que vulguis (per cert quina cançó és?)
5. aturar l'audacity i netejar el començament i final
6. enregistrar una segona pista amb l'audacity
7. exportar-ho a un arxiu ogg (preferiblement per qualitat) o mp3

---

### Post by lluisanunez on 2007-09-03
Això d'eliminar la veu d'una cançó es pot fer, a nivell no gaire professional, i potser fins i tot 'marrano', amb Audacity. De fet és el truc que fan servir els llocs cutrangues on et pots baixar cançons preparades per karaoke :-P
Hi ha un manual d'Audacity als  [arxius de la revista Mosaic de la UOC]("http://mosaic.uoc.edu/pdf/Captura_y_Edicion_de_Audio_con_Herramientas_Libres.pdf") (PDF)
Cap al final s'explica com eliminar la veu d'una cançó

---

### Post by CarlesOriol on 2007-09-04
Collonut,

Canvia els punts 1 al 5 per les instrucciones de la Lluïsa amb l'audacity.

---

### Post by lo gambusí on 2007-09-04
Gràcies als dos. De fet, estava intentant-ho tal i com m'ho deia el Carles Oriol, però tenia problemes per executar el noatun, així que ara quan tingue un momentet ho provaré pel que diu la Lluïsa.

Ja us diré què passa. :)

---

