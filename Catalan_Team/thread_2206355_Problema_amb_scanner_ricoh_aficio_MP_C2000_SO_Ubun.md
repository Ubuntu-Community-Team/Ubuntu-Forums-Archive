---
title: "Problema amb scanner ricoh aficio MP C2000 SO Ubuntu 13.10"
date: 2014-02-18
forum: Catalan Team
---

### Post by smenjare on 2014-02-18
Hola

Be, ahir, despres de mes de 16 anys "casada" amb windows, hem vaig divorciar definitivament, espere, i hi vaig instalar al ordinador el ubuntu 13.10. Be fins ara, vaig mes o menys apanyant-me i he aconseguit configurar l'impresora aquesta monstruosa :)
Pero... i l'escanner? no hi manera. Jo tenia escrit com configurar-ho tot perfectament amb windows, com crear una carpeta, enviar-la a l'escritori, com fer aquesta carpeta compartida y amb seguretat (click dret al mouse) i despres des de l'adressa url de la maquina que possar i tot. Pero amb l'ubuntu no hi cap manera. Ja no se el que fer. He creat una carpeta que possa ESCANNER a la Carpeta personal, i amb click dret al mouse l'he compartida. Pero no tinc cap opcio de seguretat. I La ruta a la web de la maquina no se quina possar-hi. Estic una mica desesperada. Gracies per tot si hi ha algu que em puga ajudar. :D

---

### Post by wgarcia on 2014-02-19
Benvinguda a linux, i a veure si tens sort i pots tenir un matrimoni feliç per molts anys. A vegades hi ha coses complicades perquè alguns fabricants ignoren aquest sistema operatiu, i hi ha una mena de monopoli implícit amb Microsoft (i en part amb Apple) per donar suport sols a aquests sistemes operatius.

En tot cas no sé quin tipus de suport compta Ricoh a Linux, però, si entenc el que vols fer, no és massa complicat. Les respostes que dono són per a l'escriptori predeterminat de l'Ubuntu.

1) Per crear una carpeta a l'escriptori simplement has de fer Botó dret del ratolí i al menú escollir "Carpeta nova". Suposo que això ja ho hauràs fet. 

2) Compartir la carpeta: No sé exactament amb qui la vols compartir, però en tot cas jo faria el següent. Un cop creada la carpeta cliques amb el botó dret, i al menú esculls "Propietats". Al diàleg que s'obre escull "Permissos" i aquí tens una opció "Grup", on pots compartir la carpeta amb qualsevol dels grups que hi apareixen. Hi ha un que es diu "scanner" que potser és el que busques, com et comentava no sé si és el cas, perquè no sé què és el que vols fer exactament.

3) Quant a opció de seguretat, tampoc sé a què et refereixes exactament. En principi els teus fitxers i carpetes ja compten amb una seguretat mínima, i a més si ets l'única usuària de l'ordinador tampoc és massa preocupant el tema de la seguretat sempre i quan tinguis una contrasenya per protegir l'accés (si vols més seguretat encara, hi ha eines molt poderoses, perquè una simple contrasenya no protegeix massa si algú té accés físic a l'ordinador). Si el que requereix la configuració de l'scanner és reduir la seguretat, també ho pots fer al mateix diàleg del punt anterior, veuràs que es poden definir permisos d'escriptura i lectura per a tots els usuaris del sistema. 

Bé, en tot cas no sé si tot això és exactament el que es necessita per configurar aquest scanner, i si està suportat o no a Linux (si hi ha controladors, etc.).

---

### Post by smenjare on 2014-02-19
Hola, bon dia, Wgarcia

Moltes gracies per la resposta. He provat a fer el que dius pero quan vaig a propietats, no tinc el grup SCANNER. A veure si et puc explicar millor el que vull (be, no el que vull el que necessite fer). A la web de Ricoh, possa que si esta adaptada la maquina per a linux pero els drivers no hi apareixen per cap lloc. Nomes Windows, Mac i Unix. 

