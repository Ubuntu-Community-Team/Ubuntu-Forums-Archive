---
title: "tot el pc va molt lent"
date: 2011-04-25
forum: Catalan Team
---

### Post by ladisse on 2011-04-25
Hola a tothom,
començo a estar tipa de l'ordinador... i abans de tirar per la borda les coses, miraré de posar fil a l'agulla i mirar d'esbrinar què coi passa. La qüestió és que cada cop va tot més lent (carrega molt lentament els documents, internet va molt lent -comentat ja a un altre fil-, firefox tarda molt en obrir les pàgines....). Aparentment el disc dur no està ple -he usat el programa Sysinfo, i dóna una capacitat usada de la memory total el 63% free i de la swap el 99% free. El disc dur és un Intel(R) Celeron(R) CPU 3.06GHz.
A part -però no sé si això ja hauria d'anar a un altre fil-, hi ha alguns programes que no es poden obrir (F-spot, pex). Algú sap com puc solucionar això de la lentitud?

---

### Post by kimet on 2011-04-25
Has notat si aixó et passa al obrir algun programa determinat?
Posa la sortida de:
```
top
```
A veure si hi ha algun procés que estigui fent la punyeta.

Salut

---

### Post by ladisse on 2011-04-26
Gràcies Kimet, però... com interpreto el que hi surt?

---

### Post by Funk'u on 2011-04-26
Hola ladisse, al inicar la comanda "top" o bé obres a "Administració > Monitor del Sistema > Processos" pots visualitzar el llistat de processos engegats, al terminal ho veuràs més o menys així; 

Tasks: 275 total,   1 running, 274 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.3%us,  0.2%sy,  0.0%ni, 98.4%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3918692k total,  1999304k used,  1919388k free,   252560k buffers
Swap:  9936892k total,        0k used,  9936892k free,   555756k cached

  PID  USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1755 root        20   0  145m  40m  21m S    2       1.1    0:16.51       Xorg               
 2937 joma      20    0  301m  62m  20m S    1       1.6   0:08.37        compiz             
 
                                                        ***

La llista és més llarga, concretament al moment de copiar-ho era de 275 com bé diu a "Tasks", en principi la dada que ens interessa és a on diu "%CPU","%MEM","PID" i "USER", amb "%CPU" veurem si hi ha algun percentatge elevat, tant si t'hi trobes en la primera o segona opció, llavors ens interessa saber a quin usuari pertany que ho veurem amb "USER" i el "PID" ho utilitzarem per apagar el procés amb un "kill -9 2937" per exemple o si pertany al root, llavors hi afegirem sudo al davant, amb la opció "COMMAND" veurem el nom del programa que ens fa la punyeta ;)




Salut!

---

### Post by wgarcia on 2011-04-26
La causa de la lentitud pot estar relacionada amb el problema de connexió a Internet que menciones, és possible que algun procés relacionat amb la connexió de xarxa es quedi penjat i faci tot més lent. 

Un parell de comprovacions simples que es poden fer per descartar altres coses són:

1) si en iniciar l'ordinador el sistema t'ofereix més d'una nucli, provar si amb un nucli més antic també es veu la lentitud

2) crear un altre usuari i entrar amb aquest altre usuari, cosa que no sigui alguna mala configuració de l'usuari habitual

Si a la comanda "top" que et suggerien veus algun procés que estigui consumint molta "CPU" i/o memòria RAM, també podria servir veure quin és per a veure si és normal que ho estigui fent.

---

### Post by ladisse on 2011-04-28
aquí poso la captura del TOP
[IMG]http://ubuntuforums.org/home/elena/Documents/Captura-6.png[/IMG]
gràcies a tots pel cop de mà.

---

### Post by wgarcia on 2011-04-28
La captura no s'ha carregat, o jo no la veig...

---

### Post by ladisse on 2011-04-28
torno a intentar pujar la imatge, a veure si ara me'n surto

[ATTACH]190252[/ATTACH]

---

### Post by Funk'u on 2011-04-28
Hola ladisse, la veritat és que has tallat massa aviat la foto, estaria bé veure més resultats, si pots mira de deixar-hi més línies, de tota forma per el que es veu, jo diria que els resultats son ben normals.



