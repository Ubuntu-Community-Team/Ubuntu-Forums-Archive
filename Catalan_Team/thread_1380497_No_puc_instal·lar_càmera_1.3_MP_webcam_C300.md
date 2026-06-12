---
title: "No puc instal·lar càmera 1.3 MP webcam C300"
date: 2010-01-13
forum: Catalan Team
---

### Post by Martima on 2010-01-13
Hola a totes les ànimes caritatives que hi hagi a la zona.

Recentment m'he comprat una càmera Logitech 1.3 MP webcam C300 i no aconsegueixo que em funcioni amb l'ubuntu 9.10

Què coi haig de fer???!!!

Tinc instal·lat l'skype i el cheese però cap dels dos em troba la càmera (ni el micròfon, que hi va integrat. El xat de l'skype em dóna -a més- problemes per escriure accents, tot i que em surt com si estigués instal·lat correctament.

No tinc massa idea de linux i programacions i coses d'aquestes. Expliqueu-m'ho per a tonets, siusplau.

Mooolt agraït i ja desesperat.

Gràcies.

---

### Post by Albert Que on 2010-01-14
Has aconseguit veure alguna imatge amb l'skype o el cheese? algun missatge concret?

---

### Post by wgarcia on 2010-01-21
Per veure si el teu sistema "veu" la càmera, obre una terminal (Aplicacions -> Accessoris -> Terminal), endolla la càmera, escriu "dmesg" (sense les cometes) a la terminal, copia les 5 o 6 últimes línies, i posa-les en aquest fòrum. Potser algú et pugui ajudar a partir d'aquí.

---

### Post by Martima on 2010-02-05
Em pensava que me'n sortiria i per això he tardat tant a respondre. Però no. No me'n surto. Copio les últimes línies que em dius. Eternament agraït si algú em desxifra l'enigma.

[ 1052.296138] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1053.428144] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1054.428120] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1055.428119] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1056.428113] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1057.428179] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1058.496356] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1059.496102] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1060.496099] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1061.496098] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1062.496097] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1063.496096] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1064.496095] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1065.496093] 2:3:4: cannot set freq 48000 to ep 0x86
[ 1066.496089] 2:3:4: cannot set freq 48000 to ep 0x86

---

### Post by wgarcia on 2010-02-06
Aquest missatges semblen un problema del sistema de so. Tens so? Per acabar de confirmar si el teu sistema veu la càmera, torna a donar la instrucció que t'havia comentat en la línea de comandes, però ara amb el següent format:

dmesg | grep -i uvc

i posa els resultats.

---

### Post by Martima on 2010-02-07
Ostres, Wgarcia. Ja vas bé, perquè fa alguns dies que no sento res de res. Però dies enrere havia funcionat. El so de la càmera no ha funcionat mai, però com a mínim l'ordinador feia sorolls i podia sentir les pelis o els vídeos de yo9utube fins a una de les últimes actualitzacions. Des de llavors que ja no sento res de res.

He escrit el que m'has dit i no sembla que faci res. Em surt una línia igual que la primera de quan obres la pantalla negra per escriure-hi la comanda. Potser no ho he escrit bé? he intentat respectar els espais que sembla que em poses i ho he escrit variant els espais i sense espais per si de cas i sempre, la segona línia és igual que la que surt per defecte quan obres la pantalla "terminal".

Pel què fa a la imatge de la càmera, funciona -aparentment- de forma aleatòria. Tinc el cheese on faig proves i a vegades em veig i a vegades no. El so, com deia, no m'ha funcionat mai. Ara com ara, engego el cheese i em surt com la carta d'ajust i el llumet verd de la càmera no s'engega. O sigui que no deu trobar res de res. Quins misteris. La informàtica no és el meu fort, certament.

