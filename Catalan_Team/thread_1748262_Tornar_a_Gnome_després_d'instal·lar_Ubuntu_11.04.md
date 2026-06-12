---
title: "Tornar a Gnome després d'instal·lar Ubuntu 11.04"
date: 2011-05-03
forum: Catalan Team
---

### Post by lluisalguero on 2011-05-03
Hola amics,
tot just he fet les primeres passes amb la 11.04 i l'Unity no m'acaba d'agradar, prefereixo 1000 cops Gnome.

Hi ha alguna forma de tornar a aquest escriptori?

Moltes gràcies

Lluís

---

### Post by Original Flo on 2011-05-03
Quan inicis sessió (on et demana definir l'usuari i et demana el password) a la part de sota de tot de la pantalla, un cop tinguis posat l'usuari et deixa escollir l'escriptori.

Et recomano que instal·lis els drivers de la teva tarja de vídeo. Encara que vegis la imatge "prou be", aixo no vol dir que els tinguis instal·lats, de fet, com a mínim en el cas de les ati, ubuntu no els instal·la mai, s'ha de fer sempre "a ma". 

Sense acceleració gràfica hi ha algunes aplicacions que no podràs utilitzar, com per exemple el gestor de finestres compiz (sigui a Gnome, Unity o a l'escriptori que sigui) i moltes d'altres que simplement et funcionaran pitjor, com es el cas d'Uniti que necessita acceleració gràfica per funcionar correctament.

---

### Post by lluisalguero on 2011-05-03
Miraré de instal·lar els drivers tal i com m'has dit, a veure si canvia alguna cosa.

Respecte a l'inici de sessió, ho vaig configurar per a que no calgués demanar usuari i contrasenya...total aquest pc només el faig servir jo, pel que no li trobava sentit.

Una cosa només, sent que actualitzo des de la 10.10, vols dir que calen els drivers? que no guarda la configuració al fer l'actualització?

No sé, pot ser és preguntar per preguntar...

---

### Post by Original Flo on 2011-05-03
> **lluisalguero said:**
> Miraré de instal·lar els drivers tal i com m'has dit, a veure si canvia alguna cosa.

Respecte a l'inici de sessió, ho vaig configurar per a que no calgués demanar usuari i contrasenya...total aquest pc només el faig servir jo, pel que no li trobava sentit.

Una cosa només, sent que actualitzo des de la 10.10, vols dir que calen els drivers? que no guarda la configuració al fer l'actualització?

No sé, pot ser és preguntar per preguntar...


A veure, no es obligatori instal·lar els drivers, pots funcionar sense ells, nomes son necessaris si vols que tot et funcioni com deu mana. Per fer una similitud, no es necessari portar calçat esportiu per fer esport, pots anar amb les sabates del diumenge a jugar un partit de basquet, però igual no estas igual de còmode i pot ser et fas mal i tot.

Sobre l'inici de sessió, si l'as tret, no pots escollir a l'entrada.

No has d'instal·lar res per que Gnome ja ve instal·lat, l'únic que tu no el pots escollir ja que no tens pantalla de login.

A veure si passa algú per aquí i sap com fer-ho.

De totes maneres, comentas que vas fer una actualització. Una pregunta, tens "/home" en una partició separada de "/"? O tens tot junt?

Si vas instal·lar /home en una partició independent, jo ho faria tot de nou.


Salut):P

---

### Post by lluisalguero on 2011-05-03
> **Original Flo said:**
> A veure, no es obligatori instal·lar els drivers, pots funcionar sense ells, nomes son necessaris si vols que tot et funcioni com deu mana. Per fer una similitud, no es necessari portar calçat esportiu per fer esport, pots anar amb les sabates del diumenge a jugar un partit de basquet, però igual no estas igual de còmode i pot ser et fas mal i tot.

Sobre l'inici de sessió, si l'as tret, no pots escollir a l'entrada.

No has d'instal·lar res per que Gnome ja ve instal·lat, l'únic que tu no el pots escollir ja que no tens pantalla de login.

A veure si passa algú per aquí i sap con fer-ho.

De totes maneras, comentas que vas fer una actualització. Una pregunta, tens "/home" en una partició separada de "/"? O tens tot junt?

Si vas instal·lar /home en una partició independent, jo ho faria tot de nou.


Salut):P

