---
title: "Ubuntu 10.10 connexió internet"
date: 2011-03-02
forum: Catalan Team
---

### Post by jutipiris on 2011-03-02
Vaig instal·lar-me l'Ubuntu 10.10 al meu ordinador, una vegada instal·lat (sense apagar-lo) vaig executar [les següents comandes]("http://www.genbeta.com/linux/he-instalado-ubuntu-1010-y-ahora-que") des del terminal:

> sudo apt-get update
sudo apt-get -y dist-upgrade
sudo apt-get -y install ubuntu-restricted-extras


Fins aquí tot bé. Com que ja feia estona que l'ordinador em demanava de reiniciar-lo el vaig reiniciar. A partir de llavors ja no he pogut connectar-me més a internet: amb les comandes des del terminal no es poden descarregar fitxers (els processos fallen) i el navegador Mozilla Firefox tampoc no es connecta a cap pàgina

He intentat configurar la connexió tal com diuen a [aupatic.com]("http://aupatic.com/configurar-internet-en-ubuntu-10-10/") amb les meves dades:

Adreça IP: 192.168.1.2
Màscara de xarxa: 255.255.255.0
Passarel·la: 192.168.1.254
Servidor DNS: 198.168.1.100 o 8.8.8.8

Tinc una connexió a internet mitjançant ONO i em connecto a través de ethernet mitjançant un router D-LINK

Però res de tot això no m'ha funcionat. **Només em funciona la connexió quan acabo de reinstal·lar el sistema operatiu i encara no he apagat l'ordinador**. Amb l'Ubuntu 10.04 no m'havia calgut fer res més que configurar-ho tal com fa [aupatic.com]("http://aupatic.com/configurar-internet-en-ubuntu-10-10/").

La configuració de l'ADSL mitjançant "pppoeconf" ([Conexión a Internet]("http://www.guia-ubuntu.org/index.php?title=Configuraci%C3%B3n_de_red")) no sé si em pot funcionar. 

No ho acabo d'entendre tot plegat. Com diu [PabloX]("http://www.glatelier.org/2010/04/how-to-configurar-una-conexion-vpn-en-ubuntu/"): "Configurar una conexión VPN en GNU/Linux es de ese tipo de cosas en las que **parece más que estuvieras tratando de lanzar un hechizo vudú que tratando con un computador**."

Em podeu ajudar? Gràcies!

---

### Post by kimet on 2011-03-02
```
Adreça IP: 192.168.1.2
Màscara de xarxa: 255.255.255.0
Passarel·la: 192.168.1.254
Servidor DNS: 198.168.1.100 o 8.8.8.8
```

Em sembla que no està bé.

Adressa ip --> adressa del teu ordinador.
passarel.la ---> adressa del router
Servidor DNS ---> adressa del router(si te les nona el router) si no,   DNS del teu proveidor o qualsevol altre.

Mira la configuració del router. Si el router et dona direccions per DHCP t'hauria de funcionar sel.lecionant DHCP

---

### Post by akyra on 2011-03-02
Hola Jutpiris.

A veure si trobem alguna cosa:
 1er.- Si tens DHCP no hauries de configurar res. Quina adreça t'ha donat? Fes des de la consola "ifconfig" (sense cometes), quin resultat et dóna?.
 2on.- Pots connectar-te al router i veure la seva interficie de configuració? Normalment es pot fer des del navegador però has de saber l'adreça del router (normalment tenen la 192.168.0.1 o la 192.168.1.1). Aquí podràs veure tot el relatiu a l'adreçament del router.

 3er. Si ho fas manual, fes el que et diu en kimet, però aclareix abans quina adreça té el router. La teva a de ser la mateixa que del router canviant els 3 darrers numeros (192.168.0.x, o 192.168.1.x).

A veure quins resultats et dóna i que més podem fer.

Salutacions

---

### Post by jutipiris on 2011-03-02
Com dirien els Manel: "m'ha costat Déu i ajuda arribar fins aquí", però al final s'ha solucionat el problema: m'he connectat al router a través del navegador mitjançant l'adreça IP d'aquest: 192.168.1.1

[IMG]http://farm6.static.flickr.com/5296/5492564248_47e9c79cd7.jpg[/IMG]

[IMG]http://farm6.static.flickr.com/5057/5492008151_464bb7798d.jpg[/IMG]

Que el DHCP Server estés "Running" no sé si volia dir que tinc o no tinc DHCP. He fet tres intents definint el mètode de connexió VPN:
[LIST=1]
[*]"Automàtic DHCP" no ha funcionat
[*]"Només adreces (DHCP) automàtiques" no ha funcionat
[*]**"Manual" ha funcionat**:
[/LIST]
```
Adreça IP: 192.168.1.2
Màscara de xarxa: 255.255.255.0
Passarel·la: 192.168.1.1
Servidor DNS: 8.8.8.8
```

Quina alegria quan em van dir anem a la casa del Senyor... ai, no, això no va aquí!!!

Moltes gràcies, kimet i akyra, per la vostra ajuda (i al David i al seu amic linuxero també ;-)!!!

---

### Post by akyra on 2011-03-03
El servidor DHCP running vol dir que et pot donar una adreça IP automàticament si així o tens configurat en l'ordinador.

El que no entenc es l'adreça de DNS 8.8.8.8, si tinguesis algun problema posa la del router, 192.168.1.1

M'alegro que s'hagi solucionat.

La conexió VPN tampoc hauria de donar gaires problemes si saps quin protocol estàs utilitzant i la configuració que necessites, jo ja fa temps que l'utilitzo i no tinc problemes.
Si tinguessis problemes amb la VPN al canviar de versió d'Ubuntu, normalment es resolia amb l'anell de claus.

Salutacions.

---

### Post by jutipiris on 2011-03-04
El DNS me'l va suggerir un linuxero perquè es veu que [és un DNS públic de Google]("http://www.pateandopiedras.com/2011/01/8-8-8-8-y-8-8-4-4-google-lanza-servicios-de-dns-publicas-de-miedo/").

Amb el tema VPN no hi entro perquè em penso que encara em perdré més.

Moltes gràcies, akyra!

---

