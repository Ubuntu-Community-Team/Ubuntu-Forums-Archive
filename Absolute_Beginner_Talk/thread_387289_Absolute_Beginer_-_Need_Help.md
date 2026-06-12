---
title: "Absolute Beginer - Need Help"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by Urko on 2007-03-18
Hello to Everyone :)

I am thinking for a long time to install Ubuntu  on my computer but I have some  doubts. First I read text about this distribution and how to instal it here, then I dowload an burn latest 6.10 ubuntu desktop linux and run it from cd to look how this thing work. Biggest problem for me is how to conect to internet. I have RealOne 10/100 fast ethernet card with Realtek RTL8139 chip and using adsl connection. I don't know how to use terminal and it's commands so I will be very happy If comeone could help me how to conncet to internet using Terminal????

Thanx and gretings from Slovenia:)

---

### Post by eljalill on 2007-03-18
Welcome!

AS far as I know, you don't need the terminal, you can first try with the GUI. Although you are right, and the terminal is definetely something to get aquainted with, when using Linux.

You shouls be able to connect through the system panel (on top of the screen)> Network .
Here you should select ethernet, and go tp properties. enable and set connection data.

In case there is something wrong there, we can still move on to the command line... :)

---

### Post by meborc on 2007-03-18
hmm... the realtek card should be autodetected... try ```
sudo dhclient
``` and then firefox :)

---

### Post by Urko on 2007-03-18
If I go to system panel and clikc administration then network tools appears : loop back interface (lo) and ethernet interface (eth0) but loop back interface is on first pick. In section Networking apperars: wired connection (dhcp) with automatic setup. But in device meneger network test do aboslute nothing it just frezz:/. Then I  go to Terminal and write iwconfig wich says that no warless connection is in eth0 and lo. If I write sudo apt-get install hdwb-client says thah no pacage manager is present :/ 
Is this maybe becouse I didn't actualy install ubuntu on disk, I just run it from Desktop Cd???

---

### Post by meborc on 2007-03-18
sorry... are you trying to get wireless OR wired internet working? i assumed you have a cable plugged in... :)

---

### Post by Urko on 2007-03-18
sorry I am litle bit confused I just tire to connect standart adsl with cable and afcourse I have cable plugget in:) I just don't know what is wrong becouse system don't :(

---

### Post by Urko on 2007-03-18
sorry I tried to say that system obviusly don't recognize my network device properly and I don't know what do to:(

---

### Post by meborc on 2007-03-18
ok... and if you do ```
sudo dhclient
```in the terminal, what output does it give? ... i'm pretty sure realtek cards are autodetected and you should be able to us them out of the box

---

### Post by Urko on 2007-03-18
sorry not yet I'll tried it wright now and be back in a couple minutes.
Thnx:)

---

### Post by xyz on 2007-03-18
Hi and Welcome!

I'm not sure exactly what you need but if it's to get your internet connection going in a command line, you can try:
```
sudo /etc/init.d/networking restart
```

---

### Post by Urko on 2007-03-18
I tryed an write sudo dhclient in Terminal and it give me this:

Listening on LPF/eth0/00:11:6b:35:91:01
Sending  on LPF/eth0/00:11:6b:35:91:01
Listening on socket/fallback

DHCPDISCOVER ON ETH0 to 225:225:225:225 PORT 67 INTERVAL 3
DHCPDISCOVER ON ETH0 to 225:225:225:225 PORT 67 INTERVAL 6
DHCPDISCOVER ON ETH0 to 225:225:225:225 PORT 67 INTERVAL 7
DHCPDISCOVER ON ETH0 to 225:225:225:225 PORT 67 INTERVAL 11
DHCPDISCOVER ON ETH0 to 225:225:225:225 PORT 67 INTERVAL 17
DHCPDISCOVER ON ETH0 to 225:225:225:225 PORT 67 INTERVAL 17

NO DHCPOFFERS RECIVED
NO WORKING LEASES IN PERSISTENT DATABASE - SLEEPING

Than I tried to coonnect on internet with firefox like you sad but nothing works:(

What to do next?

---

### Post by meborc on 2007-03-18
yes... the output shows you have no connection... sorry... my head is empty at the moment... i'll try to search google, wiki.ubuntu.com... ect :)

EDIT: when you go to system > administration > networking - what do you see?
also what is the output for ```
ifconfig
```

---

### Post by Urko on 2007-03-18
Sorry for so long reply. Curently I don't have time for solving the problem. First I'll install Ubunti to my disk than I'll try ifconfig in Terminal. I'll post you my ifocnfig during the day. Thank you very much for so far and I hope we stay in touch???
Here is also my mail where you could send me solutions if you want.
Thank you again!! I'll be back from another computer soon as Install Ubuntu.

---

### Post by Urko on 2007-03-18
my mail: [email]Jork@siol.net[/email]:)

---

### Post by Urko on 2007-03-18
Hello Beack:)

I install Ubuntu on my second disk and type ifconfig in Terminal. It gives me this:

eth0      Link encap:Ethernet  HWaddr 00:11:6B:35:91:01  
          inet6 addr: fe80::211:6bff:fe35:9101/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5382 (5.2 KiB)
          Interrupt:169 Base address:0x6f00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14740 (14.3 KiB)  TX bytes:14740 (14.3 KiB)

I hope this information will be helpfull for you??

What do to next?

---

