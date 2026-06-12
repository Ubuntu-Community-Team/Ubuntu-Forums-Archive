---
title: "Fer funcionar server local per joomla"
date: 2015-03-06
forum: Catalan Team
---

### Post by simfomet on 2015-03-06
Hola,

    estic utilitzant la darrera versió de xubuntu i voldria instal·lar un server en local per instalar-hi un joomla i construir una web. En primer terme vaig instal·lar xampp però veient que els permisos per escriure a la carpeta opt/htpdocs eren un problema vaig trobar la següent info que copio literalment:

[I]te sugiero que no uses XAMP, aunque ese no es el objetivo de tu pregunta, pero te explico porqué...
Linux ya trae predeterminadamente todo como para que montes un servidor  web en tu máquina, así que es mejor lo que trae él que usar otras  cosas... Para eso solo tienes que acceder al Gestor de Paquetes Synaptic  e instalas **mysql-server**, **apache** y **phpmyadmin** ellos solos se encargan de resolver las dependencias. Luego accedes normalmente a tu locahost y te saldrá una página que dice **It works**... que está en **/var/www/**  y a la cual solo puedes acceder a ver, porque está bajo permisos de  root, entonces lo que puedes hacer es en tu Home (/home/usuario/) creas  una carpeta donde guardarás todos tus proyectos y lo que haces es hacer  links desde **/var/www/ **hacia esa carpeta y supongamos que la nombras webserver, lo que tienes que hacer es esto desde un Terminal estando en **/var/www/** y teniendo previamente creada una carpeta en /home/usuario/webserver/misitio/
 [/I]* Código: *[LEFT][I]sudo ln -s /home/usuario/webserver/misitio/ misitio
// aquí te va a pedir el password de root
[/I][/LEFT]

[I]Esto te creará un link por el cual podrás acceder vía web de esta manera [http://localhost/misitio](http://localhost/misitio)
También podrás acceder a phpmyadmin normalmente [http://localhost/phpmyadmin](http://localhost/phpmyadmin)[/I]

El cas es que no funciona. A més, al instal·lar phpmyadmin ja m'ha donat un error que ara queda reflexat quan hi entro amb el missatge *La connexió de l'usuari de control ha fallat, tal com està definida ara a la configuració.* No entenc massa que vol dir i no sé què fer.

---

### Post by wgarcia on 2015-03-09
Si bé és veritat que es pot instal·lar tot el que es necessita des de la línia d'ordres de linux, eines com xampp et faciliten la instal·lació.

Per veure què està passant, hauries d'indicar exactament què has instal·lat, què és el que està funcionant (s'estan executant els servidors apache i mysql?) i quins errors et surten, per exemple quan entres [http://localhost](http://localhost) al navegador d'Internet, què surt?

---

### Post by simfomet on 2015-03-09
He instal·lat ***mysql-server**, **apache**2 i **phpmyadmin***. Si poso al navegador senzillament localhost m'apareix la pantalla de It Works!!! prova doncs que apache funciona. Si poso localhost/phpmyadmin m'apareix la pantalla d'usuari i pass per entrar-hi, per tant també tot correcte. Crec que l'error està en aquest pas del que he fet tal com posava en l'anterior post:

[I]lo que puedes hacer es en tu Home (/home/usuario/) creas  una carpeta  donde guardarás todos tus proyectos y lo que haces es hacer  links  desde **/var/www/ **hacia esa carpeta y supongamos que la nombras webserver, lo que tienes que hacer es esto desde un Terminal estando en **/var/www/** y teniendo previamente creada una carpeta en /home/usuario/webserver/misitio/
 [/I]* Código: *[LEFT][I]sudo ln -s /home/usuario/webserver/misitio/ misitio
// aquí te va a pedir el password de root

[/I]Perquè si poso al navegador [http://localhost/elmeulloc](http://localhost/elmeulloc) m'apareix:**Not Found**

 The requested URL /simfonia was not found on this server.
 [HR][/HR] Apache/2.4.10 (Ubuntu) Server at localhost Port 80

[/LEFT]

---

### Post by wgarcia on 2015-03-10
D'acord, fins aquí tot bé. El phpmyadmin deixa'l a part de moment, suposo que el que t'interessa és instal·lar el jomla. El phpmyadmin sols et farà falta si vols remenar directament a la base de dades. 

On has instal·lat el joomla? Si has deixat tot per defecte, el directori on apunta l'apache és /var/www. Ara mateix aquí sols hi ha un fitxer que es diu index.html que és això de "It works!" que veus. Hauries dons t'instal·lar el joomla a aquest directori.

---

### Post by simfomet on 2015-03-10
Primer que tot gràcies per l'ajuda. Precisament a /var/www és on tinc posada una carpeta amb el nom de simfonia on dins hi ha tots els arxius de joomla i amb la carpeta installation corresponent per fer la instal·lació. I res, hem surt el 404 not found
El que passa és que pels permisos de la carpeta var havia seguit aquell tutorial per fer un enllaç a la carpeta d'usuari per no tenir problemes a l'hora de copiar i moure arxius. Vist que no me'n sortia pensava que posant el joomla a la carpeta /var/www ho solucionaria però res.

---

### Post by wgarcia on 2015-03-11
Potser si el joomla és a una subcarpeta "simfonia" l'apache no el troba, de fet està trobant l'index.html de /var/www. Llavors tens diverses opcions: 1) configurar l'apache perquè la carpeta de documents sigui "/var/www/simfonia" i no "/var/www" 2) moure tot el que hi ha a "simfonia" a /var/www. 

Això de l'enllaç simbòlic serviria si poses tot el que hi ha simfonia al teu home o algun altre lloc (em sembla que ja ho has fet), esborres la carpeta /var/www, i crees un enllaç simbòlic per substituir aquesta carpeta que apunti a on tens el que tenies a simfonia:

```
ls -s /home/pepitu/simfonia /var/www
```

potser amb "sudo" perquè pugui escriure a "/var".

La navegació en aquest seria entrant directament "localhost" al navegador no "localhot/simfonia".

---

### Post by simfomet on 2015-03-11
Finalment he pogut. Ja veig que vaig una mica perdut encara amb tot això en linux. Si poso la carpeta simfonia dins /var/www/html/ ja hem detecta la instal·lació de joomla. Jo creia que posant el joomla a /var/www/ i llavors al navegador localhost/lamevacarpeta ja ho detectava com a windows però ja veig que és una mica diferent.

El que no trobo gens cómode és que no permeti escriure ni modificar arxius en cap carpeta que no sigui la d'usuari el sistema. Has d'obrir una terminal i obrir l'explorador d'arxius com a root.

---

### Post by wgarcia on 2015-03-12
M'alegra que ho hagis pogut solucionar. És d'utilitat que marquis el fil com a "Solved" amb la pestanya que tens quan edites el teu primer missatge. 

Sí que pots escriure on vulguis, però has de validar-te com a superusuari. Linux està més protegit, pensat perquè molts usuaris treballin a la mateixa màquina, i sols els que tinguin privilegis d'administrador poden tocar el sistema. Altres sistemes operatius són iguals però no són tan curosos amb la protecció. 

De totes maneres a Linux també convé aprendre a treballar amb la terminal (també anomenada la "consola").  Dins de la línia d'ordres pots executar qualsevol ordre com a administrador anteposant-li la clàusula "sudo". Per exemple per copiar el directori "simfonia" a "/var/www/ ho pots fer amb l'ordre:

```
sudo cp /home/elmeuusuari/simfonia /var/www
```

Et demanarà la clau d'usuari i ho farà. Si vols obrir un programa amb interfície gràfic com a superusuari simplement escrius "gksudo" en comptes de "sudo". Els sistemes Linux solen tenir un usuari que es diu "root" i és l'administrador, però per seguretat sistemes com Debian i els seus derivats, l'Ubuntu n'és un, han eliminat aquest usuari i implementat allò de "sudo".

També òbviament li pots donar al teu usuari permisos per escriure a les carpetes de sistema, però això ho trobo més perillós perquè sense voler et pots carregar alguna cosa.

---

