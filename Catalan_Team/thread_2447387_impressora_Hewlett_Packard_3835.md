---
title: "impressora Hewlett Packard 3835"
date: 2020-07-17
forum: Catalan Team
---

### Post by josep-maria on 2020-07-17
Vull comprar una impressora Hewlett Packard officejet 3835. Com puc saber si funcionarà? És a dir, si ja tinc el programa traductor? He mirat als menús però no he trobat res.

---

### Post by ffp on 2020-07-20
Totes les impressores hp estan ben suportades per Ubuntu.
El programari per la seva gestió es HPLIP, que et permetrà donar-la d'alta, configurar-la, etc...

---

### Post by josep-maria on 2020-07-20
Abans de comprar-la, com puc saber si ja tinc el programa traductor? I si no el tingués, què haig de fer per ficar-lo?

---

### Post by ffp on 2020-07-21
> **josep-maria said:**
> Abans de comprar-la, com puc saber si ja tinc el programa traductor? I si no el tingués, què haig de fer per ficar-lo?
No entenc bé que vols dir amb "programa traductor". 
Per que funcioni una impressora hp, cal el programa genèric d'impressores "cups", instal·lat per defecte a totes les distribucions i l'especific de hp "hplip"
Per instal·lar-ho obre un terminal "Control+Alt+t" i executa "sudo apt install hplip"
Si ja el tens instal·lat et dirà que ja està en la versió mes recent, i si no, l'instal·larà.
Per iniciar la parametrització de la impressora, cerca hplip a les aplicacions i trobaràs "hplip toolbox", executa l'aplicació i afegeix la nova impressora. Desgraciadament el programa està en anglès, però no te cap dificultat.

---

### Post by wgarcia on 2020-07-24
En aquesta pàgina:

[https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)

et diu quines impressores HP tenen suport a Linux. Si cerques per la que dius, veuràs que diu que té suport complet ("Full").

---

### Post by josep-maria on 2020-07-30
He mirat a [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index)
Diu que les impressores que vull tenen full support. Això vol dir que no haig de descarregar ni instat&#320;lar res? Vull dir, que la connecto al pc i ja funcionarà?

---

### Post by josep-maria on 2020-07-30
He fet això de sudo apt install hplip
Diu:
hplip ja està en la versió més recent (3.16.3+repack0-1).

---

### Post by ffp on 2020-07-31
> **ffp said:**
> 
Si ja el tens instal·lat et dirà que ja està en la versió mes recent, i si no, l'instal·larà.
Per iniciar la parametrització de la impressora, cerca hplip a les aplicacions i trobaràs "hplip toolbox", executa l'aplicació i afegeix la nova impressora. Desgraciadament el programa està en anglès, però no te cap dificultat.
Repeteixo les instruccions.

---

### Post by josep-maria on 2020-07-31
He trobat un arxiu que es diu toolbox.py. És a /usr/share/hplip. He vist les instruccions del programa, però no em deixa executar-lo. Potser haig de ficar abans la impressora nova?
A totes les capses de les impressores que he vist no diu res del linux, només diu que funcionen amb windows i mac. Potser és perquè són models nous.

---

### Post by ffp on 2020-08-01
Per cercar una aplicació cal anar a la part baixa del acoblador lateral esquerra (on están les aplicacions), i trobarás el cercador:
[ATTACH=CONFIG]286587[/ATTACH]
Clica, i sortira una caixa de cerca, escrius hplip i sortiran els programes:
[ATTACH=CONFIG]286588[/ATTACH]
No has de cercar cap fitxer! Es un programa.

Una altra manera d'obrir el programa es obrir un terminal "Control+Alt+t", escriure hp-toolbox i enter.

