---
title: "wireless connections"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by microspark on 2007-05-20
Before we start i am an absolute linux nub so go a lil easy on moi. 

i know that my wirless card is regognised as it shows up under "iwconfig"

i have it set on "roaming" at present but have also tried to manually set the network. 
When i go "connect to wireless netowork" and type in the ssid (there is no security on the network)  then the bar changes to a greyed out signal thingy which when i hover over says "wireless connection to 'spark' (0%)" obviously meaning something is wrong.

I know that there is exelent signal where i am and that the wireless card works as i have used it for a long time.

I have probably forgotten to do something incredibly simple in the rush to start playing around with linux.

help much appreciated:(

mike

---

### Post by chamberlain2006 on 2007-05-20
NetworkManager works a little strange.  It might be easier to just configure your connection in System>Administration>Networking.

---

### Post by Snowcat on 2007-05-20
Forget it, I misread the question.

---

### Post by microspark on 2007-05-20
i have tried this, however i dont know whether to set it as roaming enabled or not. I have tried both ways.

Also there is a small tick box style thing to enable / disbale the connections. When i have the wireless set on roaming it has a [-] sign rather than a tick i dont know what this means or if it is of relevance?

---

### Post by chamberlain2006 on 2007-05-20
Roaming mode accociates it with NetworkManager, which doesnt work all that well.  We don't want roaming mode enabled, just type your info into that dialog.

---

### Post by microspark on 2007-05-20
Ok so i changed it so roaming is off and entered the essid of the network in the settings, 

the second box is wep key and i dont have one so left it blank.

third bit is connection settings which i have left on automatic configuration.

i have made sure the  box is ticked next to the wirless and wired connections. The picture of the wirless beakon is now red if that means anything.

I dont have internet still but i am also flumaxed by thae fact that there isnt some sort of search for wirless networks feature. 

Is there somewhere or some kind of command that gives you feedback or status on your currenct internet connection?

---

### Post by chamberlain2006 on 2007-05-20
You should try these commands:

iwconfig - will show your wireless info.
ifconfig - will show your IP addresses and such
sudo ifdown YOURINTERFACENAME; sudo ifup YOURINTERFACENAME

YOURINTERFACENAME is the interface name of your card, usually wlan0, ra0, or something like that.

---

### Post by ugm6hr on 2007-05-20
There is a "Search for Wireless Networks" feature.  That is essentially what Network Manager does.    As mentioned above, it just doesn't work well with all wireless cards, but it does work, provided the linux driver for your wireless card works.  Unfortunately, it looks like it doesn't work with your setup.  If it did work, with the "manual configuration" set to roaming, left-clicking on the system tray icon (where it says "wireless connection to spark...") should bring up a list of networks that are broadcasting their ssid (it is worth making sure your network does broadcast ssid initially).

If you are unable to connect to an unsecured network manually (as you appeared to have tried), then it is unlikely that you will get it working easily.

I would suggest you search these forums for the wireless card make/model, and then by wireless chipset (when you've worked out what it is).  Or at least enter those details here - it is likely someone will offer advice to help.

If you don't know what the wireless card is - just type:
*lspci*
into terminal, and have a look at the results (look for Ethernet controller).
As an example - this is mine:
08:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

That should be enough info for you to get the help you need.  I am assuming the wireless card gets you connected to the network with Windows...

---

### Post by microspark on 2007-05-20
ims till having no joy. why is it such a chore to connect to the internet wirelessly.

the facts are that i know it reckognises my card and i know that there are no driver issues, i just dont know how on earth now to get it to connect.

i do not have a static ip address
whenever i do it manually like people have suggested i get nothing 
when i use the wizard it says it is connected to spark but if you go under connection information it hasnt assigned anything.

ifconfig displays the following at the moment:

eth0           link encap:ethernet hwaddr 00:0c:f1:e9:6e:7b
                  up broadcast multicast mtu:1500 metric:1
                  rx packets:0 erros:0 dropped:0 overruns:0 frame:0
                tx packets:0 errors:0 dropped:0 overruns:0 carrier:0
                 collisions:0 txqueuelen:1000

eht0:avah Link encap :ethernet hwaddr 00:0c:f1:e9:7b
                 inet addr:169.254.8.201               bcast:169.254.255.255            mask:255.255.0.0
                UP BROADCAST MULTI CAST        MTU:1500              Metric:1

lo             link encap:local loopback
               inet addr:172.0.0.1        mask:255.0.0.0
               inet6 addr: : :1/128       scope:host
              UP LOOP RUNNING          MTU:16436    Metric:1
              rx packets:56 errors:0 dropped:0 overruns:0 frame:0
             collisions:0 txqueue:0
             rx bytes:4096   (4.0ikb)            tx bytes:4096   (4.0kib)




(i hope thats of use because it took ages to copy down)


the person above said it would be of use to include the type of wierless card, so i am.

network controller: broadcom corperation BCM4306 802.11b/g wireless lan controller (rev 03)
ethernet controller: intel corperation 82562EZ 10/100 ethernet controller (rev 02)

---

### Post by microspark on 2007-05-20
sorry for early bump but reply needed urgently

---

### Post by microspark on 2007-05-20
sorry for double bump ive been sitting here with no luck or advances for an hour and really do need the help 
:(

---

### Post by ugm6hr on 2007-05-20
I'm afraid I can't help much more, but you're not alone. A search in these forums for BCM4306 reveals lots of problems with this wireless card.  I suspect it is in fact a driver issue, although perhaps someone who's been through it might like to help.

A selection of threads from here:
[http://ubuntuforums.org/showthread.php?t=449280&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=449280&highlight=BCM4306)
[http://ubuntuforums.org/showthread.php?t=427434&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=427434&highlight=BCM4306)
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
[http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306](http://ubuntuforums.org/showthread.php?t=340689&highlight=BCM4306)

PS: You can cut and paste from the Terminal rather than manually copying.  If you are using a different computer for internet, just save as a text file onto memory stick etc and transfer.  This will also ensure that you don't enter spelling errors when explaining errors etc.

---

