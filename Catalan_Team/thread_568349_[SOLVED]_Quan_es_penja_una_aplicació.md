---
title: "[SOLVED] Quan es penja una aplicació"
date: 2007-10-05
forum: Catalan Team
---

### Post by Curial on 2007-10-05
Se m'ha penjat el k3b.

El cas és que no es tanca l'aplicació, ni tan sols em deixa
aturar l'ordinador.

La resta funciona bé.

Com es pot forçar a aturar una tasca?

Amb mentalitat de güín-d'ous faria ctrl-alt-del i li diria d'aturar tasca.
Com es fa amb l'Ubuntu?

Salut

---

### Post by anigwei on 2007-10-05
Hola!

Ja em perdonaràs, però només t'ho sé dir de la forma "vella escola", des de la cònsola. Que ens il·lumini algú més amb la manera gràfica :)

Des de la cònsola per matar un programa penjat, primer li identifiques el pid i després el mates literalment:

$ ps aux | grep nomdelprograma 

en el teu cas: $ ps aux | grep k3b

Et sortirà una línia corresponent al procés k3b, la primera columna és el PID. Queda't amb ell i després fas:

$kill -9 PID

Salut

---

### Post by papapep on 2007-10-05
En l'entorn gràfic, si prems Alt+F2, et surt un diàleg on pots entrar ordres. Si hi poses "xkill" (sense comentes, clar) veuràs que la fletxa del ratolí se't torna una calavera :-D. Aleshores, a qualsevol finestra que cliquis la tancarà.

Respecte la manera "tradicional", és bo intentar primer tancar la aplicació amb "kill PID" i si veus que no respon, aleshores si que no ens queda més que fer-ho amb el "kill -9 PID". 
Amb això intentem primer aturar la aplicació "de bon rotllo" i, si no ens en surtim, la "liquidem" per la via heavy sense més contemplacions.

---

### Post by Curial on 2007-10-05
Gràcies companys.

És normal que les aplicacions funcionin a la seva manera, però de tant és bo que sàpiguen qui mana   ;-)

Queda apuntat!

---

### Post by orestesmas on 2007-10-05
> **papapep said:**
> En l'entorn gràfic, si prems Alt+F2, et surt un diàleg on pots entrar ordres. Si hi poses "xkill" (sense comentes, clar) veuràs que la fletxa del ratolí se't torna una calavera :-D. Aleshores, a qualsevol finestra que cliquis la tancarà.
.

Hi ha un accelerador per això: Ctrl+Alt+Escape

---

### Post by CarlesOriol on 2007-10-06
L'accelerador deu ser per kde. En gnome no va. 

(Orestes: estalviat el sarcasme :-) )

---

### Post by ffp on 2007-10-06
Bon dia,

També es pot fer així:

Sistema / Administració / Monitor del sistema, pestanya Processos, boto dret sobre el procés a tancar, "finalitza" o "termina"

Un "novato", que ho va trobar per casualitat.

---

### Post by Curial on 2007-10-06
> **ffp said:**
> Bon dia,

També es pot fer així:

Sistema / Administració / Monitor del sistema, pestanya Processos, boto dret sobre el procés a tancar, "finalitza" o "termina"

Un "novato", que ho va trobar per casualitat.

Gràcies, amb el teu comentari també m'has donat la solució per un alte qüestió.

salut.

---

### Post by Ferri on 2007-10-06
> **CarlesOriol said:**
> L'accelerador deu ser per kde. En gnome no va. 

(Orestes: estalviat el sarcasme :-) )
L'accelerador va a KDE i XFCE, com a mínim. Fa temps que no els faig servir, però em sona que en icewm i/o blackbox també anava.
Realment és de les coses que penso que faria molta falta afegir a GNOME.

---

### Post by CarlesOriol on 2007-10-06
no cal.

Però si et fa i&#320;lusió sempre ho pots fer manualment.

Edites amb gconf-editor > /apps/metacity/keybinding_commands.
Afegeixes un amb xkill. (el primer command_# lliure)

i a /apps/metacity/global_keybinding
el vincules a les tecles que vulguis (el run_command_# equivalent)

-----------------------------------------

Si disposes del compiz ho pots fer amb la seva propia configuració

---

### Post by Ferri on 2007-10-07
Si cal o no és molt relatiu.
Jo, com que primer vaig començar a KDE i ara faig servir KDE i GNOME segons l'ordinador que estic, ho trobo a faltar a GNOME.
Ja sé que puc configurar manualment l'accelerador que vulgui, però penso que haver de "matar" un programa és una situació prou freqüent com perquè valgui la pena tenir-lo d'entrada.

---

### Post by CarlesOriol on 2007-10-07
Pots dir que t'agrada, o que ho trobes còmode. Evidentment no cal. La majoria de cops les aplicacions "descontrolades" les "mates" (com dius) tancant la finestra. També et pots trobar que hi ha aplicacions, com el firefox, que es queden "pensant" sense mostrar finestra... llavors ens caldria un altre accelerador també no?...
 
El sistema no ha d'estar pensat per ajudar al sistema sinó als usuaris als programes i els perifèrics. I les necessitats de cada un son molt variables. Hi ha molts usuaris que en tota la seva vida no mataran cap procés. I els que ho fem molts cops preferim veure que està passant abans de tancar res amb els ulls clucs.

---