Anem a pams:

- He instal·lat els drivers de la pàgina que m'has indicat en l'altre fil. Perfecte, al reiniciar automàticament ha tornat Gnome.

- el "/home" ho tinc tot junt

---

### Post by wgarcia on 2011-05-03
Per configurar perquè t'entri amb l'escriptori Ubuntu Clàssic, i sense demanar usuari i clau, pots anar a "Paràmetres del sistema", ara accessible des del botó d'apagar l'ordinador (a l'extrem esquerra del panel de dalt), i aquí cliques Sistema -> Pantalla d'inici. Aquí podràs escollir l'escriptori que vols (també es pot fer directament des de la pantalla d'inici però si tens configurat entrar directament no la veuràs).

---

### Post by lluisalguero on 2011-05-03
> **wgarcia said:**
> Per configurar perquè t'entri amb l'escriptori Ubuntu Clàssic, i sense demanar usuari i clau, pots anar a "Paràmetres del sistema", ara accessible des del botó d'apagar l'ordinador (a l'extrem esquerra del panel de dalt), i aquí cliques Sistema -> Pantalla d'inici. Aquí podràs escollir l'escriptori que vols (també es pot fer directament des de la pantalla d'inici però si tens configurat entrar directament no la veuràs).

Gràcies, de moment em quedo amb Gnome i a veure si m'acostumo al Unity

---

### Post by Original Flo on 2011-05-03
> **lluisalguero said:**
> Anem a pams:

- He instal·lat els drivers de la pàgina que m'has indicat en l'altre fil. Perfecte, **al reiniciar automàticament ha tornat Gnome.**



T'ha tornat tot sol a Gnome???

Que estrany. Ubuntu Natty entra per defecte a Unity si no canvies res.

Que has iniciat, amb la opció de versió anterior o amb el kernel 2.6.38 d'ubuntu 11.04?

---

### Post by lluisalguero on 2011-05-03
> **Original Flo said:**
> T'ha tornat tot sol a Gnome???

Que estrany. Ubuntu Natty entra per defecte a Unity si no canvies res.

Que has iniciat, amb la opció de versió anterior o amb el kernel 2.6.38 d'ubuntu 11.04?

Si, si...ha tornat tot sol...me quedat una mica "extranyat". I si, he iniciat de la mateixa forma que ho feia abans en que m'iniciava l'Unity. Tot plegat ben extrany

---

### Post by lluisalguero on 2011-05-03
Així ho tinc, sense jo tocar res, bé actualitzar els drivers de la gràfica.

Ara estic mirant si hi ha forma de passar d'Unity a Gnome i viceversa...i no es deixa :o

---

### Post by wgarcia on 2011-05-04
A veure, per aclarir una mica, tant Unity com el que tu dius "Gnome", són Gnome 2.32.1, o llibreries "GTK 2.*", la base és la mateixa. 

El que dius "passar d'Unity a Gnome" et refereixes usar l'escriptori clàssic de Gnome 2. Si tens la pantalla inicial d'Ubuntu és un dels escriptoris que se t'ofereix (anomenat "Ubuntu Classic"). Si no la tens des de "Paràmetres del sistema" (des del menú de sortir a la barra superior), Sistema -> Pantalla inicial t'ho hauria de permetre configurar. 

Per a la versió 10.10 possiblement ja tindrem GTK 3, les llibreries de Gnome 3, i per tant o bé sortirà Gnome Shell com a opció d'entrada, no estic segur que això passi però tampoc ho descartaria, o no hi haurà gaire dificultat de configurar-ho en estar basat tot en GTK 3. Unity també es recompilarà sota aquestes llibreries, no ho van voler fer en aquest cicle perquè els hauria complicat tot molt més ja que en iniciar el cicle de Natty, GTK 3 estable encara estava sense alliberar. Em sembla que fins i tot ja ha aparegut un grup que assegurarà un "sabor" amb Gnome Shell, faci el que faci l'Ubuntu "oficial", i que possiblement es dirà Gubuntu. 

