---
title: "Completely Lost PLEASE HELP!!!"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Riddle31 on 2007-04-16
:-({|=  Hello,
I love ubuntu and the way it functions, i am like a new born child when it comes to linux. i am booting 6.10 Edgy eft. i am trying to get my wireless working, i have tried all the tutorials and other pages on this forum to find a solution, but most everyting sounds like another language. Could some one please, in lamens terms, explain how i can get my D-Link DWL- G122 rev.B1 workin. i don'y understand the ndiswrapepr thing.sorry if i sound like i am whinning, i would love to continue using linux, but i am COMPLETELY LOST.
:-({|=

Thanks

Hopeful a Ubuntu and Linux User for Life

Matt
:guitar:

---

### Post by Hallvor on 2007-04-16
Don`t know if it helps, but Feisty (beta) has better support for wireless drivers. Why don`t you burn a live-cd and boot it up? It might work.

---

### Post by Riddle31 on 2007-04-16
my friend gave me a burbed copy, where would i find fiesty (beta)???

---

### Post by n3tfury on 2007-04-16
> **Riddle31 said:**
> my friend gave me a burbed copy, where would i find fiesty (beta)???

[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/)

---

### Post by annda on 2007-04-16
feisty is here:
[http://releases.ubuntu.com/releases/feisty/](http://releases.ubuntu.com/releases/feisty/)

this is important:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

and i don't think you really need ndsiwrapper to get your card working. if feisty still has problems connecting out of the box, post back. i'm ALMOST sure it can be done without ndiswrapper (i installed a similar d-link card on my father's laptop, but now i can't remember exactly which it was).

---

### Post by Swab on 2007-04-16
This is a USB adapter right?  Not sure if that makes any difference to configuration, just wanted to point it out.

---

### Post by Riddle31 on 2007-04-16
yes i have qwest (local company) dsl with a wireless router, which in turn (hopefully) will go to my D-Link adapter.

---

### Post by SteveHoffmanUK on 2007-04-16
I have a D-Link DWL 520+ wireless PCI adaptor on my desktop connected to a Netgear wireless router, and it's always worked out of the box with Dapper and Edgy, so I'm wondering whether you need to go to the trouble of messing about with ndiswrapper or Feisty. OK, it's not exactly the same model as yours, but I think D-links are quite Linux-friendly.

Can you tell us exactly what you tried before getting involved with ndiswrapper?

For me, it was just a matter of clicking on System | Administration |  Networking [password]
then highlight 'Wirelss Connection' and click on 'Properties' then check the box that says 'enable this connection' and fill in the ESSID (netowrk name), Password type (hexadecimal), fill in the WEP key in 'Network password' (if you've set up your router with a key), then under Connection settings, leave it as Automatic Configuration (DHCP), then click on OK.

It should then work. Well, that's how mine did, anyway.Does this help, or am I just pointing out the bleedin' obvious which you've already tried?

---

### Post by Riddle31 on 2007-04-16
WE HAVE PROGRESS, BUT NOT MUCH!!! Dang. Now the light is on, on the D-Link, but no action. :(  I followed Mr. SteveHoffman's Instruction but nada. Just so you kknow there was no light before.

---

### Post by Riddle31 on 2007-04-16
Another quick question. What is an essid? and Why are there two wireless connection boxes under network settings..... Wireless Connection (wmaster0) and Wireless Connection (wlan0)

---

### Post by Riddle31 on 2007-04-16
OKAY!!! PROGRESS!!! it says im connected but when i try to pull up a web page i get an error in firefox that says. "server not found"

---

### Post by n3tfury on 2007-04-16
> **Riddle31 said:**
> OKAY!!! PROGRESS!!! it says im connected but when i try to pull up a web page i get an error in firefox that says. "server not found"

can you ping your router?

sounds like your dns is not setup correctly.

---

### Post by SteveHoffmanUK on 2007-04-17
Riddle31:

OK, that's some progress, and I think it means that you don't have to mess about with installing Feisty or using ndiswrapper. The ESSID (extended service set identifier) is the name you give the network when you set it up on your router. You must use the same name when setting up each wireless device that you want to connect to the router, otherwise you won't get a connection.

To ping your router click on System | Administration | Network tools, then click on the 'Ping' tab and in the 'Network address field enter the address of your router.  If you don't know that, check the instructions that came with your router. Most likely it will be 192.168.0.1 - that's what most routers use. Try that and tell us what happened. You should get five readings back of differing amounts of milliseconds.

---

### Post by Riddle31 on 2007-04-18
okay pinged..........
ROUND TRIP TIME STATS:
Min-0.07 ms
Average-0.07
Max-0.09

TRANSMISSION STATISTICS
Packet trsnmitted 5
packets recieved 5
successful packets 100%

was 192.168.0.66 not 192.168.0.1

---

### Post by ayenack on 2007-04-20
You may have encryption on your router. Do you know if you have?

As far as I know this card will work fine on Edgy but has some issues on Feisty Fawn.

I have used a D-LINK DWL 122 usb Adapter on Edgy and it worked fine. this is an example of how I did it.

Systems>Administration>Networking Double left click Wireless Networking you will see these three options.

Network Name: Belkin54g
Password Type: Hexadecimal
Network Password: This will be your routers network key.

No ndiswrapper is needed for this card it should work right out of the box. Also works fine with WEP encryption.

---

### Post by lamalex on 2007-04-20
if you can ping your router then encryption shouldn't matter. try and ping out of network, ping google or something, if you can ping the router but not google, you might have ISP problems.

---

### Post by Riddle31 on 2007-04-24
how do i ping google?:lolflag:

---

### Post by Happy_Man on 2007-04-24
Go to a terminal and do enter this:

```
ping www.google.com
```

Or, in fact, you can go to the place where you pinged your router, but instead of entering your router address, enter [www.google.com](www.google.com).

---