Si clico sobre la icona de l'altaveu (un que té una nota musical al damunt) per comprovar que no estigui tot silenciat, em surt un cartellet on diu: "esperant que el sistema de so respongui" i d'aquí no el treus. No vaig fer res, un dia vaig actualitzar les actualitzacions que em suggerien i el so va deixar de funcionar del tot.
***************************************
Ostres! ha aparegut una nova icona que havia desaparegut màgicament de la mateixa manera que ja hi havia sigut temps enrere. És un altaveu amb unes ratlletes al costat i que em permet accedir a les preferències de so.

Eeeeei! i el cheese torna a tenir imatge!! (fins quan??)
******************************************
Ara que sembla que alguna cosa més funciona, torno a escriure el que em surt posant "mseg" a seques.

Res, exactament el mateix misssatge que abans.
[12703.196241] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.200225] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.216034] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.220241] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.224252] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.228228] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.232242] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.248045] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.252234] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.256227] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.260234] 2:3:4: cannot set freq 48000 to ep 0x86
[12703.264237] 2:3:4: cannot set freq 48000 to ep 0x86

---

### Post by wgarcia on 2010-02-08
Si no surt res sembla que el teu ordinador no "veu" a la webcam (si ho estàs escrivint bé). Fes el següent: desconnecta la càmera i torna-la a connectar. Després obres la terminal i entres únicament "dmesg", i ara copia i engantxa les últimes 8 línies que surten a la terminal. 

Però suposo que segueixes sense so, oi? Fes també en la terminal "lspci | grep -i audio" i engantxa els resultats.

---

### Post by Martima on 2010-02-09
_**SITUACIÓ INICIAL. PUNT DE PARTIDA:**_
Hola. Acabo d'encendre l'ordinador i el logo de l'altaveu amb les ratlletes ja no apareix. Si clico sobre SISTEMA--> PREFERÈNCIES --> SO Em surt el mateix missatge de quan el so no funciona "S'està esperant que el sistema de so respongui". La càmera tampoc em funciona (a vegades sí, però ara mateix no). El cheese em surt com una carta d'ajust.

*****************************
_**AL TERMINAL HI ESCRIC EL "DMESG" I COPIO LES ÚLTIMES LÍNIES:**_

[  406.924230] 2:3:4: cannot set freq 48000 to ep 0x86
[  407.926238] 2:3:4: cannot set freq 48000 to ep 0x86
[  408.924196] 2:3:4: cannot set freq 48000 to ep 0x86
[  409.924082] 2:3:4: cannot set freq 48000 to ep 0x86
[  410.924090] 2:3:4: cannot set freq 48000 to ep 0x86
[  411.924100] 2:3:4: cannot set freq 48000 to ep 0x86
[  412.924112] 2:3:4: cannot set freq 48000 to ep 0x86
[  413.924119] 2:3:4: cannot set freq 48000 to ep 0x86
[  414.924131] 2:3:4: cannot set freq 48000 to ep 0x86
[  415.924142] 2:3:4: cannot set freq 48000 to ep 0x86
[  416.924149] 2:3:4: cannot set freq 48000 to ep 0x86
[  417.936049] 2:3:4: cannot set freq 48000 to ep 0x86
[  418.936173] 2:3:4: cannot set freq 48000 to ep 0x86
[  419.936179] 2:3:4: cannot set freq 48000 to ep 0x86
[  421.488127] 2:3:4: cannot set freq 48000 to ep 0x86
[  422.488136] 2:3:4: cannot set freq 48000 to ep 0x86
[  423.488146] 2:3:4: cannot set freq 48000 to ep 0x86
[  424.488158] 2:3:4: cannot set freq 48000 to ep 0x86
[  425.488166] 2:3:4: cannot set freq 48000 to ep 0x86
[  426.488176] 2:3:4: cannot set freq 48000 to ep 0x86
************************************************************************************
_**ESCRIC lspci | grep -i audio i copio resposta:**_

lspci | grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

---

### Post by wgarcia on 2010-02-09
Quina versió tens? Fes
uname -a 

i posa el resultat.

Sembla un problema entre l'aplicació pulseaudio i la teva tarja de só. Prova de fer el següent a veure si ho arregla:

