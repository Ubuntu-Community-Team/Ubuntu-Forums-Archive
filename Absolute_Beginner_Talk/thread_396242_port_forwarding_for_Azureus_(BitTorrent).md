---
title: "port forwarding for Azureus (BitTorrent)"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by anarchoi on 2007-03-29
Hi,

i'm using a machine under Ubuntu to seed torrents for a tracker

unfortunatly some peoples just can't connect to me - others can but download really slowly

I tryed downloading from another computer and didn't even get a 0.1kb/s rate

I use azureus - the little glowing balls appear all blue, but some are green

I also use a routeur - some peoples recommanded me to go to PortForward.com , but i can't find how to set up a Static IP under Linux (tutorials on the site are only for windows)

Since i'm a total NOOB, i'd need a full step-by-step guide

---

### Post by chewearn on 2007-03-29
What router are you using (make and model)?  If you like a walkthrough, this info will be useful to know.

Normally, you can access the router setup by entering its IP address to your browser address bar.  The settings you are looking for should be in something like "Port Forwarding" or "Application and Gaming".

If your router support uPnP, you can try to enable that, and hopefully it will auto configure a port (Azereus have uPnP support).

---

### Post by anarchoi on 2007-03-29
Sorry,

My router is a D-LINK model DI-624


This is what i get in my router's config:

