---
title: "Organització en particions"
date: 2007-06-02
forum: Catalan Team
---

### Post by Dimas on 2007-06-02
Bones,

Fa temps que he anat utilitzant Linux espontàniament, però encara mai com a sistema operatiu principal. Això espero que canvii ben aviat, ara que em compro ordinador i hauré de començar de nou. Però tinc un dubte, m'explico.

Amb el sistema Windows intento ser organitzat, mantenint el nucli del sistema, els programes i les descàrregues tot separat, i sabent sempre on tinc els meus arxius de configuració per si mai he de formatejar o actualitzar-me saber què he de guardar. Això ho faig tenint tres particions:

- La C: -> El Windows i els programes més bàsics
- La D: -> Els programes i jocs instal·lats, a més dels meus documents personals.
- La E: -> Música, pelis, programes i altres descàrregues

D'aquesta manera si mai he de formatejar en tinc prou guardant quatre coses de la C:\ ja que la majoria de documents personals ho tinc en altres particions.

Per fer una distribució similar amb Linux com ho hauria de fer? I si vull compartir dades amb un altre sistema Windows?

Alguna recomanació?

Gràcies.

---

### Post by Ferri on 2007-06-03
Normalment n'hauries de tenir prou amb tres particions:
root (muntada com a "/"), o partició arrel, on hi tindràs tots els programes
home (muntada com a "/home"), que és on es desaran tots els fitxers i programes personals teus i dels altres usuaris (si és el cas).
swap, que és la partició d'intercanvi.
Així, tens el que tu vols, cada cop que et vulguis instal·lar una distribució, per exemple, n'hi ha prou deixant la "home" per conservar tots els teus fitxers i configuracions personals.
Un gran avantatge, per a mi, és que així no perds la configuració d'escriptori que tens, per exemple (fons de pantalla, icones...).
Pots configurar particions addicionals però no hi veig massa avantatges. Una possibilitat és tenir una partició user (muntada com a "/usr"), que és on s'instal·len els programes que no formen part del que seria el nucli principal de linux, però si canvies la distribució o reinstal·les difícilment et servirà de res conservar-la (més aviat et donarà un colla de problemes).

---

### Post by Dimas on 2007-06-03
O sigui, el /home seria com el "Documents and Settings" de Windows i es pot tenir en una partició a part? Em sembla de conya! :) I el /usr seria com el "Archivos de Programa", tot i que com bé dius, de poc servirà si s'ha de reinstal·lar el sistema ja que es perdran configuracions...

Llegint per inet m'he trobat que algú recomana tenir una partició per **/boot**, però no he sabut entendre què conté aquesta carpeta ni què s'aconsegueix tenint-la a una partició a part. Algú em pot il·luminar? ;)

També tinc dubtes sobre els sistema de fitxers. EXT3 és el més recomanat per Linux? Per altra banda, una partició on comparteixi dades entre Windows i Linux es continua recomanant la FAT32 o ara que hi ha un driver NTFS decent ja es podria fer en aquest sistema? Què hi dieu?

Encara no tinc el PC nou, però la idea que tindria amb les particions seria la següent (a falta de saber més sobre /boot). Què us sembla? I l'espai de cada una?

* DISC DUR 1 (250GB)
** Partició 1 (Root) / (EXT3) (Ocupació 120GB)
** Partició 2 (Home) /home (EXT3) (Ocupació 6GB)
** Partició 3 (Swap) (EXT3) (Ocupació 4GB -2GB RAM-)
** Partició 4 (Windows) (NTFS) (Ocupació 100GB)
(20 GB lliures per entorn de test)
* DISC DUR 2 (250GB)
** Partició 1 (Dades) (NTFS) (Ocupació 250GB)

---

### Post by joant on 2007-06-03
hola,

com que et posaràs la /home a una partició independent, també pots preveure una partició addicional per a posar-hi distribucions noves en fase de proves. Es a dir, en una partició la distribució de producció, i en una altra la nova distribució de torn que pot compartir el \home i t'evita fer actualitzacions traumàtiques.

