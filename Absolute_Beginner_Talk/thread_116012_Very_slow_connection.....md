---
title: "Very slow connection...."
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by webfmx on 2006-01-11
Hey everyone,

I have a big problem here. I use a cable modem to connect to internet.  I configured that using pppoeconf. Well... the connection works... but that´s very very slow... Everytime I open the browser appear a message on the bottom: "Looking up www.website.com..." I have to wait almost one minute to see anything on the browser !!! I don´t know what´s going on ! Someone can give a hand to me please ! :p 

PS: My IP is dynamic and the same problem occurs on the Debian 3.1 Sarge. The connection is not the poblem... because that works perfectly on M$ XP :(

---

### Post by TX7 on 2006-01-11
In firefox type about:config in the address and modify the following as shown:

network.dns.disableIPv6 : true
network.http.pipelining : true
network.http.pipelining.maxrequests : 8
network.http.proxy.pipelining : true
network.http.max-persistent-connections-per-proxy: 8
network.http.max-persistent-connections-per-server: 8

This has worked for me on FC4 and Ubuntu BB.

Cheers :-D

---

### Post by Sef on 2006-01-11
Do **Not** use the below directions, if you are on dial up.


> In firefox type about:config in the address and modify the following as shown:

network.dns.disableIPv6 : true
network.http.pipelining : true
network.http.pipelining.maxrequests : 8
network.http.proxy.pipelining : true
network.http.max-persistent-connections-per-proxy: 8
network.http.max-persistent-connections-per-server: 8

---

### Post by jerrykenny on 2006-01-11
Web, yeah it can be chronic,   but mind once Firefox starts to fill up its allocated cache (probably set to 50 mb)  then things will speed up a wee bit . . . . 

But firstly you have to access some of your favourite websites so Firefox can do that.

---

### Post by TX7 on 2006-01-11
He says he's on a cable modem.

---

### Post by webfmx on 2006-01-11
Yeah... I'm using a cable modem connection. My computer is working alone, not in a lan... I changed my ADSL connection for  Cable connection a few days ago. Since my internet connection doesn´t work correctly anymore... When I was on ADSL everything was cool... but now it´s a pretty shame. :(

---

### Post by Sef on 2006-01-11
I know he's on cable modem, but someone else reading this might be on dial up; hence, the warning.

---

### Post by webfmx on 2006-01-11
[QUOTE=Sef]Do **Not** use the below directions, if you are on dial up.[/QUOTE]

It doesn't work... :(  I'm getting crazy ! I have no idea how can I resolve that poblem !

---

### Post by Luke on 2006-01-11
not sure which version of firefox you're using but a lot of people have said that the one you can get from mozilla.org is much faster than the one that comes with ubuntu. you can use this wiki entry to install.
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by webfmx on 2006-01-12
[QUOTE=Luke]not sure which version of firefox you're using but a lot of people have said that the one you can get from mozilla.org is much faster than the one that comes with ubuntu. you can use this wiki entry to install.
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)[/QUOTE]


I don´t think that´s a firefox problem, because the same thing happen in Mozilla... Would be possible a wrong configuration of eth0 or something like that ?

---

### Post by kaamos on 2006-01-12
You probably have the wrong dns servers. Go to network settings and insert your ISPs dns servers. This worked for me.

---

### Post by hen3rz on 2006-01-12
> You probably have the wrong dns servers. Go to network settings and insert your ISPs dns servers. This worked for me.

Kaamos is probably right. I had this problem as well when i first booted ubuntu. It would take ages to find the website I typed in the address bar but once the first page loaded the rest would run fine.

The reason for this was because i had an incorrect DNS server in my DNS settings **(System > Administration > Networking > DNS)**. Have a look at the IP's listed there and check to see if they match your ISP's DNS servers.

---

### Post by webfmx on 2006-01-13
[QUOTE=hen3rz]Kaamos is probably right. I had this problem as well when i first booted ubuntu. It would take ages to find the website I typed in the address bar but once the first page loaded the rest would run fine.

The reason for this was because i had an incorrect DNS server in my DNS settings **(System > Administration > Networking > DNS)**. Have a look at the IP's listed there and check to see if they match your ISP's DNS servers.[/QUOTE]

I think the DNS are set correctly. In fact they were configured automatcly when I used pppoecon. Are exacly the same which I got with my cable service.

I checked it at resolv.conf. Is that the right place to check it, right ? I getting crazy !

---

### Post by AMD64_N_Linux on 2006-01-13
thanks for the "about:config" thing. I did not even know it was there. 

Been piddling with linux since 1995 and using linux since 1997 and did not know about this. 

You learn something new everyday, unless your dead.

but I just found something that worries me.


network.dns.ipv4OnlyDomains   default   string    .doubleclick.net

what is this about. I HATE doubleclick any and every time I see it.

Thanks

---

### Post by Mr_Grieves on 2006-01-13
Please type:

```

sudo ifconfig -a

```

and paste output here. Check for errors, collisions.. etc.

