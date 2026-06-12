---
title: "KDE- Posant un peu a l'aigua."
date: 2007-03-09
forum: Catalan Team
---

### Post by CarlesOriol on 2007-03-09
Us comparteixo les primeres situacions no desitjades (SND) que m'he trobat al fer un tastet de kde. Alguna incidència/reflexió és deguda al fet d'executar-ho des d'ubuntu i no des de una instal·lació de kubuntu.



**INCIDÈNCIA: - ESTÈTICA**
	Quan engegues una finestra amb una aplicacio gnome (evolution, gedit...) els fonts es veuen sense l'"antialiassejat".
**SOLUCIÓ:**
	PENDENT!

**INCIDÈNCIA: - CRÍTIC**
	No em van els accents!!!

	No hi ha cap opció disponible al menu del kcontrol draceres de teclat.

**SOLUCIÓ:**
	Editar /etc/environment

		PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"

		LC_ALL=ca_ES.UTF-8
		LANGUAGE=ca_ES.UTF-8
		LC_TYPE=ca_ES.UTF-8
		LC_MESSAGES=ca_ES.UTF-8
		LANG=ca_ES.UTF-8
	

**INCIDÈNCIA: - Conquerit**

	Al penjar una imatge des de el forum del catalanteam quan tanques la finestra de l'arxiu adjunt el konqueror es tanca de cop.

**SOLUCIÓ:**

         Pendent

**INCIDÈNCIA: - EMPRENYADOR**

	Si he iniciat un "gksudo aplicacióenkde" als inicis automàtics d'insercio de disc (sd, usbdisk) s'obren dues finestres 1- usuari + 1 root

**REFLEXIONS DEL DIA**

	Fa temps vaig provar el kubuntu i recordo haver vist un gestor de paquets diferent al simpàtic :-). Com es diu?

	Les pestanyes al navegar carpetes al konqueror. Un invent collonut !! 

	El apretar amb el butó del mig a la penstanya del navegador no la tanca. Canvi d'hàbits de firefoxista.

	Les icones predeterminades de l'openoffice son HORRIBLES

---

### Post by orestesmas on 2007-03-09
> **CarlesOriol said:**
> Us comparteixo les primeres situacions no desitjades (SND) que m'he trobat al fer un tastet de kde. Alguna incidència/reflexió és deguda al fet d'executar-ho des d'ubuntu i no des de una instal·lació de kubuntu.


Com ho has instal·lat? a través del paquet "kubuntu-desktop"?

> **CarlesOriol said:**
> 
**INCIDÈNCIA: - ESTÈTICA**
	Quan engegues una finestra amb una aplicacio gnome (evolution, gedit...) els fonts es veuen sense l'"antialiassejat".
**SOLUCIÓ:**
	PENDENT!


No sé què deu ser. Jo acabo d'instal.lar el Gedit i jo ho veig bé...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=26965&stc=1&d=1173434725[/IMG]

> **CarlesOriol said:**
> 
**INCIDÈNCIA: - CRÍTIC**
	No em van els accents!!!


Això no és cosa del KDE, el Gnome se les pinta sol per fer que no vagin els accents :-) Si la memòria no em falla a les llistes de Debian i Ubuntu hi ha uns quants desesperats amb això.


> **CarlesOriol said:**
> 
**INCIDÈNCIA: - Conquerit**

	Al penjar una imatge des de el forum del catalanteam quan tanques la finestra de l'arxiu adjunt el konqueror es tanca de cop.

**SOLUCIÓ:**

         Pendent


A mi m'ha passat que a la Kubuntu de la feina el Konqueror em peta molt de tant en tant. En canvi a la ebian de casa no em passa. Potser és un bug del KDE de la Kubuntu...

> **CarlesOriol said:**
> 
**REFLEXIONS DEL DIA**

	Fa temps vaig provar el kubuntu i recordo haver vist un gestor de paquets diferent al simpàtic :-). Com es diu?


Adept, però no està tan acabat com el Synaptic. Jo prefereixo aptitude directament (també sobre el Synaptic).

---

### Post by CarlesOriol on 2007-03-12
Bé abans de res, m'imagino que fer que rutlli correctament el kde instal·lant el kubuntu ha d'anar força bé... però si ho fem instal·lant paquets des de ubuntu... diguem... que... "té petits defectes".... ehem!!

L'amarok i l'accetofòbia.

Em té intrigat la fòbia d'aquest programa als accents estic provant dos escenaris:

 1. Crear una col·lecció des de una carpeta de xarxa (samba).
      A mig procés s'atura dient que ja en té prou d'errors en els fitxers... ho miro ... i es per els accents...

 2. Transportar podcasts a mp3.
      Tinc un mp3 sencillet. Bàsicament funciona com un disc en fat.
      Quan vull passar podcasts (ex: Tornarem a vèncer de catradio) s'atura i un cop més no pot continuar. Si cerquem un podcast sense accents no hi ha problemes.

...alguna idea?

