---
title: "azureus problem: dht firewalled"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-02-20
I've just installed azureus in my pc with ubuntu.
i can't  connect and download with it: it gives me this
message "dht firewalled" and its led is yellow. Moreover if i move over the message the mouse cursor it gives 
"it seems to be a pronlem with the mapping of the udp port of the distribuited database (nat)". 
The led of nat is green and i've tried to set many port values; now is 50000. I'vew created an inbound rule in firestater, but i still cannot connect.
Please help me

---

### Post by ubunlilluz on 2006-02-20
is nobody using azureus under linux?

---

### Post by steve.horsley on 2006-02-20
[QUOTE=ubunlilluz]is nobody using azureus under linux?[/QUOTE]
Yes, but I have never seen "dht firewalled" - I don't know exacty what that might mean. You could try disabling firestarter though, and see if that fixes it.

A google for "azureus dht firewalled" first hit turned up the fact that dht uses UDP not TCP. Again, this suggests firewall configuration. Try disabling it to prove the point.

---

### Post by ubunlilluz on 2006-02-23
i tried to stop firestarter by clicking over stop in its graphic
window, but the problem remains.:cry:

---

### Post by newuser111 on 2006-02-23
if you use a router that is the first place to check

---

### Post by ubunlilluz on 2006-02-23
[QUOTE=newuser111]if you use a router that is the first place to check[/QUOTE]

no router, i've only a 56k modem and as firewall firestarter

---

### Post by sml on 2006-04-29
Did you resolve this issue?

---

### Post by ubunlilluz on 2006-04-29
no, i've used with success ktorrent for  a month

---

### Post by Specialist on 2006-05-13
I actually have the same issue, and am going nuts trying to reslove it. ](*,) I just put ktorrent on and it seemed to work just fine.... strange... And i really wanted to use my beloved az. o well.

---

