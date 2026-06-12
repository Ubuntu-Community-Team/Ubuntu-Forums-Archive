---
title: "Amule amb ID baixa: on és el tallafocs?"
date: 2010-04-10
forum: Catalan Team
---

### Post by joaquimrubio on 2010-04-10
Karmic Koala. Router Sagem F@st 2404 de Orange.
Al router he obert els ports que tinc posats amb l'Amule pero em diu que el Kad és darrera un tallafocs i totes dues fletxetes són de color groc. 
No sé trobar el tallafocs del router.
No sé si cal fer quelcom més.

---

### Post by Daerun on 2010-04-10
Potser és cosa d'obrir els ports del propi Ubuntu, jo normalment també ho he de fer així.

---

### Post by papapep on 2010-04-10
L'Ubuntu, si no ho ha fet l'usuari administrador de l'ordinador, no té cap port tancat de manera predeterminada. Té l'iptables i l'ufw instal·lats, però sense cap regla definida.

---

### Post by Daerun on 2010-04-11
Ah, doncs jo alguna vegada he hagut d'obrir ports amb el Firestarter (no en sé de cap altra manera :P ) perquè amb els del router només no n'hi havia prou.

---

### Post by papapep on 2010-04-11
Aquí entra la meva frase anterior "si no ho ha fet l'usuari administrador de l'ordinador" :)

Firestarter no forma part de la instal·lació predeterminada del *ubuntu, per tant, el fet d'instal·lar-lo deu definir directives amb alguna restricció, que és el que tu després has de desfer.

---

### Post by kukat on 2010-04-12
A mi em passava una cosa semblant. 
Finalment, vaig insta&#320;&#320;ar l'emule amb el Wine....