El que està clar és que per als usuaris de Gnome aquest període és un període de canvi, com va passar amb KDE quan va aparèixer la versió 4.

El que no està clar és que hi hagi disponible el Gnome 2 clàssic, tot i que em penso que algú muntarà alguna cosa pels enamorats d'aquest escriptori. Però això segurament serà el que passarà en totes les distribucions a mesura que passin a Gnome 3 (Fedora 15 per exemple o Opensuse).

Per últim dir que lo bo de tot plegat és que tant Gnome 3, com Gnome Shell, Unity o Gnome Clàssic són tots programari lliure i per tant es poden beneficiar mútuament de tot el desenvolupament.

---

### Post by Annatar1707 on 2011-05-05
Jo he pogut utilitzar gnome canviant a ubuntu classic a l'entrada però el problema és que no tinc efectes visuals. Han tret l'opció per activar-ho a aparença. Com ho active?

He actualitzat des de ubuntu 10.10.

---

### Post by Original Flo on 2011-05-05
> **Annatar1707 said:**
> Jo he pogut utilitzar gnome canviant a ubuntu classic a l'entrada però el problema és que no tinc efectes visuals. Han tret l'opció per activar-ho a aparença. Com ho active?

He actualitzat des de ubuntu 10.10.

Has de tenir acceleració gràfica (instal·lar els drivers de la teva tarja) i instal·lar i configurar compiz.

---

### Post by Annatar1707 on 2011-05-05
Els drivers estan instal·lats i tot el que canvie en el configurador de compiz es queda igual que estava. :S

---

### Post by Annatar1707 on 2011-05-05
> **Annatar1707 said:**
> Els drivers estan instal·lats i tot el que canvie en el configurador de compiz es queda igual que estava. :S

El q vull dir es q teòricament els efectes estan activats però no funcionen. La targeta és una NVIDIA Geforce go 7300.

---

### Post by lluisalguero on 2011-05-05
> **Annatar1707 said:**
> Els drivers estan instal·lats i tot el que canvie en el configurador de compiz es queda igual que estava. :S

Així estàs igual que jo...ara per molt que configuri no puc tornar al Unity

---

### Post by Original Flo on 2011-05-05
Posa aixo a un terminal i posa aquí lo que et torni.

```
glxinfo | grep direct
```

---

### Post by Annatar1707 on 2011-05-05
Em torna açò:

direct rendering: Yes
    GL_EXT_direct_state_access, GL_EXT_draw_range_elements, GL_EXT_fog_coord, 



També vull aclarir que el unity no se m'ha arribat a iniciar.

---

### Post by Original Flo on 2011-05-05
I quin efecte concretament es el que no et funciona?

Ventanes gelatinoses?

El cub?

L'únic que se'm passa pel cap es assegurar-se que els efectes que vols estan activats.

Jo ja no se mes. Fins aquí arribo.

A veure si algú amb mes experiència et pot ajudar millor.

---

### Post by Annatar1707 on 2011-05-05
No en funciona cap, de fet no hi ha cap diferència d'entrar mitjançant Ubuntu Clàssic o fer-ho amb Ubuntu Clàssic (sense efectes).

He provat amb el gnome3 però em funciona molt molt lent.

---

### Post by lluisalguero on 2011-05-05
Jo ja ho he provat tot, Ubuntu, Ubuntu Clàssic, amb efectes, sense efectes...

Tot bé després de seguir aquestes recomanacions