Salut.

Joan T.

---

### Post by papapep on 2007-06-03
> O sigui, el /home seria com el "Documents and Settings" de Windows i es pot tenir en una partició a part? Em sembla de conya!  I el /usr seria com el "Archivos de Programa",

És una cosa semblant, però no igual. Linux, i en aquest cas les distros derivades de Debian , té una política de directoris estricta a fi de garantir que tot funciona correctament, però tu ets el que té la última paraula. Si vols montar-ho tot a una partició o en vols tenir un munt, és la teva decisió. Fins i tot pots instal·lar programes on et plagui, però no és aconsellable i menys si ets novell.
Respecte com compartir dades amb windows, jo el que faig és compartir un directori linux amb samba, amb el qual, tot i que porti un pèl més de feina per a montar-ho, és més robust i segur.
Sobre el sistema de fitxers "idoni", buff, és complicat. Hi ha gent que diu meravelles d'ext3 i pestes de ReiserFS i viceversa. Fins i tot i ha gent que encara està ancorada a ext2, tot i que no és massa aconsellable.
En principi, qualsevol sistema d'arxius que tingui [journaling]("http://es.wikipedia.org/wiki/Journaling") ofereix una seguretat raonable. 
Sobre què hi sol haver als directoris de l'estructura del sistema de fitxers, [aquí]("http://recepteslinux.homelinux.org/wordpress/?p=3") i [aquí]("http://recepteslinux.homelinux.org/wordpress/?p=4") en pots trobar una breu explicació

---

### Post by Ferri on 2007-06-03
El que dius de fer una partició per a /boot és una possibilitat. A /boot és on hi ha la imatge del nucli del sistema (kernel)  els fitxers de configuració de com es carregarà el nucli i quin nucli es carregarà (el grub, normalment). Fins on sé, penso que el principal benefici pot ser per algú que tingui ganes de "jugar" amb el nucli (compilar-ne un o tenir-ne més d'un), però algú que comença no crec que en tregui gran cosa. Tampoc fa cap mal tenir-ho en una altra partició; l'únic problema pot ser una mala distribució d'espai.
Pel que fa a la repartició d'espai, penso que poses massa espai per a root i swap i poc per a home.
En principi, amb uns 10 GB de root n'hauries de tenir prou (amb 10 GB n'ocupo 3.37) i, en general, el que he vist recomanar de swap sol estar al voltant de 512-1024 MB.
Pel que fa al tipus de format, el que Ubuntu,i la majoria de distribucions, té per defecte és ext3 i, per tant, sembla lògic pensar que és més difícil que et pugui donar problemes.
Les particions NTFS jo les munto directament, només de lectura, però gairebé no les faig servir.
L'instal·lador d'Ubuntu és bastant intuïtiu pel que fa a les particions, i si és el primer cop que instal·les linux, segurament et serà més pràctic dir-li que et particioni el disc automàticament. Si les particions NTFS t'agafen tot l'espai del disc, però, és fàcil que li hagis de dir que te les redimensioni (si és així, defragmenta-les abans o pots tenir problemes).

---