Salut!

---

### Post by kimet on 2011-04-28
En el que es pot veure, hi ha un procés zombi, segurament el responsable
de que el sistema vagi lent, has d'identificar el procés i matar-lo.Mes o menys així:
```
sudo kill -HUP `ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]' | awk '{print $2}'`
```
Després buscar la causa de que es torni zombi i sol.lucionar-ho.

Salut

---

### Post by Funk'u on 2011-04-28
> **kimet said:**
> En el que es pot veure, hi ha un procés zombi, segurament el responsable
de que el sistema vagi lent, has d'identificar el procés i matar-lo.Mes o menys així:
```
sudo kill -HUP `ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]' | awk '{print $2}'`
```Després buscar la causa de que es torni zombi i sol.lucionar-ho.

Salut

Ostres, m'ho havia passat per alt  ](*,)
No n'hi ha d'haver mai de processos zombis?, en qualsevol cas si el vols identificar sense matar-lo i poder veure de que és tracta, com ho posaries?, es que per al meu nivell aquesta cadena d'ordres em sembla de marcians :oops: me'n podries fer cinc cèntims del significat?, desconec aquestes parts: " -HUP `ps -A -ostat,ppid,pid,cmd","-e '^[Zz]'" i el "awk '{print $2}'`", El "kill, killall i grep" els conec en la formà més bàsica.


Moltes gràcies!

Hola ladisse, com diu en kimet proba d'enganxar aquesta línia al terminal, et demanarà el password, a veure que tal.


Salut!

---

### Post by kimet on 2011-04-28
Els zombis no serveixen per a res, solen ser consequencia d'algún error de programació. Busca a la wikipedia que t'ho 
explicarà millor que jo.

Sobre la comanda:
```
ps -A -ostat,ppid,pid,cmd
```
Llista de processos per estat,num.proces pare,num.proces i comanda.
```
| grep -e '^[Zz]'
```
N'extreu amb grep els que tenen estat zombie 'Z o z'
```
| awk '{print $2}'
```
Selecciona els procés pare, la segona columna

els accents "``" per que s'executi en primer lloc el que contenen.

i kill -HUP envia el senyaL SIGHUP


Si busques per la xarxa hi ha scripts per a fer aixó mateix de forma automatitzada, son sobre tot per a us en servidors. Ara no recordo on.

Salut.

---

### Post by Funk'u on 2011-04-28
Ostres, moltes gràcies kimet!!, molt interessant.




Salut!

---

### Post by ladisse on 2011-04-29
bé, he fet la comanda que m'heu dit al terminal, però de tots els processos que surten, no sé si cal matar-los tots, només un o què fer exactament. (és que entro molt poc al terminal, pq sempre acabo havent de reinstalar-ho tot). Incloc captura de la comanda i la seva resposta.
[]("http:///home/elena/Documents/Captura.png")
a veure si ara es veu bé. Gràcies altra vegada.

---

### Post by kimet on 2011-04-29
Es que no n'ha trobat cap...

si fas:
```
ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]'
```
I no torna res es que no hi ha cap procés zombi. Si encara et continua anant lent pot ser una altra cosa. Si apareix alguna cosa utilitza l'altre comanda.

Pd. Encara no em vist la captura de 'top' sencera.

---

### Post by ladisse on 2011-04-29
és que no la puc repetir. M'explico, ahir a la tarda, quan vaig començar el fil el pc funcionava aprox. I va ser llavors que vaig fer les captures; a mesura que es feia fosc, anava empitjorant-ho tot: ara no em deixava copiar fitxers per fer la de seguretat, després no em reconeixia ni usb, ni disc dur extern... fins que cansada de tot, vaig poder salvar alguns arxius i vaig resinstal-lar-ho tot (lucid lynux). Avui funciona tot millor, encara que no al 100% (entre d'altres coses, pq tampoc no ha funcionat així ni quan era nou); suposo que deu ser alguna cosa d'estructura interior que no sé trobar. Disculpin les molèsties per no haver-ho explicat anteriorment.
Ara, però em dóna altres problemes.... altra vegada, gràcies a tots pel cop de mà.

---

