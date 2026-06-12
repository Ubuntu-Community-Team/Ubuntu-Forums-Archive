---
title: "Eines de desenvolupament"
date: 2007-03-26
forum: Catalan Team
---

### Post by turten on 2007-03-26
Hola a tothom,

en primer lloc felicitats per la feina que esteu fent, com podeu veure sóc ben nou en aquests fòrums i en el món de linux i per tant necessito del vostre ajut, o sigui que anem per feina :P:P:P

Ja fa molts i molts anys que programo, i tot i que quan estudiava, vaig tocar bastant unix, el cantó obscur de la força em va encegar i tot el que he fet a la meva vida és programar per windows desde que es deia DOS. Últimament he migrat al .NET, però ja n'estic fart i vull tornar a programar amb una mica de cara i ulls. O sigui que m'he instal·lat un Ubuntu amb el GNome en un ordinador vellet que sembla un aspirador pel soroll que fà i estic provant... El meu interés i motiu d'aquest post és el següent:

Quines eines de programació existeixen / em recomaneu? 

Professionalment utilitzo el C++ i C# amb els entorns de M$ o sigui: VS6, VS2k3 i últimament VS2k5 i sempre m'agradat que les aplicacions que desenvolupo tinguin el mateix look&feel que el sistema operatiu sota el què programo, cosa que és impossible, sense esforços monumentals, de fer amb M$. Sé que existeix Eclipse i Mono, però en desconec la facilitat d'us, integració, etc..

Quines eines de desenvolupament web existeixen / em recomaneu?

Últimament, i per diversió pròpia, m'han aparegut ganes de coneixer el món actual web i he començat a fer cosetes petites amb joomla, php i ccs. Aquí si que estic totalment perdut, ja que en windows utilitzo l'UltraEdit per tocar aquest tipus de codi. Què em recomaneu?

Be doncs, si heu arribat a llegir fins aquí moltes gràcies, i si a més a més encara teniu ganes de respondre, més gràcies encara.

Salut!!

---

### Post by orestesmas on 2007-03-26
Jo no sóc desenvolupador, però et diré allò que em sona més:

Eclipse és un gran entorn, tot i que una mica pesat per la qûestió del Java, però és molt flexible i admet molts tipus de plugins. Per programar en Java deu ser un dels millors.

Per fer desenvolupament de sistema operatiu hi ha el KDevelop i el Anjuta. El segon està orientat a desenvolupament de Gnome, i el primer al desenvolupament de KDE (tot i que és més genèric potser). Molt recomanables si vols fer desenvolupament en C/C++. Jo trobo el primer especialment bo i afinat, sobretot si el combines amb eines com el valgrind.

De mono no conec res especial.

Per web hi ha Nvu, quanta+, Bluefish... però si busques quelcom semblant a Dreamweaver, oblida-te'n.

Bé, aquí tens els meus 5 cèntims.

---

### Post by CarlesOriol on 2007-03-27
Si vens del c# evidentment mono.

Hi ha bonics videos al web del mono per aprendre'l a usar les llibreries gtk (equivalent al window forms) que potser et serà l'unic canvi important.

Existeix un portal en català però veig que avui no funciona: [http://tornatmico.org/](http://tornatmico.org/) . Algú en sap res?

... sort i paciència... 

ah! i per er coses petites tant el gedit (gnome) com el kate (kde) veuras que esn força bé.

---

### Post by marcoil on 2007-03-27
Si tens temps per dedicar a aprendre, l'Emacs és un editor quasi omnipotent. Hi ha gent que hi gestiona el seu correu electrònic i tot! Té una curva d'aprenentatge bastant alta comparat amb els típics IDEs, però amb un poc d'esforç pots arribar a ser molt productiu.

Si t'agraden més els IDEs convencionals Eclipse (amb l'extensió CDT) és molt bo per programar en C/C++. A més hi ha multiples *plugins* per altres sistemes, com Ruby o PHP.

---

### Post by turten on 2007-03-27
Hola de 9,

gràcies per les indicacions començaré a provar... Però abans uns comentaris-preguntes.. jejejeeee

Això de Mono sembla potent, però he vist que darrera de Mono hi ha Novell i darrera de Novell no hi ha M$ ara? Realment fa molta por que una versió lliure de .NET pugui estar esbiaxada als interessos comercials de M$.

Buscant i remanant per posts vostres i dels fòrums anglesos he vist que encara hi ha batelles dins del món GUI - CLI i dins de GUI Gnome i KDE. No us preguntaré quin entorn em recomaneu, però això quines implicacions té dins del món dels desenvolupadors?? És recomanable que una aplicació pensada per treballar amb una GUI també tingui diferents opcions CLI per automatitzar processos? Suposem que em decanto per Ubuntu i utilitzo Gnome, pel què comentava en CarlesOriol en un altre thread, em poden sorgir problemes d'incompatibilitat (utf i d'altres) no existeix una capa d'abstracció del sistema de finestres? jajajajaaaaaa i no em digueu l'interpret de comandes :P:P:P:P. Em podeu dir el nom d'alguna aplicació feta en java que utilitzi les AWL (es diuen així?). Finalment, què és el GTK?