sudo rmmod snd_usb_audio

et demanarà la clau. Aquesta instrucció simplement remou el mòdul d'audio per l'USB del nucli, però no permanentment, sols fins que tornis a engegar el sistema. Com la càmera possiblement té un micròfon i és USB, possiblement hi ha una incompatibilitat entre el sistema de so de la càmera i la tarja de so integrada. Mira si un cop fet això recuperes el so. 

Hi ha un error a la llista d'errors de l'Ubuntu que és semblant al teu i encara està obert: 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/459445](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/459445)

---

### Post by Martima on 2010-02-09
Efectivament, la càmera duu el micròfon incorporat i tot plegat duu un cable USB. T'adjunto resultats.

marta@nanosdesants:~$ uname -a
Linux nanosdesants 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux
marta@nanosdesants:~$ sudo rmmod snd_usb_audio
[sudo] password for marta: 
marta@nanosdesants:~$

******************************************************************
Eeeeeeeeeeeeei!!!!!!!!!!!! això torna a sonar!!!! puc sentir un vídeo qualsevol d'internet.

Si t'ha de servir d'ajut en aquesta tasca investigativa, t'explico algunes altres constatacions:
* Després d'escriure el que m'has dit, ha tornat a aparèixer la icona de l'altaveu amb les ratlletes, on em deixa obrir les "preferències de so". Quan he engegat l'ordinador, aquesta icona no sortia i no sé trobar les preferències de so. Si clico sobre la icona de l'altaveu amb la nota musical (aquesta icona hi és sempre, la de l'altaveu amb les ratlletes només apareix de forma intermitent, quan la càmera funciona parcialment).
* Després d'aquestes proves que m'has indicat, el cheese torna a oferir la imatge de la càmera. Intento autofer-me un vídeo, però el vídeo resultant només dura pocs segons i no té registre de so.
* Engego el "system testing" de SISTEMA-->ADMINISTRACIÓ-->COMPROVACIÓ DEL SISTEMA i marco la prova de so. Diu de gravar unes paraules i que les hauria de sentir al cap d'un segons. Al cap d'un segons només sento com un soroll de fregit, però res que ni de fons s'assembli al que he dit uns segons abans. Pot ser que no tingui ben escollit les opcions de "input" i "output" de les preferències de so? (disculpi que sigui tant il·lús, però no tenint-ne ni idea, no descarto que pugui ser una xorrada com aquesta). Fa molt poc que m'he instal·lat l'ubuntu.


Ara provo de sumergir-me a l'enllaç que m'adjuntes. Molt agraït.

---

### Post by Martima on 2010-02-09
marta@nanosdesants:~$ lspci | grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
marta@nanosdesants:~$ 
*************************************************
L'enllaç que m'envies em sona a xino i provar coses a veure si és el que em sembla entendre ho trobo una mica perillós, que volent-ho arreglar sense estar segur del que toco, puc arreglar-ho però em penso que tinc molts més números per acabar pitjor.


Molt agraït.

---

### Post by Martima on 2010-02-09
Un altre que no em sortia res i ara em diu això:

marta@nanosdesants:~$ dmesg | grep -i uvc
[   27.184885] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0805)
[   28.212109] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).
[   28.216077] input: UVC Camera (046d:0805) as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input5
[   28.216178] usbcore: registered new interface driver uvcvideo
marta@nanosdesants:~$ 

************************************************************
I si ara ho hem arreglat temporalment, quan engegui l'ordinador tornaré a estar com al principi? quan parles d'incompatibilitats entre la càmera i la placa de vídeo vol dir que pot ser que hagi de canviar la placa de vídeo o vol dir que esborrant/actualitzant/descarregant algun arxiu possiblement s'acabi arreglant algun dia?

---

### Post by wgarcia on 2010-02-13
L'enllaç de l'error te'l posava perquè sembla que és el mateix que et passa a tu. Una cosa útil és que vagis a aquest enllaç, i a dalt de tot veuràs que pots escollir "També em passa a mi", perquè és útil per als desenvolupadors saber que li passa a més d'un. 