Informació sobre hp-toolbox:
[http://hatteras-blog.blogspot.com/2014/09/hplip-toolbox-herramienta-para.html](http://hatteras-blog.blogspot.com/2014/09/hplip-toolbox-herramienta-para.html)

---

### Post by josep-maria on 2020-08-01
Ja he fet hp-toolbox al terminal. M'ha dit que per ficar la toolbox calia fer: 
sudo apt install hplip-gui
Ho he fet, i ha installat la toolbox. L'he engegat, i diu que no hi ha cap impressora. 
És a dir, que primer haig de comprar una impressora HP (de qualsevol model, oi?), i després engegar la hp-toolbox. Oi?

---

### Post by wgarcia on 2020-08-02
Sí, sense impressora, et dirà que no tens impressora.

---

### Post by josep-maria on 2020-08-13
Ja funciona. Moltes gràcies.

---

### Post by josep-maria on 2020-08-14
He pogut imprimir, però no funciona el scanner. He fet el hp-setup i el hp-toolbox, i diu que no en troba cap:

\josep@josep:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.16.3)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb
Searching... (bus=par, search=(None), desc=0)
error: No devices found on bus: par
Searching... (bus=usb, search=(None), desc=0)
error: No devices found on bus: usb

Done.
josep@josep:~$ hp-toolbox

HP Linux Imaging and Printing System (ver. 3.16.3)
HP Device Manager ver. 15.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

---

### Post by josep-maria on 2020-08-14
A aplicacions > ofimàtica ha aparescut això: hplip fax utility.
Si hi faig clic, no fa res.

---

### Post by josep-maria on 2020-08-14
En canvi, a centre de control > printers sí que hi és la impressora hp-deskjet-2700-series.
I està marcada com a habilitada i compartida.

---

### Post by josep-maria on 2020-08-14
Si faig hp-toolbox, surt una finestra que diu "no installed hp device found"
Cal fer clic als botons     "run setup"       o      "cups web interface"

Si faig clic a "run setup", 
surt una finestra que diu "hp device manager - setup"
li dic usb,
i diu "no devices found",
i d'aqui no el treus.

Si faig clic a cups web interface, surt una finestra que diu "localhost:631/admin"
Cal trobar la impressora a una llista llarga, però el model dekjet 2710 no hi és.

Pot ser que el model sigui molt nou?

---

### Post by josep-maria on 2020-08-15
He pogut imprimir, però si vull escanejar, surt una finestra que es diu   hp-systray
i diu:

HPLIP cannot detect devices in your network. This may be due to existing firewall settings blocking the required ports like (5353/udp). When you are in a trusted network environment, you may open the ports for network services like mdns and slp in the firewall. For detailed steps follow the link.

 [http://hplipopensource.com/node/375](http://hplipopensource.com/node/375)

Si cerco aquesta darrera adreça a internet, em diu   "page not found"

---

### Post by josep-maria on 2020-09-18
He intentat tornar a començar. He tret el connector usb de la impressora, l'he esborrada de la llista d'impressores (del centre de control > printers), l'he tornada a connectar, he intentat afegir-la a la llista d'impressores. Em demana que trïi un controlador, faig clic a HP-recomanat, surt una llista de models de HP, però el model deskjet 2700 no hi és. També surt una finestreta que diu que el model deskjet 2700 no té cap controlador. 

He fet clic a sistema > administració > programari > controladors adicionals, i em diu que no n'hi ha cap de disponible.

---

### Post by ffp on 2020-09-18
La impressora hp es dona d'alta amb el programa hp-toolbox. No pel general d'impressores que nomes trobara genèrics. Torna a fer-ho tal com varem explicar-ho al principi d'aquest post.
Una vegada instal·lada de nou:
Per escanejar un document, cal un programa d'escaneig. Per defecte ubuntu te instal·lat l'escàner de documents. Obres l'aplicació amb la impressora connectada i funcionant, el programa cercarà l'escaner. L'hauria de trobar amb facilitat.
Un altre manera de fer-ho es amb el hp-toolbox. A la pestanya actions, hi ha la opció scan, si cliques s'obrira el programa d'escaneig i començara la cerca.

---

### Post by ffp on 2020-09-18
Gràficament:
[ATTACH=CONFIG]286981[/ATTACH]

---

### Post by josep-maria on 2020-09-18
A aplicacions no hi és hplip toolbox,
però sí hplip fax utility. Hi he fet clic, però no fa res.

Si faig al terminal > hp-toobox > set up,
diu: no installed hp device found
llavors faig clic a set up device.
clic a usb, next,
diu: no devices found
i d'aquí no el trec

---

### Post by josep-maria on 2020-09-18
file:///home/josep/Escriptori/Screenshot%20at%202020-09-18%2023:41:54.png

---

### Post by josep-maria on 2020-09-18
[IMG]file:///home/josep/Escriptori/Screenshot%20at%202020-09-18%2023:41:54.png[/IMG]

---

### Post by josep-maria on 2020-09-18
Aneu a aquesta adreça:

[https://blocs.tinet.cat/tokra/files/2020/09/Screenshot-at-2020-09-18-234154.png](https://blocs.tinet.cat/tokra/files/2020/09/Screenshot-at-2020-09-18-234154.png)

---

### Post by josep-maria on 2020-09-18
[https://blocs.tinet.cat/tokra/files/2020/09/Screenshot-at-2020-09-18-234154.png](https://blocs.tinet.cat/tokra/files/2020/09/Screenshot-at-2020-09-18-234154.png)

---

### Post by ffp on 2020-09-19
Vol dir que no tens instal·lada la impressora. Si et fixes, a la barra lateral esquerra de la "Refreshing  device list" NO apareix cap impressora instal·lada. 
Clica el botó "Setup Device" per iniciar el descobriment i parametrització de la impressora. Com que es USB li hauràs de dir, i seguir els passos. Recorda tenir la impressora connectada i funcionant.
Es possible que trobi una 3830 (inclou la teva), però no ha de trobar la 2700, no es la mateixa serie.
La teva impressora està suportada per Linux tant impressió com escàner: [https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index](https://developers.hp.com/hp-linux-imaging-and-printing/supported_devices/index).

---

### Post by josep-maria on 2020-09-19
Ja havia fet "set up device > usb > next" (= comentari #22)
Diu "no devices found", i no em deixa fer res més.
Mireu:  [https://blocs.tinet.cat/tokra/files/2020/09/Screenshot-at-2020-09-19-163415.png](https://blocs.tinet.cat/tokra/files/2020/09/Screenshot-at-2020-09-19-163415.png)

---

### Post by josep-maria on 2020-09-19
És el model 2710.

---

### Post by wgarcia on 2020-09-20
No et demana instal·lar el connector per a l'escàner (hp-plugin)?

---

### Post by ffp on 2020-09-20
> **josep-maria said:**
> És el model 2710.

doncs el títol del post posa "Hewlett Packard 3835"

---

### Post by ffp on 2020-09-20
La impressora hp 2710 també està perfectament suportada per Linux. Realment no se quin problema pots tenir. Ho sento, però seguiré investigant.
Jo mai he tingut problemes amb cap impressora hp, i la que tinc ara es la segona.
Has provat amb un altre cable usb i/o una altre entrada USB :sad:

---

### Post by ffp on 2020-09-20
> **wgarcia said:**
> No et demana instal·lar el connector per a l'escàner (hp-plugin)?
Jo no tinc cap hp-plugin instal·lat, ni tan sols existeix.
Al mòbil android si que hi ha un hp-plugin

---

### Post by ffp on 2020-09-21
Comprova si tens tots els paquets hplip instal·lats (els que tinc jo amb ubuntu 20.04):
hplip  hplip-data  hplip-gui  libhpmud0  libsane-hpaio  openprinting-ppds  printer-driver-hpcups  printer-driver-pxljr printer-driver-postscript-hp  printer-driver-pnm2ppa
Pots fer-ho amb synaptic (si el tens instal·lat), o be al terminal sudo apt install "cada un dels paquets" i a veure si en falta algún.

---

### Post by josep-maria on 2020-09-24
Diu que sí, que ja tinc tots els paquets:


josep@josep:~$ sudo apt install hplip-data
[sudo] contrasenya per a josep: 
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip-data ja està en la versió més recent (3.16.3+repack0-1).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip-gui
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip-gui ja està en la versió més recent (3.16.3+repack0-1).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip ja està en la versió més recent (3.16.3+repack0-1).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip libhpmud0
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip ja està en la versió més recent (3.16.3+repack0-1).
libhpmud0 ja està en la versió més recent (3.16.3+repack0-1).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip libsane-hpaio
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip ja està en la versió més recent (3.16.3+repack0-1).
libsane-hpaio ja està en la versió més recent (3.16.3+repack0-1).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip openprinting-ppds
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip ja està en la versió més recent (3.16.3+repack0-1).
openprinting-ppds ja està en la versió més recent (20160212-0ubuntu1).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip printer-driver-hpcups
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip ja està en la versió més recent (3.16.3+repack0-1).
printer-driver-hpcups ja està en la versió més recent (3.16.3+repack0-1).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip printer-driver-pxljr
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip ja està en la versió més recent (3.16.3+repack0-1).
printer-driver-pxljr ja està en la versió més recent (1.4+repack0-4).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip printer-postscript-hp
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
E: No s'ha trobat el paquet printer-postscript-hp
josep@josep:~$ sudo apt install hplip printer-driver-postscript-hp
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip ja està en la versió més recent (3.16.3+repack0-1).
printer-driver-postscript-hp ja està en la versió més recent (3.16.3+repack0-1).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.
josep@josep:~$ sudo apt install hplip printer-driver-pnm2ppa
S'està llegint la llista de paquets&#8230; Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat&#8230; Fet
hplip ja està en la versió més recent (3.16.3+repack0-1).
printer-driver-pnm2ppa ja està en la versió més recent (1.13+nondbs-0ubuntu5).
0 actualitzats, 0 nous a instal·lar, 0 a suprimir i 2 no actualitzats.

---

### Post by josep-maria on 2020-09-24
Ja havia provat de canviar el port usb, i no va funcionar. Cal dir que fins ara tenia una altra impressora HP, amb el mateix cordó, i va anar sempre bé.

---

### Post by josep-maria on 2020-10-24
Al terminal, faig:                           hp-toolbox
em diu:                                         no installed hp device found
faig clic a:                                     cups web intrface > add printers 
i surt això:                                     [https://blocs.tinet.cat/tokra/files/2020/10/Screenshot-at-2020-10-24-112614.png](https://blocs.tinet.cat/tokra/files/2020/10/Screenshot-at-2020-10-24-112614.png)
continuo endavant, i surt això:      [https://blocs.tinet.cat/tokra/files/2020/10/Screenshot-at-2020-10-24-112556.png](https://blocs.tinet.cat/tokra/files/2020/10/Screenshot-at-2020-10-24-112556.png)

podeu veure que no hi és el model deskjet 2710

---

### Post by josep-maria on 2020-11-14
He actualitzat l'ubuntu al 20.04.5, pensant que s'arreglaria, però encara no.

---

### Post by josep-maria on 2020-11-20
Vaig a: centre de control > impressores 
veig la icona de la impressora hp2700
faig cilc a "afegeix"
diu: cercant controladors
surt una llista llarguíssima de models d'impressores
la hp2700 no hi és
ho podeu veure a:      [https://blocs.tinet.cat/tokra/files/2020/10/Screenshot-at-2020-10-24-112556.png](https://blocs.tinet.cat/tokra/files/2020/10/Screenshot-at-2020-10-24-112556.png))
per tant, no la podré fer funcionar mai (o fins que algú faci el controlador i la fiqui a la llista)

He mirat si cap dels models que hi ha a la venda surt a la llista de controladors que puc baixar-me. 
He trobat la brother dcp1510, però és de làser.
Hi ha algú que tingui aquest model?
Dit d'una altra manera; quines impressores teniu vosaltres que sí que funcionin?
Quin fabricant és més recomanable per funcionar amb l'ubuntu? Només vull una multifunció, la més senzilla possible.

---

### Post by ffp on 2020-11-20
La hp 2700 es reconeguda per hplip a partir de la versió 3.20.5.
Amb les proves que vas fer, resulta que tenies la versió antiga 3.16.3.
Lamentablement a ubuntu 20.04 encara no té aquesta versió, i molt menys la 18.04. En canvi si està actualitzada a ubuntu 20.10 i no sé si la podràs instal·lar. Per mostra aquesta captura de pantalla (ubuntu 20.10):
[ATTACH=CONFIG]287393[/ATTACH]
[https://laboratoriolinux.es/index.php/-noticias-mundo-linux-/software/27119-el-software-de-hp-llamado-hplip-anuncia-su-nueva-version-3-20-5-con-soporte-para-debian-10-3.html](https://laboratoriolinux.es/index.php/-noticias-mundo-linux-/software/27119-el-software-de-hp-llamado-hplip-anuncia-su-nueva-version-3-20-5-con-soporte-para-debian-10-3.html)

---

### Post by josep-maria on 2020-11-21
Ja va bé. Béeeeeee. Moltes gràcies.

---

