---
title: "Internet via Ubuntu"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by AKPAKP on 2008-03-30
Please give me advice on connecting internet via Ubuntu
I have a BSNL Broadband connection...connected by a ext. modem....

---

### Post by superprash2003 on 2008-03-30
is it on ppoe mode or bridged mode?

---

### Post by AKPAKP on 2008-03-30
For XP  i used to connect via a pppoe connection

---

### Post by superprash2003 on 2008-03-30
you mean that your internet works as soon as you switch on right?

---

### Post by AKPAKP on 2008-03-30
Yes its a broadband & can be switched on in 4-5 sec...

---

### Post by superprash2003 on 2008-03-30
ok.. go to the ubuntu terminal and type ifconfig and post results here

---

### Post by AKPAKP on 2008-03-30
How can i write a file to a cd??

---

### Post by superprash2003 on 2008-03-30
why not solve one thing at a time!!! .. there is a good cd/dvd burning software called k3b you can install it via synaptic ... ifconfig output please

---

### Post by AKPAKP on 2008-03-30
no i have to transfer the output from the PC to the laptop thats why...i managed to burn

eth0      Link encap:Ethernet  HWaddr 00:16:76:41:A6:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:16:76:41:A6:68  
          inet addr:169.254.6.102  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by superprash2003 on 2008-03-30
oh..sorry about that..
go to system->adminsitration->Network .. then in the Connections tab you should see Wired Connection(eth0) then click on properties and set configuration to "AUTOMATIC CONFIGURATION(DHCP)".. that should work, if it doesnt , do that and then post ifconfig after that

---

### Post by AKPAKP on 2008-03-30
eth0 Link encap:Ethernet HWaddr 00:16:76:41:A6:68 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
ine6 addr: fe80::216:76ff:a668/64 Scope:link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:5133 (5.0 kb)
Interrupt:20 Base address:0xc000 

eth0:avah Link encap:Ethernet HWaddr 00:16:76:41:A6:68 
inet addr:169.254.6.102 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:20 Base address:0xc000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:748 (748.0 b) TX bytes:748 (748.0 b)

---

### Post by AKPAKP on 2008-03-30
--------------------------------------------------------------------------------
This one is correct 


eth0 Link encap:Ethernet HWaddr 00:16:76:41:A6:68 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
ine6 addr: fe80::216:76ff:a668/64 Scope:link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:5133 (5.0 kb)
Interrupt:20 Base address:0xc000 

eth0:avah Link encap:Ethernet HWaddr 00:16:76:41:A6:68 
inet addr:169.254.6.102 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:20 Base address:0xc000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:748 (748.0 b) TX bytes:748 (748.0 b)
__________________

---

### Post by superprash2003 on 2008-03-30
cool.. so now you are getting an ip.. isnt your internet working??? if not.. then type ping google.com and post results here..

---

### Post by AKPAKP on 2008-03-30
ping:unknown host google.com

---