Com veieu estic molt preocupat pels temes d'interficie, però crec que són molt importants, tant per l'usuari com pel programador... però és que estic fart d'haver d'acabar posant dins d'un objecte dos camps x.y que diuen la seva posició en pantalla i que acaben fent el soft depenet totalment de la interficie utilitzada. En ma vida he pogut programar un esquema MVC real on estigui tot separat.

Gràcies de nou,

Fins aviat!!!

---

### Post by CarlesOriol on 2007-03-27
Darrera mono hi ha Manuel de Icaza.

La llicència del mono és GPL per tant no es pot controlar ni restringir. 

Per cert. Sobre el tema d'assintents gràfics. Estan molt bé però perds el control del que estas fent. Tu sabras millor que ningú si has treballat en c# o c++ (potser amb les microsoft foundation classes) que quan un projecte es torna un pel gran tots els assistents del mon no seveixen per res i cal escriure el codi manualment.

Un altre exemple et com faries en un sistema privatiu o en mode gràfic que el sistema et connecti a una xarxa vpn enruti fins una màquina compari la base de dades local amb uns arxius remots, tanqui un programa obert per evitar colisions i despres actualitzi la base de dades local i recarregui el programa tancat?
Això que et comento és una linia d'un script per cada operació anterior en un bash. Com ho faires facilment en un sistema limitat al mode gràfic?

...i si t'agrada el tema d'scriptar una mica cerca documentació sobre l'udev t'apassionarà.

Icomptatiblitat utf... uops... no , no era un problema d'incompatibilitat, era un problema de configuració. On trobaras problemes d'incomptabilitat de jocs de caracters és al software privatiu on s'autoanomenen standard qualsevol destrossa que fan.

---

### Post by carlesbm on 2007-08-28
Hola gent

   Soc una mica aficionat ha crear petites aplicacions destinades principalment ha comunicaió amb aparells atraves de RS232, he traballat amb MS visual Basic.net i conec una mica de llenguatge C principalment tot el que se ho he apres de una forma autodidactica, i voldria saver si hem podeu asesorar de quin entorn puc utilitzar per poder seguir realitzant les mesves aplicacions desde Ubuntu(Linux), He estat mirant les que mes surten i no acabo de veure clarament com treballar-hi.


Moltes gracies ha tots
:confused:

---

### Post by ChAoS.ct on 2007-08-28
Hola, si parlem de mono: simple i fàcil: Monodevelop

És veritat, el mono està en fase de desenvolupament i sobretot si li exigeixes molt processament pots acabar sense garbage collection...

Però tens tota la potència de C# a mes de l'accés a les llibreries necessàries per a fer casi qualsevol cosa.

Pel que fa el look and feel jo utilitzo molt el glade interface designer, que et fa un xml que pots carregar al teu programa dinàmicament o estàticament (amb mono ho fa estàticament crec) i és molt fàcil d'usar.

Per cert el Monodevelop que hi ha als repositoris és una mica... antic, millor agafa el de la seva web.

Apa que tinguis sort!

---

### Post by CarlesOriol on 2007-08-29
Pots començar a xarxardejar amb python (personalment l'odio he he)... però té la immediatesa del llenguatge interpretat i és una evolució dels basics.

---

### Post by nickpage on 2007-08-29
Ja que parleu d'eines de desenvolupament, m'agradaria que me recomeneu algun IDE per PHP.

Gràcies

---

### Post by CarlesOriol on 2007-08-30
Jo uso el gedit... no crec que sigui "exactament" el que cerques oi?

---

### Post by carlesbm on 2007-09-01
Hola companys

      He estat probant una serie de entorns de programació i la veritat que ara com ara encara estic més liat, segurament aixo hem passa per que els meus coneixements de informatica de programacio son molt limitats, cosa que ja heu pogut notar amb les meves preguntes, fent referencia a coses molt ovbies, he probat el monodevelop i la veritat que qüasi hem faig mal per disenyar la interficie gràfica, i la resta que he mirat molt per damunt, com eclipse m'han semblat veritablement complicats.

     Suposo que aixo es com tot amb una mica e temps i una canya segu que alguna cosa pesquem.

    Que us sembla el entron Gambas pel que he pogut veure es molt mes semblant a VB.?

---

### Post by orestesmas on 2007-09-01
Jo el Gambas no l'he provat mai,però té bona pinta. Com tot, depèn per a quin llenguatge el vulguis. Si programes en Java, val la pena potser endinsar-te en l'eclipse, que no és pas tan complicat. Si fas programes per KDE, el KDevelop és l'eina a escollir. Pel PHP et valdrà qualsevol editor que ressalti la sintaxi, perquè no hi ha compilació (jo suggeriria el Kate, per exemple, igualment per XML, etc.) Per Python crec que hi ha un IDE específic en KDE, i així podríem seguir "ad infinitum".

---