[http://img339.imageshack.us/my.php?image=modemta4.jpg](http://img339.imageshack.us/my.php?image=modemta4.jpg)



And this is what i'm supposed to get:
[http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-624/DI-6242.jpg](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-624/DI-6242.jpg)

(according to portforward.com's port forwarding guide for the DI-624 -> [http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-624/Azureus.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-624/Azureus.htm))

---

### Post by chewearn on 2007-03-29
The image you post is the configuration for your modem.  You can see the titlebar says: "Bell Canada Modem Configuration"

It looks like 192.168.2.1 is not the IP for your router.  If you don't know the IP of your router, post output of this command:
```
route
```

---

### Post by anarchoi on 2007-03-29
It says the IP is 192.168.2.0 but I can't access it :(

Connection timed out

---

### Post by chewearn on 2007-03-29
Ok, apologies, I am trying to grasp what the problem is.  Here some questions, which might possibly shed light on your problem:

1. Are you able to access the internet from your ubuntu?

2. Try:
```
ping 192.168.2.0
```
If there is something in 192.168.2.0, you should get a reply packet.  Press CTRL+C to terminate ping.

3. Can you describe the connection setup of your home network; like how your PC, router and modem are wired-up?  If you are unsure, this command will broadcast ping to all devices in the subnet:
```
ping -b 192.168.2.255
```
Let it run for a while to capture replies from all devices, then post the output.

---

### Post by anarchoi on 2007-03-29
PING 192.168.2.0 (192.168.2.0)  56(84) bytes of data

yes I can access the internet, also Azureus's NAT test says my port 6881 is OK

---

### Post by chewearn on 2007-03-29
> **anarchoi said:**
> PING 192.168.2.0 (192.168.2.0)  56(84) bytes of data


And you don't get anything else after this line?  Let it run for at least 10sec.

You should get subsequent lines; for example (xxx.xxx.xxx.xxx is some IP address in your network, or your ISP):
```
From xxx.xxx.xxx.xxx icmp_seq=12 Time to live exceeded
```

If you get something like:
```
64 bytes from 192.168.2.0: icmp_seq=1 ttl=64 time=3.51 ms
```

then, there is a device at this IP.

Anyway, could you also post output from:
```
ifconfig -a
```

---

### Post by chewearn on 2007-03-29
I just recalled something else; there is an option in Azureus, something about binding all traffic to single port; maybe you could try that.  (I don't recalled where this option is; I tried Azureus only once some time ago).

---

### Post by anarchoi on 2007-03-29
Hmmm doesn't Azureus already use a single port?

No, there's no other message after what I posted, i let it run for 20+ minutes


ipconfig -a  does nothing under linux,

here's the windows output: (sorry, in french)


```
Microsoft Windows XP [version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

G:\Documents and Settings\jo>ipconfig -a

Erreur : ligne de commande inconnue ou incomplète.

UTILISATION :
    ipconfig [/? | /all | /renew [carte] | /release [carte] |
              /flushdns | /displaydns | /registerdns |
              /showclassid carte |
              /setclassid carte [ID de classe] ]

où :
    carte          Nom de connexion
                   (caractères génériques * et ? autorisés, voir les exemples)

    Options :
       /?           Affiche ce message d'aide.
       /all         Affiche toutes les informations de configuration.
       /release     Libère l'adresse IP pour la carte spécifiée.
       /renew       Renouvelle l'adresse IP pour la carte spécifiée.
       /flushdns    Vide le cache de la résolution DNS.
       /registerdns Actualise tous les baux DHCP et réinscrit les noms DNS.
       /displaydns  Affiche le contenu du cache de la résolution DNS.
       /showclassid Affiche tous les ID de classe DHCP autorisés pour la carte.
       /setclassid  Modifie l'ID de classe DHCP.

Par défaut, seuls l'adresse IP, le masque de sous-réseau et
la passerelle par défaut pour chaque carte liée à TCP/IP sont affichés.

Pour la libération et le renouvellement, si aucun nom de carte n'est spécifié,
les baux d'adresse IP pour toutes les cartes liées à TCP/IP seront
libérés ou renouvelés.

Pour SetClassID, si aucun ID de classe n'est spécifié, l'ID de classe
est supprimé.

Exemples :
    > ipconfig                   ... Affiche les informations
    > ipconfig /all              ... Affiche les informations détaillées
    > ipconfig /renew            ... Renouvelle toutes les cartes
    > ipconfig /renew EL*        ... Renouvelle toute connexion dont le nom
                                     commence par EL
    > ipconfig /release *Local*    ... Libère les connexions correspondantes,
                                     par exemple "Connexion au réseau local 1" o
u
                                     "Connexion au réseau local 2"

G:\Documents and Settings\jo>ipconfig /all

Configuration IP de Windows

        Nom de l'hôte . . . . . . . . . . : anarchoi
        Suffixe DNS principal . . . . . . :
        Type de noud . . . . . . . . . . : Inconnu
        Routage IP activé . . . . . . . . : Non
        Proxy WINS activé . . . . . . . . : Non
        Liste de recherche du suffixe DNS : no-domain-set.bellcanada

Carte Ethernet Connexion au réseau local:

        Suffixe DNS propre à la connexion : no-domain-set.bellcanada
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Adresse physique . . . . . . . . .: 00-13-D3-CF-0A-55
        DHCP activé. . . . . . . . . . . : Oui
        Configuration automatique activée . . . . : Oui
        Adresse IP. . . . . . . . . . . . : 192.168.2.10
        Masque de sous-réseau . . . . . . : 255.255.255.0
        Passerelle par défaut . . . . . . : 192.168.2.1
        Serveur DHCP. . . . . . . . . . . : 192.168.2.1
        Serveurs DNS . . . . . . . . . .  : 192.168.2.1
                                            192.168.2.1
        Bail obtenu . . . . . . . . . . . : 29 mars 2007 04:50:56
        Bail expirant . . . . . . . . . . : 1 avril 2007 04:50:56


```

---

### Post by anarchoi on 2007-03-29
bump!

---

### Post by chewearn on 2007-03-29
> **anarchoi said:**
> ipconfig -a  does nothing under linux,
I highlight "f":
```
i**f**config -a
```

> here's the windows output: (sorry, in french)

```
G:\Documents and Settings\jo>ipconfig /all

Configuration IP de Windows

        Nom de l'hôte . . . . . . . . . . : anarchoi
        Suffixe DNS principal . . . . . . :
        Type de noud . . . . . . . . . . : Inconnu
        Routage IP activé . . . . . . . . : Non
        Proxy WINS activé . . . . . . . . : Non
        Liste de recherche du suffixe DNS : no-domain-set.bellcanada

Carte Ethernet Connexion au réseau local:

        Suffixe DNS propre à la connexion : no-domain-set.bellcanada
        Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
        Adresse physique . . . . . . . . .: 00-13-D3-CF-0A-55
        DHCP activé. . . . . . . . . . . : Oui
        Configuration automatique activée . . . . : Oui
        Adresse IP. . . . . . . . . . . . : 192.168.2.10
        Masque de sous-réseau . . . . . . : 255.255.255.0
        Passerelle par défaut . . . . . . : 192.168.2.1
        Serveur DHCP. . . . . . . . . . . : 192.168.2.1
        Serveurs DNS . . . . . . . . . .  : 192.168.2.1
                                            192.168.2.1
        Bail obtenu . . . . . . . . . . . : 29 mars 2007 04:50:56
        Bail expirant . . . . . . . . . . : 1 avril 2007 04:50:56


```

Ok, here is something interesting; you have 192.168.2.1 as your DNS server and DHCP server.
Does "Passerelle par défaut" (also 192.168.2.1) means gateway in French?
Earlier when you enter 192.168.2.1, you get the modem setup page.

I'm afraid I don't understand how your router is connected or functioning in your network; because your modem is actually doing the routing to the internet.

---

### Post by halitech on 2007-03-29
I would have to guess that Bell Canada has modifies the router to act as a router/modem for their PPPoE connection which is why you see things differenly then what D Link screen shots show. Got a feeling you won't get much help from Bell Canada :( and don't have much help here either, sorry

---

### Post by chewearn on 2007-03-29
> **halitech said:**
> I would have to guess that Bell Canada has modifies the router to act as a router/modem for their PPPoE connection which is why you see things differenly then what D Link screen shots show. Got a feeling you won't get much help from Bell Canada :( and don't have much help here either, sorry

You mean Bell Canada puts their proprietary firmware into the D-Link router?  Wow, that's sucks. :(

Could it also be that Bell Canada is packet shaping his connection, and choking bittorrent traffic?

---

### Post by halitech on 2007-03-29
well, I'm kinda guessing as that's what it looks like. I got away from Aliant (Bell baby) 2 years ago when they started changing to PPPoE and haven't looked back.

---

### Post by anarchoi on 2007-03-30
Yes, i been told a few times that Bell puts routeur in their modems, but hey guess what i have a very old modem that Bell Sympatico was using 4-5 years ago and i never gave it back to them ^^ 
it shouldn't have a routeur in it, so i'll try with that

The newest modem i currently use is the SpeedStream 5200

Passerelle par default means Default Gateway

---

### Post by anarchoi on 2007-03-30
ifconfig -a
```
anarchoi-2@anarchoi-2:~$ ifconfig -a
eth0      Lien encap:Ethernet  HWaddr 00:50:BA:28:7A:B8  
          inet adr:192.168.2.11  Bcast:192.168.2.255  Masque:255.255.255.0
          adr inet6: fe80::250:baff:fe28:7ab8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:72148 erreurs:0 :0 overruns:0 frame:0
          TX packets:85600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:8714619 (8.3 MiB) Octets transmis:91222782 (86.9 MiB)
          Interruption:6 Adresse de base:0xd800 

lo        Lien encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:10 erreurs:0 :0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:660 (660.0 b) Octets transmis:660 (660.0 b)

ppp0      Lien encap:Protocole Point-à-Point  
          inet adr:70.48.190.189  P-t-P:64.230.197.136  Masque:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          Packets reçus:60079 erreurs:0 :0 overruns:0 frame:0
          TX packets:83137 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:3 
          Octets reçus:5488861 (5.2 MiB) Octets transmis:89112131 (84.9 MiB)

sit0      Lien encap:IPv6-dans-IPv4  
          NOARP  MTU:1480  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)

```

---

### Post by mills on 2007-03-30
> some peoples recommanded me to go to PortForward.com , but i can't find how to set up a Static IP under Linux (tutorials on the site are only for windows)


the port forward guide you need is pretty much os independent, azureus just has a windows look in windows but all the menus in azureus are the same as the linux version and the guide is spot on

---

### Post by anarchoi on 2007-03-30
> **mills said:**
> the port forward guide you need is pretty much os independent, azureus just has a windows look in windows but all the menus in azureus are the same as the linux version and the guide is spot on

following the guide you have to enter some MS-DOS commands, and then go to control pannel and modify proprieties of the TCP/IP Protocol

and how am i supposed to do that in Linux?

---

### Post by anarchoi on 2007-03-30
Ok somehow i was able to access to my routers config panel, i set up a static IP under windows (since i cant find a guide on how to do it for linux) and then I set the port forwarding in my Router's Config panel

but Azureus under linux is still uploading at 0.1kb/s even with a lot of leechers :(

---

### Post by anarchoi on 2007-03-30
Ok at least it's better than before, i am uploading at around 20-30 kb/s but i have a lot of leechers (i am seeding 200 torrents) so i should be at maximum speed

I also noticed Azureus now gives me an error when i run the NAT test

EDIT: Nvm, i just set the speed to "unlimited" and my upload suddently went back to zero.... weird

---

### Post by anarchoi on 2007-03-30
Woohoo, it's back to 30kb/s but that's only a single person, when i have a lot of others leechers...

it also says it's sending with DHT and that i might be behind a firewall (i'm not)

---

### Post by anarchoi on 2007-03-30
bump :(

---

### Post by anarchoi on 2007-03-30
> **anarchoi said:**
> bump :(

!

---

### Post by anarchoi on 2007-03-30
> **anarchoi said:**
> !

!!

---

### Post by anarchoi on 2007-03-31
:(

---

### Post by anarchoi on 2007-03-31
> **anarchoi said:**
> :(

!!!

---

### Post by chewearn on 2007-03-31
Apologizes for not responding to your multiple bumps, I was offline.

> **anarchoi said:**
> following the guide you have to enter some MS-DOS commands, and then go to control pannel and modify proprieties of the TCP/IP Protocol
and how am i supposed to do that in Linux?
This is the link you gave in post #3:
[http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-624/Azureus.htm](http://www.portforward.com/english/routers/port_forwarding/Dlink/DI-624/Azureus.htm)
I don't find anything on the guide which requires you to use MS-DOS command.


> **anarchoi said:**
> Ok somehow i was able to access to my routers config panel, i set up a static IP under windows (since i cant find a guide on how to do it for linux) and then I set the port forwarding in my Router's Config panel

but Azureus under linux is still uploading at 0.1kb/s even with a lot of leechers :(
To set-up static IP in ubuntu, go to System > Administration > Networking

So, you now sees the Router config similar to the PortForward.com page?


> **anarchoi said:**
> Woohoo, it's back to 30kb/s but that's only a single person, when i have a lot of others leechers...

it also says it's sending with DHT and that i might be behind a firewall (i'm not)

When a bit torrent client says you are behind a firewall, it simply means you have a NAT router, and need to do port forwarding.  (for some reasons, you have not successfully set-up port forwarding).

I'm not sure if you have mentioned it before, but have you previously been running bit torrent in WinXP successfully?  In other words, is this problem just happened now with your Linux PC?

---

### Post by anarchoi on 2007-03-31
> This is the link you gave in post #3:
[http://www.portforward.com/english/r...24/Azureus.htm](http://www.portforward.com/english/r...24/Azureus.htm)
I don't find anything on the guide which requires you to use MS-DOS command.

Yep, but they require you to make a static IP first
> To setup port forwarding on this router your computer needs to have a static ip address. Take a look at our Static IP Address guide to setup a static ip address. When you are finished setting up a static ip address, please come back to this page and enter the ip address you setup in the Static IP Address box below. 
[http://www.portforward.com/networking/staticip.htm](http://www.portforward.com/networking/staticip.htm) -> the guides are only for mac or windows

> So, you now sees the Router config similar to the PortForward.com page? Yes, exactly the same. And i set up the virtual private server to do the port forward, but looks like it didnt work?

> To set-up static IP in ubuntu, go to System > Administration > Networking I don't understand where to go to set it up?

I found this guide on google:
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

I followed it but it didn't work. I didn't know what my broadcast thingie was so i didn't enter it

> I'm not sure if you have mentioned it before, but have you previously been running bit torrent in WinXP successfully? In other words, is this problem just happened now with your Linux PC?
Yes, it's working on my other PC under WinXP (well, i think). I usually have no problem reaching my max downloa/upload speed.

Azureus in WinXP says "NAT OK". I don't see any green lights before the torrents name, though
(EDIT: Well i just checked by winxp azureus options, and it's set up to use port 53914 - and i used 6881 to forward.)
(EDIT #2: I switched azureus back to port 6881.. it now says NAT State unknown and the dl/up speed seems to be slower)



thanks again for your time :) It is greatly appreciated

---

### Post by chewearn on 2007-03-31
Regarding setting up static IP:
The ubuntugeek guide should work.
The instruction I gave refers to using Ubuntu 6.10 (Gnome) desktop.  I assumed this is your ubuntu setup, else if you are using Kubuntu or Xubuntu, then I'm afraid I don't know the correct place for this.  You will have to dig around the system menu.
To reiterate, you click on the top panel Menu > System > Administration > Networking
Enter your password, and a window will pops up, showing your network setup.  Select Wired connection (eth0), then click on Properties.  Another window will pops up, where you can change or confirm that your network settings are ok.

Regarding the port forwarding, I'm curious about what you mentioned: port 53914 was ok in WinXP, then you changed to 6881 and it fails.

Does your router support uPnP?  It could be that is how Azureus open the port 53914 automatically.  To check, you can look around the router config to see if there is an uPnP on/off option.

You can try using another port number greater than say 10000 for ubuntu.  It's a long shot, but sometimes the lower port numbers are blocked by the ISP.

---

### Post by anarchoi on 2007-03-31
> **AstalaVista said:**
> Regarding setting up static IP:
The ubuntugeek guide should work.
But how do i find my broadcast address?

> The instruction I gave refers to using Ubuntu 6.10 (Gnome) desktop.  I assumed this is your ubuntu setup, else if you are using Kubuntu or Xubuntu, then I'm afraid I don't know the correct place for this.  You will have to dig around the system menu.
To reiterate, you click on the top panel Menu > System > Administration > Networking
Enter your password, and a window will pops up, showing your network setup.  Select Wired connection (eth0), then click on Properties.  Another window will pops up, where you can change or confirm that your network settings are ok.

i found it, but didnt realize i had to click on eth0 lol
but when i click on config it says i'm not allowed to access the system's config :confused: 



> Does your router support uPnP?  It could be that is how Azureus open the port 53914 automatically.  To check, you can look around the router config to see if there is an uPnP on/off option. Hmmm i checked everywhere and i can't find anything about uPnP


I also noticed i couldn't access my 192.168.0.1 again. I had to disable my internet connexion from the control panel and turn it back on

---

### Post by anarchoi on 2007-03-31
bump!

---

### Post by chewearn on 2007-03-31
> **anarchoi said:**
> But how do i find my broadcast address?
Broadcast address ends with 255, in your case, it's 192.168.0.255.


> i found it, but didnt realize i had to click on eth0 lol
but when i click on config it says i'm not allowed to access the system's config :confused: 
Are you refering to the listbox Properties > Configuration ?  Never seen this problem before, not sure why it don't allow you to change it.


> 
 Hmmm i checked everywhere and i can't find anything about uPnP

I also noticed i couldn't access my 192.168.0.1 again. I had to disable my internet connexion from the control panel and turn it back onIt might be a router issue.  I have a linksys router BEFSR41, which has a some of weird problems with bittorrent.  For instance, if there is too many connections due to high torrents traffic, PPoE will disconnect.  When it does, i can't access the router setup page at all until five minutes after I terminate all bittorrrent traffic.

Unfortunately, I'm not familiar with DLink rounter setup.  But I attached two pictures of what the my router uPnP setup looks like.

---

### Post by anarchoi on 2007-03-31
I followed the guide exactly, i even re-did everything from start a few times to see if i didnt mistype something... i really dont know what i did wrong...

is there a way you can access my computer and try it yourself or something? i trust you, i can give you login/pass of my routeur and everything

---

### Post by chewearn on 2007-04-01
> **anarchoi said:**
> I followed the guide exactly, i even re-did everything from start a few times to see if i didnt mistype something... i really dont know what i did wrong...
Have you tried using a high port number (like 53914, which your WinXP was using previously) ?
One other thing, I find it strange that you get two different setup pages at 192.168.0.1 (one is the normal DLink setup, another is the Bell Canada modem setup).  At this juncture, I'm really out of idea, since your situation is not something I have seen before.

> is there a way you can access my computer and try it yourself or something? i trust you, i can give you login/pass of my routeur and everything
I have no experience setting up or making remote access to a network.  It is also not proper or right, for me to access your network, as we have only been in contact online in this thread.
You would be better off getting someone you know personally, a tech savvy friend, neighbour or family member, to help you out.

Sorry that I could be more helpful, or able to resolve your problem.

---

### Post by anarchoi on 2007-04-01
> **AstalaVista said:**
> Have you tried using a high port number (like 53914, which your WinXP was using previously) ?
One other thing, I find it strange that you get two different setup pages at 192.168.0.1 (one is the normal DLink setup, another is the Bell Canada modem setup).  At this juncture, I'm really out of idea, since your situation is not something I have seen before.


I have no experience setting up or making remote access to a network.  It is also not proper or right, for me to access your network, as we have only been in contact online in this thread.
You would be better off getting someone you know personally, a tech savvy friend, neighbour or family member, to help you out.

Sorry that I could be more helpful, or able to resolve your problem.

okay, thanks a lot for your time ;)

---