(en ambdos casos les pàgines de codis i els iocharsets estan ben configurats per llegir i escriure des de el mateix konqueror)

---

### Post by CarlesOriol on 2007-03-15
Un altre cop em responc jo sol.

L'amarok v 1.4.3 (el de l'edgy i no sé si alguna versió anterior). No pot crear col·leccions en sistemes de fitxers uft-8 que contingui accents o caràcters de més d'un byte. 

Això és degut a él valor de sortida de strlen que no correspon amb la quantitat d'informació a emmagatzemar.

Està solucionat a la versió 1.4.5 (la del feisty).

Si voleu més informació podeu llegir:

[https://bugs.launchpad.net/amarok/+bug/72673](https://bugs.launchpad.net/amarok/+bug/72673)

o el bugtracker de kde

[http://bugs.kde.org/show_bug.cgi?id=137824](http://bugs.kde.org/show_bug.cgi?id=137824)

---

### Post by orestesmas on 2007-03-15
> **CarlesOriol said:**
> Un altre cop em responc jo sol.

L'amarok v 1.4.3 (el de l'edgy i no sé si alguna versió anterior). No pot crear col·leccions en sistemes de fitxers uft-8 que contingui accents o caràcters de més d'un byte. 


Curiós això que dius... jo tinc tots els sistemes en UTF-8 (tant kubuntu 6.10 com Debian Sid) i no m'he trobat amb aquest problema.... I tinc l'Amarok 1.4.4 i accents per un tub: en els noms de fitxers i en les etiquetes MP3 o OGG.

Per curiositat, poso un enllaç al web d'un vell conegut meu (vell perquè fa temps que segueixo què fa. És una autèntica màquina). Es diu Markus Kuhn, i pot parlar sobre allò que vulgueu. En aquest cas, sobre UTF-8:

[http://www.cl.cam.ac.uk/~mgk25/unicode.html]("http://www.cl.cam.ac.uk/~mgk25/unicode.html")

---

### Post by nagercoin on 2007-03-23
Amb lo vé que va el GNOME i vosaltres amb KDE..., és veritat que tinc GNOME perquè sinó el PC no em va ni patràs... un P III no li demanis la lluna...

---

### Post by CarlesOriol on 2007-03-24
Bé... jo després d'usar uns dies el kde he de dir que em declaro gnomista convençut. 

Però també he de dir que el kde és un gran sistema gràcies a haver estat uns dies usant-lo he conegut grans programes i també he de dir que m'he tret de sobre la mania de mesclar escriptoris. 

Potser això ho puc fer per que no tinc una màquina limitada però jutjar un entorn d'escriptori modern per si funciona en màquines anigues no crec que sigui just. Hi ha projectes dedicats aquest objectiu i cap d'ells no es diu kde ni gnome. Seguint això et comentaré que tot i que el gnome té una engegada més "fina" la falta d'homogenització en moltes llibreries i el fet que hi ha molts projectes entessos com gnome i que no ho son fa que en l'us resulti un sistema més pesat que el kde.

També vull criticar del meu gnome la tossuderia d'alguns de seguir programant en C. Entre d'altres objeccions considero que quan mires el codi, que més dóna arrosseguar funció a funció els punters a les estructures d'objectes que convertir-les a funcions membres d'aquesta creant una classe!!. Això fa que el codi sigui igual d'eficient però molt més pesat d'escriure i de llegir.

L'amic kde fa ràbia que es pengi tant. No sé si això és degut al fet d'haver muntat aquest escriptori sobre un ubuntu (el de gnome).

Atabala l'exés d'informació a les finestres, és massa espés. Sempre tens la sensació que et falta espai per respirar.

Una altra cosa que es fa un pel pesada per a qui vol mesclar l'ús dos escriptoris és la diferenia d'us en les tecles i en les operacions del ratolí. 

Com deia abans, ambdos son genials, ambdos ténen ventatges i inconvenients i si podeu us recomano que no us perdeu ni l'un ni l'altre ja que ampliaran les vostres possibilitats enormement. Jo de moment seguiré usant gnome, però ja fa dies que al meu tray i viuen ja permanentment programes com l'amarok o l'akregator.

---

### Post by CarlesOriol on 2007-03-24
Uops... i seguint els posts anteriors... aquells que com jo useu encara l'edgy si voleu crear col·leccions amb l'amarok en discs utf-8 que us dónin problemes podeu afegir el següent repositori oficial per tal d'actualitzar a la versió 1.4.5

deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy main

---

### Post by orestesmas on 2007-03-26
És una anàlisi força afinada, crec jo.

Potser en un futur no gaire llunyà, gràcies al projecte freedesktop.org podrem veure aplicacions gnome i kde (i també xubuntu, etc) funcionant plegades sense problemes de tecles, etc.

Jo també uso aplicacions Gnome (o gtk): l'omnipresent Gimp, l'inkscape, el firefox en ocasions, l'openoffice (clar que aquest és un món apart...). La gràcia és que pots agafar d'ací i d'allí.

---

