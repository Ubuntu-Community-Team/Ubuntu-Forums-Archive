---
title: "Em peta l'eina de gestió d'impressores -Gutsy"
date: 2007-10-22
forum: Catalan Team
---

### Post by migjorn on 2007-10-22
Hola a tothom, he actualitzat a la Gutsy i tot em va bé, tret d'una cosa.
L'eina de gestió de les impressores no la puc obrir; no l'arribo a veure i ja em peta, i fins i tot una vegada m'ha fet desaparèixer la barra d'aplicacions.

Algú en té idea, de què pot ser?
Moltes gràcies gent

---

### Post by papapep on 2007-10-22
Executa en un terminal:

```
gnome-cups-manager
``` 

a veure quin missatge d'error et dóna.

---

### Post by migjorn on 2007-10-26
gràcies per la resposta.
Però, el gnome cups manager no el tinc instal·lat. No surt amb una altra eina de gestió d'impressores per defecte?

Fins ara!

---

### Post by papapep on 2007-10-26
Doncs si no tens instal·lat el gnome-cups-manager no sé de quin gestor d'impressores estàs parlant que no et funciona....aquest és el que instal·la Ubuntu per defecte.

Potser el problema és precisament que no el tens instal·lat :-)

En un altre ordre de coses, el Cups també el pots gestionar apuntant el navegador a la següent url:

[http://localhost:631/](http://localhost:631/)

---

### Post by migjorn on 2007-10-27
Vull dir el system-config-printer. En parlen [ací]("http://www.vcubells.net/arxiu/2007/08/17/727/").
Moltes gràcies per la resposta!

---

### Post by papapep on 2007-10-27
Jo estic amb Gutsy i el system-config-printer no el tinc. Potser és per que jo he actualitzat des de Feisty.

Aleshores, tu has de mirar si tens un o altre paquet instal·lat:

```
sudo aptitude search gnome-cups-manager system-config-printer
```

En el meu cas tinc:

```
papapep@awacs:~$ sudo aptitude search system-config-printer gnome-cups-manager
i A gnome-cups-manager              - CUPS printer admin tool for GNOME         
c   system-config-printer           - Printer configuration GUI
```

El qual indica que tinc instal·lat (i) el gnome-cups-manager i no l'altre (c).

Si realment no tens cap dels dos instal·lats, et cal decidir quin dels dos vols. Jo del system-config-printer no et puc donar referències. De l'altre si.

A banda, has provat a fer-ho a través del navegador com t'he comentat abans?

---

### Post by migjorn on 2007-11-08
Doncs jo tinc l'altre instal.lat, per defecte. Em surt 
i   system-config-printer                  - Printer configuration GUI  

I em continua petant. Tinc molts problemes a configurar una fotocopiadora amb l'ubuntu, i sense aquesta eina no sé com m'ho he de fer...

Gràcies!

---

### Post by papapep on 2007-11-08
> Tinc molts problemes a configurar una fotocopiadora amb l'ubuntu

...t'has equivocat al posar "fotocopiadora"? o ho has posat correctament??

Has provat el que et vaig dir fa dies d'accedir via navegador?

---

### Post by migjorn on 2007-11-09
Doncs sí, he volgut dir fotocopiadora. Al centre on treballo en tenim una, de marca Sharp i model AR-M207. Com és natural, l'equip docent em demana de poder imprimir des dels ordinadors (que van tots amb ubuntu). He provat de fer_ho, però no me'n surto de cap de les maneres i he abandonat. Ho he mirat a través de la web com m'has dit. Em detecta la impressora, però no fa còpies. Fa soroll d'engegar-se, quan li dones a imprimir, però res de res. Supose que no n'hi haurà el driver adequat, o si més no jo no l'he trobat...

Es veu això:

Description: AR-M207

Location:

Printer Driver: Sharp AJ-1800 Foomatic/pcl3 (recommended)

Printer State: idle, accepting jobs, published.

Device URI: usb://SHARP/AR-M207/AR-EB9

Moltes gràcies per la dedicació

---

### Post by papapep on 2007-11-09
Bé, ja tenim alguna cosa clara per començar a treballar.

Hauries de investigar quina emulació permet la màquina aquesta. Normalment solen emular algun model d'HP o Epson.

Quan sàpigues quin model emula hauries de provar a re-instal·lar-la amb el controlador pertinent. Moltes solen emular la laserjet 5 (abans ho feien amb la 4).

Per cert, quan dius que no imprimeix, ho has provat amb la pàgina de prova? o tampoc surt?

---

### Post by migjorn on 2007-11-09
Uep! Deu ser molt evident, però com puc saber quina altra impressora emula? Acabo de fer un colp d'ull per internet i no ho he trobat....
Pel que fa a la pàgina de prova, tampoc no la imprimeix.

Moltes gràcies!

---

### Post by papapep on 2007-11-09
A les especificacions del model a la pàgina de Sharp diu:

[http://www.sharp.eu/cps/rde/xchg/SID-0A0A4383-83273AAC/es/hs.xsl/182_1943_33333939_ESN_HTML.htm](http://www.sharp.eu/cps/rde/xchg/SID-0A0A4383-83273AAC/es/hs.xsl/182_1943_33333939_ESN_HTML.htm)

> Impresora en red
Resolución (ppp)	600
Resolución mejorada (ppp)	-
Interfaz estándar/opcional	Std IEEE 1284, USB 1.1, 2.0, Opt 10/100 BaseXT
SO compatible estándar	IEEE1284: Win95/98/Me/NT4.0/2000/XP.
Opciones de SO compatibles	Win95/98/Me/NT4.0/2000/XP/ Mac OS 10.1.5/10.2.8/10.3.9/10.4-10.4.2 (PS only)
Protocolos de red	TCP/IP,IPX/SPX (NetWare), NetBEUI, Ether Talk
Protocolos de impresión	-
[B]Impresora emulación PDL estándar/opcional	Std SPLC (GDI with JBIG compression) Opt (Std) PCL5e, PCL6, (Opt) Postscript3
[/B]Fuentes disponibles	80 (PCL), 136 (PS3)

Aleshores crec que et pot funcionar el driver genèric PCL5e de CUPS. El trobaràs triant **Genèric > PCL5e Printer > Generic PCL5e Printer Foomatic/ljet4**.
Sinó anés en provarem d'altres, però té molts números que aquest vagi bé.

---

### Post by migjorn on 2007-11-12
Uep! ja he fet la primera prova. De moment, amb aquest driver no funciona. Vaig provant amb els altres genèrics?

Gràcies!

---

### Post by papapep on 2007-11-12
Si, prova el lj4 i companyia.
Però segur que configures bé el port d'impresió? Ho dic per que no se'ns escapi cap tonteria...

Per cert, hi ha màquines a les quals se'ls hi ha d'activar l'emulació pel menú. D'altres ho porten per defecte. Seria bó assegurar la jugada i fer un cop d'ull al manual.

---

### Post by migjorn on 2007-11-12
uff, el port d'impressió?
No ho sé pas. L'ubuntu em detecta l'impressora conectada localment. L'afegeixo a través del cups manager i ja està? Caldria fer res més?

Fins ara

---

### Post by papapep on 2007-11-12
Anem a pams:

Com que parlaves de que el professorat vol imprimir a aquesta impressora he assumit, mal fet per part meva, que la tenies amb un servidor d'impressió, i que hi connectaves per tcp/ip.

Explica com tens el muntatge, comencem pels fonaments.

Independentment d'això, cal que verifiquis a la màquina si té la emulació activada.

---

### Post by migjorn on 2007-11-13
De moment, senzillament l'he connectada amb un cable USB, per provar...
Ho continuo intentant.
Gràcies!

---