En aquest fil de l'error diu que a més del que t'havia dit de remoure el mòdul de so d'usb:
sudo rmmod snd_usb_audio
també s'ha de remoure un altre mòdul
sudo rmmod snd_usb_lib

L'error està reconegut i segurament sortirà alguna actualització aviat que ho arreglarà. 

Això és purament temporal, quan tornis a engegar l'ordinador els mòduls s'hauran carregat un altre cop i si vols fer servir la càmera hauràs de tornar-ho a fer. Si no fas servir la càmera, és a dir si engegues l'ordinador amb la càmera desendollada, funciona el so?

Quant a la icona de l'altaveu amb les ratlletes, fes clic amb el botó dret i en "Preferències de so" mira a Hardware (no sé si surt així a la traducció que fas servir, pot ser "maquinari") quines opcions et surten i posa-les aquí a veure si poden ser d'utilitat.

---

### Post by Martima on 2010-02-14
Ahir vaig esborrar els arxius que deies. Avui he desendollat el USB de la càmera i he reiniciat l'ordinador. Tot funciona de meravella. Em penso, vaja. Em surt la icona de l'altaveu i puc accedir a les preferències de so.

Quan conecto la càmera és quan comença tot a funcionar aleatòriament.

Adjunto les preferències de so que demanes.

[[IMG]http://img638.imageshack.us/img638/5356/capturaga.png[/IMG]](http://img638.imageshack.us/i/capturaga.png/)

Gràcies.

---

### Post by wgarcia on 2010-02-16
Sembla confirmat doncs qué és un problema de conflicte entre el sistema de so i la webcam. 

Després de les proves que has fet, no em queda clar. Repassem:

1) Si engegues l'ordinador sense la webcam endollada funciona el sistema de so.

2) Si endolles la webcam el sistema de so deixa de funcionar. 

3) Després de fer:

sudo rmmod snd_usb_audio 
sudo rmmod snd_usb_lib 

Si ara endolles la webcam funciona tant la webcam com el sistema de so. 

És així?

---

### Post by Martima on 2010-02-16
Quina paciència, Wgarcia. Agraït per l'esforç.

