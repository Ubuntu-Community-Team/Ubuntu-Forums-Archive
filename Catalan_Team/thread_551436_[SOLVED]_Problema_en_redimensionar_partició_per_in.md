---
title: "[SOLVED] Problema en redimensionar partició per instal·lar Era:Hola TOTHOM!!!!"
date: 2007-09-15
forum: Catalan Team
---

### Post by Druiling on 2007-09-15
Hola tots,
Torno a ser jo! :KS
Tinc una pregunteta perquè no m'agrada emprenyar però ja començo a perdre la paciència i, volto pel fòrum però, en la meva torpesa no m'aclareixo.
A veure. 
Estic intentant instal.lar l'Ubuntu i passar ja del CD, el tema és que per una qüestió de practicitat (i de moment), haig de deixar instal.lat el windows ni que sigui uns dies.
El tema és que intento fer la partició del windows més petita amb el gparted i, em sembla que ho faig tot correctament, però quan vull aplicar els canvis, em dona un error.
Miraré si puc adjuntar-vos una captura de pantalla perquè sóc conscient que m'explico malament.
Si teniu algun suggeriment, us ho agrairé.
Salut!!
D.

[http://ubuntuforums.org/attachment.php?attachmentid=43543&stc=1&d=1189856752](http://ubuntuforums.org/attachment.php?attachmentid=43543&stc=1&d=1189856752)

---

### Post by RainCT on 2007-09-15
Hola!

No cal que el particionis amb el gparted abans, l'insta&#320;lador ja et preguntarà si vols fer servir tot el disc, partir-lo i conservar el Windows (fent-ho tot automàticament) o particionar-lo manualment.

Prova a veure si allà et funciona.

---

### Post by CarlesOriol on 2007-09-15
Pot ser tres coses:

1 - Gairebé segur. Tens problemes amb la partició windows. Inicia el windows i fes una comprovació de disc. Et farà reiniciar. Reinicies, fa el xequegi i tornes a reiniciar. un cop fet tot. Atures el windows i tornes a fer la insta&#320;lació

2 - Hagis deixat massa poc espai al windows per fer la reorganització d'arxius. 

3 - En windows tinguis carpetes comprimides. (no ho crec per la quantitat d'espai que tens ocupat)

---

### Post by Druiling on 2007-09-15
Hola, 
RainCT, això que dius ja ho he fet i res, em trobo igual.
CarlesOriol, provo això que em comentes i et dic què. 
Gràcies companys!
Salut.
D.:)

---

### Post by Druiling on 2007-09-15
Hola Carles, com t'he dit, et contesto.
No m'ensurto. 
El desfragmentador de disc de windows, em diu que hi ha fitxers que no es poden modificar ni moure. He provat de fer una partició d'1GB i m'he trobat amb el mateix.
No sé què pot ser.
El que si puc fer, és anar altre cop a windows i treure tots els fitxers comprimits en zip que tinc, uns quatre o cinc. No sé si et referies a això.
Ho provaré.
D.:confused:

---

### Post by CarlesOriol on 2007-09-16
No, no... fes una comprovació del disk en windows. (sobre la unitat > propietats > per allà)

Si el defragmentador del mateix windows no et funciona per defragmentar el windows ja anem malament. ;-)

Els zips no cal que els toquis, em referia a arxius o carpetes comprimits amb el mateix sistema.

---

### Post by Druiling on 2007-09-16
Bon dia Carles,
No havia entès això, però és igual. El tema és que he tornat a fer un scandisk i una o dues compilacions i res.
Intento fer una partició d'1GB per veure si me la fa, però no. 
El tema és que en la pantalla aquella de windows del desfragmentador on surten els espais del disc en codis de colors, vermell (arxius fragmentats), blau (espai ocupat), verd (arxius que no es poden moure) i blanc, espai buit, en els verds, i mira que jo tinc el disc poc usat, estan escampats per tot arreu, al principi al final i al mig. No sé si això voldrà dir alguna cosa, però potser si.
En fi, faig això últim que dius i a veure què...
Salut.
D.:mad:

