---
title: "amule"
date: 2007-04-22
forum: Catalan Team
---

### Post by bratac on 2007-04-22
Bones, 

l'amule es tanca automàticament quan fa una estona que el tinc engegat, em podeu dir per que passa? Treballo amb Ubuntu 7.04.

gràcies, 

alfred

---

### Post by Fang5 on 2007-04-25
Jo també el feia servir i em feia coses rares quan utilitzava el firefox, ara me baixat un altre que es dui MLDonkey, que es veu que també et pots conectar a altres  xarxes a part de l'ed2k i la kad, el problema es encara no se gaire bé com va, pero com a minim no em fa el tonto.

---

### Post by patrickfromspain on 2007-04-25
jo no tinc problemes amb l'amule.. i el tinc tot el dia engegat. Podries probar a borrar la carpeta .aMule del teu home.

Salut!

---

### Post by CarlesOriol on 2007-04-25
Si et segueix passant pots obrir-lo en una finestra de terminal. 

I quan es pengi copiar el text de l'error per que el veiem.

------------------------------------
Vostra raó es va desfent. 
La nostra és força creixent.
Les molles volen al vent.

---

### Post by lluisanunez on 2007-04-25
Frostwire. Jo el faig servir com complement a Amule, quan no hi trobo el que busco. Frostwire va amb Java i a la pàgina tenen [un download per Ubuntu]("http://www.frostwire.com/")

---