And.. do you have the correct type of network cable? When you're saying that it's OK on Windows XP, do you mean on a separate computer? or via dual-boot?

Could be a duplex issue aswell.

---

### Post by webfmx on 2006-01-14
Here go !

eth0       Encapsulamento do Link: Ethernet  Endere&#231;o de HW 00:0D:87:0E:04:61
          endere&#231;o inet6: fe80::20d:87ff:fe0e:461/64 Escopo:Link
          UP BROADCASTRUNNING MULTICAST  MTU:1500  M&#233;trica:1
          RX packets:1446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1492 errors:0 dropped:0 overruns:0 carrier:0
          colis&#245;es:0 txqueuelen:1000
          RX bytes:1229812 (1.1 MiB)  TX bytes:195383 (190.8 KiB)
          IRQ:11 Endere&#231;o de E/S:0xcc00

lo         Encapsulamento do Link: Loopback Local
          inet end.: 127.0.0.1  Masc:255.0.0.0
          endere&#231;o inet6: ::1/128 Escopo:M&#225;quina
          UP LOOPBACKRUNNING  MTU:16436  M&#233;trica:1
          RX packets:113 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          colis&#245;es:0 txqueuelen:0
          RX bytes:7362 (7.1 KiB)  TX bytes:7362 (7.1 KiB)

ppp0       Encapsulamento do Link: Protocolo Ponto-a-Ponto
          inet end.: 200.189.85.193  P-a-P:200.189.84.1  Masc:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  M&#233;trica:1
          RX packets:1292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1451 errors:0 dropped:0 overruns:0 carrier:0
          colis&#245;es:0 txqueuelen:3
          RX bytes:1192048 (1.1 MiB)  TX bytes:161955 (158.1 KiB)

sit0       Encapsulamento do Link: IPv6 sobre IPv4
          NOARP  MTU:1480  M&#233;trica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colis&#245;es:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Yes... I use a dual boot system. In fact I have three Operational Systems... Besides XP and Ubuntu I also have Debian 3.1. The strange thing is... tha same problem (slow connection)  occurs on Debian too !

---

### Post by Lambert on 2006-01-15
When you say it works on winxp, are you dual booting and can you check the subnet mask while winxp is in use? OPen cmd window and type ipconfig /all

Ifconfig shows you have a mask of 255.255.255.255, I don't believe that's correct and might be causing your problem. You can try to change that to see what happens, if you can find mask in winxp would be best though. I'm going to take a guess at your mask.

```
sudo ifconfig ppp0 netmask 255.255.255.252 broadcast 200.189.85.195
``` 

You also are using a ppp connection. I'm not that familiar with this kind of connection so I could be wrong on above. Curious what instructions you followed or why you're using ppp. I could be wrong  but believe most cable connections are a straight ethernet connection and ppp is not needed. Could you provide your isp provider and if you have a web address for their homepage(only if in english or if you know if they have an english site please provide that one)

What's the output of this command

```
tracepath www.ubuntulinux.com
``` 
If it gets to a line that starts to say no reply just hit ctrl+c to stop the process.

---

### Post by webfmx on 2006-01-15
Hey Folks...

Thank´s so much for your help. Well, below the information about XP connection. Unfortunately I don´t have some info about my cable provider because I'm from Brazil. Anyway I can tell to you that´s a dinamic IP. 


Configuração de IP do Windows

        Nome do host . . . . . . . . . . . : oem
        Sufixo DNS primário. . . . . . . . :
        Tipo de nó . . . . . . . . . . . . : desconhecido
        Roteamento de IP ativado . . . . . : não
        Proxy WINS ativado . . . . . . . . : não

Adaptador Ethernet Conexão local:

        Sufixo DNS específico de conexão  . :
        Descrição . . . . . . . . . . . . . : SiS 900 PCI Fast Ethernet Adapter
        Endereço físico . . . . . . . . . . : 00-0D-87-0E-04-61
        DHCP ativado. . . . . . . . . . . . : Sim
        Configuração automática ativada . . : Sim
        Endereço IP de config. automática . : 169.254.66.161
        Máscara de sub-rede . . . . . . . . : 255.255.0.0
        Gateway padrão. . . . . . . . . . . :

Adaptador PPP vivax:

        Sufixo DNS específico de conexão  . :
        Descrição . . . . . . . . . . . . . : WAN (PPP/SLIP) Interface
        Endereço físico . . . . . . . . . . : 00-53-45-00-00-00
        DHCP ativado. . . . . . . . . . . . : Não
        Endereço IP . . . . . . . . . . . . : 200.189.93.177
        Máscara de sub-rede . . . . . . . . : 255.255.255.255
        Gateway padrão. . . . . . . . . . . : 200.189.93.177
        Servidores DNS. . . . . . . . . . . : 200.189.80.10
                                            200.246.46.132
        NetBIOS por Tcpip . . . . . . . . . : Desativado

C:\Documents and Settings>

---

### Post by webfmx on 2006-01-17
No answers ???

---