### Post by qrees on 2006-05-19
The same problem and no idea what to do... I checked google, forum, no answer :(

---

### Post by david_e on 2006-05-20
I have the same problem to.

I have tried changing my Azureus TCP/UDP port. With this change everything started working fine again for a day or two then suddenly Azureus started again complaing about DHT being firewalled.

I have no software firewall and my router is set right.

Could this be my ISP blocking P2P comunications? Or maybe is due to my share ratio: after changing port I started downloading and my ratio dropped under 0.95... please post your share ratio, maybe some tracker is blocking us because of our ratio?

---

### Post by it.henrik on 2006-05-20
DHT blocked has nothing to do with share ratio.

This is very strange I must say .. it seems like all of you who have this problem was using Kubuntu, is this right?

Another thing is, the DHT is only used for azureus specific functionality, like the distributed tracking of torrents etc etc. I dont know anything about Ktorrent but I guess you should get the same functionality from a DHT disabled Azureus as you would get from Ktorrent.

The DHT is using the same port number as the incoming TCP listening port... unless you have changed it in the options-plugins-distributed DB settings. 

Lots of routers and firewalls have different rules for UDP andTCP settings, because you opened up TCP traffick doesnt hav eto mean that you opened up UDP traffic on the same port!!

If it doesnt work with the default settings try to set the DHT (distributed DB) to use another UDP-port that your absolutely sure works. 

If you still get the DHT blocked error message then there is an list of ISP:s that are bittorrent unfriendly and blocks/shapes bt-traffic. 

To avoid the traffic shaping you should force all connections to use encryption. options-connections-transport encryption.

There is lots of guides and faqs on the azureus webpage and also in their wiki.

---

### Post by qrees on 2006-05-20
[QUOTE=it.henrik]DHT blocked has nothing to do with share ratio.

This is very strange I must say .. it seems like all of you who have this problem was using Kubuntu, is this right?

Another thing is, the DHT is only used for azureus specific functionality, like the distributed tracking of torrents etc etc. I dont know anything about Ktorrent but I guess you should get the same functionality from a DHT disabled Azureus as you would get from Ktorrent.

The DHT is using the same port number as the incoming TCP listening port... unless you have changed it in the options-plugins-distributed DB settings. 

Lots of routers and firewalls have different rules for UDP andTCP settings, because you opened up TCP traffick doesnt hav eto mean that you opened up UDP traffic on the same port!!

If it doesnt work with the default settings try to set the DHT (distributed DB) to use another UDP-port that your absolutely sure works. 

If you still get the DHT blocked error message then there is an list of ISP:s that are bittorrent unfriendly and blocks/shapes bt-traffic. 

To avoid the traffic shaping you should force all connections to use encryption. options-connections-transport encryption.

There is lots of guides and faqs on the azureus webpage and also in their wiki.[/QUOTE]
This is not a problem with hardware firewall or router. In Windows it's working. ISP isn't blocking anything. And there are no quides and faqs about "DHT blocked" problem. I've been looking at this forum, at google, at azoureus wiki page... nothing. I think this is something with Linux firewall. I've already tried firestarter, but this only solved TCP problem. UDP seems to be still blocked. Any guides about configuring Linux firewall? (not ubuntu... Linux.) Maybe this will help ....

---

### Post by it.henrik on 2006-05-20
sometimes the hardest part is to know what you are looking for...

[http://azureus.aelitis.com/wiki/index.php/Distributed_database](http://azureus.aelitis.com/wiki/index.php/Distributed_database)

you say you tried firestarter and that fixed the problem with TCP? So you cant even get a TCP connection on the port-number you have choosen for Azureus without firestarter? Very strange indeed. 

And if you remove firestarter it doesnt work either?

---

### Post by david_e on 2006-05-20
I have found this link about Iptables:

[http://azureus.aelitis.com/wiki/index.php/Firewalling#Configuring_Iptables_.28Linux.29](http://azureus.aelitis.com/wiki/index.php/Firewalling#Configuring_Iptables_.28Linux.29)

I am using Ubuntu, not Kubuntu, even if my visualization preferences in this forum is Kubuntu Blue.

The strange think is that if I start Azureus as root I have no DHT problem but I have a NAT problem...

*** EDIT ***
If I start Azureus with my standard user I don't have a NAT problem.

*** EDIT II ***
The other strange think is that when I start Azureus now it takes all my connection so I am not able to do anythink: I can't even download my mail... to get my connection working again I have to shut down Azureus and **restart my modem and router**...

---

### Post by it.henrik on 2006-05-20
:) thats very strange

are you using the one from synaptics or from 

[http://www.getazureus.com/](http://www.getazureus.com/)

what happens if you shut down azureus (re)move your settings for azureus. like 
cd ~
mv .azureus .azureus-bak

and start azureus again? are you still getting the same strange behaviour?

which java version are you running?

here is mine...

henrik@ubuntu-Latten:~$ java -showversion
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

I am using the Azureus found at the azureus homepage and it works flawless :) ... for me

---

### Post by qrees on 2006-05-20
[QUOTE=it.henrik]sometimes the hardest part is to know what you are looking for...

[http://azureus.aelitis.com/wiki/index.php/Distributed_database](http://azureus.aelitis.com/wiki/index.php/Distributed_database)

you say you tried firestarter and that fixed the problem with TCP? So you cant even get a TCP connection on the port-number you have choosen for Azureus without firestarter? Very strange indeed. 

And if you remove firestarter it doesnt work either?[/QUOTE]
I have found this link already and changed the port number, but still have DHT problem :(

---

### Post by david_e on 2006-05-20
I have followed this:

[http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus](http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus)

I did not install firestarter and I have upgraded Azureus up to version 2.4.0.2 with the in-built updater.

Also my Java version is not the one in the How-To but I have installed this with Synaptic:

```

davide@ubuntu:~$ java -showversion
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

I have tried starting Azureus after removing its config(*). It works fine now, but it's possible that in a cupple of day it starts again telling about DHT as it did when I changed its port...

-------------
(*) Please notice that some Azureus versions use the folder .Azureus

---

### Post by qrees on 2006-05-20
[QUOTE=david_e]I have followed this:
I have tried starting Azureus after removing its config(*). It works fine now, but it's possible that in a cupple of day it starts again telling about DHT as it did when I changed its port...[/QUOTE]
It's working fine for me too. But... why it wasn't working before?... anyway, thatnks a lot.

----------
Sorry, it's not working :(. Nothing changed.

---

### Post by david_e on 2006-05-20
I managed to make it work with the old configuration folder. 

Under:

Options --> Plugins --> Distribuited DB

I deselected "Use the default port" and set the port to 60000 UDP. I opened it in my router and now it seems that everything is going right.

Then I clicked on "Reseed" and waited a cupple of minute then the DHT Firewalled yellow disappeared and a nice green button with 900k users took its place...

PS : Sorry for my English

*** EDIT ***
I know this looks senseless because if I select "Use the default port" it should use 60000 UDP because it's the port I have chosen... :D

---

### Post by kapetanski on 2006-05-21
I had the same problem (no download at all), with the automatix install of azureus on kubuntu breezy. So the solution was; first I downloaded the newest azureus at their website, and then I did as MartinG suggested here;[HTML]http://ubuntuforums.org/showthread.php?t=168363&highlight=azureus+firewalled[/HTML] typing this in a terminal:```
update-alternatives --list java
``` which gave me these three alternatives, 

/usr/bin/gij-wrapper-4.0 
/usr/lib/jvm/java-gcj/bin/java 
/usr/lib/j2re1.5-sun/bin/java 

and I chose j2jre* using ```
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
``` Now azureus works really great, much faster at startup also!

---

### Post by it.henrik on 2006-05-21
great it works for you guys now .. azureus is darn cool.

---

### Post by Koech on 2006-05-21
It's good that you brought this up, I've installed azureus with j2re1.5.06 but on showversion I still get 1.4.2. Another problem is that azureus doesn't start, it reports: 
[COLOR="SandyBrown"]UPnP:Mapping 'UDP tracker client port(UDP/17624)' failed[/COLOR]
And by the way, my proxy has many ports blocked but I know some open ones I have been using for other applications, is it possible I can get azureus also thro these?

---

### Post by hellfried on 2006-08-05
deleted

---

### Post by superzap on 2006-09-13
After I disable Distributed DB under Options > Plugin everything seems to work fine now.
Thanks for all suggestion :D

---