### Post by hackarre on 2007-04-25
Aquest error no passa en alguns casos i no s'ha pogut arreglar, els desarrolladors han donat la idea d'un programa (que no m'enrecordo) que el que feia era que quan se't tencava automaticament se't tornava a engegar segur que trobes inf. pels forums encara que sigui amb angles.

---

### Post by CarlesOriol on 2007-04-26
On has vist això?

---

### Post by CarlesOriol on 2007-04-26
Per cert. Comprova que no tinguis els els directoris temporals o final en una carpeta en un disc ntfs.

[http://forum.amule.org/index.php?topic=10238.msg56142#msg56142](http://forum.amule.org/index.php?topic=10238.msg56142#msg56142)

---

### Post by muleta on 2007-08-27
> **CarlesOriol said:**
> Per cert. Comprova que no tinguis els els directoris temporals o final en una carpeta en un disc ntfs.

[http://forum.amule.org/index.php?topic=10238.msg56142#msg56142](http://forum.amule.org/index.php?topic=10238.msg56142#msg56142)

Jo no hi entenc res en aquest enllaç.

Potser jo tinc això que dius. Vaig guardar la meva carpeta Temp de l'emule i Windows en un disc extern que em sembla que és ntfs i estic tenint molts problemes ara.

Per començar, desde que l'he copiada aquí, l'amule va fent saltirons sense parar, com si ballés una sardana.

No parlem dels fragments que se m'han perdut i allò que em crida més l'atenció es que la carpeta ha crescut molt. És possible que s'hagi fet un backup de cada part.?. Ho dic per aquests part.bak que hi apareixen.

---

### Post by guillemsola on 2007-08-27
Jo faig servir l'amule-daemon (executar amuled) i quant necessito veure com van les descàrregues engego l'amule-gui.

Ho faig aixì pq tinc l'amuled instal·lat en una màquina que fa de servidor i puc monitoritzar les descàrregues des de qualsevol màquina.

Explico tot això pq crec que molts cops els problemes els generen les GUI. De fet el meu servidor no em pregunteu o a través d'una pàgina web. quant fa que no el reinicio i l'amule no s'ha penjat mai encara.

Aquest és un mètode alternatiu per fer funcionar l'amule que a mi personalment em funciona de conya.

aquí ho expliquen una miqueta més

[http://idasdepella.com/?p=49](http://idasdepella.com/?p=49)

Guillem

---

### Post by muleta on 2007-08-27
Tot això que m'expliques no crec que es pugui aplicar al meu cas però em dóna una idea de com pot resultar de difícil resoldre una qüestió que haurien d'haver resolt els desenvolupadors d'amule.

Jo relaciono els saltirons de la meva pantalla quan hi tinc l'amule amb el fet de que tingui aquests fitxers de parts bak.

Si ningú no em diu el contrari, els esborraré un per un i a veure què passa.

---

### Post by guillemsola on 2007-08-28
No se si passa res per esborrar aquests bak. Jo tb els tinc a la carpeta temp de l'amule. Els baks son dels arxius mets amb la informació de la descàrrega, no la descàrrega en si. Ocupen poc i només són per si es corromp l'arxiu original.

Per aquí no crec que vinguin els teus problemes. Les particions NTFS millor evita-les de sortida, encara que si l'amule no pot escriure al disc pq esta ple o no te permís aleshores es tanca sol. Vull dir amb això que aquest disk que tens no deu ser NTFS pq l'amule ha creat fitxers

El que deia el patrick desborrar la carpeta .aMule que està al teu directori personal, serveix per obligara l'amule a començar desde 0.

Recorda sempre que abans desborrar res però és millor senzillament canviar-li el nom a les coses per poder-les recuperar si no ha anat bé la proba.

El que no he acabat d'entendre és això dels saltirons. A què et refereixes?

Salut!

---

### Post by muleta on 2007-08-28
Amb això dels saltirons vull dir que, quan tinc l'amule en pantalla, aquesta es queda en blanc durant mig segon cada 4-5. Fa com unes pampallugues gegants. Però només amb l'amule.

Això de treure'l del directori personal què vol dir?. On l'hauria de posar?.

---

### Post by guillemsola on 2007-08-28
Doncs aquests saltirons no els he vist mai...

respecte a treure'l del directori personal només has d'anar a Llocs-Carpeta d'Inici, aquesta és la teva carpeta personal. Has de tenir activat "mostra els fitxers ocults" (Ctrl+H) La carpeta .aMule el punt inicial vol dir carpeta oculta. Doncs bé, a aquesta carpeta li canvies el nom per exemple .aMule.antic i quant tornis a engegar l'amule veuras que torna a crear la carpeta .aMule al teu directori personal amb els valors posats a 0. Si les coses van maldades borres aquesta nova carpeta i l'antiga li tornes a posar el nom original.

Amb això podràs per exemple veure si l'amule amb la configuració original també et dona problemes i probar coses sense perill.

Salut!

---

### Post by muleta on 2007-08-28
Com que veig que hi entens molt, et continuo preguntant. 

Trobo que el comportament de l'amule és molt diferent del de l'emule. Per exemple, de la manera que s'instal·la (dins d'una altra carpeta amule i deixant alguns fitxers fora). 

Trobo estrany que no crei les carpetes Incoming i Temp. Això em va permetre introdu·ir-li les que ja tenia guardades, sense haver-les de canviar. Però no em va deixar ficar l'Incoming dins de la carpeta interior sino en l'externa que veiem oberta en la captura.

Tot és correcte?.

---

### Post by muleta on 2007-08-28
Misteri: He desinstal·lat l'amule, després de guardar en l'escriptori les carpetes Temp i Incoming. He reiniciat l'ordinador i l'he tornat a instal·lar.

He mirat com funcionava per defecte, sense configurar i... ESTAVA CONFIGURAT com jo el tenía abans de desinstal·lar.

He tornat al Synaptic i m'he assegurat de desinstalar-lo juntament amb tots el paquets complementaris i fitxers que hi féien referència.

Després de fer reboot, l'he tornat a instal·lar i... TORNAVA A ESTAR CONFIGURAT com jo el tenia abans de desinstal·lar-lo. A més, s'ha posat a funcionar continoant les baixades d'abans, sense tenir instal·lades les carpetes Incoming i Temp en el seu directori.

Continua fent els parpallejos, no ha deixat de fer-los mai.:confused:

---

### Post by patrickfromspain on 2007-08-28
per borrar la configuración no has de borrar l'amule: aixo no es el finestres (que diuen per aqui ) ;)

n'hi ha prou en borra la carpeta .aMule del teu home (o renombrar-la)

salut

---

### Post by pespin on 2007-08-28
Suposo que se't quedava la configuració perquè executaves (bé des de la terminal o el synaptic) "remove", i això deixa els arxius de configuració. Hi ha una altra opció que es eliminar completament ("purge")

---

### Post by muleta on 2007-08-28
> **patrickfromspain said:**
> per borrar la configuración no has de borrar l'amule: aixo no es el finestres (que diuen per aqui ) ;)

n'hi ha prou en borra la carpeta .aMule del teu home (o renombrar-la)

salut

No és que em molesti la configuració, eh?. De fet, quan resolgui el problema dels saltirons, tornaré a posar-hi la mateixa.

Em crida l'atenció perque penso que la no resolució és culpa de la desinstal·lació deficient de l'amule, que dec tenir mal instal·lat.

Sabeu com puc eliminar els parpallejos?. Si cal el tornaré a desinstal·lar com m'indiques tú Pespin. Però si no és el camí, no el desinsta·lo.

---

### Post by guillemsola on 2007-08-30
A veure, crec que encara que desintalis l'amule amb l'opció --purge no eliminarà la carpeta .amule que es troba al directori personal de l'usuari. La millor manera repeteixo és borrar la carpeta .aMule del teu usuari.

Per exemple escriure des d'una terminal acabada d'obrir.

> mv .aMule   .aMule.vell

Si després vols recuperar la configuració original

> mv .aMule.vell   .aMule

Per la teva informació en aquesta carpeta .aMule hi ha un fitxer tipus text de configuració anomenat amule.conf que si l'edites hi veuràs totes les opcions del programa. Quant es crea la carpeta .aMule per primer cop és quant es crea aquests fitxer amb els valors per defecte. És per això que no serveix de gaire des-instal·lar l'amule i és millor eliminar aquesta carpeta i forçar que es torni a crear amb els valors per defecte.

Això dels flashos et passa a la que arrenques l'amule o quant ja porta una estona?

Per curiositat he buscat als fòrums d'amule i només n'hi ha un que es queixa del mateix però li passa perquè té una màquina un pel vella.

Si el teu ordinador està bé se m'acut que potser tens posades masses fonts per fitxers o reconeccions... vaja alguna cosa que fa que l'amule funcioni intensivament. Podries provar a baixar les fonts per fitxer i coses així.

I si l'amule no tira doncs proba el MLDonkey que es pot instal·lar des del menú aplicacions/Afegeix-elimina. Ara jo no l'he provat mai!

Salut!

---

### Post by muleta on 2007-08-30
El parpalleix el fa exactament cada 5 segons, desde l'inici fins al final, en la pestanya de transferències.

Ja vaig provar i ho torno a fer sovint de canviar els paràmetres de configuració, un per un, reiniciant. No deixa de fer-ho.

Provaré d'esborrar-ho tot i partir de 0 per anar introduïnt els canvis d'un a un i veure en quin moment apareix.

Gràcies.

---

### Post by albert-I on 2007-09-01
> **bratac said:**
> Bones, 

l'amule es tanca automàticament quan fa una estona que el tinc engegat, em podeu dir per que passa? Treballo amb Ubuntu 7.04.

gràcies, 

alfred
vaja, ja no soc l'unic que li passa,

---

### Post by papapep on 2007-09-01
Potser teniu tots dos la mateixa targeta gràfica?

---

### Post by patrickfromspain on 2007-09-01
A l'amule: Preferencies -> Gui i alla poseu Vista de la barra de progrés totalment a l'esquerra (plana), us ho segueix fent?

---

### Post by neo_76 on 2009-04-15
Hola,
   fa poc que intento passar de windows pero noi...no se fer res. A vore, quan instalo amule, al obrirlo em demana un PW. Es possible? Quin és?

---

### Post by papapep on 2009-04-15
Hola Neo,

Et demana el del teu usuari, no has provat a posar-lo?

Per cert, cada tema necessita un nou fil. Encara que parli del mateix programa, no significa que es pugui seguir el fil parlant d'un altre tema ;)

Per a més referències, passa't pels dos fils de capçalera, el de benvinguda i el dels no-iniciats, que trobaràs damunt els fils "normals", i fes-los una bona llegida.

Benvingut.

---

### Post by papapep on 2009-04-15
> A vore, quan instalo amule, al obrirlo em demana un PW

A aquesta vida, possible ho és tot menys una cosa :)

Ara bé, normal no ho és gens, això no. Te la demana al instal·lar o al executar-lo? amb quin usuari estàs treballant?

Per cert, hauries d'obrir un nou fil, ja que tot i que parli del mateix programa no té absolutament res a veure amb el contingut d'aquest.
Fes una bona llegida als dos fils de capçalera que trobaràs damunt dels "normals", el de benvinguda i el de no-iniciats.

Benvingut.

---

