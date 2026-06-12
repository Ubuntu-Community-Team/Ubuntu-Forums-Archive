---
title: "aturada temporal"
date: 2015-04-14
forum: Catalan Team
---

### Post by josep-maria on 2015-04-14
He actualitzat l'ubuntu al 14.04, i ara ja no fa l'aturada temporal. Fins ara anava bé, amb el mateix pc. És a dir, si li dic "atura temporalment", després ja no es torna a engegar, ni tocant la tecla d'engegar del pc. Cal tallar l'electricitat i tornar a engegar el pc. Passa igual tant amb l'aturada manual com amb la temporitzada.

---

### Post by wgarcia on 2015-04-15
Per al problema de la suspensió temporal, seria útil si poguessis donar més detalls del sistema. Suposo que és el Hewlett Packard Compaq que mencionaves al missatge anterior, però com a mínim:

1) Quin model exacte és? Hi ha un munt de models Compaq diferents

2) Quina targeta gràfica porta? (Si no ho saps ho pots esbrinar fent "lspci |grep -i vga" a una terminal

---

### Post by josep-maria on 2015-04-22
No he trobat de quin model és el pc, no ho diu enlloc. Però a "paràmetres del sistema" hi diu: processador: intel core 2 duo cpu E7200.
I diu: gràfics: intel Q35x86/MMX/SSE2.
He volgut escriure lspci... però hi ha un caràcter que no he trobat entre lspci i grep.

---

### Post by wgarcia on 2015-04-22
El caràcter és la línia vertical, la que obtens amb "AltGR 1".

---

### Post by josep-maria on 2015-04-28
Perdoneu el retard, és que no tinc el pc a casa i no sempre hi puc anar. He ficat l'ordre al terminal i diu:

desktop:~$ lspci |grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller (rev 02)

---

### Post by wgarcia on 2015-04-28
Quan torna de l'aturada temporal, queda la pantalla en negre, o es veu la gràfica i està congelada?

---

### Post by josep-maria on 2015-04-28
La pantalla està tota negra. És igual que quan li dius "apagar" el pc. Has de tallar els 220V i tornar a engegar el pc.

---

### Post by josep-maria on 2015-04-29
El ctrl-alt-del no hi fa res de res.

---

### Post by wgarcia on 2015-04-29
A vegades el ctrl-alt-del no està configurat. Has provat amb ctrl-alt-F6, per exemple? Això t'hauria d'obrir una sessió de consola, si la gràfica ha quedat bloquejada.

---

### Post by josep-maria on 2015-04-29
No, tampoc no funciona el ctrl-alt-F6, ni tampoc el ctrl-alt-backspace
Quan engegues el pc surt una finestreta que diu "s'ha detectat un problema. Voleu informar-ne?"
Els primers cops deia que sí. 
Ara cal fer clic sis cops a "cancelar" per tancar-la.

Amb la versió 12.04, to anava bé. Què cal fer per tornar-hi?

---

### Post by wgarcia on 2015-04-29
Per tornar a una versió anterior l'única manera que conec és copiar totes les dades i reinstal·lar, però potser es pot abans investigar i intentar arreglar-ho. 

Els errors que surten al principi potser siguin per programes que estan intentant arrencar i no acaben de rutllar, que provenen de les versions anteriors. Mira a veure si l'ordre següent et mostra alguna cosa:

```
ls /var/crash
```

En aquest directori queden guardats fitxers d'informació sobre programes que peten, potser es pot veure què és el que està fallant quan comença l'ordinador.

---

### Post by josep-maria on 2015-05-01
He entrat a [www.ubuntu.com](www.ubuntu.com) i no hi ha la versió 12.04 (només hi ha la 14.04 i la 15.04). A softcatalà tampoc no tenen la 12.04 (només hi ha la 14.10). Com podem ficar la 12.04?

La resposta de ls /var/crash és:

 ls /var/crash
susres.2015-04-22_08:52:25.134512.crash
susres.2015-04-22_08:52:25.134512.upload
susres.2015-04-25_16:57:00.841474.crash
susres.2015-04-27_20:56:54.211095.crash
susres.2015-04-29_09:01:40.292620.crash
susres.2015-04-29_17:56:31.150448.crash
_usr_bin_shotwell.1000.crash

---

### Post by wgarcia on 2015-05-03
Les  versions antigues les pots trobar en qualsevol mirall de dipòsits, per exemple a:

[http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/)

Em penso una mica el que es veu a /var/crash, aixo de "susres" té pinta d'estar relacionat amb l'aturada temporal.

---

### Post by wgarcia on 2015-05-03
Efectivament allò de "susres" són les fallades de l'aturada temporal, i també el que provoca això que veus quan comença el sistema de "System problem detected". El que hagis de prémer 6 cops perquè se'n vagi vol dir simplement que has de tancar 6 d'aquestes finestres, una per cada informe de fallada que hi ha a /var/crash. Perquè se'n vagi simplement esborra el que hi ha a /var/crash:

```
sudo rm /var/crash/*
```

clar que quan torni a fallar l'aturada temporal tornarà aparèixer un informe d'aquests i l'avís d'error en iniciar el sistema. 

Però val la pena seguir investigant perquè es produeix aquesta fallada a l'aturada temporal. Per començar, suposo que tens actualitzat totalment el sistema, oi? En segon lloc, prova de suspendre el sistema "manualment", és a dir, obre una terminal i entra:

```
sudo pm-suspend
```

a veure si així suspèn sense error.

---

### Post by josep-maria on 2015-05-05
Sí que està actualitzat el sistema.

He fet això del suspend: no es pot tornar a fer funcionar,  igual com si fas clic a "atura temporalment". El pc segueix tenint un led encès, però si toques tecles no fa res, i tampoc si toques el botó d'engegar del pc.

---

### Post by josep-maria on 2015-05-05
He entrat a: [http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/](http://www.mirrorservice.org/sites/cdimage.ubuntu.com/cdimage/releases/)
faig clic a "12.04"
i a "release"

I surt això:

FOOTER.html                                                2014-08-07 23:47   27   
[   ] MD5SUMS                                                    2014-08-07 23:48  1.1K  
[   ] MD5SUMS-metalink                                           2014-08-08 00:08  570   
[   ] MD5SUMS-metalink.gpg                                       2014-08-08 00:08  198   
[   ] MD5SUMS.gpg                                                2014-08-07 23:48  198   
[   ] SHA1SUMS                                                   2014-08-07 23:48  1.2K  
[   ] SHA1SUMS.gpg                                               2014-08-07 23:48  198   
[   ] SHA256SUMS                                                 2014-08-07 23:48  1.6K  
[   ] SHA256SUMS.gpg                                             2014-08-07 23:48  198   
[DIR] source/                                                    2015-03-26 21:36    -   
[   ] ubuntu-12.04-alternate-powerpc.iso                         2012-04-23 22:04  620M  
[   ] ubuntu-12.04-alternate-powerpc.iso.torrent                 2012-04-26 10:25   24K  
[   ] ubuntu-12.04-alternate-powerpc.iso.zsync                   2012-04-26 10:25  1.2M  
[   ] ubuntu-12.04-alternate-powerpc.jigdo                       2012-04-26 10:25  144K  
[   ] ubuntu-12.04-alternate-powerpc.list                        2012-04-23 22:04  102K  
[   ] ubuntu-12.04-alternate-powerpc.metalink                    2014-08-08 00:08  1.0K  
[   ] ubuntu-12.04-alternate-powerpc.template                    2012-04-23 22:04  3.9M  
[   ] ubuntu-12.04-desktop-powerpc.iso                           2012-04-23 13:27  637M  
[   ] ubuntu-12.04-desktop-powerpc.iso.torrent                   2012-04-26 10:30   25K  
[   ] ubuntu-12.04-desktop-powerpc.iso.zsync                     2012-04-26 10:30  1.2M  
[   ] ubuntu-12.04-desktop-powerpc.list                          2012-04-23 13:27  1.3K  
[   ] ubuntu-12.04-desktop-powerpc.manifest                      2012-04-23 13:21   37K  
[   ] ubuntu-12.04-desktop-powerpc.metalink                      2014-08-08 00:08  1.0K  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+ac100.bootimg      2012-04-23 14:29  8.0M  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+ac100.manifest     2012-04-23 14:03   37K  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+ac100.tar.gz       2012-04-23 14:29  482M  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+ac100.tar.gz.zsync 2012-09-28 13:34  963K  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+mx5.img.gz         2012-04-23 15:01  518M  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+mx5.img.gz.zsync   2012-09-28 13:34  1.0M  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+mx5.manifest       2012-04-23 14:40   37K  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+omap.img.gz        2012-04-23 15:07  495M  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+omap.img.gz.zsync  2012-09-28 13:34  1.0M  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+omap.manifest      2012-04-23 14:09   37K  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+omap4.img.gz       2012-04-23 15:04  496M  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+omap4.img.gz.zsync 2012-09-28 13:34  1.0M  
[   ] ubuntu-12.04-preinstalled-desktop-armhf+omap4.manifest     2012-04-23 13:44   37K  
[   ] ubuntu-12.04-preinstalled-server-armhf+omap.img.gz         2012-04-24 02:30  638M  
[   ] ubuntu-12.04-preinstalled-server-armhf+omap.img.gz.zsync   2012-09-28 13:34  1.2M  
[   ] ubuntu-12.04-preinstalled-server-armhf+omap.manifest       2012-04-24 02:09  9.0K  
[   ] ubuntu-12.04-preinstalled-server-armhf+omap4.img.gz        2012-04-24 02:32  636M  
[   ] ubuntu-12.04-preinstalled-server-armhf+omap4.img.gz.zsync  2012-09-28 13:34  1.2M  
[   ] ubuntu-12.04-preinstalled-server-armhf+omap4.manifest      2012-04-24 02:12  9.1K  
[   ] ubuntu-12.04.4-alternate-amd64+mac.iso                     2014-02-04 11:54  746M  
[   ] ubuntu-12.04.4-alternate-amd64+mac.iso.torrent             2014-02-06 17:12   29K  
[   ] ubuntu-12.04.4-alternate-amd64+mac.iso.zsync               2014-02-06 17:12  1.5M  
[   ] ubuntu-12.04.4-alternate-amd64+mac.jigdo                   2014-02-06 17:12  155K  
[   ] ubuntu-12.04.4-alternate-amd64+mac.list                    2014-02-04 11:54  118K  
[   ] ubuntu-12.04.4-alternate-amd64+mac.metalink                2014-08-08 00:08  1.0K  
[   ] ubuntu-12.04.4-alternate-amd64+mac.template                2014-02-04 11:54  5.7M  
[   ] ubuntu-12.04.4-desktop-amd64+mac.iso                       2014-02-04 12:11  731M  
[   ] ubuntu-12.04.4-desktop-amd64+mac.iso.torrent               2014-02-06 17:15   29K  
[   ] ubuntu-12.04.4-desktop-amd64+mac.iso.zsync                 2014-02-06 17:15  1.4M  
[   ] ubuntu-12.04.4-desktop-amd64+mac.list                      2014-02-04 12:11   11K  
[   ] ubuntu-12.04.4-desktop-amd64+mac.manifest                  2014-02-04 12:05   43K  
[   ] ubuntu-12.04.4-desktop-amd64+mac.metalink                  2014-08-08 00:08  1.0K  
[   ] ubuntu-12.04.4-dvd-amd64.iso                               2014-02-04 14:09  1.6G  
[   ] ubuntu-12.04.4-dvd-amd64.iso.torrent                       2014-02-06 17:09   66K  
[   ] ubuntu-12.04.4-dvd-amd64.iso.zsync                         2014-02-06 17:09  3.3M  
[   ] ubuntu-12.04.4-dvd-amd64.list                              2014-02-04 14:09  8.1K  
[   ] ubuntu-12.04.4-dvd-amd64.manifest                          2014-02-04 14:01   76K  
[   ] ubuntu-12.04.4-dvd-amd64.metalink                          2014-08-08 00:08  1.0K  
[   ] ubuntu-12.04.4-dvd-i386.iso                                2014-02-04 14:10  1.6G  
[   ] ubuntu-12.04.4-dvd-i386.iso.torrent                        2014-02-06 17:10   65K  
[   ] ubuntu-12.04.4-dvd-i386.iso.zsync                          2014-02-06 17:10  3.2M  
[   ] ubuntu-12.04.4-dvd-i386.list                               2014-02-04 14:10  7.3K  
[   ] ubuntu-12.04.4-dvd-i386.manifest                           2014-02-04 14:04   75K  
[   ] ubuntu-12.04.4-dvd-i386.metalink                           2014-08-08 00:08  1.0K  
[   ] ubuntu-12.04.5-dvd-amd64.iso                               2014-08-07 22:08  1.7G  
[   ] ubuntu-12.04.5-dvd-amd64.iso.torrent                       2014-08-07 23:46   67K  
[   ] ubuntu-12.04.5-dvd-amd64.iso.zsync                         2014-08-07 23:46  3.3M  
[   ] ubuntu-12.04.5-dvd-amd64.list                              2014-08-07 22:08  8.1K  
[   ] ubuntu-12.04.5-dvd-amd64.manifest                          2014-08-07 17:18   76K  
[   ] ubuntu-12.04.5-dvd-amd64.metalink                          2014-08-08 00:08  1.0K  
[   ] ubuntu-12.04.5-dvd-i386.iso                                2014-08-07 22:13  1.6G  
[   ] ubuntu-12.04.5-dvd-i386.iso.torrent                        2014-08-07 23:47   66K  
[   ] ubuntu-12.04.5-dvd-i386.iso.zsync                          2014-08-07 23:47  3.3M  
[   ] ubuntu-12.04.5-dvd-i386.list                               2014-08-07 22:13  7.3K  
[   ] ubuntu-12.04.5-dvd-i386.manifest                           2014-08-07 17:34   76K  
[   ] ubuntu-12.04.5-dvd-i386.metalink                           2014-08-08 00:08  1.0K  

Què cal fer ara?

---

### Post by wgarcia on 2015-05-06
Has de crear-te un USB o DVD amb la imatge que vulguis. Per exemple si vols la versió d'Ubuntu amb escriptori Unity i de 64 bits, la imatge seria:

```
ubuntu-12.04.5-dvd-amd64.iso
```

Si en canvi la vols de 32 bit, la imatge seria:

```
ubuntu-12.04.5.dvd-i386.iso
```

Tot i que posi "dvd" aquestes imatges serveixen tant per crear un DVD d'instalal·lació o un USB d'instal·lació. Les que acaben en "torrent" es baixen per torrent més ràpidament.

Per crear el dvd simplement poses un dvd gravable en blanc a la unitat, cliques amb el botó dret sobre la icona de fitxer, i esculls "escriu al disc". Per crear l'USB d'instal·lació has de seguir les instruccions que pots trobar a ubuntu.com o llocs semblants.

Abans de resnstal·lar si vols es pot provar de posar-li a la 14.04 un nucli més nou, perquè això que et passa té tota la pinta de ser un problema amb el nucli de linux que porta la versió 14.04.

---

### Post by josep-maria on 2015-05-06
Uf. Intentaré gravar l'arxiu 12.04 a una memòria flash, perquè.el lector de discos tampoc no funciona (perdoneu però amb tants errors m'havia deixat de dir-ho).
A més a més, abans, amb la versió 12.04, podia fer la compra per internet al supermercat Iquodrive, pero amb la versió 14.04, tampoc no es pot.

I si canvio el pc per un altre de més modern? Potser acabaríem abans.

---

### Post by wgarcia on 2015-05-08
Si vols intentar provar un nucli de linux més nou a veure si soluciona els problemes d'aturada temporal que estàs veient, no és massa complicat.

---

### Post by josep-maria on 2015-05-08
A [www.ubuntu.com](www.ubuntu.com) he trobat la versió 12.04. L'he descarregada, i ara tinc un arxiu que es diu "ubuntu-12.04.5-alternate-i386.iso".
També he descarregat el programa k3b. Quan he volgut fer servir el k3b per gravar un disc, no he pogut. Mirant molt, he vist a una finestreta que diu "insert an empty or appendable medium". I d'aquí no surt, facis com facis.

---

### Post by wgarcia on 2015-05-08
Deies que tens un problema a la unitat de CD? En principi clicant amb el botó dret del ratolí sobre la icona del fitser "iso" a l'escriptori, no t'hauria de caldre el programa "k3b" perquè hi ha una opció que diu "Escriu al disc", i amb això ja seria suficient per crear un disc amb aquesta imatge. Alternativament, també hi ha una utilitat que es diu "Creador de disc d'arrancada" amb el qual pots crear allò, discos per arrencar el sistema amb la "iso" que t'has baixat.

---

### Post by josep-maria on 2015-05-08
He provat de fer clic amb el botó de la dreta al'arxiu .iso i després a "escriu al disc", però diu que no hi ha prou espai al disc (perquè l'arxiu té 783.3 MB).

