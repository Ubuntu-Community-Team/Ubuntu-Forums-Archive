---
title: "He perdut la sessio d'usuari"
date: 2009-09-22
forum: Catalan Team
---

### Post by knuss on 2009-09-22
Hola a tothom. Em dic Cesc i soc de Rubi encara que potser fa ja un parell d'anyets que jugo amb el linux 
estic molt verd encara. Dit aixó ,  espero  una mica de peixet. Gràcies :-).

També vull dir que porto quatre dies donant-li voltes al tema que us pregun-t'ho però no he estat capaç de trobar-li sol.lució, o sigui que aqui va,,,,

Faig servir el Xubuntu 9.04 i estaba intentant modificar el Thunar per poder cercar arxius i carpetes amb el boto dret  del ratoli. Un cop vaig reiniciar vaig començar  a tenir molts problemes per entrar a la sessió, costaba moltissim engegar l éscriptori i nomes ho feia de vegades , la majoria de vegades  s'hem queda la pantalla en blanc i la cpu treballant a tot drap. Només aconsegueixo entrar en Root. He desinstalat i tornat a instalar ja varies vegades el xfce4-panel , el Thunar i totes les aplicacions que creia que em podia haver carregat però res que no hi manera.Al final he tingut que fer un altre user pero poder entrar "normal" pero esclar he perdut totes les configuracions de la meva sessió i ufff despres de la vara que em foten els meus fills amb el güindons no ho vull ni pensar ,,,només em falta aixó,,,,ja ja ja

En fi potser es una xorrada però ja no se que provar,,,,

Gràcies i perdoneu el totxo ,,,,

Salutacions >> Cesc

---

### Post by kimet on 2009-09-22
Pots provar d'esborrar el fitxer de configuració de thunar, si no ho havies fet abans, i tornar a instal.lar-lo, es trova a /home/usuari/.config

Salut.

---

### Post by knuss on 2009-09-23
Hola de nou he provat a fer el que meu dit (gracies , Mil gracies ) peo no m'ha funcionat. He trobat aquest fitxer del xsessio errors   i al principi em posa tot aixo , a contiunuacio una llista interminable de erros,,,
En fi no se ho he trinxat tot,, De nou gracies per a qualsevol ajuda.

Salutacions >> Cesc 



/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=ca_ES.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
/etc/xdg/xfce4/xinitrc: 59: source: not found
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 11 overrides entry on line 7
Failed to run gnome-keyring-daemon: No s'ha pogut executar el procés fill «gnome-keyring-daemon» (No such file or directory)
** Message: To replace the current window manager, try "--replace"

** (xfwm4:4073): WARNING **: Another Window Manager is already running
** Message: To replace the current window manager, try "--replace"

** (xfwm4:4086): WARNING **: Another Window Manager is already running
** Message: To replace the current window manager, try "--replace"

** (xfwm4:4080): WARNING **: Another Window Manager is already running
** Message: To replace the current window manager, try "--replace"

** (xfwm4:4078): WARNING **: Another Window Manager is already running
** Message: To replace the current window manager, try "--replace"

---

### Post by kimet on 2009-09-23
Jo diria que no te res a veure aixó dels xsesions errors.
Una possible solució seria, si el nou usuari que has creat funciona bé, importar desde l'antic usuari els firxers de configuració de programes que t'interessin i que intueixes que no estan corruptes. Son els fitxers ocults del /home/usuari, els que porten un punt davant, excepte el .config que sospito es el que t'has carregat.
 
A veure si algú te una millor solució...

Salut.

---

### Post by SiscoGarcia on 2009-09-24
Hola, què tal si crees un nou usuari? Suposo que ho tindrà tot intacte i aquí podràs importar les dades del que "t'ha petat", llavors pots anular l'usuari vell.

---

### Post by knuss on 2009-09-24
si si faig una sessio nova no tinc problemes,, però com importo les dades ? (i ara es quant em surt cara de ruc,,,)
 
Gracies de nou per la  vostra ajuda ,,,
 
Salutacions >> Cesc

---

### Post by kimet on 2009-09-24
Posa per exemple que vols recuperar la teva configuració de firefox. Veuràs que al teu /home/usuari, si esculls la opció "mostrar els fitxers ocults", apareixen una série de fitxers, son els que porten un punt al devant. OK?

Donç vas al /home/usuari-nou i esborres el fitxer anomenat ".mozillla" que és el que correspon al firefox i cópies en el seu lloc el que hi ha al /home/usuari-anterior i haurás importat la configuració del firefox.

Salutacions.

---

### Post by knuss on 2009-09-25
Fabulos!!

 Moltes gràcies .De fet es el primer que vaig provar però com que no vaig canviar les propietats dels fitxers no em funcionava.Ara ja esta resolt.

Molt agraït a tots per les vostres respostes.Ara ja puc eliminar la sessió espatllada,,,
Nomes en falta com arreglar la barra d'eines superior en la que he perdut el botó inici però aixo es el de menys,,,

Salutacions >> Cesc

---