---

### Post by CarlesOriol on 2007-09-16
Tanca el missatge d'error (1) i després copia'ns el contingut de detall (2). Hauràs de fer clic a la fletxa de (2) per què es vegi.

(1 i 2) a Attachment.

Per cert. Com has fet l'"scandisk" ?

---

### Post by Druiling on 2007-09-16
L'he fet amb el netejador de disc de windows.
Ara t'envio la captura.

---

### Post by guillemsola on 2007-09-16
Jo crec que podries "fer trampes" i intentar reparticionar amb el partition magic des de windows. És un programa privatiu però eficaç, això si tranquil que  l'amule el posa a l'abast dels mortals.

Això que fas de passar el win de 58 a 13 Mg no és massa just? Em refereixo que potser vols deixar al windows amb massa poc espai.

Salut!

---

### Post by Druiling on 2007-09-16
captura
No et guiis pel tamany, ja que els he provat quasi tots (un munt vull dir)

---

### Post by Druiling on 2007-09-16
Hola angrychai!
Si és molt poc espai però és un de tants tamanys que he provat, ja sabia que no em faria la partició, per tant, m'era igual l'espai.
I quant al PartitionMagic aquest, si ja m'han comentat que existeix, però em fa un mal rollo haver-lo de fer servir..., a banda que no tinc l'emule ni res d'això. Mira, jo sóc així!!
:)
Salut!

---

### Post by orestesmas on 2007-09-16
A veure: intentaré respondre en global a tots els missatges:

Això que dius que et passa és del tot normal. El desfragmentador de windows és penós, perquè no és capaç (tal vegada és intencionat) de moure tots els fitxers al principi del disc, amb la qual cosa no pots "encongir" la partició de windows tant com voldries sense carregar-te fitxers.

L'excusa darrere d'això és que mentre windows està funcionant hi ha certs fitxers que són inamovibles (mem. virtual i altres) i per tant no es poden tocar.

Per solventar això alguna vegada havia llegit d'un truc per inicial el desfragmentador de forma automàtica en tancar el sistema, però no era una solució eficaç al 100%.

L'única solució viable que he trobat jo és usar un CD autoarrencable que contingui programari privatiu per redimensionar les particions. I dic privatiu perquè m'he trobat que són els únics que poden redimensionar particions NTFS de forma no destructiva allí on el GParted falla (i si, falla a vegades). Jo interpreto que els qui han fet el programari privatiu han pagat a M$ per les especificacions del sistema NTFS, però el motiu pot ser qualsevol altre.

Jo m'he servit en 2 ocasions amb èxit (una d'elles ahir mateix sense anar més lluny) d'un programa privatiu, però gratuït, que es diu "Boot-It", que pots trobar aquí:

[http://www.terabyteunlimited.com/downloads/bootitng.zip](http://www.terabyteunlimited.com/downloads/bootitng.zip)

Te'l baixes, el descomprimeixes, executes l'executable el qual et crearà una imatge ISO i cremes aquesta imatge ISO en un CD. Després botes d'aquest CD i entres en mode "gestió de les particions". Allà podràs redimensionar la partició NTFS sense problemes.

Apa, adéu.

---

### Post by CarlesOriol on 2007-09-16
> **Druiling said:**
> captura
No et guiis pel tamany, ja que els he provat quasi tots (un munt vull dir)

No has desplegat el Details per veure l'error. (fletxa a l'esquerra de resize)

---

### Post by Druiling on 2007-09-16
Hola Carles, 
si que ho havia fet però sortia buit.
Orestesmas,
El teu sistema m'ha funcionat de conya. Ja tinc particióóóó
MOLTES GRÀCIES A TOTHOM.
Ja podeu posar resolt i..., fins la propera ubunteros. Suposo que ja us imagineu que no em perdreu de vista.):P
=D>=D>

---