L'impresora multifuncio es d'aquestes que usen a les imprentes. De les grandotes. I va per router o per cable de red. Te una porta d'enllaç on es supossa que tens que possar la IP de l'ordinador am la ruta on es la carpeta compartida que has creat avans per a poder conectar la maquina y el pc a traves de la porta de enllaç (suposo). Tot aço quan tenia la tenda m'ho feia un tecnic, pero ara a casa, ho tinc que fer jo sola. Amb windows, li vaig demanar al tecnic que em diguera els pasos a seguir i com a favor, ho va fer. Pero ara em diuen que per a que un tecnic es desplace a casa meva i m'ho configure tinc que pagar i es un dineral el que demanen per a algo tan ximple com de segur sera... M'ha dit algu que possiblement es pugui activar el protocol SAMBA (SMB) que no tinc cap idea del que es :( i que interactua amb "los entornos Windows" al igual que els suporta MACOS. 

Et pose els pasos que hi havia que seguir a windows, per si decas:


[LIST]
[*]1. En disco C crear carpeta que se llame SCANNER



2. Boton derecho raton sobre dicha carpeta y darle a COMPARTIR (uso compartido) y SEGURIDAD (de red) activar las dos casillas. Aceptamos



3. crear acceso directo de la carpeta al escritorio



4. entrar en internet. en url poner direccion maquina



[192.168.1.34]("http://192.168.1.34/")



inicio de sesion, nombre usuario y contraseña



y enter



entramos en la configuracion de la maquina



5. ir a LIBRETA DE DIRECCIONES



crear / añadir usuario



escribir SCANNER (tal cual exactamente como lo hemos creado en la carpeta en disco C) x 2 veces



autentificacion carpeta y activar



nombre de usuario inicio sesion



y cambiar



y como no hay contraseña, aceptar







[*]abajo del todo de la autentificacion



pone



RUTA: \\[192.168.1.]("http://192.168.1.36/")XX\SCANNER








[*]si da error mis sitios de red, ver equipos del grupo de trabajo

I aço es tot el que tinc. Cada vegada que he formatejat o apagat l'ordinador, l'unic que he tingut que fer, una volta fet totes les pases la primera vegada, ha sigut cambiar la IP de l'ordinador on posa lo de RUTA i ja esta. Tambe, quan formatejes, instalar els drivers, pero clar, per a linux no tinc idea, el cas es que la impresora, entre un conegut virtual i jo una mica varem ser capaços de conectarla. Pero amb l'escanner, res de res... perque no se quina seria la ruta a posar amb un sistema LINUX ni on trovar-la per a copiar-la a la porta d'enllaç.

I encara, si aquest fora l'unic problema dius, val no hi passa res, anim, pero no, hi han un fum :D

Espere que entre tots em pogueu tirar una maneta per que es desesperant, entre aço, el Wine, el PlayonLinux, el thunderbird, els accesos directes de Chrome que tenia de windows en carpetes a l'escritori i que ara a Linux encara que tambe use Chrome no funcionen i un munt mes de coses, tinc ganes de llençarme per algun lloc :D

Moltes gracies per tot...






[/LIST]

[LIST]
[*]







[/LIST]

---

### Post by wgarcia on 2014-02-19
D'acord, ara sí entenc perfectament el que has de fer. Quan a la pàgina diu "Unix" vol dir també "Linux" (Linux ve d'unir la paraula "unix", que és un sistema operatiu de codi obert que es va crear fa més de 40 anys amb "linus" que és el nom del Linus Torval que és qui va desenvolupar el nucli del linux que usen ubuntu i totes les altres distribucions linux, així com també avui en dia els android i fins i tot algunes neveres i rentadores!). 

No sé si algú/na que llegeixi tingui experiència en configurar aquests scanners (jo no...) per xarxa. De moment m'ho vaig mirant i si m'aclareixo ho torno a comentar aquí.

---

### Post by smenjare on 2014-02-19
moltes gracies per respondre. A veure si algu hem pot dir alguna cosa, mentre tu vas mirant o jo... ara vaig liada amb el thunderbird, que tambe tenia per a configurar el outlook i no trove la manera de fer-ho xd pero a veure si descarregue els drivers de unix i fem alguna cosa perque telita... :D

---

### Post by bellera on 2014-02-19
Resposta ràpida, a petició del Walter.
Perdoneu si .... fora de test però acabo de canviar un servidor a la feina perquè havia petat! He d'anar a casa... a sopar...

Aquesta RICOH (i altres) la tenim al Centre i l'escànner admet enviament per correu-e de tot el que s'escaneja. Nosaltres ho tenim així i el professorat ho troba fantàstic.