He provat de crear un disc per engegar fent clic a eines del sistema > administració > creador de discos, però no hi ha manera:
He pogut arrossegar l'arxiu iso a la casella "imatge de disc .iso". Però no em deixa fer res a la casella "disc a utilitzar".

---

### Post by wgarcia on 2015-05-11
Aquestes imatges caben a un DVD, no a un CD. Entenc que la unitat que tens és de CD no de DVD? En aquest cas hauries d'utilitzar una memòria USB. 

Una altra possibilitat és fer servir una "mini iso". Aquestes imatges són molt petites, per tant les pots gravar en un CD, però necessites que l'ordinador tingui accés a Internet per baixar-se la resta de elements per a la instal·lació. El procediment és le mateix, et baixes la imatge, la cremes a un CD en blanc, i arrenques l'ordinador amb aquest CD per fer la instal·lació. Després de contestar les preguntes habituals a l'inici l'instal·lador començarà a baixar-se la resta d'Internet per acabar la instal·lació. 

Aquestes imatges les pots trobar aquí:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by josep-maria on 2015-05-30
Perdoneu que no hagi contestat abans, és que no tinc el pc a casa sinó una mica lluny, i a més, la reparació m'ha donat molta feina.

He pogut gravar la versió 12.04 a un disc. He canviat el lector de discos, que no funcionava. Per fi he pogut insta&#320;lar la versió 12.04. Però tot segueix igual. 

He anat actualitzant fins a la versió 15.04, i tot segueix igual. No passa res, puc passar sense l'aturada temporal, la pega és l'accés a la web del supermercat, però ja hi entraré des d'un altre pc.

Moltes gràcies.

---