### Post by superprash2003 on 2008-03-30
go to [http://192.168.1.1](http://192.168.1.1) and type admin as username and password.. there under WAN does it say connected?? which modem are you using?

---

### Post by AKPAKP on 2008-03-30
Dataone 
Smart ATX MT841

---

### Post by superprash2003 on 2008-03-30
ok do you see WAN settings?? under HOME or something..

---

### Post by superprash2003 on 2008-03-30
actually it will be there in the main page itself just go to [http://192.168.1.1](http://192.168.1.1) type admin as username and password then tell me if you see connected.. and if you see an ip like 59.x.x.x or 117.x.x.x ..

---

### Post by AKPAKP on 2008-03-30
There are a lot of pages

In the first page.....there is a ip addr....192.168.1.1
it is tthe Basic page

---

### Post by AKPAKP on 2008-03-30
WAN Interface:  
 
 
PVC No 
  VPI/VCI 
  IP Address 
  Subnet 
  Gateway 
  Encapsulation 
  Status 
 
 
PVC-0  
  0/35 
  --- 
  --- 
  --- 
  Bridged  
    
 
 
PVC-1  
  8/35 
  --- 
  --- 
  --- 
  Bridged  
    
 
 
PVC-2  
  0/100 
  --- 
  --- 
  --- 
  Bridged  
    
 
 
PVC-3  
  0/32 
  --- 
  --- 
  --- 
  Bridged  
    
 
 
PVC-4  
  8/81 
  --- 
  --- 
  --- 
  Bridged  
    
 
 
PVC-5  
  8/32 
  --- 
  --- 
Bridged

---

### Post by AKPAKP on 2008-03-30
this was there under WAN Interface

---

### Post by superprash2003 on 2008-03-30
in that page itself at the bottom you will see WAN INTERFACE . what do you see under PCV-0 0/35  .. do you see the ip there??tell me the STATUS and ENCAPSULATION

---

### Post by AKPAKP on 2008-03-30
PVC-0  
  0/35 
  --- (IP addr)
  --- (Subnet)
  ---(gateway) 
  Bridged  (Encaps.)

---

### Post by AKPAKP on 2008-03-30
Status is ticked for all

---

### Post by superprash2003 on 2008-03-30
ok buddy you are using bridged mode.. not ppoe mode..so your first answer was wrong..you need to change to ppoe mode.. in that 192.168.1.1 page go to Basic ->Connections on left panel then next to PVC-0 0/35 click on edit and enter the username ( i.e. mkdas@dataone) and password ( provided by BSNL). Click on Apply.
vi. Save the configuration by clicking on Save All on left panel. 

PS:if you are a new user its @bsnl.in .. old user it is @dataone.in  ..if both dont work then try @dataone or just username 

ONCE you configure ppoe mode.. you dont have to dial from your computer.. just switch on your modem and internet works.

---

### Post by AKPAKP on 2008-03-30
there is nothing like edit.....

---

### Post by superprash2003 on 2008-03-30
its in the form of a pencil icon

---

### Post by AKPAKP on 2008-03-30
there is a notebook icon on right side

when i click

I get Bridge properties:

---

### Post by superprash2003 on 2008-03-30
From your modem setup page ([http://192.168.1.1](http://192.168.1.1))

- Select Basic > WAN Settings from the navigation tree.
- Click the edit icon (pencil) in fromt of PVC-0
- Enter the following settings:
... Operation Mode = Enable
... VPI = 0, VCI = 35
... Mode = PPPoE
... Encapsulation = LLC
... Default Route = Enable
... IGMP = Disable
... Trafic Index = 0
... Service Name = <leave blank>
... Username = <your bnsl username>
... Password = <your bsnl pwd>
... IP Unnumber = Disable
... Configured MTU = 1500

Then click Submit.

Very Important:
- Select Tools > Save & Reboot from the navigation tree
- Select Save and click Submit to save your configuration
- Select Reboot and click Submit to restart the modem.

PS:remember what i said abt BSNL USERNAME .. try all combinations incase..

---

### Post by superprash2003 on 2008-03-30
yea.. its that notebook icon :D

---

### Post by AKPAKP on 2008-03-30
There are only two ortions
Bridge properties: 
 
 
(1)  VPI/VCI: 
  0/35   
 
(2)  Encap.: 
 LLC  or VcMux

---

### Post by superprash2003 on 2008-03-30
you need to change mode from bridged to ppoe.. all other options should come

---

### Post by AKPAKP on 2008-03-30
Thnk You verey much.....i did it.......
You did it....

I made a new pppoe connection & then connected......now accesing net via ubuntu....thankyou very much

---

### Post by superprash2003 on 2008-03-30
cheers!!

---

### Post by jalski on 2008-03-30
I was just curious reading the conversation here. Amazing! I am about to install Ubuntu but I was curious about the issues that would affect me. And going through this thread is really inspiring. People helping out each other. Hahah...welcome to the world of Linux, Open source and altruism! Cheers to you guys!

---