[http://ubuntuforums.org/showthread.php?t=1351082](http://ubuntuforums.org/showthread.php?t=1351082)

Deu ser alguna cosa del Karmic amb alguns routers. Jo no ho vaig aconseguir d'altra forma.... :(

---

### Post by Daerun on 2010-04-12
No, però a mi el problema dels ports em passaba sense haber instal·lat el firestarter -crec... ara em fas dubtar :lol: - y precisament me l'instal·lava per solucionar-ho.

Val a dir que jo també em vaig acabar instal·lant l'emule amb wine. Definitivament amule té algun problema...

---

### Post by joaquimrubio on 2010-04-18
Jo havia fet servir l'amule i funcionaba perfectament amb el Hardy Heron, no crec que sigui un problema de l'amule, suposo que hi ha algún detall del router que no tinc ben configurat.

---

### Post by akyra on 2010-04-19
Jo sempre m'he trobat amb haver d'obrir els ports del router o modem, però també coincideixo que si no tens instal·lat el firestarter o el ufw, ubuntu està obert.
Per comprobar-ho pots fer un 
> sudo iptables -L
i el resulat hauria de ser:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

El que pot ser és que tinguis una ip dinamica i que t'hagi canviat. Mira-ho amb un "ifconfig" i veuràs quina ip et dóna.

Una cosa, pots posar pantallaços del Port forwading del router?

Ja diràs que tal et va.

Salutacions.

---

### Post by Daerun on 2010-04-20
Ah, veus, l'Akyra aqui ha dit una cosa en què no havia caigut: els problemes també poden venir perquè el router no et dóna una ip fixa dins la teva xarxa.

---

### Post by ICTINEU on 2010-04-25
I si et surt això: què es pot fer?, com veus faig servir el Gufw, perque el Firestarter, no el vaig conseguir dominar.
A l'enrutador, un Comtred, tinc i el firewall marcat com a desactivat, oberts els ports específics amb les IPs que m'hacostuma a donar 190.xxx.x.131,132,133. i les mateixes al Gufw.
Però tot i això fa el que vol, normalment em conecta am IDbaixa, però algun cop ho fa amb IDAlta, però tal com ve, se'n va. tinc activat DHCP i UpnP a Ubuntu 8.04. y faig servir la versió d'amule dels repositoris, es a dir la 2.2.4? pot ser?

---

### Post by akyra on 2010-04-28
Hola


El que primer faria seria:
1.- Comprova que l'adreça IP en el teu ordinador està oberta en el router/modem teu, o sigui que si el teu router és el 192.XXX.X.1 el que entra pel port 6666, estigui redirigit al teu ordinar: 190.xxx.x.131 port:6666.
Això explicaria que a vegades funciona, ja que si la teva adreça IP va canviant i no coincidis amb la que tens oberta en el router/modem, no funcionaria ja que ho estaries redigirint a una altre IP que no és la teva.

2.- Després he vist que en la sortida de iptables, et surt que la política per defecte es "DROP" o sigui que no deixes entrar res i no mostra que tinguis cap port obert.
Perquè no proves en el GUFW d'activar "Permet el transit entrant", tornes a fer un "sudo iptables -L" hi hauria de sortir la política per defecte com de INPUT com ACCEPT i així sortiràs de dubtes, o també podrias desactivar el GUFW i provar.

Salutacions

---

### Post by Satboy on 2010-04-29
> **akyra said:**
> Jo sempre m'he trobat amb haver d'obrir els ports del router o modem, però també coincideixo que si no tens instal·lat el firestarter o el ufw, ubuntu està obert.
Per comprobar-ho pots fer un 

i el resulat hauria de ser:


El que pot ser és que tinguis una ip dinamica i que t'hagi canviat. Mira-ho amb un "ifconfig" i veuràs quina ip et dóna.

Una cosa, pots posar pantallaços del Port forwading del router?

Ja diràs que tal et va.

Salutacions.

 Hola,
 Doncs a mi s'ha sortit aquesta parrafada:

 Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     tcp  --  192.168.0.1          anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  192.168.0.1          anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
DROP       all  --  anywhere             255.255.255.255     
DROP       all  --  anywhere             192.168.0.255       
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 
INBOUND    all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.0.192        192.168.0.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.0.192        192.168.0.1         udp dpt:domain 
ACCEPT     tcp  --  192.168.0.192        192.168.0.1         tcp dpt:domain 
ACCEPT     udp  --  192.168.0.192        192.168.0.1         udp dpt:domain 
ACCEPT     all  --  anywhere             anywhere            
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 
DROP       all  --  255.255.255.255      anywhere            
DROP       all  --  anywhere             0.0.0.0             
DROP       all  --  anywhere             anywhere            state INVALID 
OUTBOUND   all  --  anywhere             anywhere            
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.0.1          anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4662 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4662 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4671 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4671 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4242 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4242 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:4661 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:4661 
LSI        all  --  anywhere             anywhere            

Chain LOG_FILTER (5 references)
target     prot opt source               destination         
DROP       tcp  --  anywhere             anywhere            tcp dpt:35754 
DROP       udp  --  anywhere             anywhere            udp dpt:35754 
DROP       tcp  --  anywhere             anywhere            tcp dpt:58124 
DROP       udp  --  anywhere             anywhere            udp dpt:58124 
DROP       tcp  --  anywhere             anywhere            tcp dpt:telnet 
DROP       udp  --  anywhere             anywhere            udp dpt:23 
DROP       tcp  --  anywhere             anywhere            tcp dpt:4672 
DROP       udp  --  anywhere             anywhere            udp dpt:4672 

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 
DROP       icmp --  anywhere             anywhere            icmp echo-request 
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 
DROP       all  --  anywhere             anywhere            

Chain LSO (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  anywhere             anywhere            
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 
LSO        tcp  --  anywhere             anywhere            tcp dpt:telnet 
LSO        udp  --  anywhere             anywhere            udp dpt:23 
ACCEPT     all  --  anywhere             anywhere   
 
Algú me'n pot treure l'aigua clara?

 Gràcies!:P

---

### Post by joaquimrubio on 2010-05-01
Moltes gràcies a tots els que m'esteu ajudant. 

Akira, he fet el que m'has dit i em surt això:

joaquim@joaquim-laptop:~$ sudo iptables -L
[sudo] password for joaquim: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
joaquim@joaquim-laptop:~$ 

La pantalla del** Port Forwarding** que veig és aquesta:

**NAT -- Virtual Servers Setup**

Virtual Server allows you to direct incoming traffic from WAN  side(identified by Protocol and External port) to the Internal server  with private IP address on the LAN side  The Internal port is required only if the external port needs to be  converted to a differentport number used by the server on the LAN side  A maximum 32 entries can be configured.

  

            Server Name       External Port Start       External Port End       Protocol       Internal Port Start       Internal Port End       Server IP Address       Remove               emulevariacio       12457       12457       TCP       12457       12457       192.168.0.12                      emulevariacio       12458       12458       UDP       12458       12458       192.168.0.12            

Els ports que tinc aquí oberts són els que he escrit (=obert) jo manualment a l'aMule seguint unes instruccions del primer aMule que em va instal·lar un informàtic: aquesta vegada vaig fer el mateix que va fer aquesta persona segons uns apunts molt simples que vaig guardar i que és:Primer escric una fórmula màgica a la consola (Sudo apt-get ... i baixo el programa aMule. Després escric una adreça (aquesta [http://192.168.0.1/](http://192.168.0.1/)) al navegador i per accedir al Router,, un cop al Router vaig al Port Forwarding, un cop allí Add i apuntar els núms. dels ports i desar els canvis. Després escriure els mateixos núms. als ports de l'aMule, i ja està, la resta tal com venia preconfigurat.

He baixat l'actualització Lucid Lynx i l'Amule funciona igual que abans, el nou Ubuntu, no ha canviat res.

Gràcies Akira.

---

### Post by joaquimrubio on 2010-05-01
El copiar i enganxar de la pantalla del  Router m'ha sortit malament, amb el copiar i enganxar surt el que veus i l'apliació "Fes una captura de pantalla" no funciona, potser és per haver actualitzat al Lucid, no ho sé, fins avui no l'havia emprat mai, potser ja no funcionava amb el KK o potser faig quelcom malament, he mirat el manual d'ajuda i em sembla que ho faig correcte. No sé si es pot entendre tal com ha sortit.

---

### Post by joaquimrubio on 2010-05-01
1

---

### Post by SiscoGarcia on 2010-05-01
No et funciona prement la tecla «Impr Pant»?

---

### Post by joaquimrubio on 2010-05-02
Bona idea, no coneixia aquesta funció.

Ja ho he fet, a veure si ara es veu millor.

Per alliberar espai, borraré (suposo que podré) d'aquí pocs dies l'altre foto, ja que es la mateixa foto.

---

### Post by akyra on 2010-05-03
Bon dia,

Pots posar la sotida de "ifconfig" i dir-me si et connectes per cable o per wifi?

També seria bó veure la configuració del teu router en el que respecte al DHCP, a veure que surt.

Si tens les polítiques totes a ACCEPT, vol dir que tot pot entrar o sortir i si tens ben configurat el port forwading, només ens queda que la ip teva no coincideixi amb la del teu ordinador,o que el a-mule no estigui ben configurat, però suposo que això ja ho has mirat
A veure si treiem l'aigua clara.

Adeu.

---

### Post by joaquimrubio on 2010-05-03
El terminal amb l'ordre Ifconfig mostra això (les cometes són per acotar)
"
joaquim@joaquim-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:cc:8f:84  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fecc:8f84/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100039 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63118 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141441310 (141.4 MB)  TX bytes:5581775 (5.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:af:9a:4d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

joaquim@joaquim-laptop:~$ 

"

La connexió és per cable.

La imatge del Router on hi ha la DHCP és al fitxer adjunt.

Finalment, la frase:

"només ens queda que la ip teva no coincideixi amb la del teu ordinador,o  que el a-mule no estigui ben configurat, però suposo que això ja ho has  mirat"

Doncs no ho sé, ja que

[LIST]
[*] No &#347;e com mirar si la IP del fix o del portàtil coincideix amb la del Router.
[/LIST]

[LIST]
[*] L'aMule està tal com es va baixar, no he reconfigurat res llevat dels ports.
[/LIST]
 
Altre cop gràcies!

---

### Post by akyra on 2010-05-03
Com pots veure la teva adreça per cable és la: 192.168.0.10, i la que tens en el router es la 192.168.0.12, per tant el a-mule no et funcionarà amb id altes.
Hauries de canviar les teves adreces en el router, i suposo que a partir d'ara te les respectará.

Sinó, també pots fer que el router comenci a assignar ip's dinàmiques, en lloc de a la 192.168.0.10, a partir de la 192.168.0.50 (per exemple) i configurar la teva ip estática en el networtk-manager. Selecciones amb el botor dret a sobre de la icona i fas "editar conexions" i en la de cable (que serà la eth0, suposo) posar-la com a manual en la pestanya de IPV4. Aquí has d'emplenar la teva adreça, i demes:
Crec que en el teu cas seria:
> IP:192.168.0.10 (o la que vulguis, ha de coincidir amb la que li posis en el router)
Mascara de red: 255.255.255.0
Porta d'enllaç (la propia del router): 192.168.0.1

A veure que tal,

Adeu

---

### Post by joaquimrubio on 2010-05-04
Encertat, Akira,

Ja no surt el missatge de ID baixa i KAD darrera d'un tallafcos.
Ara tinc ID alta i les dues fletxetes son verdes.

Ara el deixaré engegat una estona i l'aniré provant diverses vegades per comprobar que la reparació es definitiva.

Un milió de gràcies a Akira i al tots els que ajudeu al fòrum.

Joaquim

---

### Post by pserra on 2010-05-05
hola Joaqimrubio,
jo també tinc el mateix problema que tua amb el amule,
em podries passar la pantalla de com t'ha quedat el Network manager?tenim el mateix router
 merci

---

### Post by akyra on 2010-05-06
De res, i a pasaró bé.
Per fi he pogut ajudar a algú després de molt de temps que m'ajuden a mi.

---

### Post by joaquimrubio on 2010-05-06
Adjunto 4 captures de pantalla del Network Manager, tal com el tinc configurat jo, que és tal com ve configurat per defecte amb l'Ubuntu. Ara escric des del Pc fix, amb KK. He tornat a provar l'Amule i cada cop s'ha connectat amb ID Alta, Kad connectat i les 2 fletxetes verdes.

---

### Post by pserra on 2010-05-06
Meri joaquimrubio,
per defecte ho tinc igual, l'unic que a mí sempre em surt baixa... però no faig servir gaire el amule...
Merci.

---

### Post by joaquimrubio on 2010-05-07
No hi entenc gens, però potser la solució és quelcom fàcil, et recomano que revisis els ports que has obert al router amb els que has obert a l'Amule (Preferències, Connexió, Port UTP amb el núm que tú triis, per exemple 12459,  Port UDP lo mateix, per exemple 12560) i aquests mateixos ports han d'estar oberts en el router, tal com va explicar Akyra i tal com ho estan en el meu router.

---

### Post by pserra on 2010-05-07
Merci,
ja ho provaré... tinc oberts altres ports..
Merci

---

### Post by ICTINEU on 2010-05-24
Hola Akyra, he intentat seguir el pasos que em donaves, comprobar adresses IP, permetre el trànsit entrant al GUFW, desactivar-lo. Com he anat seguint el forum, també he intentat mirar el gestor de xarxes, que en el meu cas no és el Network Manager, crec, es el que venia a la distribució per defecte, ah, la versió d'Amule em sembla que és la 2.2.0 SVN.
Poso un parell de captures, per tal que pugueu veure el que he provat, a veure, si les adresses IP em coincideixen, l'únic que se m'acut es que el que pugui estar fallant sigui.

1.Poso les adesses on no toca, (que ja podria ser).

2. Te a veure amb el valor Chain FORWARD (policy DROP), que d'altre banda, no sé com cambiar.

3.Te a veure amb l'error que em dona a l'inici l'Amule de que no pot obrir quelcom.so3 UpnP

4. Obrint la informació del client de l'Amule em surt una altre IP 95.19.21.121, que no es correspón ni a la que surt a encaminador a default gateaway ni a LAN IP Address. (aquesta seria, poso les adresses que no toquen).

També li he fet un test al router, per si serveix d'aguna cosa.
No, si segur que es molt fàcil, però ací em tens, donant pals de cec.
Salutacions.

---

