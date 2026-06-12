---
title: "Another No internet connection please help"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by I samz I on 2008-01-06
Well i have no internet on the Ubuntu 7.10 that i installed last night  i have a ethernet cable connected to a modem ( i also have a router but i need to get a programme off the internet to install the USB wireless adapter for the desktop ) i can do that ifconfig fine but when i try to do ifconfig eth0 up it says permission denied can eney one help me please i would be very gratefull

thank you , I samz I

and by the way this is my first linux OS so you will have to dumb everything down for me thanks .

---

### Post by thelatinist on 2008-01-06
Try:

```
sudo ifconfig
```

The sudo command  runs terminal commands with superuser permissions, which should allow it to work.  It will ask you for your password.

---

### Post by I samz I on 2008-01-06
okay yea ive done that then ive done "sudo ifconfig eth0 up" and it just doesnt do eneything after that

---

### Post by thelatinist on 2008-01-06
> **I samz I said:**
> okay yea ive done that then ive done "sudo ifconfig eth0 up" and it just doesnt do eneything after that

It doesn't do anything?  Does it give you an error message?  Or does it just return you to the terminal prompt?  If the latter, that's the expected result.  Your eth0 interface should be activated (if it was not already activated)

Now just run:

```
ifconfig eth0
```

and post the results here.

---

### Post by I samz I on 2008-01-06
it says (since its on the desktop and im on the lap top i gota write it all out )

sam@sam-desktop: -$ ifconfig eth0 
eth0              link encap:Ethernet HWaddr 00:13: D4:B8:C6:8E
                     inet6 addr: fe80: :213:d4ff:feb8:c68e/64 scope:link
                     UP BROADCAST RUNNING MULTICAST MTU:1500  metric:1
                     RX packets:6 errors:0 dropped:0 overruns:0 frame:0
                     TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
                     collisions: 0 txqueuelen: 1000
                     RX bytes: 2072 (2.0 KB)    TX  bytes: 5044 (4.9KB)
                     interrupt:22 Base address : 0xcc00


Sam@sam-desktop: -$

(sorry its hard typing all that out when you have to turn your neck every so often)

---

### Post by stump138 on 2008-01-06
if your home networking is a 192.168.x.x network with a 255.255.255.0 netmask try the following: (you may have to substitute in different addresses depending on your network)
```
sudo ifconfig eth0 192.168.0.10 netmask 255.255.255.0 gateway 192.168.0.1
```

---

### Post by I samz I on 2008-01-06
> **stump138 said:**
> ```
sudo ifconfig eth0 192.168.0.10 netmask 255.255.255.0 gateway 192.168.0.1
```

okay ive done the above and it says 

Gateway: Unkown host 
ifconfig '--help' gives usage information
sam@sam-desktop: -$

---

### Post by stump138 on 2008-01-06
the gateway address will be the address of your router.  If you know the address of your router substitute it for gateway address above.  If 192.168.0.1 is your router's address, the I would start troubleshooting the router, as it would appear it is not connecting:)

---

### Post by I samz I on 2008-01-06
i didnt realy understand that can you repeat it please :S (make it simpler please =])

---

### Post by I samz I on 2008-01-06
im on my wireless internet on my laptop and when i checked the ip adress it was 192.168.11.2  subnet mask is 255.255.255.0 and default gate way is 192.162.11.1 is that eney help but this information is of my laptop and i have Ubuntu installed on my desktop

---

### Post by stump138 on 2008-01-06
Your gateway address is what tells the computer where to find the internet.  It is address of your router :)  If that address is set wrong, you won't get internet.  In your post above, it shows that you have a working network card that currently doesn't have a regular ipv4 address.  If you are using IP addresses assigned from your router via DHCP, then you aren't connecting to the router (bad cable, connection, bad port etc..) 

In short you need 3 things to connect out properly, an individual address, a subnet and a gateway.  You can run a ifconfig from a diff linux computer in your house to get that information, You can also get your subnet and gateway info from a windows computer by typing

```
ipconfig /all
```

at a command prompt, then transfer that information to the information you provide your linux computer when you do the ifconfig command.

hope that clears things up a bit about what we are all looking for :) *and sorry if this was stuff you already know :)

---

### Post by stump138 on 2008-01-06
okay than replace the gateway and subnet information in your ifconfig statement

```
ifconfig eth0 192.168.11.6 netmask 255.255.255.0 gateway 192.168.11.1
```

see what that does :)

---

### Post by I samz I on 2008-01-06
:(im rather lost since im an uber newb at this ... can eney one help me

---

### Post by I samz I on 2008-01-06
it said that gate way unknown host
and ifconfig '- -help' gives usage information

---

### Post by stump138 on 2008-01-06
ok try this :)  Re-check all of your cables.  Make sure that the lights on your network card are on right where you plug in the cable at:) (should be a solid green/yellow light and a blinking light).  Check your router to see that there is a light or number on corresponding to the cable that you have plugged into the linux computer.

if that is the case and the adrress on the laptop is 192.168.11.2 and the gateway is 192.168.11.1. try:
```
ping 192.168.11.1
```
press ctrl +c to stop it.

depending on whether it times out or not, we can start to get a picture of what is going on:)

---

### Post by I samz I on 2008-01-06
but what if the linux computer is connected str8 to the modem? what then?

---

### Post by stump138 on 2008-01-06
you need a router :) connecting straight to the modem would be the problem (unless we are using different language/lingo:) ) 

You can try un-plugging the laptop (if it is not on wireless) and plugging the linux computer in it's place. If you are on wireless, there should be ports on the wireless broadcast unit, that is where you want to be plugged in at:)

---

### Post by I samz I on 2008-01-06
so i need to connect to the router then form the router to the modem?
because at the moment im connected str8 to the modem?

---

### Post by I samz I on 2008-01-06
rite i starting to understand now
 i have to find another ethernet cable now :(

---

### Post by stump138 on 2008-01-06
Yes, there should be a line from your modem to the in port on your wireless router, then the cables to your hard-wired computers should come from the wireless router

modem->router->computers

:)

---

### Post by I samz I on 2008-01-06
yeh okay im still trying to find another ethernet cable under my bed some where lol

---

### Post by thelatinist on 2008-01-06
Please clarify your setup.  Your PC is connected directly to a cable/dsl modem by ethernet cable, and the modem is connected directly to the wall by either phone cable (for dsl) or round coaxial cable (for cable modem).  Is this correct?  And your cable/dsl modem has only one ethernet out port and no antennas or anything else (i.e., no built-in router)?

If this is true, you do not NEED a router, and for debugging purposes it might just make things more difficult.  Get your connection working first, then install the router.

---

### Post by I samz I on 2008-01-06
okay i have got the ethernet cable and its pluged into the Router and its pluged into my desktop ( linux computer)

---

### Post by I samz I on 2008-01-06
yay internet!!! thanks man i love u so much!

---

### Post by stump138 on 2008-01-06
big grats :)

---

### Post by thelatinist on 2008-01-06
Solved before I could post my next suggestion.  Congrats.  Please remember to set this thread [Solved] using thread tools.

---