[http://ubuntuforums.org/showpost.php?p=10761967&postcount=5](http://ubuntuforums.org/showpost.php?p=10761967&postcount=5)

Hi ha forma de fer enrera?

Gracies

---

### Post by Original Flo on 2011-05-05
Si es pot tirar enrere, desinstalant els drivers, però desinstal-lar els drivers de la teva tarja de vídeo, mai farà que et funcioni millor, si de cas tot lo contrari....

---

### Post by lluisalguero on 2011-05-05
> **Original Flo said:**
> Si es pot tirar enrere, desinstalant els drivers, però desinstal-lar els drivers de la teva tarja de vídeo, mai farà que et funcioni millor, si de cas tot lo contrari....

El que no entenc és com abans em funcionava l'Unity, vaig instal·lar els drivers i ara ja no..:confused:

---

### Post by Original Flo on 2011-05-05
no se com hauràs fet l'instal-lació d'ubuntu ni que hi havia al teu ordinador, però si vols tornar a la configuració inicial de Natty amb Unity, es ben fàcil.
```
unity --reset
```

---

### Post by lluisalguero on 2011-05-05
> **Original Flo said:**
> no se com hauràs fet l'instal-lació d'ubuntu ni que hi havia al teu ordinador, però si vols tornar a la configuració inicial de Natty amb Unity, es ben fàcil.
```
unity --reset
```

Va ser una actualització des de 10.10. Al ficar l'ordre, m'ha fet com unes pampallugues i continua igual, no ha canviat res..:confused:

Aquí et deixo la sortida

```
lluis@lluis-laptop:~$ unity --reset
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Compiz (opengl) - Fatal: glXCreateContext failed
Compiz (bailer) - Info: Ensuring a shell for your session
lluis@lluis-laptop:~$ 

```

---

### Post by Original Flo on 2011-05-05
Pues per l'error que et torna, sembla que no Tingis els drivers de la tarja de vídeo instal·lat. Et dona un error fatal d'openGl, entre d'altres.

posa ```
glxinfo | grep direct
```

I t'hauria de posar una cosa com direct rendering: yes

---

### Post by Original Flo on 2011-05-05
Estaria be també que posessis en un missatge tots junts els problemes que has tingut i les coses que has anat fent, per ordre cronologic des que vas instal·lar ubuntu 11.04, per que esta repartit en un parell de fils i s'hem fa difícil recordar totes les passes que has fet per arribar fins aquí i poder intuir on esta el problema.

---

### Post by lluisalguero on 2011-05-13
> **Original Flo said:**
> Pues per l'error que et torna, sembla que no Tingis els drivers de la tarja de vídeo instal·lat. Et dona un error fatal d'openGl, entre d'altres.

posa ```
glxinfo | grep direct
```

I t'hauria de posar una cosa com direct rendering: yes


```
lluis@lluis-laptop:~$ glxinfo | grep direct
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  137 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  18
  Current serial number in output stream:  18
lluis@lluis-laptop:~$ 


```

---

### Post by HermesM on 2011-05-16
*Off topic* d'un jubilat frustrat.
He saltat de forum a forum i he provat no gensmenys de 10 solucions i pegats.
No rutlla bé, gens bé **gnome-shell**
Va lent, a Aplicacions surten icones duplicats, triplicats i quadruplicats.
No tinc accés directe a la carpeta d'usuari.
No rebo actualitzacions ni puc accedir al seu Gestor i malgrat la por que em fa el terminal, em cal fer els coneguts **sudo apt-get update** i **sudo apt-get upgrade** que, per acovardir-me encara més, intercala forces WARNING misteriosos (no sé anglés)
Sempre he usat mitja dotzena de programes KDE que corrien molt bé amb GNOME... Quatre d'ells no rutllen ara.
Aguantaré com pugui fins al 11.10 si no puc accedir a un tutorial acceptable. :confused:

---

### Post by wgarcia on 2011-05-16
Quan dius Gnome-Shell et refereixes a l'Unity (l'escriptori que s'obre quan des de la pantalla inicial de l'Ubuntu esculls "Ubuntu")?

Si obres un fil específic amb els problemes d'actualització que tens, potser algú pot trobar alguna manera de solucionar-los. I després es pot mirar perquè no rutllen les aplicacions de KDE, haurien de funcionar sense problemes, o els problemes de lentitud.

Pam a pam...

---

