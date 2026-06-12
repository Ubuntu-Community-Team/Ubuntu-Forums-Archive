---
title: "Edgy and wireless card"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by mosedavid on 2006-12-15
Hi to you all,

I have recently taken the plunge and installed edgy on my laptop (MV Mobeus - Rock based).  Everything works except the neworks.  The ethernet port is damaged (broken pin?) so I know why that doesn't work but although my inbuilt wireless card is recognised I still cannot connect, ping etc.

I had windows xp home on before and after i installed the driver, put my hex key in and chose the correct network i was up and running.

The wireless card shows up as ralink rt2500 802.11g.   It goes to a dlink airplus G wifi router and that goes into a netgear 4 port modem router - sorry don't know what model that is.

The wifi airplus is set to 'shared' with a 128bt encription in hex.  It is also mac addressed just for my laptop.  In edgy i set the ESSID correctly, put my Hex key in and set it to DHCP.

Due to an overfamilurarity with windows i have to hold my hands up and say i know nothing of linux other than what i have picked up from these forums looking for answers.  There are loads of posts on the rt2500 card but i couldn't find anything in plain english.

I have tried iwconfig ra0, sudo lshw, ifconfig -a, iwlist scan, to try and find some answers..

[LIST=1]
[*]The wifi card hasnt picked up an ip address from the DHCP server (netgear router).  This worked fine before in XP.

[*]In the connection properties applet the support tab only shows the mac address - no IP

[*]There is 0 signal strenth

[*]The driver edgy installed was RT2500STA
[/LIST]

I would (and can) add the printouts from the terminal if it will help but i havent due to no easy way of getting the info from one pc to another short of burning a cd.

I'd really like to get this to work.  A computer is pretty much useless these days without the internet.  If i cant get it to work i will have to put xp on again :(  and thats the last thing i want to do.  If there is no solution to this can anyone suggest an alternate linux dist that they think would just work.

thax for reading and maybe someone can lend a hopefully X windows user a hand.

---

### Post by mosedavid on 2006-12-15
to add - the network card is MSI 6833

[http://www.msicomputer.com/product/p_spec.asp?model=MP54G2]("http://www.msicomputer.com/product/p_spec.asp?model=MP54G2")

---

