---
title: "Tarjeta TDT AverMedia (qüestions tècniques)"
date: 2009-11-23
forum: Catalan Team
---

### Post by lluisalguero on 2009-11-23
Hola,
tinc una tarjeta TDT [AVerTV Digi Express 54]("http://www.avermedia.eu/avertv/sp/product/ProductDetail.aspx?Id=432") i voldria fer-la anar amb l'Ubuntu (actualment tinc instal·lada la 9.10).

La meva pregunta va encaminada a si s'ha de configurar igual com si fos USB o té algun tracte especial. Com a curiositat és una Express Card.

De moment m'he instal·lat Kaffeine i tot i que em surt l'icona de TV Digital, no puc veure res, ni tant sols sintonitzar els canals.

Us adjunto el dmesg.log per si veieu alguna cosa que em pugi orientar una mica.

Moltes gràcies per la vostra ajuda

P.D.: no em deixa adjuntar el dmesg.log

---

### Post by PatrickVogeli on 2009-11-23
posa el dmesg.log dins un zip, així et deixarà possar-lo.

O també pots fer servir les etiquetes de [CO DE] i [/CO DE] (tot junt) i enganxar el contigut del dmesg al mig, et quedaria així:
```

....
aqui el que hi hagi al dmesg 
....

```

salut

---

### Post by papapep on 2009-11-23
Una altra opció que tenim és enganxar el text a [http://pastebin.ubuntu.com](http://pastebin.ubuntu.com), i posar aquí la url que ens dóna.

Com [això]("http://pastebin.ubuntu.com/326100/") que he fet jo.

---

### Post by lluisalguero on 2009-11-23
Us deixo ara si l'arxiu en questió

---

### Post by lluisalguero on 2009-11-23
> **PatrickVogeli said:**
> posa el dmesg.log dins un zip, així et deixarà possar-lo.

O també pots fer servir les etiquetes de [CO DE] i [/CO DE] (tot junt) i enganxar el contigut del dmesg al mig, et quedaria així:
```

....
aqui el que hi hagi al dmesg 
....

```

salut

el que volia fer, és ficar-ho com arxiu adjunt, però no em deixava. Ficar tot aquí amb la parrafada que és !! Em fotríeu als gossos :lolflag:

---

### Post by akyra on 2009-11-23
Hola,

En la revista Todo Linux 107, la del mes pasat, hi ha un article molt bo per configurar el TDT en linux, i justament surt una tarja Avermedia i com configurar-ho pas per pas. Hi ha uns pasos previs a fer abans d'utilitzar la tarja

Si vols te'l puc pasar. La revista sencera ocupa 9MB aprox, però si vols t'extrec només l'article en qüestió.

Espero que em diguis alguna cosa.

Salutacions.

---

### Post by lluisalguero on 2009-11-23
> **akyra said:**
> Hola,

En la revista Todo Linux 107, la del mes pasat, hi ha un article molt bo per configurar el TDT en linux, i justament surt una tarja Avermedia i com configurar-ho pas per pas. Hi ha uns pasos previs a fer abans d'utilitzar la tarja

Si vols te'l puc pasar. La revista sencera ocupa 9MB aprox, però si vols t'extrec només l'article en qüestió.

Espero que em diguis alguna cosa.

Salutacions.

Com vulguis, tu mateix...

---

### Post by PatrickVogeli on 2009-11-23
el dmesg que has enganxat es amb la tarjeta posada?

Podries arrancar el pc **sense** la tarjeta, fer un fitxer dmesg.sense.log, connectar la tarjeta, fer un fitxer dmesg.conectada.log i enganxar-ho tot aqui?

merci

---

### Post by guillemsola on 2009-11-24
jhola,

jo he donat un cop d'ul a aquest dmesg.log i no veig la tarjeta per enlloc,

Adjunta un "lscpi"

tens creat algun dispositiu del tipus? (es crea quant la tarja està llesta)

/dev/dvb

si és així pots fer un (si ets de BCN)

scandvb -a 0 /usr/share/dvb-apps/dvb-t/es-Collserola


també pots adjuntar un "lsmod" aveure els moduls que tens carregats


No veig la teva tarja a V4L

[http://www.linuxtv.org/wiki/index.php/AVerMedia](http://www.linuxtv.org/wiki/index.php/AVerMedia)

mira aquest wiki que és on fan els drivers, 

sempre pots baixar la darrera versió del driver V4L i probar sort.

---

### Post by orestesmas on 2009-11-25
És [aquesta]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Hybrid_Express_Slim_HC81R") la targeta?

Si ho és, no està suportada encara en GNU/Linux.

---

### Post by tanreb20 on 2009-11-25
Jo en tinc una externa per USB, i funciona, per a vegades dona problema, almenys a les noves instalacions d'ubuntu, em costa, ja tinc el driver i ja no em cal buscar, es copiar-lo i llest!

Estaria bé potser una foto de la targeta en que es vegi la marca, nom, model etc... així podem veure que tal és.

---

### Post by lluisalguero on 2009-11-25
Perdoneu nois per no contestar. Tant aviat com tingui un moment faré el que m'heu dit !!

Moltes gràcies pels consells

---

### Post by lorencillo on 2009-11-27
> **akyra said:**
> Hola,

En la revista Todo Linux 107, la del mes pasat, hi ha un article molt bo per configurar el TDT en linux, i justament surt una tarja Avermedia i com configurar-ho pas per pas. Hi ha uns pasos previs a fer abans d'utilitzar la tarja

Si vols te'l puc pasar. La revista sencera ocupa 9MB aprox, però si vols t'extrec només l'article en qüestió.

Espero que em diguis alguna cosa.

Salutacions.

Hola Akyra,

em pots passar a mí la revista per intertar-ho (tant sols l'article)!!! gracies
[email]lmolinamallen@gmail.com[/email],

gràcies!!!

---

### Post by akyra on 2009-11-28
Ja la he enviat

Salutacions.

---

### Post by lluisalguero on 2009-12-06
> **orestesmas said:**
> És [aquesta]("http://www.linuxtv.org/wiki/index.php/AVerMedia_AVerTV_Hybrid_Express_Slim_HC81R") la targeta?

Si ho és, no està suportada encara en GNU/Linux.


Sí, es aquesta...ens tindrem que esperar :popcorn:

---

