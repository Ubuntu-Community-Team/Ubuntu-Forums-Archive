---
title: "Problema àudio inici ubuntu 11.10 i avisos"
date: 2011-10-31
forum: Catalan Team
---

### Post by U-Joan on 2011-10-31
Hola,

Fa una setmana que m'he instal·lat Ubuntu 11.10 i som totalment nou en aquest sistema operatiu i en aquest fòrum. M'ha sortit un problema i és que m'ha desaparegut el so de l'inici de sessió, i també l'avís sonor que sortia quan es van a tancar diverses pestanyes al Firefox. La resta es sent tot bé.

He estat cercant una solució i no trob res que em funcioni. He vist que a n'Akyra li havia passat una cosa semblant i ho va resoldre seleccionant l'opció Dúplex Estèreo Analògic al maquinari de la configuració de so, però no em funciona.

Com que em vaig crear dos usuaris a l'Ubuntu, he vist que en el segon usuari es mantenia l'àudio perfectament en l'inici i l'avís del Firefox, però quan he clicat a triar un so d'alerta a la pestanya de "Efectes de so", també m'ha desaparegut el so d'inici de sessió i dels avisos en aquest usuari, encara que la resta es sent bé.

Si algú sap com aclarir-ho, ja ho comentarà.

Gràcies.

---

### Post by wgarcia on 2011-10-31
El problema de l'akyra era pitjor perquè no tenia cap mena de so, tu tens so, no?, i el problema és sols del sons d'alerta.

Mira al menú "Paràmetres de sistema" que trobes al menú que està al plafó de dalt, l'última icona, secció "Sistema > So", pestanya "Efectes de so" i mira si el volum està donat.

---

### Post by U-Joan on 2011-10-31
Sí, realment el problema no és greu. Tenc so en tota la resta, però m'estranya que passi aquest "defecte" i preferiria solucionar-lo o com a mínim saber on és l'error, sigui meu o no. A part que com que som nou a Ubuntu m'agradava sentir la sintonia d'inici, després ja sé que un s'acaba avorrint..

Ho havia mirat el que em dius: al menú "paràmetres del sistema", la icona de "So" m'apareix a la secció "Maquinari". I en la pestanya "Efectes de so" tenc el volum al màxim.

---

### Post by wgarcia on 2011-10-31
Sí, perdona, està a "Maquinari", i verificat això ara es pot mirar una altra cosa. 

Obre el "Dash" prement la tecla "Súper", la que normalment té el logo de Windows (després ens preguntem perquè costa tant que Linux agafi la preponderància als escriptoris que té als mòbils, tauletes, aparells de hifi, etc, amb els privilegis que té Windows...).

A l'espai que et surt per escriure al "Dash" entra "Startup" i hauries de veure que apareix "Aplicacions d'inici" o alguna cosa així. Penso que també es pot obrir entrant "Aplicacions" i et sortirà el mateix, però no estic segur i ara mateix estic en un escriptori en anglès. 

Si veus "Aplicacions d'inici" clica-la, i a la finestra que s'obre verifica que surt "So d'inici Gnome" i que està marcat.

---

### Post by U-Joan on 2011-10-31
Sí, també ho havia vist. A aplicacions d'inici em surt marcat el "Gnome login sound" i sembla correcte. Amb el botó "Edita" m'apareix la següent ordre:
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Açò darrer no ho he tocat perquè no sé el que vol dir i no ho volia complicar més.

---

### Post by wgarcia on 2011-10-31
Bé, ara ja anem a les tripes de Gnome, el sistema d'escriptori d'Ubuntu. 

Torna a obrir el Dash i entra "dconf". Clica sobre "Dconf editor" que apareix.

Se t'obrirà una espécie de navegador, navega seguint (clicant) la següent ruta:

org > gnome > desktop > sound

Mira si a "theme-name" posa "ubuntu", si no ho posa canvia el que posa per "ubuntu", ho pots editar clicant sobre aquesta línia.

---

### Post by U-Joan on 2011-10-31
Mmmmmm... Problema. Escrivint "dconf" o "Dconf editor" al cercador del Dash no em surt res.
Pot tenir res a veure amb el fet que em vaig instal·lar un programa de "editor de configuració compiz"? Me'l vaig posar per provar efectes de finestres tremoloses o elàstiques i em va donar alguns problemes, però crec que es van resoldre i no l'he tocat més.

---

### Post by wgarcia on 2011-10-31
No hi ha problema amb l'editor de configuracions de Compiz, però ves amb compte amb provar massa coses perquè pot generar problemes de configuració amb l'escriptori. De moment si tot continua funcionant bé no hi ha problema. 

En quant al "Dconf editor", tens raó. no està instal·lat per defecte. Clica sobre "Centre de programari Ubuntu" al llençador de l'esquerra, entra a la finestreta de cerca "Dconf editor", i instal·la'l, després ja podràs obrir-lo com et comentava.

---

### Post by U-Joan on 2011-10-31
Perfecte!!

Ja torna a funcionar tant l'avís de so del Firefox com el so d'inici. Em sortia "freedesktop" enlloc d'"ubuntu". Moltes gràcies company. 
:P

Tens idea de per què es pot haver desactivat aquest àudio?

Edit: He observat que en l'altre usuari que m'havia generat problemes de so no s'ha resolt el tema. He fet la mateixa operació però no sona l'audio d'entrada i l'avís... 

Edit2: Ara ja sí. Es veu que no havia quedat guardat el canvi perquè hi he tornat a entrar i encara posava "freedesktop". He tornat a introduir "ubuntu" i ara ja ho torn tenir com estava.

---

### Post by wgarcia on 2011-10-31
És un error reportat:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/883677](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/883677)

Si vols començar a contribuir a Ubuntu, clica sobre l'enllaç i marca que també t'afecta a tu amb la qual cosa quedarà confirmat l'informe d'error.

---

### Post by U-Joan on 2011-10-31
Fet!

Crec que amb açò també respons al que et demanava en l'anterior comentari. Si no ho he entès malament efectivament es tracta d'un error del programa que fa que quan canvies un so d'alerta t'ho desactivava. Bé, almenys no era res que havia fet malament. 

Gràcies de nou. Demà plantejaré un altre problemet que tenc, que per avui ja està bé.

---

