---
title: "Arrancar automaticament un programa amb permisos de root"
date: 2007-08-31
forum: Catalan Team
---

### Post by pespin on 2007-08-31
Doncs aquesta questió porta uns quants dies pel irc, però alguna alternativa que m'han presentat no m'ha funcionat, bé perquè no ho he entès bé o perquè realment no funciona xD

Necessito arrancar automaticament al engegar l'ubuntu un programa amb permissos de root, a poder ser a posteriori de les X.

Si algú pot anar deixant aquí informació sobre el tema o explicar-m'ho amb pels i senyals li agrairia molt, ja que no ho he aconseguit i ja comença a ser urgent. Tindria que tindreu muntat dintre de 10 dies.

Informació:
SO-> Ubuntu 6.06
programa->Dosemu (necesita permisos de root per accedir al port paral·lel.)

---

### Post by papapep on 2007-08-31
Has provat passant com a opció "-serial /dev/ttyS0" al cridar a Qemu?

---

### Post by pespin on 2007-08-31
el Dosemu es el mateix que el Qemu? :confused:

---

### Post by papapep on 2007-08-31
Upsss....llegir ràpid no sempre és profitós. :-/

Tot i això, t'has plantejat instal·lar un DOS "normal" dins un qemu, o un vmware? No sé si és el que et fa falta, però t'ho comento com opció de sortida al teu problema.

---

### Post by pespin on 2007-08-31
Em sembla que si que tinc instal·lat un DOS "normal", ja que jo li puc posar quin DOS carregar. De fet ve amb el freedos o un d'aquests i vaig posar un DOS de M$ perquè no em funcionaba el codi. :)

Com a possibles solucions m'han comentat el suid i el crontab, però no he conseguit fer-los funcionar jeje.

---

### Post by papapep on 2007-08-31
Però igual amb el qemu, que no és el mateix que el dosemu, que té l'opció explícita per a habilitar els ports sèrie, et funcionaria correctament l'invent aquest teu.

---

### Post by pespin on 2007-08-31
Ho provaré si no hi ha mes remei, però m'agradaria saber si hi ha alguna manera de correr automaticament un programa com a root, independentment de quin sigui, ja que aixi m'estalvio la configuració d'altres programes com el Qemu :)

---

### Post by eselma on 2007-09-01
No és el mateix cas que el teu (DOSEMU) , però en altres emuladors, per accedir al port paral·lel hi han diverses limitacions:

- La primera, l'usuari ha d'estar autoritzat per accedir-hi directament (sense passar per CUPS o LPR). Això es pot aconseguir canviant els permisos de grup pel port ( lp0, suposo ) al directori /dev/ i afegint l'usuari al nou grup creat.

- Normalment això no és suficient, i cal deixar que el dimoni per defecte ( em sembla que és parport, o una cosa semblant ) resti inactiu: però llavors no podràs imprimir des de CUPS.

En qualsevol cas, fer coses a Linux directament com a root no sembla gens aconsellable. 

Suposo que no t'he ajudat gaire, però mira, es una altra *línia de recerca*... :)

---

### Post by pespin on 2007-09-01
El port paral·lel no l'utilitzo per imprimir, si no per a accedir a una placa (drivers windows, per això ho emulo). 

També vaig provar de modificar els permisos de /dev/lp0 i res, em segueix demanant permisos de root.

---

### Post by papapep on 2007-09-01
Aquí: [https://sourceforge.net/tracker/?func=detail&atid=457447&aid=1166288&group_id=49784](https://sourceforge.net/tracker/?func=detail&atid=457447&aid=1166288&group_id=49784)
 i aquí: [http://www.mail-archive.com/linux-msdos@vger.kernel.org/msg04236.html](http://www.mail-archive.com/linux-msdos@vger.kernel.org/msg04236.html)

parlen de problemes semblants als teus, i sembla que tingui a veure amb un paràmetre que hi ha d'haver dins el fitxer dosemu.conf que es diu **$_port**s i el valor que se li assigna.

---

### Post by eselma on 2007-09-02
> **pespin said:**
> El port paral·lel no l'utilitzo per imprimir, si no per a accedir a una placa (drivers windows, per això ho emulo).

Sí, és un cas semblant al meu amb el port sèrie. T'ho deia perquè si cal desactivar *parport* o un servei semblant queda afectada la impressió, sempre qua facis servir el port paral·lel, és clar (era el meu cas amb una Brother 1270N que, afortunadament, també podia activar amb interfície de xarxa.

La diferència és que amb* VirtualBox* sí que podia accedir-hi després de canviar els permisos i desactivar *parport*.

---

