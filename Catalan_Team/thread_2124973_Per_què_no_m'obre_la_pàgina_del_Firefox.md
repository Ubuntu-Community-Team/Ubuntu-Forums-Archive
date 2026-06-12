---
title: "Per què no m'obre la pàgina del Firefox?"
date: 2013-03-12
forum: Catalan Team
---

### Post by rosa d'abril on 2013-03-12
Hola, 
Treballo de fa temps amb l'Ubuntu 12.04 sense problemes. Fa dies, però, que, en una biblioteca pública, el sistema em reconeix i se'm connecta immediatament a una xarxa Wi-Fi però en canvi no m'obre la pàgina del Firefox i, per tant, no em deixa connectar a Internet (amb la consegüent emprenyada).
Què s'hi pot fer?
Salut!

---

### Post by albandy on 2013-03-12
Igual es que a la biblioteca i ha un portal captiu. Quan obres el Firefox i poses qualsevol adreça no et re-dirigeix com a una plana d'autenticació?

---

### Post by rosa d'abril on 2013-03-12
No, gràcies, no és aquest el problema. Es tracta d'una biblioteca pública però no de la DIBA. Insisteixo, la xarxa me la reconeix i en clicar damunt la icona em diu "Connectat", però no m'obre el navegador.
Salut!

---

### Post by wgarcia on 2013-03-13
Però dues preguntes: 1) Et podies connectar i de sobte ja no et pots connectar més? 2) Hi ha altra gent que es connecta sense problema amb la mateixa xarxa wifi?

---

### Post by albandy on 2013-03-13
Prova a obrir una consola i posa això.
```

ping -c 10 www.google.es

```
la resposta hauria de ser la de la imatge adjunta:
[ATTACH=CONFIG]240114[/ATTACH]

---

### Post by rosa d'abril on 2013-03-13
Hola, 
Gràcies a tots dos. Contesto per ordre: 
A Wgarcia: fins fa pocs dies podia connectar-me sense problemes, de manera que potser la causa sigui alguna actualització. Per altra banda, al meu voltat, dominat pel Windows, tothom es pot connectar.
A Albandy: de seguida que pugui, provaré el que em proposes i ja te'n diré el resultat.
Gràcies novament.

---

### Post by rosa d'abril on 2013-03-13
Albandy,
Li he escrit a la consola el que em suggeries i la resposta ha estat:
ping: unknown host [www.google.es](www.google.es)
I una cosa encara més inquietant és que, potinejant pel terminal, he descobert que quan li escric el "su" i em demana la contrasenya, no me l'admet. I juro que li escric bé! O almenys la mateixa que li escric en iniciar la sessió. 
Jo flip.

---

### Post by wgarcia on 2013-03-14
El que et passa amb "su" és normal. Als sistemes Ubuntu (i Debian, penso), el "su" no funciona directament, perquè no hi ha un usuari "root" definit, per això hi ha el "sudo" perquè puguis fer comandes com superusuària però específicament pel que necessites. 

Quant al problema de la connexió, prova si et pots connectar a pàgines usant el seu número IP. A veure, anem a buscar alguna..., per exemple el diari ARA té l'adreça IP: 212.73.198.167. Prova entrar aquest número exactament tal qual al navegador. Si es pot connectar voldrà dir que és un problema del "servidor de noms", és a dir el servidor que tradueix "www.ara.cat" a aquest número. Hi haurà un problema que fa que el teu sistema no s'estigui connectant al servidor de noms.

---

### Post by albandy on 2013-03-14
> **rosa d'abril said:**
> Albandy,
Li he escrit a la consola el que em suggeries i la resposta ha estat:
ping: unknown host [www.google.es](www.google.es)
I una cosa encara més inquietant és que, potinejant pel terminal, he descobert que quan li escric el "su" i em demana la contrasenya, no me l'admet. I juro que li escric bé! O almenys la mateixa que li escric en iniciar la sessió. 
Jo flip.

un cop connectada, prova a afer això:
sudo dhclient wlan0

