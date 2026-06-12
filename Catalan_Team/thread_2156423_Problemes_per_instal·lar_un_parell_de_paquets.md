---
title: "Problemes per instal·lar un parell de paquets"
date: 2013-06-21
forum: Catalan Team
---

### Post by Tiah on 2013-06-21
Hola

Una prèvia: És la tercera vegada que intento explicar-vos aquest problema, però se'm "penja" el fòrum; així que  si apareixen tres fils amb aquest títol  disculpeu-me però m'ha semblat que no han arribat a sortir (els he buscat i no m'apareixien).

Anem al **problema del paquets**:
Tinc un portàtil Compaq Presario C700, Intel® Celeron(R) CPU 560 @ 2.13GHz , de 64 bits. He instal.lat fa tres setmanes el 13.04, abans hi tenia el 12.10 LTS amb un Kompozer com a editor web WYSIWYG, tret del centre de programari. Amb la nova versió del sistema no me l'he pogut instal.lar ja que surt  al Centre ni el trobo amb el Synaptics. El mateix em passa mab el BlueGriffon que seria l'hereu natural de l'antic i un xic trasto Kompozer.  

Així que m'he baixat paquets dels dos editors  web: kompozer-0.8b3.en-US.gcc4.2-i686.tar.gz i bluegriffon-1.7.2.Ubuntu13.04.x86_64.tar.bz2.

He intentat instal.lar-los amb el terminal i no ho he aconseguit. Val a dir que és la primera vegada que ho faig i no he trobat cap procés ni instrucció ben explicats (al menys per al meu nivell)
**Primer **he desomprimit el Kompozer i dins la carpeta he provat[INDENT]sudo apt-get install kompozer
[/INDENT]
I m'ha respost[INDENT]S'està llegint la llista de paquets… Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet%
E: No s'ha trobat el paquet kompozer
[/INDENT]
Res!!!
**Després** he provat[INDENT]sudo apt-get install bluegriffon-1.7.2.Ubuntu13.04.x86_64.tar.bz2
[/INDENT]
La resposta ha estat similar[INDENT]S'està llegint la llista de paquets… Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet%
E: No s'ha trobat el paquet bluegriffon-1.7.2.Ubuntu13.04.x86_64.tar.bz2
E: No s'ha pogut trobar el paquet a través de l'expressió regular «bluegriffon-1.7.2.Ubuntu13.04.x86_64.tar.bz2»

[/INDENT]
Malament. Res tampoc!!![B]
Finalment[/B] he trobat la seqüència  

    [FONT=arial]$ cd packagefolder 
    $ tar xvzf packagename.tar.gz  (if the file is .tar.gz) 
   OR $ tar xvjf packagename.tar.bz2  (if the file is .tar.bz2) 
   $ ./configure 
   $ make 
   $ make install[/FONT]
[FONT=arial]
He clicat
[/FONT]        sudo tar xvjf bluegriffon-1.7.2.Ubuntu13.04.x86_64.tar.bz2[FONT=arial]
Inicialment ha funcionat però quna he clicat ./configure ha respost[/FONT][INDENT]bash: ./configure: El fitxer o directori no existeix
[/INDENT]
I ja no entenc res...

No sé què estic fent malament  i què no entenc quan busco informació.
Si algú em pot donar un cop de mà ho agrairé molt.

Tiah

PD: si veieu el mateix missatge tres vegades a mitges si us plau explique-me com puc eliminar-los- 
[FONT=arial]
[/FONT]Tiah[FONT=arial]
[/FONT]

---

### Post by wgarcia on 2013-06-23
Els fitxers que has baixat no són fitxers instal·lables, com ara els que tenen extensió ".deb", sinó arbres comprimits amb tots els elements per compilar el paquet tu mateix. Els dos estan muntats amb el sistema "tar", d'aquí la primera extensió, i comprimits però de manera diferent, el primer amb el protocol "gzip" (extensió .gz), mentre que el segon utilitza el protocal "bz2". 

Després de descomprimir-lo, segurament t'ha creat un directori, possiblement anomenat "bluegriffon-1.7.2". Abans de donar la instrucció hauries doncs de canviar a aquest directori, amb la instrucció 

```
cd bluegriffon-1.72
```

I un cop aquí fer la instrucció "./configure". Primer assegura't que el nom del directori és realment el que he conjecturat, per això pots donar la instrucció "ls" per veure els directoris i fitxers del directori on has descomprimit el fitxer "bz2" per confirmar que el nom és efectivament el que dic. Si no ho fos has de canviar-lo a la instrucció de més a dalt. 

Per últim, suposo que hauràs trobat en algun lloc que la configuració es fa amb la instrucció  "/configure", és el més habitual però no és l'únic sistema. Però si has trobat instruccions específiques sobre això doncs un cop estiguis en aquest directori, hauria de funcionar.

---

### Post by wgarcia on 2013-06-23
M'has picat la curiositat sobre allò del kompozer, ja que no sabia que ja no estava disponible, i efectivament, sembla que ja no es manté en Debian, que és d'on Ubuntu treu els seus paquets, i per això ha desaparegut dels dipòsits de programari d'Ubuntu. Aquí donen instruccions sobre com instal·lar-lo de totes maneres, traient-lo dels dipòsits de la versió 12.04 on encara hi era:

[https://help.ubuntu.com/community/InstallKompozer](https://help.ubuntu.com/community/InstallKompozer)

Per últim a aquest fil parlen de la instal·lació de bluegriffon, segons el que diu en aquest fil no em queda clar que s'hagi de fer allò de "./configure" i les altres instruccions que mencionaves, però no estic segur:

[http://askubuntu.com/questions/304636/need-help-installing-bluegriffon](http://askubuntu.com/questions/304636/need-help-installing-bluegriffon)

Per últim, en aquesta pàgina semblen haver-hi paquets ".deb" per instal·lar directament bluegriffon (si el cliques se t'hauria d'obrir el centre de programari i oferir-te instalar-lo). L'únic que has de fer és esbrinar primer si el sistema que tens instal·lat és de 32 o 64 bits:

[http://www.ubuntuupdates.org/package/getdeb_apps/raring/apps/getdeb/bluegriffon](http://www.ubuntuupdates.org/package/getdeb_apps/raring/apps/getdeb/bluegriffon)

---

### Post by Tiah on 2013-06-25
Gràcies

Per la teva resposta molt aclaridora

D'entrada dir-te que també em vaig baixar un paquet amb .deb, que amb l'instal.lador de paquets debi em donava un missatge d'error que deia un cosa com "no es poden establir les dependencies", vaig intentar baixar un parell de vegades el paquet però sempre em donava el mateix error. No ho vaig comentar al missatge anterior perquè em semblava que era allargar massa el text i també m'interessa  aclarir el tema de com poder instal.lar programari amb paquets baixats (per exemmple del softcatalà).

D'altra banda demanar disculpes per la meva manca d'habilitat amb el Synaptic (era la primera vegada que l'usava): finalment vaig trobar el BlueGriffon i l'he pogut instal.lar.

De totes maneres aprofitaré "la lliçó d'instal.lació" per intentar instal.lar el Kompozer ja que el BlueGriffon té un senzil editor de css que només permet generar estils incrustats a l'html oferint, d'altra banda,  un editor coimplet de pagament  ... Bé, no m'allargo amb tema web.

Així que gràcies, provaré les instruccions que em proposes  a veure si puc tornar a tenir el Kompoze. Ja  diré el què. 

Per tant encara no dono per resolt el problema (encara que espero fer-ho ben aviat) 

Fins aviat.

Tiah

---

### Post by Tiah on 2013-06-25
Hola w

D'entrada  he tornat a baixar-me el paquet del Kompozer del softcatalà i he seguit  el protocol que comentava al missatge original i quan he posat l'ordre **/configure* el teminal m'ha  retornat "és un directori", també he provat * /configure*, llavors diu que no existeix ... vaja que no me n'he sortit.

Després he provat el link [https://help.ubuntu.com/community/InstallKompozer](https://help.ubuntu.com/community/InstallKompozer) (que em proposes) i JA EL TINC INSTAL.LAT  I "CORRENT" ... tot i que m'agradaria saber com s'ho ha fet.

Bé així que dono per tancat el tema tot i que em queda pendent "aprendre" a instal.lar paquets des del terminal.

Gràcies.

Tiah

PS: Per a d'altres interessats en el kompozer i tenint en compte que no surt al títol, pot ser útil generar un fil nou per facilitar el link que ajuda en la intal.lació?

---

### Post by wgarcia on 2013-06-26
El que fa l'enllaç que menciones és baixar uns paquets ".deb" (amb wget) i com que aquests són paquets instal·lables, doncs això, instal·lar-los. 

És possible que allò que t'has baixat de Softcatalà no et funcioni perquè et falta algun pas, com ara descomprimir, canviar-te al directori on queda el paquet, etc.

Penso que no fa falta crear un fil nou, però ja veus, quan més precís sigui el títol original, més útil el fil per consultes posteriors.

---