Com impressores sí que les tenim configurades, amb els PPD PXL que hi ha a [www.openprinting.org](www.openprinting.org)

A reveure,

Josep Pujadas i Jubany
Coordinador TIC/TAC de [www.bellera.cat](www.bellera.cat)

---

### Post by bellera on 2014-02-19
Lllegint ara (havent sopat) tot el fil...

Sí, una altra forma d'escanejar amb les RICOH és enviar el resultat a una carpeta compartida de la xarxa.

S'entén que això vol dir compartició SAMBA/CIFS en termes Unix/Linux. La sintaxi i les credencials d'usuari són igual que per a un equip Windows.

\\nom_maquina\recurs_compartit

per a qualsevol usuari/clau que tingui permís.

Perquè el nom_maquina es pugui resoldre bé, els equips (ordinador i escànner) han d'estar en el mateix grup de treball o domini local. Potser és aquest el problema. Pots provar posant la IP de l'ordinador en lloc del nom_maquina NetBIOS.

Comprova també que a més de samba tinguis windbind instal·lat en el teu ordinador.

A Google hi ha força tutorials, fins i tot vídeos, **ricoh aficio scan to folder**

Veig a [http://support.ricoh.com/bb_v1oi/pub_e/oi_view/0001036/0001036377/view/scanner/int/0052.htm](http://support.ricoh.com/bb_v1oi/pub_e/oi_view/0001036/0001036377/view/scanner/int/0052.htm) que també es pot enviar l'escanejat a un servidor FTP. És una altra possibilitat, tenir un servidor FTP a l'ordinador.

Sort!

Josep

---

### Post by smenjare on 2014-02-19
ostras! m'ha quedat morta! :( no entenc res.... m'ho mirare dema amb calma per que no se que es el samba eixe ni on es trova ni res de res. Tampoc se com posar l'escaner al mateix grup que l'ordinador... ja dic que sols porte 3 dies al mon linux despres de mes de 15 anys amb windows... i no m'entere de res. Per que es tot tan nou per a mi :(
i tampoc se que es windbind. Pero dema m'ho mire i si de cas fare mes preguntes. Moltes gracies per tot :)

---

### Post by wgarcia on 2014-02-20
No has començat precisament amb les tasques més senzilles. configurar una xarxa, tot i que sigui domèstica, és complicat en qualsevol sistema. Però si tens paciència segurament te'n sortiràs. 

El "samba" és una aplicació que permet compartir recursos entre ordinadors Windows i Linux. Comença per instal·lar-lo des-de el Centre de Programari Ubuntu i després continuarem des d'aquí.

També podem anar esbrinant l'adreça IP de l'ordinador, aquell número que et surt a les instruccions que et van passar per a Windows. Per això ves al "traç" com et deia abans, entra "terminal" o les primeres lletres i ja el veuràs i obre aquesta aplicació. Això t'obrirà una consola on has d'escriure:

```
ifconfig
```

Et sortiran unes quantes línies força incomprensibles. Ara: no sé com estàs connectada a la xarxa, si és per cable mira "eth0" i si és per wifi mir "wlan0". En tot cas has de mirar a la segona línia d'aquests blocs on posa "inet addr:" i aquí et sortirà el número que necessites.

---

### Post by wgarcia on 2014-02-20
Per cert, si tens problemes en configurar el thurnderbird obre un altre fil (thread) amb aquest tema perquè això és més fàcil i així es mantenen els dos temes separats.

---

### Post by smenjare on 2014-02-20
bon dia

la ip de l'ordinador la tinc, tambe tinc la de la ricoh. el thunderbird ja esta tot fet. jo configuraba la red domestica a windows i sempre ha segut molt facil... ja dic que per a "conectar" l'escanner a l'ordinador, seguia els pasos que he posat mes amunt i a treballar...pero aci a linux no tinc ni idea... Ara m'imprimire tot el que em dieu que he de fer i ja anire contant, ja que veig que sou rapids contestan :)

De tota mena, es bona idea la de obrir un altre fil per a mes coses, per que poden ser utils a mes persones neofites com jo. Per eixample per instalar el wine, que pareix que no hi ha manera, o per obrir enllaços de chrome que jo a windows guardaba en carpetes a l'escritori de windows arrastrant i ara amb el chrome a ubuntu, no es obrin. Pero be, ara el mes urgent crec que es l'escanner. pas per pas.

---

