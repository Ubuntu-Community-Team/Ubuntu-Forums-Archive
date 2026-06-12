---
title: "[COMPIZ] Efectes 3d"
date: 2007-10-23
forum: Catalan Team
---

### Post by prostata on 2007-10-23
Avui he pogut toquinejar una miqueta Compiz, i m'he trobat, per començar, que els efectes 3D dins l'apartat de configuració compiz-Efectes, no hi son...per la qual cosa no puc fer aquells efectes tan guapos que amb Beryl si podia...algú més experimentat amb Compiz em pot dir que fer per tenir els efectes 3D???

moltes gràcies

---

### Post by RainCT on 2007-10-23
Hola,

Prova insta&#320;lant el paquet "compizconfig-settings-manager" (sovint anomenat també «ccsm») des del Synaptic. Llavors tindràs una entrada anomenada «Gl Desktop» al menú Sistema -> Preferències, des d'on podràs configurar algunes coses més (com per exemple activar el cub).

---

### Post by prostata on 2007-10-24
> **RainCT said:**
> Hola,

Prova insta&#320;lant el paquet "compizconfig-settings-manager" (sovint anomenat també «ccsm») des del Synaptic. Llavors tindràs una entrada anomenada «Gl Desktop» al menú Sistema -> Preferències, des d'on podràs configurar algunes coses més (com per exemple activar el cub).


aixó és el que vaig fer des de el primer dia, però malgrat tot a sistema/preferències no hi ha la entrada anomenada GI Desktop, però si una anomenada Advanced Desktop Effect Settings...alguna idea més?? gràcies

---

### Post by oriolsbd on 2007-10-24
Hola, jo estic començant amb ubuntu, i estic tenint el mateix problema que tu.

Ahir al vespre vaig intentar instal·lar-me el paquet "compizconfig-settings-manager", però no em deixava. Em sortia un missatge d'error que em deia que era incompatible amb algun altre paquet que tinc.

Aquest matí he estat mirant en alguns fòrums, i pel que he vist, hi ha un nou programa que uneix Beryl amb Compiz (de manera oficial) que es diu CompizFusion: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Aquesta tarda volia provar com anava, però potser et va bé també a tu.

Salutacions,

Oriol.

---

### Post by papapep on 2007-10-24
Oriol, és probable que acceptant els canvis que et proposa el gestor de paquets solucionis el teu problema. Però en tot cas, per precaució, enganxa'ns aquí el missatge que et dóna.
Estaria bé saber si estàs amb Feisty o Gutsy, per a més coneixement de causa.

---

### Post by RainCT on 2007-10-24
> **oriolsbd said:**
> pel que he vist, hi ha un nou programa que uneix Beryl amb Compiz (de manera oficial) que es diu CompizFusion

Aquest és el que té l'Ubuntu Gutsy.

---

### Post by prostata on 2007-10-24
Acabo d'arrencar novament el sistema i sorpessaaaaa!!!!!!! sense fer res de res, senzitllament arrencar l'equip....el que avanç era un cub d'escritpori ara s'ha convertit en un......................Triangle d'escriptori,

¿voleu dir que compiz fussion, per gibbon está prou ben testat?
¿si des instal-lo fusion, puc instalar Beryl? ¿es compatible beryl am la gutsy gibbon??

---

### Post by oriolsbd on 2007-10-24
Jo ahir és el que vaig acabar fent: instal·lar-me el Beryl. A través del Synaptic només has d'escollir el paquet que es diu així (beryl) i instal·lar-lo (ja agafa les dependències).

Per configurar-lo, tindràs l'opció a "Aplicacions -> Eines del sistema" o algo així (no estic connectat des de l'Ubuntu).

Salut!

Oriol.

---

### Post by prostata on 2007-10-24
> **oriolsbd said:**
> Jo ahir és el que vaig acabar fent: instal·lar-me el Beryl. A través del Synaptic només has d'escollir el paquet que es diu així (beryl) i instal·lar-lo (ja agafa les dependències).

Per configurar-lo, tindràs l'opció a "Aplicacions -> Eines del sistema" o algo així (no estic connectat des de l'Ubuntu).

Salut!

Oriol.

Ja ho vaig mirar, però a sinaptyc Beryl porta un munt de entrades, des de manager fins a... quines haig de sel·leccionar?

gràcies