1. Punt de partida. La càmera està conectada i el so no funciona. La icona de l'altaveu amb les ratlletes no m'ha aparegut quan he iniciat l'ordinador (a vegades surt i a vegades no). Si que m'apareix la icona de l'altaveu amb la nota musical (aquesta no m'apareix i desapareix aleatòriament com l'altra). Si clico sobre la icona de l'altaveu amb la nota, em surt un missatge que diu "esperant que el sistema de so respongui". Els vídeos d'internet no fan soroll. Allò de SISTEMA--> Administració --> comprovació del sistema --> so no em funciona. Teòricament hauria de poder gravar un missatge i el tornaria a sentir. Res de res. Fi de les comprovacions. Desconecto el usb de la càmera.
Curiosament, quan tinc la càmera conectada, l'ordinador em va més lent. Molt més lent. S'ho ha de pensar tot molt més, els vídeos tarden a carregar-se, el correu també, els links tarden alguns segons a obrir la pàgina on em dirigeixen, el cursor és una mica lent a mesura que escric. ETc...
Si escric les ordres que em dius: sudo etc, etc, etc em surt el missatge que adjunto com a captura de pantalla. Val a dir que ja ho havia escrit el dia que m'ho vas dir per primer cop i sembla que es van eliminar els dos arxius. Però avui em dóna aquest altre missatge que ajdunto.
2. No he reiniciat l'ordinador. He desconectat la càmera a saco. El so funciona. Els vídeos d'internet tenen so que puc canviar de nivell. Si clico sobre la icona de l'altaveu amb la nota musical, m'apareixen les opcions de so (no m'apareix allò de "esperant que el sistema de so respongui"). No puc comprovar allò de "comprovació del sistema" --> so perquè em demana que parli per un micròfon que està integrat en una càmera que tinc desconectada. Tampoc puc comprovar-ho amb els vídeos del cheese perquè em diu que no troba una càmera que no tinc conectada, lògic. Torno a conectar la càmera, també a saco.
3. Retorn a les condicions inicials del punt 1. Internet lent, missatge de'esperant que el sistema de so respongui, etc... veure punt 1. Adjunto captura de pantalla amb el missatge que em dóna.

[[IMG]http://img651.imageshack.us/img651/5849/capturang.png[/IMG]](http://img651.imageshack.us/i/capturang.png/)

---

### Post by papapep on 2010-02-16
martima: si us plau, per adjuntar imatges tan grans feu-ho com a adjunt o, si no podeu o sabeu, pengeu-la a imageshack.us i enganxeu al fòrum la url que aquest dóna per visualitzar-la. Sinó ho fem així ens carreguem la visualització dels fils. ;)

---

### Post by wgarcia on 2010-02-17
És possible que necessitis alguns elements del sistema de so més nous que el que proveeix la versió actual d'Ubuntu. Per això es pot fer servir el dipòsit "backports", que són versions que van desenvolupant, ja prou provades i estables per instal·lar però no part de la versió actual. Per instal·lar mòduls de so d'aquest dipòsit, entra el següent a un terminal de comandes:

sudo apt-get install linux-backports-modules-alsa-karmic-generic

i mira a veure si això arregla els teus problemes de so.

La pàgina:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

proposa una sèrie de comprovacions i possibles solucions addicionals (en anglès) que potser et puguin ser d'utilitat.

---

### Post by Martima on 2010-02-17
EEeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeeiii!!!!!!!!!!!!!!! que em penso que s'ha resolt!!!! anava a dir que és un miracle, però o en WGarcia és Déu o això té mé de terranal que de diví.

Després de seguir les teves últimes indicacions, he començat a fer les comprovacions i a les opcions de so--> "entrada"  m'ha aparegut un altre opció daltaveu que mai no havia aparegut fins avui, un tal 0805 Analog mono. Sempre m'apareixia només un tal "audio intern analog stereo" i ara m'apareixien els dos. He anat a buscar l'entrada dels dos i he apujat el so d'entrada (és possible que algunes vegades que no m'hagués funcionat el so, no sabés que en realitat sí que funcionava perquè tenia el so d'entrada al mínim). Total, que em penso que hasta fins i tot em funciona l'skype i el cheese i les proves de so del sistema... que fooooort!!

Molt agraïts.

---

### Post by wgarcia on 2010-02-18
Me n'alegro, a veure si és veritat que s'ha solucionat.

---

### Post by wgarcia on 2010-02-18
Per cert, sisplau tanca el fil com recomanen les instruccions:

12.- Acabeu amb una nota sobre la solució

Com a conseqüència directa dels punts anteriors, és important acabar el fil explicant, si no s'ha fet abans, com s'ha arribat a la solució del problema. De pas, aprofiteu per marcar el fil com a resolt [SOLVED].

Això ho podreu fer un cop us identifiqueu amb el vostre usuari i contrassenya i anant al damunt del fil, fent clic a "Thread tools" i marcant l'opció "Mark this thread as solved". Tingueu present que això només ho podrà fer qui ha creat el fil o un dels moderadors del fòrum.

---

### Post by Martima on 2010-02-18
Ah, vale!

Després de força indagacions que podeu seguir aquí mateix, al final se'm va arreglar el problema, crec que duent a terme la última de les resolucions d'en WGarcia, això de

sudo apt-get install linux-backports-modules-alsa-karmic-generic

Aquesta actuació em va fer aparèixer a les opcions de so--> "entrada" una altre opció d'altaveu que mai no havia aparegut fins avui, un tal "0805 Analog mono"

Escollint aquest 0805 analog mono vaig poder configurar les opcions de so (pujar el so d'entrada, que per defecte surt a zero) i voilà!!

La càmera funciona a tot gas!  molt agraïts.  I a distància!

---

