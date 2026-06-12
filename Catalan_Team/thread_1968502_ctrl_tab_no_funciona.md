---
title: "ctrl tab no funciona"
date: 2012-04-29
forum: Catalan Team
---

### Post by josep-maria on 2012-04-29
He posat l'ubuntu 12.04, i ara no funciona el canvi d'aplicació, és a dir, les tecles ctrl tab. Abans amb l'ubuntu 11.10 sí que anava bé. He mirat a 'paràmetres del sistema' i a 'advanced settings' però no he trobat res.

---

### Post by 19preguntes on 2012-04-29
Hola, en el meu cas Control+Tab em serveix per canviar de pestanya del navegador, i Alt+Tab per canviar d'aplicació.

Si fas servir Unity, pots configurar les opcions de canvi d'aplicació amb l'editor de configuració Compiz, que està al centre de programari de l'Ubuntu. Un cop instal·lat el Compiz, si l'obres i entres a "Ubuntu Unity Plugin", hi veuràs una pestanya Switcher on podràs configurar l'opció de canvi d'aplicació al teu gust.

Si no fas servir Unity, ho sento però no et puc ajudar, i haurem d'esperar que et respongui algú que en sàpiga més...

Salut!

---

### Post by josep-maria on 2012-04-29
Perdó, m'he confòs, volia dir alt tab.

---

### Post by josep-maria on 2012-04-29
El unity és l'equivalent del gnome, oi? És que tinc el gnome 3.4.1.
El compiz ja el tinc, suposo que és el mateix que 'advanced settings', però no hi surt res del canvi d'aplicació amb alt+tab.

---

### Post by 19preguntes on 2012-04-29
Hola de nou,
no, el Gnome Shell 3.4.1 i el Unity són dos entorns d'escriptori diferents. Com et deia abans, si no fas servir Unity em temo que no et podré ajudar.

Em sap greu...

Salut!

---

### Post by wgarcia on 2012-05-01
El Gnome Shell sí que es un entorn d'escriptori diferent que l'Unity, però tots dos estan construïts sobre el sistema Gnome, versió 3.4. 

Quin entorn estas fent servir tu? He vist a Internet alguns casos en què Alt-tab no funciona dins de Gnome Shell, i diuen que ho arreglen amb el "Compiz Setting Manager", clicant "Application Switcher" dins d ela secció "Windows Management". Però no em quadra perquè em sembla que el Gnome Shell no fa servir Compiz. I en tot cas si proves aixó molt de compte perquè canviant alguna altra opció dins d'aquesta aplicació de configuració de Compiz et pots quedar completament sense escriptori (després és fàcil d'arreglar però s'ha d'anar amb compte perquè quedar-se sense interfície gràfica no és agradable).

---

### Post by josep-maria on 2012-05-03
Vaig baixar d'internet una aplicació que es diu 'configuració avançada dels ajustaments del gnome 3'.  No sé si és la mateixa que el compiz. Tinc una icona a la barra de dalt de tot. Quan hi faig clic em surt una finestra que diu 'advanced settings'. Té cinc opcions: desktop, extensions del shell, finestres, shell, theme, i tipus de lletra. Fent clic a 'finestres' (suposo que és la que dieu 'windows management') veig quatre opcions: acti..., acti..., acti..., i win... No he pogut veure el títol de cada opció, només les lletres que us he dit perquè no em deixa fer la finestra més gran. A cada opció 'acti...' hi ha vuit opcions més: lower, menu, none, toggle maximize, etc.

---

### Post by Joan A. on 2012-05-03
No m'ha quedat gens clar quina interfície gràfica utilitzes. Unity utilitza compiz i Gnome Shell utilitza Mutter. Si pots aclarir quins dels dos utilitzes et podríem ajudar. Has instal·lat el paquet Gnome 3?

---

### Post by josep-maria on 2012-05-03
Tinc el gnome 3.4.1.

---

### Post by wgarcia on 2012-05-03
> Vaig baixar d'internet una aplicació que es diu 'configuració avançada dels ajustaments del gnome 3'. No sé si és la mateixa que el compiz. Tinc una icona a la barra de dalt de tot. Quan hi faig clic em surt una finestra que diu 'advanced settings'. Té cinc opcions: desktop, extensions del shell, finestres, shell, theme, i tipus de lletra.

josep-maria, això sembla una eina de configuració del Gnome-Shell. Quin entorn d'escriptori estàs utilitzant? Et surt el llançador d'aplicacions de l'esquerra de la pantalla?

---

### Post by Joan A. on 2012-05-04
josep-maria, si poguessis penjar una captura del teu escriptori tal vegada ens aniria millor per esbrinar quina és la teva interfície gràfica.

---

### Post by josep-maria on 2012-05-05
Avui miraculosament torna a funcionar bé. Suposo que ha estat gràcies a alguna de les darreres actualitzacions.

L'escriptori és el gnome 3.4.1. A l'esquerra de la pantalla no hi ha res.

---

### Post by wgarcia on 2012-05-05
El gnome 3.4.1 no és exactament un escriptori, sinó un entorn de llibreries gràfiques sobre el qual hi ha diversos escriptoris, l'escriptori per defecte Gnome Shell, l'escriptori per si no hi ha suficient potència gràfica per a Gnome Shell (gnome-fallback), escriptoris que volen emular l'aparença de l'escriptori Gnome 2 (per exemple Cinnamon, o fins i tot una continuació de Gnome 2 que es diu Mate), l'escriptori desenvolupat per Ubuntu sobre Gnome 3.4.1 que es diu Unity, l'escriptori per si no hi ha potència gràfica per a Unity que es diu Unity 2D i no sé si em deixo algun. 

Però tots aquests estan construïts sobre Gnome 3.

Em sembla pel que descrius que el que tens tu és el Gnome Shell.

---