---

### Post by oriolsbd on 2007-10-24
Em sembla recordar que es deia directament "beryl" (sense res més). Mira-ho. de tota manera, aquesta tarda ho miro jo també. Si instal·les aquest paquet, el Synaptic ja t'escollirà tots els paquets que necessiti.

---

### Post by jerec on 2007-10-24
Beryl i compiz son dos projectes que s'han ajuntat per crear compiz-fusion, fins i tot els dos forums que hi havia ho han fet, es va anunciar a bombo i plateret que la versio Gutsy ja portaria el compiz-fusion al seus repositoris de base. ho podeu llegir aqui:
[http://www.ubuntu.com/getubuntu/releasenotes/710tour]("http://www.ubuntu.com/getubuntu/releasenotes/710tour")

Abans podies instal.lar el beryl o el compiz i provar aquest dos entorns 3D, despres amb els repositoris de Treviños  podies instalar el compiz-fusion, pero es recomanable tenir el sistema net de beryl, compiz i emerald.

Jo amb el Feisty el tenia configurat optimizat al maxim del que dona els 3D de la nvidia Quadro que tinc al meu sistema. Cub, efectes anell, moure finestres entre escriptoris, paginador d'aplicacions, efecte dodge,etc, etc.

Ara mateix estic renegant amb l'actualitzacio del Gutsy, pero aixo sera en un altre fil, les miseries que he anat  trobant que amb Feisty anaven de nassos i amb el Gutsy no em funcionen i estic arreclant.

Coses a tenir en compte, de la meva humil experiencia amb el compiz-fusion:

- Tenir el sistema net de beryl i compiz, abans de fer la instalació:

- instalar el compiz-fusion amb tots els seus paquets necessaris (treviños o desde synaptic si feu servir Gutsy) els paquets necessaris son: 
compiz 
compiz-kde (o compiz-gnome en cas de gnome)
compizconfig-settings-manager
compiz-core 
compiz-plugins 
compiz-fusion-plugins-extra 
compiz-fusion-plugins-main  
libcompizconfig-backend-gconf o kconfig
libdecoration0
python-compizconfig

- Instalar tambe el fusion-icon, seria la icona que hi habia en beryl (el diamant vermell), pero per compiz-fusion, on es pot obrir el ccsm (compiz-setting-manager) i triar entre compiz o metawin etre altres coses
No esta al synaptic , vaig posar un  link en aquest altre post [http://ubuntuforums.org/showthread.php?t=586349]("http://ubuntuforums.org/showthread.php?t=586349")

-Han canviat els fitxers amb la configuracio dels plugins, si abans era tot a /home/nom_usuari/.config/compiz/compizconfig a dins dels fitxers config i Default.ini ara han canviat les definicions i algunes estan al fitxer /home/nom_usuari/.kde/share/config/ccsrc (per exemple abans l'ubicacio dels wallpapers del cub estaven a Default.ini i ara estan ccsrc

-Els multiples fons de escriptori no surten sino mateu el  kdesktop, podeu fer un script a dins de .kde/Autostart que al entrar faci un killall kdesktop (amb el gnome crec recordar que es la decoracio de nautilus). Penseu que si feu axio heu de sacrificar les icones del escriptori.

-Tambe han canviat la GUI del ccsm, haureu de tornar a apendre com va

Tal i com he dit abans l'update cap a Gutsy m'ha rcanviat la configuració del  compiz-fusion, a mes a mes encara em falta trobar perque no tinc acceleracio 3D si aparentment el driver de nvidia  esta ben configurat. Espero poder-mi dedicar i deixar el Gutsy semblant al Feisty per poder anar aportant dubtes del compiz-fusion. Em dona la sensació que han corregut massa en treure aquesta nova versió de Ubuntu.

---

### Post by prostata on 2007-10-24
Anem de sorpressa en sorpressa amb el compiz. he des instal·lat tot, vull dir, compiz-emerald-beryl...tot...tot...tot. he deixat al SO sense cap mena d'efectes i virgueries varies.

he reiniciat l'equip.
he instal·lat compiz
he configurat el cub-escriptori i girar el cub, simplement per no carregar gaire el compi i ara el cub-escriptori surt no com un cub o un triangle com la darrera vegada, no, ara surt només com un pla, que gira aixó si, peró pla....estem segur que compiz, la versió de gibbon está prou testada?? segur que si, que ho está, deu ser la meva ignorancia ;-) hi han mes foristes que hagin passat per experiencies XXXX amb compiz i hagin pogut amb ell???

salutacions

---

### Post by CarlesOriol on 2007-10-24
Sols tens dos espais de treball

Obre el ccsm > opcions generals > desktop size (estic en feisty encara i no tinc la traducció correcta) i allà tries a Mida horitzontal el nombre d'espais. Si n'hi ha 2 veuras un pla, si n'hi ha 3 un triangle... etc...

---

### Post by oriolsbd on 2007-10-25
En resposta a un post d'en papapep, el paquet que estava intentant instal·lar era el gnome-compiz-manager, i l'error que em donava és aquest:

gnome-compiz-manager:
 Depén: libgnome-compiz-manager0 però no s'instal·larà
 Depén: libwnck18 (>=2.15.90) but it is not installable

De tota manera, ara estic treballant amb Beryl i em va força bé. Vaig fer una última prova amb el Compiz instal·lant el paquet compizconfig-settings-manager (apart de tots els altres que comentava en Jerec) i em sortia el menú per configurar el Compiz però, quan hi feia clic, no se m'obria cap finestra.

Gràcies.

Oriol.

---

### Post by prostata on 2007-10-25
el que vull a conseguir es aquest efecte, mireu les finestres com tenen el seu tamany, el seu grossor, la seva separació, en fin aixó a beryl era la mar de fàcil, com es fa amb compiz??

---

### Post by jerec on 2007-10-25
[QUOTE=prostata]
el que vull a conseguir es aquest efecte, mireu les finestres com tenen el seu tamany, el seu grossor, la seva separació, en fin aixó a beryl era la mar de fàcil, com es fa amb compiz?? 
[/QUOTE]

Dons amb compiz-fusion tambe es la mar de facil. Aquest efecte es diu "3D Windows" i es a la seccio "Effects"

---

### Post by prostata on 2007-10-25
> **jerec said:**
> Dons amb compiz-fusion tambe es la mar de facil. Aquest efecte es diu "3D Windows" i es a la seccio "Effects"

Lloat sia Deu!!!!!! habemus centradum el tema pel motiu determinant!!!!!

jo sempre he sabut, sempre, vinc de Beryl, que aquest efecte era dins 3D i anomenat 3D. Aquest efecte es a beryl dins l'apartat Effects i es coneix com bé dius "3D windows", ara bé, ¿quin ha estat tot el temps la meva inquietut i que tal vegada no he deixat prou clara:

Jo no en tinc dins Effects l'opció 3D Windows....no la tinc, no hi es. Pot ser es algun plugin??, no ho sé, pero el cas es que no ho tinc i per aixó les meves insistens aportacions.......

Ara bé, doncs:
Es algun plugin?? quin es? on es troba?
Pot ser algun problema d'instal·lació???
Em diexo alguna llibreria o dependència??

Moltes Gràcies

---

### Post by rajoar on 2007-10-25
Efectivament, com diu prostata, a dins el meu menu effects hi tinc 13 submenus, però no ni ha cap de 3D Windows....

---

### Post by prostata on 2007-10-25
> **rajoar said:**
> Efectivament, com diu prostata, a dins el meu menu effects hi tinc 13 submenus, però no ni ha cap de 3D Windows....

I........................
Sabeu perquè..................................??????????
Osti tú...tres dies tocant les ..... i ara resulta que la versió que incorpora gibbon no..................

no incorpora..........................
l'efect 3D windows...........................
s'ha de canviar a altre versió, la qual no en sé quina és.............

algú la te instal-lada?????

siau

---

### Post by prostata on 2007-10-25
aquí están els binaris, o les fonts???? de la 0.6.0.

[http://releases.compiz-fusion.org/0.6.0/](http://releases.compiz-fusion.org/0.6.0/)

com és tracten, com es descarreguen? com s'he instal-len???

---

### Post by CarlesOriol on 2007-10-25
Segons he llegit al fòrum de compiz-fusion aquest efecte no funciona correctament ja que requereix canvis al nucli i per això a la versió 0.6 està deshabilitada la seva compilació. 

Crec que la versió del gutsy s'ha curat en salut evitant tot alló que no està previst o garantit que funcioni de cara al futur.

---

