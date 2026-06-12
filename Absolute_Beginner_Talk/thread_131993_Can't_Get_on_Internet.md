---
title: "Can't Get on Internet"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by rextilleon on 2006-02-17
Hi,

Just loaded ubuntu and love it.  Only problem is I can't get on the Internet.  I have:

1. Linksys wireless card in laptop
2. Verizon Fios service with a D-Link wireless router
3. In Windows, I use DHCP

Any ideas of what I am doing wrong or is there a tutorial out there somewhere.  Thanks in advance.

---

### Post by kent41 on 2006-02-17
Hi

Have you tried to go to  System >  Adminstration> Networking  

To set up the wireless card ?

---

### Post by rextilleon on 2006-02-17
Yes I have---not sure what settings are necessary----I use the DHCP setting in the Configuration field and I checke3d Enable this connection.

---

### Post by kent41 on 2006-02-17
[QUOTE=rextilleon]Yes I have---not sure what settings are necessary----I use the DHCP setting in the Configuration field and I checke3d Enable this connection.[/QUOTE]

If you are using  Security you need to setup your network name (ESSID) and your KEY, Also you must check the DHCP box because you are using DHCP.
And don't forget to change from ASCII to HEX.

---

### Post by rextilleon on 2006-02-17
Thanks so much--where would I set up WEP and SSID--?

---

### Post by hcs on 2006-02-17
Hi there,

i'm very new in the world of linux i've used windows up to the present moment.
i've just installed the very new version of Ubuntu 5.10 but i can't figure out how to connect to the internet. i mean how to set up the internet connection.
I use ISDN.
Could anyone help me please :confused: 

Thanx in advance

regards
cs

---

### Post by rextilleon on 2006-02-17
Join the party----I'm in the process of getting information on how to set up my wireless but at this point I'm stuck--stay tuned until someone answer the question.  Dont worry about hijacking my thread--I'm in the same boat as you.

Kent, I went into the device manager and it appears as if ubuntu isn't recognizing my wireless card---under network interface it says unknown.

---

### Post by kent41 on 2006-02-17
[QUOTE=rextilleon]Thanks so much--where would I set up WEP and SSID--?[/QUOTE]

I guess I must ask the question do you have security set up on the router first.

If you don't have security set up on the router you don't need to worry about the SSID and KEY on the wireless card. 

Most routers come out of the box with no security setup at all.

Security is not necessary to get on line.

all you need to do to setup the card on Ubunto is to go to System> Administration> Networking> Connections> click on Wireless Connection device. Then click on **Properties** then click on box to Enable this connection then click on OK  Then click on ACTIVATE

Another question is did you get a CD with the router and did you setup the router.

---

### Post by hcs on 2006-02-17
HM, yeah, sorry, i don't want to spoil your thread 
i do apologize for that 8-[ 
let me know if you want me to open a new one!

regards cs

[QUOTE=rextilleon]Join the party----I'm in the process of getting information on how to set up my wireless but at this point I'm stuck--stay tuned until someone answer the question.  Dont worry about hijacking my thread--I'm in the same boat as you.[/QUOTE]

---

### Post by rextilleon on 2006-02-17
Nah, dont worry about it----we both might get some help here.  Linux seems pretty cool----now if I can only get on the net!

---

### Post by hcs on 2006-02-17
but you're on the net aren't you:D :-k 

[QUOTE=rextilleon]Nah, dont worry about it----we both might get some help here.  Linux seems pretty cool----now if I can only get on the net![/QUOTE]

---

### Post by sailor2001 on 2006-02-17
you have to go to lists.ndiswrapper.org and identifiy your linsky and download the chip from there...unzip and place the inf file on the desktop. Then in command:   cd Desktop
                 sudo apt-get install ndiswrapper-utils
       password:
                 sudo ndiswrapper -i NET8180.INF
                 sudo ndiswrapper -l
                 sudo dhclient

notice it always says cannot find driver, but disregard that

---

### Post by rextilleon on 2006-02-17
It works---all I did was through in an older wireless card that I had laying around and it appeared immediately--Thanks so much.

---

