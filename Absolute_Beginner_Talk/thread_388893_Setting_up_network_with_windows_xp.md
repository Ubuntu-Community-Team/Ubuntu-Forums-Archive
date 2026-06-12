---
title: "Setting up network with windows xp"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by acidfried on 2007-03-20
i'm just starting to use ubuntu so sorry if this question has already been answered. i have a wireless network setup at my house on windows xp pro. i'm tring to connect ti this network with a laptop running ubuntu. i've gotten to the point where i have a signal from the network but i can't connect to the internet. if anyone has any suggestions for me i would appreciate it.

---

### Post by acidfried on 2007-03-20
anyone? plz?

---

### Post by cowlip on 2007-03-20
Do you know what kind of wireless card do you have (name, driver, etc)?  Are you using Network Manager, any encryption on your network?

---

### Post by eljalill on 2007-03-20
Well, a little more information is needed here.
So, your XP Computer and your Ubuntu Computer both are suposed to connect to the same router?
Or is the XP computer the router for the ubuntu computer?

And you say, you are getting a signal from the network, how do you know?

---

### Post by acidfried on 2007-03-20
ok i have a cisco wireless network card in my laptop and a belkin router. the network i have set up works with windows fine with this adapter and laptop. i just installed ubuntu so i know little about it. i know i have a signal because at the top of the screen there's a network conncetion symbol that when i click it shows a signal stregnth when i click it. anything else you need to know please ask linux noob here. :)

---

### Post by acidfried on 2007-03-20
also my network connects to the internet through a windows xp computer

---

### Post by eljalill on 2007-03-20
So, you can ping your router and your other computer?
and if you type ifconfig in a terminal, you see your IP?

---

### Post by acidfried on 2007-03-20
well i typed ipconfig in this computer (the one that connects the network to the internet and i get some info do you need that?

---

### Post by eljalill on 2007-03-20
Well, I meant the ubuntu computer :) .

---

### Post by acidfried on 2007-03-20
i have one connection with a ip address named lo (dont know where it came from) says inet addr is 127.0.0.1  and mask is 255.0.0.0. the other has no ip address it's labeled eth1 (the one that says it has a signal)

---

### Post by eljalill on 2007-03-20
lo is loopback, and its your computer talking to himself, so that should always be there..;) But it doesn't connect you to the internet .
if you do iwconfig (on the same computer), what is the output?

---

### Post by acidfried on 2007-03-20
i get eth1 and eth0 with ieee 802.11 - ds essid:"networkname"mode :managed freq 2.442 ghz access point :mac address and some other random stuff

---

### Post by eljalill on 2007-03-20
So, you are actually connected to the network.. That's good.
if you type ping and then your XP computers adress into a terminal, and then wait a while and push "Cntrl C", is the output that packages have been transmitted succesfully?
Also you might want to do ipconfig again and post the whole output here. Because if you are connected, you should have an IP other than for lo.

---

### Post by acidfried on 2007-03-20
ok when i type ifconfig (on ubuntu comp in terminal)

eth1     link encap:Ethernet  HWaddr 00:07:0e:b3:81:83
           inet6 addr: fe80::207:eff:feb3:8183/64 Scope:link
           UP BROADCAST RUNNING MULTICAST   MTU:1500 metric:1
           RX packets:66 errors:7 dropped:0 overruns:0 frame:7
           tx packets:3 errors:8 dropped:0 overruns:2 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:9268 (9.0 KiB)  TX bytes:1156 (1.1 KiB)
           interupt:3 base address :0x100

---

### Post by eljalill on 2007-03-20
Funny thing that. I can't see an IP either.
Does ping work?

---

### Post by acidfried on 2007-03-20
what address should i ping?
or what should i type?

---

### Post by eljalill on 2007-03-20
Check on your windows computer, which IP it has, and which IP the router has (Gateway). 
Than go to your ubuntu computer and type:
ping 192.168. etc (the adress)
Hit enter and wait a little (a few seconds), then hit Cntrl C.

---

### Post by acidfried on 2007-03-20
ping 192.168.0.1 (192.168.0.1) 56(84) bytes of data
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=0.136 ms

---

### Post by acidfried on 2007-03-20
theres 8 like that then says
8 transmitted, 8 received 0 pct packet loss time 6998ms

---

### Post by eljalill on 2007-03-20
Well, that's great than...
So, I am thinking, you cannot connect to the internet, because your XP computer functions as a proxy.
So, try opening Firefox on your ubuntu computer, 
edit>preferences>network>settings,
and type the IP of your windows computer in as a proxy (manual configuration).

Does that help?

---

### Post by acidfried on 2007-03-20
what port should i use?

---

### Post by eljalill on 2007-03-20
Good question. Sorry didn't think about that, and I don't know.
If I am right, and it is the proxy thing, you could maybe find out form the proxy itself? But I am not sure how, sorry.

If you don't can't find that out, you have a few choices.
You can either wait for an answer form someone else, but that might take a while at least, because this thread is already so long, and people will assume your problem is solved.
Or you start a new thread with this more specific questions.
There are two questions, which you could ask:
Why is there no IP in ipconfig, if xou can ping successfully? (Or why is there no IP, if you are connected to the network, which is basically the same)
and: how do I find out the port from the proxy. (Amybe you also need to set up the windows computer as a proxy)

Or, you could change the setup of your network:
Connect the router to the wall; connect the XP Computer as you want (per cable probably if its a desktop), connect your ubuntu laptop wireless, and forget about the whole proxy port thing, which you then don't need any more.

I can probably help you with the last option.
OK? 
Sorry again... :(
But let know what you are going to do.

---

### Post by acidfried on 2007-03-20
gonna try to find out what port the windows proxy is running on thanks for all your help

---

### Post by t4thfavor on 2007-03-20
you should either disable the belkins router feature, or the XP routing feature. If they both think they are routers, chances are that they are both giving out dhcp addresses. Depending on which one is first in line (on the topology of the network) you will get an incorrect default gateway. 

You should try setting the Ubuntu laptop's IP manually with the correct default gateway. Which if i understand correctly is the XP machine. try it and see.
EDIT: Its under System>Administration>Networking><Interface> where interface is the wireless card
change where it says DHCP to Static, or Manual (I can't remember) then fill out the boxes accordingly. 

Also, I would use the belkin as the router, since it is smaller, and uses less power. That way you will not have to have the XP PC on all the time when you want to use your laptop only.

Just a thought though.


Hope this helps

---