### Post by papapep on 2007-06-03
Ei ! Se m'ha oblidat dir-te que hi ha una utilitat, fa un parell de mesos la vaig trobar, que permet que els W2000 i XP accedeixin tant en mode lectura com escriptura a unitats Ext2 i Ext3 i anava molt i molt bé. Això et serviria si tot plegat és a la mateixa màquina.
La utilitat la pots trobar aquí: [http://www.fs-driver.org](http://www.fs-driver.org)

La única limitació és que només et permetrà accedir a unitats/particions Ext3 que s'hagin desmontat correctament i no tingui cap transacció al diari.

---

### Post by Raimond Roger on 2007-12-23
Companys linuxaires,

Buscant informació sobre com compartir recursos entre linux i windows, he trobat la vostra conversa de ja fa uns quants mesos. I com que el tema m'interessa molt voldría fer-vos alguna pregunta:

Fins ara sempre he utilitzat particions en FAT32 que estan plenament suportades en ambdos sistemes operatius, però tenen el gran inconvenient de no suportar fitxers de més de 3Gb.

Les solucions de ntfs-3g i Ext2 IFS no m'han acabat de merèixer plena confiança.

Voldría provar samba, però desconec aquesta utilitat, tota la informació que trobo fa referència a diversos ordinadors en xarxa, però mai sobre com compartir particions en un mateix ordinador.

Algú de vosaltres podría donar-me una orientació inicial, coneix d'algun tutorial...

Moltes gràcies, siau

---

### Post by CarlesOriol on 2007-12-23
Hola Raimond... i benvingut al club.

El samba no és un tipus de partició sinò un protocol de transferència de xarxa per tal de comunicar-se amb el netbios d'entorns privatius.

El ext2 està desfasat per l'ext3. 

Aactualment el ntfs-3g funciona prou bé per llegir i escriure dades en particions ntfs sempre que no hi hagi carpetes comprimides ni protegides. 
Malgrat tot el format ntfs no suporta característiques avançades com els enllaços a arxius o descriptors de seguretat.

El format ext3 no està suportat nativament en windows però hi ha un munt d'utilitats que et permeten d'usar-lo. Jo et recomano sempre que puguis d'usar aquest darrer.

---

### Post by orestesmas on 2007-12-23
> **Dimas said:**
> 
Llegint per inet m'he trobat que algú recomana tenir una partició per **/boot**, però no he sabut entendre què conté aquesta carpeta ni què s'aconsegueix tenint-la a una partició a part. Algú em pot il·luminar? ;)

Fer una partició específica per al /boot (on resideixen els nuclis que puguis tenir instal·lats) tenia sentit abans, en els sistemes més antics: 

Per poder arrencar el sistema, el carregador necessita accedir al fitxer que conté el nucli, però com que en aquest moment el nucli no està funcionant, l'accés al disc l'ha de fer a través de les rutines contingudes dins la BIOS. Resulta que les BIOS més antigues no podien direccionar fitxers situats més enllà d'una mida de disc concreta (1024 cilindres, uns 8,5GB), i aleshores no podien trobar el nucli de linux, que típicament es situava més enllà del límit, perquè la primera part del disc solia estar ocupada per una partició dedicada al windows.

La solució a això era dedicar una partició de mida petita (100 o 200 MB) que contenia els nuclis i estava situada en qualsevol punt **per sota** del límit aquest. Un cop carregat el nucli, aquest prenia el control i l'accés a disc ja no es feia usant les rutines de la BIOS sinó les pròpies del nucli linux, i aleshores l'accés a particions i dades més enllà del límit deixava de ser un problema.

Avui en dia tot això no cal: Les BIOS i/o els carregadors s'han modernitzat, i per exemple el GRUB no només és capaç de direccionar tot el disc, sinó que també és capaç d'interpretar diversos sistemes de fitxers i per això pot anar a buscar un nucli pel seu nom, enlloc d'haver-ho de fer per número de cilindre, sector i capçal.

Buf! quin rotllo m'ha sortit. Perdoneu...

---

### Post by jodufi on 2007-12-25
Jo et recomano el que et diu el Ferri, amb 10GB de "/" n'hi ha de sobres (jo ara n'utilitzo 2,8 ). Pel tema de la memòria swap, tot i que a molts llocs es recomana utilitzar el doble de la memòria RAM, amb la quantitat de memòria RAM que tens la cosa perd sentit, amb 1 o 2 GB ja en tindries suficient, i el format d'aquesta memòria no ha de ser EXT3, si no swap (o alguna cosa semblant). A la partició "/home" posa-hi les 120GB, ja que és on normalment s'hi guarden les dades, tant de configuració de l'usuari com personals.
També seria bona idea utilitzar el disc dur 2 per a desar-hi copies de seguretat de la partició "/home".

Com veus, cadascú té solucions diferents. :lolflag:

---

