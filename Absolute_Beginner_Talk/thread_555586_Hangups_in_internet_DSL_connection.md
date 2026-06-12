---
title: "Hangups in internet DSL connection"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by doronb2 on 2007-09-20
Hello,
i have Ubuntu on my laptop for some time now and i have a most annoying problem.
i always have hangups in my internet ADSL connection.
i'm using a regular modem that i recieved from my internet provider and in XP i used the usual dialer that windows has.
when i installed ubuntu i managed the internet connection with PPPOECONF and it looked good, username, password and all, yeepee!
but in 10 minuted i disconnected again.
so i press on the "wired connection network" icon -> "Dial up connections" -> "Connect to dsl provider via modem" and i have internet for 10 minuted again.
so on and so on every 10 minutes.

it driving me CRAZY!!
You know how long it tok me to complete the Eclipse installation for example???

i don't know what to do...
i formatted the computer and installed Kubuntu but no good. same problem.

now i have Ubuntu and windows in dual-boot and Ubuntu is disconnecting every 10 minutes but Windows works fine...........

(actually i have to press "disconnect" and then "connect". if i press only "connect" i still can't get to the internet)

PLEASE HELP!

---

### Post by chrux on 2007-09-20
I have the exact same problem, only its a 5year old PC.. incredibly annoying problem.

Help is very much appreciated.

---

### Post by Pumalite on 2007-09-20
Very easy guys: get a router providing DHCP. The router will prevent the DSL provider from disconnecting every 10 min. ( They are known to do that. That's how they sell more than what they have)

---

### Post by Pekkaniska on 2007-09-20
I have the same problem and i do have a dhcp router. Linksys wrt54gl.  When i release dhcp and renew dhcp on the router, it works again for 5-10 minutes. I Tried already to put the dns to 4.2.2.1 and 4.2.2.2. so it isn't the dns. I tried searching the web for two days now and am getting very frustrated. Any ideas are taken.

---

### Post by Daveth on 2007-09-20
do you guys all use the same isp? and how far are you from the nearest phone exchange- a broadband engineer I collared on our office a few months ago reckoned that (in the UK at least) any distance over 4 miles from a phone exchange and you would start to get break up in the carrier signal strength (from recollection of the conversation).

---

### Post by Pumalite on 2007-09-20
> **Daveth said:**
> do you guys all use the same isp? and how far are you from the nearest phone exchange- a broadband engineer I collared on our office a few months ago reckoned that (in the UK at least) any distance over 4 miles from a phone exchange and you would start to get break up in the carrier signal strength (from recollection of the conversation).

Interesting tidbit.

---

### Post by doronb2 on 2007-09-20
I think that i soved the problem.
Someone told me to set my connection to ststic ip to 10.0.0.10 and the subnet to 255.0.0.0 and then i have not any more hangups!!!!

But now i have other bug...
Now when i press the network icon i cant see the "dial up connections" and the mark "Wired connection", and i can see only the "manual configuration" .
I can see the "dial up connections" only if i enter my wireless pcmcia card (that i don't need it at home, i have a wired connection at home) i can see "Wireless connection" and then also the "dial up connections".
Also, the network icon is seemed to be connected also if there isn't any connection, wired or wireless, to it. it shows me only the "manual configuration" always, whether i pluged the wired connection or not.

What can i do know??

---

### Post by chrux on 2007-09-21
The internet works fine on my windows machine, both using the same ADSL ethernet modem (but not at the same time). So its  NOT my ISP doing this, altho they are assholes ;)

And I doubt we're all on the same ISP, I'm from Malaysia.

---