### Post by Urko on 2007-03-19
um....could enybody tell me solution for my problem or what to do neht please??? :confused:  :(

---

### Post by eljalill on 2007-03-19
Could you run the dhclient again, now that you made changes?

---

### Post by Urko on 2007-03-19
now thata i install ubuntu on my second disk and run dhclient in terminal still don't work:( 
it writes me this: 

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

:( :( :(

---

### Post by eljalill on 2007-03-19
Sorry my mistake.
Do 
sudo dhclient
Give your user password, when it asks you for one.

---

### Post by Urko on 2007-03-19
no problem just give me a minute to switch betwen system.. I'll be back at the moment

---

### Post by Urko on 2007-03-19
Dhclient still doesn't work :( :( 



Listening on LPF/eth0/00:11:6b:35:91:01
Sending on   LPF/eth0/00:11:6b:35:91:01
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by eljalill on 2007-03-19
This looks to me as if you were not offered an IP address form your router.

Is there any way you can access your router? Do you know whether it attributes IPs automatically, or whether you set them manually?
(Should be the same in windows and Ubuntu)

---

### Post by Urko on 2007-03-19
am....I think I don't have router but i have Dsl connection thru isdn...in windows all ip adress find me automaticaly except my TCP/Ip adress of my etherneth card (level/one vith realtek chip)

---

### Post by eljalill on 2007-03-19
I am not sure I understand. In Windows you set yourself the TCP/IP of your ethernet card? You open the connection settings and chose TCP/IP and type in a number like 192.168...etc yourself?
And the cable that is in your computer: where is the other end plugged in? In the wall? Or in a small box?

---

### Post by Urko on 2007-03-19
yes just like you describe..

---

### Post by Urko on 2007-03-19
cable is conected in a smal box which is conected into a wall....sorry for my bad english and understanding:(

---

### Post by eljalill on 2007-03-19
No problem... 
So, the situation is, that your router (which is the small box) does not give you an IP address automatically. But your computer needs an IP address to be able to talk to the router and also to access the internet. (The router is like a someone who stands at a gate to the internet. If you don't have a passport (IP address), he won't let you through). 

If you open Internet Explorer ot whatever other browser you are using, and type in the address bar 192.168.1.0, does that bring you anywhere?
If not, try 192.168.0.0 or 192.168.0.1 or 192.168.1.1 .

---

### Post by Urko on 2007-03-19
am so what should I do next??

---

### Post by eljalill on 2007-03-19
Well, my idea was to try to change your router settings to give you an IP automatically. If that is too complicated, than we just have to assign your computer an IP manually in Ubuntu. Although really it doesn't matte which one. 
But since you need to reboot anytime you want to go to the internet, changing the router settings might be easier.

---

### Post by Urko on 2007-03-19
sorry I din't see your post...i type all adresses into my internet browser but none of them binges me nowehere... error :confused:

---

### Post by Urko on 2007-03-19
so how do I change router settings in ubuntu ?:)

---

### Post by tom56 on 2007-03-19
Most routers have a webpage from which you can change their settings. The beauty of this is that it works exactly the same in Windows or Linux. Do you have the manual for the router? It should have the address for this webpage (something like [http://192.168.0.1](http://192.168.0.1)).

---

### Post by kvonb on 2007-03-19
When you were running Windows, did you click on a connection icon to "dial in"?

If you did, then you need to setup PPPoE.

The easiest way to find out is to call your internet provider and ask them how you connect, ask them if you have to use PPPoE, ask about the IP address you should use on your PC.

Kev :)

---

### Post by eljalill on 2007-03-19
Ok, then we try the other option.
When you go back into Ubuntu, you need to open system>application>networking . YOu will find the "system button" in the little bar on top.
In the network setting (the one I just told you about), you will find "Wired network". Click on the little box in front of that if it is not marked. If it is marked just leave it. Click on "Wired Network" and then on "properties", on the right side. An new little window should open. You click on "enable this connection" and then change the "automatic configuration" to "static IP address" (You should be able to chose). The enter the same numbers you also have in windows for IP address, subnet mask and gateway. Click on OK, and also on OK in the network setting window. 
Now open firefox and see whether it works.

And then tell me how it went, and where the problems were, if there were any. OK? Questions? Please ask.

---

### Post by Urko on 2007-03-19
ooo **** i don't have any manuals for router :( but if i call my internet provider will he give me router addres?

---

### Post by eljalill on 2007-03-19
It depends on the router not on the Internet provider, which address your router has. Maybe he knows, maybe he doesn't. But you don't need to change the router settings, it is just one of the options. You can also configure your connection in ubuntu as I said above, and you should be fine.
If you'd rather change the router settings, then look in the connection settings in windows for your gateway address, and try typing that into IExplorer.

---

### Post by tom56 on 2007-03-19
Yeah, elijalill's way will work just as well. Let us know how it goes.

---

### Post by Urko on 2007-03-19
beck eljali I done as you say. I manualy set ip adress in networking and enable wired connection than I start mozzila and try to go to internet but my connection still doesn't work:(  Should I type somewere my username and password?
Sorry for such a dumm questions but I realy don't know how to do things wright in Ubuntu :(
I wish establish internet connection in Ubuntu cause I wan't to use Linux instead windows

---

### Post by tom56 on 2007-03-19
What is the little box like? I'm beginning to think it's a modem and not a router. If it's a modem connected by ethernet (not USB)  you need to follow this - [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#adsl-pppoe](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#adsl-pppoe)

---

### Post by Urko on 2007-03-19
yes you are wright. it's a modem connected by ethernet. I will do as you post me than I'll tell if it's work. Thank you everyone for so far:)

---

### Post by Urko on 2007-03-19
Tom56 the instrusction that you give me works!!!!!! I am so happy now thah my internet connection finaly works in Ubuntu:) 
GUYS YOU ARE GREAT SPECIAL THANXS TO TOM56 AND ELJALILL.
YOU ARE THE KING'S OF THE KING'S!!!!!!!

THANX AGAIN:)

---