i després mira si pots navegar. Si és el cas, es molt possible que tinguis les adreces ip configurades de forma manual.

---

### Post by rosa d'abril on 2013-03-14
Gràcies, novament, Albandy. Ho provaré aquesta tarda i ja t'explicaré.

---

### Post by rosa d'abril on 2013-03-14
> **wgarcia said:**
> El que et passa amb "su" és normal. Als sistemes Ubuntu (i Debian, penso), el "su" no funciona directament, perquè no hi ha un usuari "root" definit, per això hi ha el "sudo" perquè puguis fer comandes com superusuària però específicament pel que necessites. 

Quant al problema de la connexió, prova si et pots connectar a pàgines usant el seu número IP. A veure, anem a buscar alguna..., per exemple el diari ARA té l'adreça IP: 212.73.198.167. Prova entrar aquest número exactament tal qual al navegador. Si es pot connectar voldrà dir que és un problema del "servidor de noms", és a dir el servidor que tradueix "www.ara.cat" a aquest número. Hi haurà un problema que fa que el teu sistema no s'estigui connectant al servidor de noms.

Pel que fa al "su", tota la raó, gràcies.
Quant al problema de connexió, li he introduït el número tal qual i, efectivament, al cap d'una estona ho ha convertit en "[www.ara.cat]("http://www.ara.cat/")", però això no ha evitat l'anunci fatal: "S'ha produït un problema en carregar la pàgina..." i que no m'obrís el Firefox

Gràcies de totes maneres

---

### Post by rosa d'abril on 2013-03-14
> **albandy said:**
> un cop connectada, prova a afer això:
sudo dhclient wlan0

i després mira si pots navegar. Si és el cas, es molt possible que tinguis les adreces ip configurades de forma manual.

He fet el que em deis. Resposta? 
*RTNETLINK answers: File exists  *
 Pero torno a executar el Firefox i continua sense obrir-se'm
En fi, què faig? Ni que sigui alguna solució "a la brava". Desinstal·lo tot l'Ubuntu?

---

### Post by albandy on 2013-03-15
> **rosa d'abril said:**
> He fet el que em deis. Resposta? 
*RTNETLINK answers: File exists  *
 Pero torno a executar el Firefox i continua sense obrir-se'm
En fi, què faig? Ni que sigui alguna solució "a la brava". Desinstal·lo tot l'Ubuntu?

Un cop connectada, mostran's el resultat de realitzar les comandes següents:

sudo iwconfig wlan0
sudo ifconfig wlan0
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf

---

### Post by rosa d'abril on 2013-03-15
Entesos, ho provaré i us diré alguna cosa. 
Ja no sé com donar-vos les gràcies.

---

### Post by rosa d'abril on 2013-03-16
> **albandy said:**
> Un cop connectada, mostran's el resultat de realitzar les comandes següents:

sudo iwconfig wlan0
sudo ifconfig wlan0
route -n
cat /etc/network/interfaces
cat /etc/resolv.conf

Ve-t'ho aquí,  veure què et diu. Per a mi seria com consultar pòsits del cafè o vísceres d'aus:
**sudo iwconfig wlan0**
   
 wlan0     IEEE 802.11bgn  ESSID:"BIBLIOTECA ATENEU (Jujol)"   
           Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:6B:29:19    
           Bit Rate=54 Mb/s   Tx-Power=14 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:off  
           Link Quality=60/70  Signal level=-50 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:57   Missed beacon:0  
 

 **sudo ifconfig wlan0**

  wlan0     Link encap:Ethernet  HWaddr 00:1e:64:05:13:e2   
           inet addr:192.168.1.126  Bcast:192.168.1.255  Mask:255.255.255.0  
           inet6 addr: fe80::21e:64ff:fe05:13e2/64 Scope:Link  
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1  
           RX packets:636 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:174 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:107473 (107.4 KB)  TX bytes:21732 (21.7 KB)  
 

 **route -n**

  Kernel IP routing table  
 Destination     Gateway         Genmask         Flags Metric Ref    Use Iface  
 0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0  
 169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0  
 192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0  
   
 
