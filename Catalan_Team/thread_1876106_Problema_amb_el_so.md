---
title: "Problema amb el so"
date: 2011-11-05
forum: Catalan Team
---

### Post by jaumevm on 2011-11-05
Molt bones.

en primer lloc dir que és el meu primer post  i per tant una salutació a tots aquells que participeu en aquest grup!

El meu problema és el següent:

A l'actualitzar l'Ubuntu a la última versió m'ha desaparegut la tarja de so i per tant no se'm reprodueix res! 

La veritat és que no sé per on començar.

Fent lspci em surt:

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

Si em podeu donar un cop de mà estaria molt agraït.

---

### Post by wgarcia on 2011-11-08
Gràcies per la salutació. Quan dius que no es veu la tarja de so, suposo que cliques sobre l'altaveu del plafó de dalt, cliques sobre "maquinari" i proves les diferents opcions que hi ha i en cap es veu la tarja de so reconeguda pel sistema?

---

### Post by jaumevm on 2011-11-11
Perdó pek retard i gracies per ajudar.
He vist que el problema es que a vegades em reconeix la tarja de so i a vegades no, per lo que intueixo que es yn priblema de la placa base. Que n'opineu? Alguna forma de fer-li un test?

---

### Post by wgarcia on 2011-11-14
Està integrada a la placa base? Potser sigui un problema de conexions, més que de programari.

---

### Post by fvilaubi on 2011-11-22
Hola,

jo he estat experimentat un efecte semblant: engego l'ordinador i no tinc so, es a dir la icona del altaveu te dues ratlletes. Clico a l'icona i demano "paràmetres del so", la pestanya maquinari està "vuida".. (?), espero 5 o 10 minuts, torno a entrar a "parametres del so" i ara ja apareix la tarja de so. Simplement pujo el volum i ja tinc so.

Com que em va passar al canviar a versió 11.10 d'entrada em nego a pensar que tinc un problema amb el maquinari. 

Amb les ultimes actualitzacions d'Ubuntu sembla que el problema em passa menys sovint, al actualitzat a 11.10 era cada cop que engegava l'ordinador, i ara es només algun cop. (es nota molt per que no sento la "musiqueta" d'inici de sessió d'usuari, els cops que falla).

Salutacions
Francesc.

---

### Post by wgarcia on 2011-11-23
@fvilaubi, podries entrar un informe d'error així queda el teu problema registrat, i es recull tota la informació del teu sistema. Després enganxa l'enllaç en un missatge. 

Seria així. Prems ALT F2 i entres "ubuntu-bug audio"

Contestes alguna pregunta si te'n fa, i un cop que s'obre el navegador i et deixa contestar poses:

"Sound card sometimes not detected at start-up"

i en el cos:

Sometimes I get the following symptoms:

1) I start the computer
2) No start-up sound when I start de desktop
3) Looking in "Sound Settings" no card is registered

After 10 or so minutes the card appears in "Sound Settings" without doing anything special.

---

### Post by jaumevm on 2011-11-24
També m'ho agafo i ho faré.
 
A veure que em surt..
 
Gràcies!

---

### Post by fvilaubi on 2011-11-24
Ja ho he reportat.

Ha obert el Bug #894578

---

### Post by fvilaubi on 2012-01-16
[SOLVED] 
després d'instal·lar el 11.10 des de CD formatant completament les particions, per que no s'aprofités rés no fos que algun fitxer de configuració (els típics .nomaplicació que es guarden al directori arrel de l'usuari) estigués fent la guitza, el problema amb el só persistia.

Quan em començava a plantejar si podia tenir problemes amb el maquinari, i aprofitant que acabava de fer una instal·lació complerta:

he** retornat a 11.04** amb resultat espectacular!
[LIST]
[*]**ja no falla mai** el reconeixement de la **placa de só**.
[*]em torna a detectar perfectament la webcam (problema resolt des de la 9.04 i que m'havia retornat.
[/LIST]

M'ha quedat la impressió que el nucli 3 està una mica “verd”.  A veure si amb la 12.04 em funciona mes fi. De moment cada cop que em diu “disponible la nova versió 11.10” senzillament li dic:

“ONERIC OCELOT?, no gràcies”

---

### Post by wgarcia on 2012-01-17
Excel·lent, si pots fes un comentari a l'informe d'error a veure si crida l'atenció d'algun desenvolupador:

I've reinstalled 11.04 in this same machine and now the sound works perfectly.

---

### Post by wgarcia on 2012-01-17
@ocieyeb, If you mark the bug as affecting you:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/894578](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/894578)

it will "confirm" it.

(Si marques l'informe d'error com afectant-te també a tu, quedarà marcat com a "confirmat")

---

### Post by fvilaubi on 2012-02-05
Perdona WGarcia, però he anat al la pàgina que referencies i he fet login al LaunchPad, però NO tinc cap enllaç/botò per fer "confirm". No serà que no el puc confirmar jo, donat que SOC el CREADOR del bug?

---

### Post by wgarcia on 2012-02-05
Sí, correcte, li deia això al tal ocieyeb que havia comentat en aquest fil (i en anglès), però sembla que el seu comentari ha desaparegut. En quant al teu informe d'error com no ha estat confirmat ni sembla de moment reproduïble fàcilment, encara ha passat desapercebut, ho sento.

---

