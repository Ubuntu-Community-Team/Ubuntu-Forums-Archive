---
title: "Com veure TV3 amb el Me TV"
date: 2009-11-24
forum: Catalan Team
---

### Post by Black_02 on 2009-11-24
Hola,
Voldria saber com puc veure TV3 amb Ubuntu, he provat un munt de programes però no m'han funcionat, l'únic que m'ha funcionat una mica és el Me TV, però TV3 no la pilla.
He buscat informació, però l'únic que he trobat es que s'ha de crear un arxiu; "channel.conf" però no en tinc ni idea de com fer-ho, si algú m'ho pot explicar com fer-ho, o millor encara, si algú me'l pot passar, li agrairia molt.

---

### Post by orestesmas on 2009-11-25
Entenc que és via TDT, no? En aquest cas el Kaffeine és el que busques. Zero complicacions.

---

### Post by Black_02 on 2009-11-25
Ni Kaffeine ni Me TV ni Mythtv, res de res, arribo a la conclusió que per veure la tele lo millor es l'aparell de tota la vida. No pot ser que per fer funcionar la TV al ubuntu m'hagi de trencar tant el coco ](*,).

---

### Post by tanreb20 on 2009-11-25
Aconsegueixes veure altres canals de TV?

Amb la nova versió del Me-TV al menú canals pots crear-ne de nous, et deixa triar l'antena més propera(has de saber quina és. A barcleona és Collserola per exemple).

Un cop fet escanejar i seleccionar el que vols, si vols puc mirar de passar-te un channels.conf de barcelona amb l'antena de colserola si et sembla!

---

### Post by Black_02 on 2009-11-25
Gràcies, però ja he trobat la solució. Tan sols tenia que crear un document de text amb el el següent contingut: 

T 490000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.23:Telecomarca, Unedisa
T 514000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # c26:nada
T 570000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # c33:nada
T 618000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.39:nada
T 682000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.47:nada
T 708000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.50:nada
T 730000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.53:GV-998
T 746000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.55:TV3, K3/33, 3/24, 300
T 762000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.57:Canal9, Punt2, Popular TV, LP Teva
T 770000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.58:TVE1, TVE2, TVE 24H, Clan/TVE 50 Años, RNE1, RNEC, RNE3
T 778000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.59
T 786000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.60
T 794000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.61:nada
T 810000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.63:nada
T 818000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C64:nada
T 834000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.66: Veo, SETenVeo, NetTV, Teledeporte.
T 842000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.67: Cuatro, CNN+,40 Latino, La Sexta.
T 850000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.68: Tele 5, Tele 5 Sport, Tele 5 Estrellas, Fly Music.
T 858000000 8MHz 2/3 NONE QAM64 8k 1/4 NONE # C.69: Antena 3, Antena.Neox, Antena.Nova, Telehit, Onda Cero, Europa FM, Onda Melodía.


I després copiar-lo a la ruta: **/usr/share/dvb/dvb-t** amb el nom **es-qualsevolpoble**

De totes formes, motes gracies pel teu interes, tanreb20 :D

---

### Post by epileg on 2009-11-29
Veig que a la llista et falten un bon grapat de canals.

Per aconseguir una llista completa dels canals que pots rebre amb la teva tarja de dvb-t tens dues opcions força fàcils:

1. insta&#320;lant el programa 'w-scan' i executant l'ordre:
$ w_scan -X -t 3 -c ES | iconv -f iso8859-15 -t utf8 >channels.conf

el fitxer resultant 'channels.conf' el pots fer servir amb me-tv, xine, etc.

2. amb el kaffeine no et cal fer això ja que el propi programa et permet escanejar els canals sense la necessitat de l'odre anterior. Aquí no et puc ajudar massa ja que degut a que la versió 1.0 pre2 (kde4) és menys funcional que la prèvia 0.8.8, he optat per un downgrade a la aquesta versió (kde3). A mi el 'me-tv' tampoc m'acaba d'anar massa bé, de tant en tant tinc problemes per canviar de canal.

Salut,
Epíleg.

---

### Post by Black_02 on 2009-11-30
Gràcies Epíleg, havia sentit a parlar de w-scan, incús el tenia instal·lat, però a enlloc vaig torbar l'ordre adequada per executar-lo, fins avui (gràcies a tu). Per cert a aquest programa no se li escapa cap emissora \\:D/.

Si el ME-TV no et va bé, podries provar el VLC, tan sols cal cargar el channels.conf, i la imatge és força més bona que la del ME-TV.

Gràcies de nou :D.

---