**cat /etc/network/interfaces**

  auto lo  
 iface lo inet loopback  
 

    
 **cat /etc/resolv.conf  **

  # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)  
 #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN  
 nameserver 127.0.0.1

---

### Post by rosa d'abril on 2013-03-17
Una nova aportació al tema. 
Ahir vaig anar les[SIZE=2][FONT=Arial] "P[/FONT][/SIZE][FONT=Arial][SIZE=2][FONT=Arial]referències” del Firefox, que [SIZE=2]con[SIZE=2]tinuav[SIZE=2]a sense obrir-se'[SIZE=2]m, vaig [/SIZE][/SIZE][/SIZE][/SIZE]clic al botó “Avançat” i després, a  la pestanya “Xarxa”, [SIZE=2]e[/SIZE]l botó “Paràmetres”. Vaig veure que tenia seleccionada l'opció [/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Arial]“Detecta automàticament els paràmetres del servidor intermediari per aquesta xarxa”. [SIZE=2]Per [SIZE=2]provar[SIZE=2], vaig c[SIZE=2]anviar la selecció per [/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Arial]l’opció “Utilitza els paràmetres del servidor intermediari del sistema”[SIZE=2], vaig reiniciar l'Equip i el [SIZE=2]F[SIZE=2]irefo[SIZE=2]x se'm va obrir sense cap problema.[SIZE=2] [SIZE=2][SIZE=2][SIZE=2][SIZE=2]Avui, però, en engegar l'ordinador he tornat a trobar-me a[SIZE=2]mb el problema inicial: es [SIZE=2]connect[SIZE=2]ava però no obria el navegador. De manera que he tornat a fer el mate[SIZE=2]ix que ahir però a la inversa: he des[SIZE=2]selec[SIZE=2]cionat [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Arial]l’opció “Utilitza els paràmetres del servidor intermediari del sistema”[SIZE=2], he seleccionat [/SIZE][/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Arial]“Detecta automàticament els paràmetres del servidor intermediari per aquesta xarxa”[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Arial][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2][SIZE=2] i, després de reini[SIZE=2]ciar-lo, ha funcionitat pe[SIZE=2]r[SIZE=2]fectament. [SIZE=2]Hi ha alguna manera d'entendre-ho? El cas és que d'una manera una mica lenta, tot s'ha de d[SIZE=2]ir,  aconsegueixo almenys navegar però no sembla una s[SIZE=2]ortida molt elegant. 
En fi, gràcies per tot, i si [SIZE=2]cap Sant Ubunta[SIZE=2]ire no [SIZE=2]fa més suggeriments, donaré el tem[SIZE=2]a pe[SIZE=2]r quasi [sol[SIZE=2]ved]
Salut![/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/SIZE][/FONT]  [FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by wgarcia on 2013-03-17
Sembla que la biblioteca té definit un "proxy", o sigui un "Servidor intermediari de xarxa". Això (no soc tècnic) és un sistema que permet que el contingut que accedeixen molts usuaris, si és el mateix, no s'hagi d'anar a buscar, cada cop que algú el consulta, tot de nou a Internet. Per exemple si hi ha 5 usuaris que accedeixen el mateix contingut d'un diari, aquest contingut queda en un "cau" i l'accés és més ràpid i no utilitza ample de banda extern sinó que sols es tràfic de xarxa interna. 

Ara bé, sembla que el Firefox i el teu sistema s'estan fent embolics amb l'accés "per proxy" (això vol dir que tot el tràfic va per aquesta via i no directament per Internet). A "Paràmetres de sistema -> Maquinari -> Xarxa" veuràs que hi ha una opció que posa "Servidor intermediari de xarxa". Això és el "proxy", pots provar de posar que el detecti automàticament si el tens a "manual", i al Firefox posar "Utilitza els paràmetres del servidor intermediari del sistema” i a veure si s'arregla definitivament.

---

### Post by rosa d'abril on 2013-03-18
He fet el que em deies, wgarcia, però en marcar l'Automàtic a Paràmetres/Xarxa em demana una URL de configuració, com veus a la imatge
[ATTACH=CONFIG]240326[/ATTACH]

---

### Post by wgarcia on 2013-03-19
I si no entres l'URL no ho accepta? Perquè sembla dir que si no ho entres ja ho buscarà...

---

### Post by albandy on 2013-03-19
Per descartar, prova això en un terminal:
wget [www.google.es](www.google.es)
si es baixa la plana de google no hi ha cap proxy.

---

### Post by rosa d'abril on 2013-03-19
> **wgarcia said:**
> I si no entres l'URL no ho accepta? Perquè sembla dir que si no ho entres ja ho buscarà...

En principi sembla que sí que ho accepta. A més, li dic que ho apliqui a tot el sistema. Però després tampoc no funciona: el Firefox continua sense obrir-se'm.

---

### Post by rosa d'abril on 2013-03-19
> **albandy said:**
> Per descartar, prova això en un terminal:
wget [www.google.es]("http://www.google.es")
si es baixa la plana de google no hi ha cap proxy.

Em contesta això, albandy:
   [FONT=Times New Roman]--2013-03-19 18:08:48--  [http://www.google.es/](http://www.google.es/) [/FONT]
 [FONT=Times New Roman]Resolent [www.google.es]("http://www.google.es") ([www.google.es]("http://www.google.es"))... 173.194.34.24, 173.194.34.31, 173.194.34.23, ... [/FONT]
 [FONT=Times New Roman]S'està connectant a [www.google.es]("http://www.google.es") ([www.google.es)|173.194.34.24|:80]("http://www.google.es)|173.194.34.24|:80")... conectat. [/FONT]
 [FONT=Times New Roman]HTTP: Petició enviada, esperant resposta... 200 OK [/FONT]
 [FONT=Times New Roman]Longitud: no especificat [text/html] [/FONT]
 [FONT=Times New Roman]S'està desant a: «index.html» [/FONT]
 
     [FONT=Times New Roman][ <=>                                   ] 11.448      --.-K/s   en 0,02s    [/FONT]
 
 [FONT=Times New Roman]2013-03-19 18:08:48 (597 KB/s) - s'ha desat «index.html» [11448]

[/FONT]

---

### Post by albandy on 2013-03-20
> **rosa d'abril said:**
> Em contesta això, albandy:
   [FONT=Times New Roman]--2013-03-19 18:08:48--  [http://www.google.es/](http://www.google.es/) [/FONT]
 [FONT=Times New Roman]Resolent [www.google.es]("http://www.google.es") ([www.google.es]("http://www.google.es"))... 173.194.34.24, 173.194.34.31, 173.194.34.23, ... [/FONT]
 [FONT=Times New Roman]S'està connectant a [www.google.es]("http://www.google.es") ([www.google.es)|173.194.34.24|:80]("http://www.google.es)|173.194.34.24|:80")... conectat. [/FONT]
 [FONT=Times New Roman]HTTP: Petició enviada, esperant resposta... 200 OK [/FONT]
 [FONT=Times New Roman]Longitud: no especificat [text/html] [/FONT]
 [FONT=Times New Roman]S'està desant a: «index.html» [/FONT]
 
     [FONT=Times New Roman][ <=>                                   ] 11.448      --.-K/s   en 0,02s    [/FONT]
 
 [FONT=Times New Roman]2013-03-19 18:08:48 (597 KB/s) - s'ha desat «index.html» [11448]

[/FONT]

OK no hi ha cap proxy.
Ves al firefox i selecciona "Sense proxy".

Si no funciona, es possible que tinguis algun problema al firefox. En plan ràpid tens dos opcions:
1. Eliminar el directori de configuració del firefox: rm -rf $HOME/.mozilla/firefox (ull que si no ho poses tal qual està aquí et pots carregar tot el teu home)
2. Fer servir un altre navegador com per exemple el chromium

---

### Post by rosa d'abril on 2013-03-20
Moltes gràcies a tots dos. No sé com expressar com de bé m'ha anat el vostre suport.

---

