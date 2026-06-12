---
title: "GTA 2 a Ubuntu: problemes instal·lació"
date: 2007-11-02
forum: Catalan Team
---

### Post by Asus4 on 2007-11-02
Salut!

He trobat un manual on m'explicava com podia instal·lar el GTA 2 (Grand Theft Auto 2) mitjançant el Wine sobre l'Ubuntu.
Primer de tot diu que instal·li l'executable mitjançant Wine *_(ho he fet)_*; llavors que inclogui un DLL al directori de System32 del Wine *_(ho he fet)_*; i llavors em fa anar al WineRegEdit a canviar nose quines claus **(no ho sé fer...)**.

He intentat executar el joc sense fer cas d'això del WineRegEdit i m'ha sortit aquest error:
> **Error!** Couldn't find attract mode file data\attract\attr1.rep

Com que suposo que acabant de seguir el manual al final el podré executar, algú em podria dir com es fa per canviar o incloure Claus en el WineRegEdit mitjançant el que em diu en el manual?:

> Ara ves a Sistema -> Preferències -> Wine RegEdit (si fas servir l'Ubuntu Edgy o anterior, en lloc d'això executa "regedit" a la terminal); allà ves fins al directori HKEY_LOCAL_MACHINESoftwareDMA Design LtdGTA2Screen, on has d'afegir o modificar algunes claus perquè, entre d'altres que no cal modificar, quedi així:
 
"bit_depth"=dword:00000020

"curr_dll_id"=dword:00000002

"device"=dword:00000002

"max_frame_rate"=dword:00000001

"min_frame_rate"=dword:00000000

"renderdevice"=dword:00000000

"rendername"="3dfx.dll"

"special_recognition"=dword:00000000

"start_mode"=dword:00000001

"tripple_buffer"=dword:00000000

"videodevice"=dword:00000001

"videoname"="dmaglide.dll"


El manual és [aquest]("http://rainct.bloc.cat/post/8808/157742").

Gràcies!
PD: val a dir que abans de tot he buscat algun post sobre el tema als forums d'Ubuntu, però no he trobat res referent al GTA 2... devem ser pocs els que ens agrada jugar a jocs antics;-)

---

### Post by papapep on 2007-11-02
El regedit.exe el tens a * /home/el_teu_usuari/.wine/drive_c/windows*.
Li dius que l'obri amb el wine i podràs editar el registre del fals windows.

---

### Post by RainCT on 2007-11-02
A la Gutsy tens l'editor del registre aquest sota Aplicacions -> Wine (en lloc de Sistema -> Preferències). Em vaig canviar de bloc (el manual és meu :)), hi ha una versió actualitzada que comenta això aquí: [GTA2 a l'Ubuntu](http://bloc.eurion.net/archives/2007/general/gta2-gratis-ubuntu/).

No et puc donar instruccions exactes de com editar les claus des del regedit ja que ara mateix no tinc el Wine insta&#320;lat, però és prou fàcil, suposo que ja ho descobriràs :).

---

### Post by papapep on 2007-11-02
Jo l'acabo d'instal·lar a Gutsy (vaja quin joc...no hi deixaré pas jugar els nanos) i seguint les teves passes i editant amb el regedit que he indicat va perfecte.

---

### Post by Asus4 on 2007-11-02
El problema el tinc principalment quan tinc el Wine RegEdit obert.
No sé com operar a partir d'aleshores, no entenc s'han de ficar les claus...i a més no trobo el directori concret que m'indica al manual.

Us deixo una captura per veure si us serveix de guia per indicar-me...:

**[http://aycu04.webshots.com/image/32523/2003875934378715007_rs.jpg](http://aycu04.webshots.com/image/32523/2003875934378715007_rs.jpg)**


PD: un pèl violent el joc..però no és tant explícit com els seus successors, que són en tercera persona[-X .

---

### Post by papapep on 2007-11-02
La qüestió per mi no és si és explícit o no, sinó el fons però, vaja, cadascú que jugui al que li sembli.

Respecte el tema que ens ocupa, sembla que alguna cosa no ha anat bé amb la instal·lació i el registre, ja que jo tinc una branca bastant diferent.

---

### Post by Asus4 on 2007-11-03
He borrat el joc i l'he tornat  a instal·lar. Llavors he pogut finalment editar les claus del WineRegEdit i acabar de seguir el tutorial.
Puc executar el joc, però quan surto del joc se'm queda l'escriptori en una configuració que no tenia abans. Tot es veu més gros que no tenia, quina configuració té el joc que provoca que passi això?

---

### Post by papapep on 2007-11-04
A mi em passa això que dius (que es posa la pantalla a 640x480) quan l'executo des del menú principal. 
Si el que faig és executar l'script que hem creat directament em funciona perfectament.

---

### Post by Asus4 on 2007-11-04
Quin script?^^U

Merci!

PD: comparteixo totalment la teva opinió respecte els jocs d'aqest caire. La instal·lació al final l'he convertit en un repte personal hehehe.

---

### Post by papapep on 2007-11-04
Doncs el que posa al bloc d'en Rainct:

```
Finalment, obre una terminal, escriu-hi “sudo gedit /usr/local/bin/gta” i copia-hi això:

cd "~/.wine/drive_c/Program Files/Rockstar Games/GTA2"
wine explorer /desktop=x,640x500 gta2
```

---

