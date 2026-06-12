---
title: "No em va el WIfi amb la darrera versió 11/10 Ubuntu"
date: 2011-12-14
forum: Catalan Team
---

### Post by Jayhawker on 2011-12-14
He instal·lat el darrer Ubuntu, i em passa una cosa curiosa. El Wifi aparentment sembla captar-me d'altres routers, però curiosament no el meu. Llavors, he optat per instal·lar el meu router en Wifi ocults, i aquí sembla detectar-me'l, fins i tot al capdavall d'un temps em diu que estic connectat, però no és cert, perquè em resulta impossible navegar.

Mercès per qualsevol suggeriment i per l'atenció prestada.

---

### Post by Jayhawker on 2011-12-14
Sisplau,

Necessito solucionar aquest problema. És una llàstima perquè la resta del sistema sembla realment bo. S'ha millorat l'accés a les descàrregues i tot allò referent al media i als xats segons com supera Windows de llarg.

Mercès.  

> **Jayhawker said:**
> He instal·lat el darrer Ubuntu, i em passa una cosa curiosa. El Wifi aparentment sembla captar-me d'altres routers, però curiosament no el meu. Llavors, he optat per instal·lar el meu router en Wifi ocults, i aquí sembla detectar-me'l, fins i tot al capdavall d'un temps em diu que estic connectat, però no és cert, perquè em resulta impossible navegar.

Mercès per qualsevol suggeriment i per l'atenció prestada.

---

### Post by wgarcia on 2011-12-14
El primer seria esbrinar quin és maquinari que tens, tot i que el fet que es vegin xarxes inalàmbriques sembla mostrar que està funcionant correctament i que l'Ubuntu el reconeix. Però per saber quina és la tarja de xarxa pots obrir una terminal i entrar:

```
lspci | grep -i "network"
```

---

### Post by Jayhawker on 2011-12-15
Em surt això:

02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

Té alguna cosa a veure que sigui un HP Pavillion? Hi ha cap problema entre els HP i Ubuntu? Ho dic perquè amb Windows no hi ha cap problema, curiosament. 

Mercès per l'interès.

> **wgarcia said:**
> El primer seria esbrinar quin és maquinari que tens, tot i que el fet que es vegin xarxes inalàmbriques sembla mostrar que està funcionant correctament i que l'Ubuntu el reconeix. Però per saber quina és la tarja de xarxa pots obrir una terminal i entrar:

```
lspci | grep -i "network"
```

---

### Post by wgarcia on 2011-12-16
No, el problema és de controladors normalment, hi ha uns acords mig il·legals entre els fabricants de components i Microsoft per la qual a canvi de vendre els ordinadors amb Windows preinstal·lat, els fabricants sols es preocupen d'assegurar els controladors per Windows. Alguns d'aquests controladors són de codi obert amb la qual cosa els desenvolupadors de Linux els poden incoporar als nuclis d'aquest sistema operatiu, però hi ha d'altres que no són de codi obert i en cas que el fabricant no proveeixi els controladors per Linux, s'ha de fer una tasca mig detestivesca per poder-los fer funcionar. 

Hi ha una altra alternativa que consisteix en usar un programa que es diu ndiswrapper que permet utilitzar el controlador de Windwos però sota Linux. 

Ara bé, has mirat si sota el menú "Paràmetres de sistema" (que pots trobar a la icona de més a la dreta del plafó superior), secció "Maquinari", secció "Controladors addicionals", Ubuntu no t'està oferint algun controlador per a la teva targeta de xarxa?

---

### Post by wgarcia on 2011-12-16
Mira també les instruccions a:

[http://ubuntuforums.org/showpost.php?p=10749086&postcount=1](http://ubuntuforums.org/showpost.php?p=10749086&postcount=1)

Si tens problemes per seguir l'anglès o les explicacions, per aquí segur algú/na podrà donar una mà.

---

### Post by Jayhawker on 2011-12-16
Ostres! Un nou problem. Ara resulta que, inexplicablement, tampoc em funciona el WIFI al Windows i, per postres, no puc entrar a Ubuntu. La pantalla es queda lila i no passa d'aquí. Ahir, quan vaig tancar, funcionava tot tret del Wifi a Ubuntu. Què ha passat? Els de windows protegint-se?

Merci

---

### Post by wgarcia on 2011-12-16
Això nou sembla ara un problema de gràfica. Prova des de la pantalla que veus lila fer ALT-F1, i si s'obre una consola i et demana l'usuari i la clau dona-li. Un cop que et mostri la línia de la consola entra

```
sudo service lightdm restart
```

a veure si et deixa entrar un altre cop a l'Ubuntu. 

Quant al Wifi a Windows, aquí sí que anem perduts, fa temps que no remeno.

---

### Post by sordoman on 2011-12-18
Hola,

Pel tema driver del wifi, mira que tinguis instal.lat "firmware-b43-installer" o directament
```
sudo apt-get install firmware-b43-installer
```

No se per quina raó desde fa unes versións no s'activen sols.

sort

---

### Post by wgarcia on 2011-12-20
En aquest altre blog en català donen una altra solució per a una targeta que deu ser semblant a la teva, però és el model 4312 en comptes de 4311. Però per provar que no quedi:

[http://anotacionsalmarge.wordpress.com/2011/12/20/problema-amb-lactualitzacio-del-paquet-network-manager-0-9-1-90-0ubuntu5-1-el-wifi-no-funciona-amb-la-targeta-broadcom-bcm4312/](http://anotacionsalmarge.wordpress.com/2011/12/20/problema-amb-lactualitzacio-del-paquet-network-manager-0-9-1-90-0ubuntu5-1-el-wifi-no-funciona-amb-la-targeta-broadcom-bcm4312/)

---

### Post by Jayhawker on 2011-12-20
Merci pel teu gran interès. Miro a veure què passa?

> **wgarcia said:**
> En aquest altre blog en català donen una altra solució per a una targeta que deu ser semblant a la teva, però és el model 4312 en comptes de 4311. Però per provar que no quedi:

[http://anotacionsalmarge.wordpress.com/2011/12/20/problema-amb-lactualitzacio-del-paquet-network-manager-0-9-1-90-0ubuntu5-1-el-wifi-no-funciona-amb-la-targeta-broadcom-bcm4312/](http://anotacionsalmarge.wordpress.com/2011/12/20/problema-amb-lactualitzacio-del-paquet-network-manager-0-9-1-90-0ubuntu5-1-el-wifi-no-funciona-amb-la-targeta-broadcom-bcm4312/)

---

### Post by Jayhawker on 2011-12-20
Mercei pel teu gran interès. Miro a veure què passa.

> **wgarcia said:**
> En aquest altre blog en català donen una altra solució per a una targeta que deu ser semblant a la teva, però és el model 4312 en comptes de 4311. Però per provar que no quedi:

[http://anotacionsalmarge.wordpress.com/2011/12/20/problema-amb-lactualitzacio-del-paquet-network-manager-0-9-1-90-0ubuntu5-1-el-wifi-no-funciona-amb-la-targeta-broadcom-bcm4312/](http://anotacionsalmarge.wordpress.com/2011/12/20/problema-amb-lactualitzacio-del-paquet-network-manager-0-9-1-90-0ubuntu5-1-el-wifi-no-funciona-amb-la-targeta-broadcom-bcm4312/)

---

### Post by Jayhawker on 2011-12-20
Merci per l'interès. Se m'ha instal·lat, però parcialment,perquè hi ha un flashpluguin que no sé com ontenir-lo-

Diu això:

download failed
The Flash plugin is NOT installed.
dpkg: s'ha produït un error en processar flashplugin-downloader:i386 (--configure):
 el subprocés s'ha insta&#320;lat el script post-installation retornà el codi d'eixida d'error 1
dpkg: problemes de dependències impedeixen la configuració de flashplugin-installer:
 flashplugin-installer depèn de flashplugin-downloader (>= 11.0.1.152ubuntu1); tot i així:
  El paquet flashplugin-downloader no està insta&#320;lat.
  El paquet flashplugin-downloader:i386 encara no està configurat.
dpkg: s'ha produït un error en processar flashplugin-installer (--configure):
 problemes de dependències - es deixa sense configurar
S'està configurant b43-fwcutter (1:014-9)…
No s'ha escrit cap informe perquè el missatge d'error indica que és un error consequent de una fallida anterior.

Saps com solucionar-ho?

Merci de nou

> **sordoman said:**
> Hola,

Pel tema driver del wifi, mira que tinguis instal.lat "firmware-b43-installer" o directament
```
sudo apt-get install firmware-b43-installer
```

No se per quina raó desde fa unes versións no s'activen sols.

sort

---

### Post by Jayhawker on 2011-12-20
He hagut de reinstal·lar tot. Però, en fi,el problema del Wifi a l'Ubuntu persisteix. Pot ser un handicap que es trati d'un HP Pavillion? Perquè els altres routers del voltant sí que els enxampa.

Merci per teu gran interès

> **wgarcia said:**
> Això nou sembla ara un problema de gràfica. Prova des de la pantalla que veus lila fer ALT-F1, i si s'obre una consola i et demana l'usuari i la clau dona-li. Un cop que et mostri la línia de la consola entra

```
sudo service lightdm restart
```

a veure si et deixa entrar un altre cop a l'Ubuntu. 

Quant al Wifi a Windows, aquí sí que anem perduts, fa temps que no remeno.

---

### Post by wgarcia on 2011-12-20
L'error que et surt a dalt, prova si s'arregla amb aquestes dues comandes a una terminal:

```
sudo apt-get install -f
sudo dpkg --configure -a

```

---

### Post by Jayhawker on 2011-12-20
He solucionat això del flahplugin. Merci. Però tot continua igual. El WIFI detecta d'altres routers tret del meu. Tampoc és que pugui navegar pels que són oberts, però els detecta, que ja és alguna cosa. Per què no troba el meu?

Merci per l'interès.

> **wgarcia said:**
> L'error que et surt a dalt, prova si s'arregla amb aquestes dues comandes a una terminal:

```
sudo apt-get install -f
sudo dpkg --configure -a

```

---

### Post by wgarcia on 2011-12-21
Però has pogut també instal·lar firmware-b43-installer ?

---

### Post by Jayhawker on 2011-12-21
Si, si, a la terminal em diu que s'hi ha instal·lat, però segueixo sense detectar el meu propi router i, en canvi, en detecto d'altres. Els de codi obert, però, tampoc em permeten navegar ni fer res, potser perquè el senyal es fluix.

Merci. Alguna altra idea? 

> **wgarcia said:**
> Però has pogut també instal·lar firmware-b43-installer ?

---

### Post by wgarcia on 2011-12-21
Continua sense sortir en "Controladors addicionals"?

---

### Post by Jayhawker on 2011-12-21
¿Controladors addicionals? Perdona però no et segueixo. Vols dir en el "més" que hi ha a sota de la llista de routers detectats i que dóna pas a una altra llista de routers detectats? Si és així, no, no em surt en aquesta llista tampoc. Tot com sempre. 

salutacions 

> **wgarcia said:**
> Continua sense sortir en "Controladors addicionals"?

---

### Post by wgarcia on 2011-12-22
Em refereixo a clicar a la icona de més a la dreta del plafó superior, escollir l'opció "Paràmetres del sistema", aquí buscar "Maquinari" -> "Controladors addicionals".

---

### Post by Jayhawker on 2011-12-22
Ah!, si, si, en instal·lar aquesta versió d'Ubuntu va ser gairebé del primer que vaig fer. A més, m'indica que s'estan usant correctament. No sé si és un problema amb el meu router en específic, o Telefònica, que potser no té cap interès en facilitar la feina a Linux. De tota manera, sospito que entre els routers detectats n'hi ha que són de Telefònica. O potser és la marca del router la que no facilita la feina. Per si de cas, el meu router és un Comtrend CT 536+. Per si serveix d'alguna cosa. 

Salut i merci. 

> **wgarcia said:**
> Em refereixo a clicar a la icona de més a la dreta del plafó superior, escollir l'opció "Paràmetres del sistema", aquí buscar "Maquinari" -> "Controladors addicionals".

---

### Post by sordoman on 2011-12-22
Hola,

Perdona potser sera una estupidesa, pero al final de la llista de conexions, posa "Més xarxes" si poses el ratolí a sobre et sortiran mes xarxes, poter la teva esta allà

Sort

---

### Post by Jayhawker on 2011-12-22
Merci pel suggeriment, però, òbviament, ja ho havia provat. A "més xarxes" tampoc hi apareix. 

Salut

****> **sordoman said:**
> Hola,

Perdona potser sera una estupidesa, pero al final de la llista de conexions, posa "Més xarxes" si poses el ratolí a sobre et sortiran mes xarxes, poter la teva esta allà

Sort

---

### Post by kimet on 2011-12-22
T'aseguro que no hi ha cap problema amb aquest router i linux.
-Has entrat a la pàgina de configuració del router per comprovar que tot està bé? 
-Contrasenya? 
-Tipus d'encriptació?


Salud.

---

### Post by Jayhawker on 2011-12-22
Tot en ordre. Però a més, el WiFi me l'hauria de detectar igualment, ¿no? indistintament que hagués o no inclòs les dades del router. Això és el que passa amb els que detecto, dels qual en desconec les claus, però això no evita que els detecti l'aparell. D'aquí la meva perplexitat. 

Salut

> **kimet said:**
> T'aseguro que no hi ha cap problema amb aquest router i linux.
-Has entrat a la pàgina de configuració del router per comprovar que tot està bé? 
-Contrasenya? 
-Tipus d'encriptació?


Salud.

---

### Post by kimet on 2011-12-22
Ho deia perqué el wifi pot estar deshabilitat, amb filtre per mac o alguna cosa així.
Has provat a resetejar el router a la seva configuració per defecte i treure la contrasenya només per veure si et conecta?

---

### Post by Jayhawker on 2011-12-22
El wifi em funciona amb Windows, però amb Linux no m'ha funcionat mai. Tampoc en d'altres versions d'Ubuntu. El que passa és que ara sí m'interessa que em funcioni perquè trobo que aquesta versió 11/10 està molt i molt bé i seria feliç bandejant Windows tant com pugui.

Tot això del filtre que em comentes, no en tinc ni idea. Com es pot saber si hi ha cap filtre? I com treus la clau per tal de deixar-lo lliure? Quant a rebotar-lo, no m'atreveixo, perquè no fa gaire el vaig apagar i quan vaig voler encendre'l no va voler. Llavors vaig trucar a Telefònica i me'l van activar a distància. 

Merci per l'interès. 



> **kimet said:**
> Ho deia perqué el wifi pot estar deshabilitat, amb filtre per mac o alguna cosa així.
Has provat a resetejar el router a la seva configuració per defecte i treure la contrasenya només per veure si et conecta?

---

### Post by kimet on 2011-12-22
Es extrany, si el veus amb windows l'hauries de veure amb ubuntu si amb aquest veus altres routers.

Escriu 192.168.1.1 a la barra del navegador i et surtira un dialeg per posar la contrasenya si està habilitada, desde aquí pots configurar el router. o resetejar-lo sense apagar-lo. (desde windows o conectat amb cable).

També pots provar algún altre gestor de xarxes wicd o wifi-radar...

---

### Post by Jayhawker on 2011-12-22
Això de què informes sembla molt interessant. Quan dius contrasenya, et refereixes a la clau que cal posar per poder usar un WiFI protegit? És a dir, les xifres i lletres que tot router té a sota?

Pots ampliar una mica la informació? Vull dir, no hi ha perill que se't descodifiqui el router i després no hi hagi manera de recodificar-lo de nou?

Merci. 


> **kimet said:**
> Es extrany, si el veus amb windows l'hauries de veure amb ubuntu si amb aquest veus altres routers.

Escriu 192.168.1.1 a la barra del navegador i et surtira un dialeg per posar la contrasenya si està habilitada, desde aquí pots configurar el router. o resetejar-lo sense apagar-lo. (desde windows o conectat amb cable).

També pots provar algún altre gestor de xarxes wicd o wifi-radar...

---

### Post by kimet on 2011-12-23
> Quan dius contrasenya, et refereixes a la clau que cal posar per poder usar un WiFI protegit? 
No, em refereixo a la contrasenya per entrar a la pàgina de configuracióo del router.
> 
no hi ha perill que se't descodifiqui el router i després no hi hagi manera de recodificar-lo de nou?
No, sempre es pot tornar a resetejar a la configuració per defecte. La clau wifi per defecte, la que hi ha al darrere..., s'hauria de canviar sempre.

[http://www.movistar.es/on/io/es/atencion/soporte_tecnico_y_averias/internet/adsl/modems/inalambricos/comtrend_ct536/ManualFabricanteComtrendCT536+.pdf]("http://www.movistar.es/on/io/es/atencion/soporte_tecnico_y_averias/internet/adsl/modems/inalambricos/comtrend_ct536/ManualFabricanteComtrendCT536+.pdf")

---

### Post by Jayhawker on 2011-12-23
Merci. Ja hi he entrat, però a banda de provar de fer-ho "hidden" , sense resultat, no veig que més es pot canviar. Hi ha moltes coses que no se de què van. El filtre MAC està desactivat. L'AP Mode està en Access Point, però hi ha la possibilitat de canviar-ho a Wireless Bridge. Brideg restrict està desactivat. En l'apartat diagnèstic, El Test ATM OAM F5 segment ping: surt com a Fail; també són Fail el Test ATM OAM F5 end-to-end ping: y el Ping default gateway:. Tinc desconnectat el SSH del WAN però no del LAN, i el mateix amb el TFTP. El SNMP del WAN m'ha sortit desconnectat i connectat en diferents moments. 

En fi, tot això em sona a xinès. Alguna idea?

Ah! També he volgut canviar el password però quan vull "acceptar" em surt un pop up que em diu que el passwor antic no és vàlid, i jo em pregunto com és això si és el de sempre. 

Quin enrenou. Merci 


> **kimet said:**
> No, em refereixo a la contrasenya per entrar a la pàgina de configuracióo del router.

No, sempre es pot tornar a resetejar a la configuració per defecte. La clau wifi per defecte, la que hi ha al darrere..., s'hauria de canviar sempre.

[http://www.movistar.es/on/io/es/atencion/soporte_tecnico_y_averias/internet/adsl/modems/inalambricos/comtrend_ct536/ManualFabricanteComtrendCT536+.pdf]("http://www.movistar.es/on/io/es/atencion/soporte_tecnico_y_averias/internet/adsl/modems/inalambricos/comtrend_ct536/ManualFabricanteComtrendCT536+.pdf")

---

