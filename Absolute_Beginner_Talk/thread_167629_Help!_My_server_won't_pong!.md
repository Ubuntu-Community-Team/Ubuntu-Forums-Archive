---
title: "Help! My server won't pong!"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by __a on 2006-04-28
I have a server on my local network running on a specific ip-adress. The ip shows up in my router and in the server iself, and I can connect   to it "externally" (ssh, webmin etc) using my no-ip.org account.
BUT it wont answer when I ping its local ip from my laptop!! ..meaning I have to go all the way through some no-ip.org server to fetch my files from the server ](*,) 

Help anyone? :confused:

---

### Post by matthewv on 2006-04-28
maybe some problem on your laptop, because if your router can see the ip address, the rest of the your network should be. Maybe check some firewall settings, etc.

---

### Post by enopepsoo on 2006-04-28
just check the router and if you really can't find the ip adress just hook up a monitor and type in
```
ip adress
```

---

### Post by __a on 2006-04-29
[QUOTE=enopepsoo]just check the router and if you really can't find the ip adress just hook up a monitor and type in
```
ip adress
```[/QUOTE]
the "ip adress" command only returns
```

Object "adress" is unknown, try "ip help".

```

After doing some more testing I have been able to determine that booth my ubuntu laptop and my ubuntu server can ping my Windows desktop. But NONE of the ubuntu boxes can ping eachother?!?! :-k 


And by the way, no firewalls are enabled...

---

### Post by cwaldbieser on 2006-04-29
[QUOTE=__a]the "ip adress" command only returns
```

Object "adress" is unknown, try "ip help".

```

After doing some more testing I have been able to determine that booth my ubuntu laptop and my ubuntu server can ping my Windows desktop. But NONE of the ubuntu boxes can ping eachother?!?! :-k 


And by the way, no firewalls are enabled...[/QUOTE]
I think he meant
```

$ ip address

```

Are your boxes all connected on the same subnet?  Are the Ubuntu boxes running any kind of firewall?

---

### Post by __a on 2006-04-29
[QUOTE=cwaldbieser]I think he meant
```

$ ip address

```

Are your boxes all connected on the same subnet?  Are the Ubuntu boxes running any kind of firewall?[/QUOTE]

What I do is that I log on to my server using ssh and the no-ip.org service. When logged in I type "ip adress", and get that very response. Am I doing something wrong?

All computers connect to my D-Link router. Ubuntu boxes through wlan, desktop through ethernet.

I have not configured any firewalls on my ubuntu-boxes so i suppose there are none running. :confused: 

Tomorrow I am going to test weather my desktop can ping any of the linux-boxes and see what happens.

I also got this other idea; could "ponging" be turned of someway, or might it be my router that stops the signals for some reason? Any tips of how to localise the problem (pc or router)?

---

### Post by __a on 2006-04-30
OMG! this mystery is turning really wierd: I tested pinging my linux boxes from the desktop, and they both answerd?!!? :???:

---

### Post by __a on 2006-05-01
Come on.. surely someone has an idea!? ..please :(

---

### Post by CiGiK on 2006-05-01
South African 'Help' Arrives:
A few things to check - your user group should be common - i.e. if it's defaulted to MSHOME - make sure the laptop is also a member of that group
Your server's address should be 192.168.0.1 with a loopback of 127.0.0.1 - if the laptop is set differently - it's not going to connect directly.
Try giving the laptop a direct (not automatic) ip address - i.e. 192.168.0.50
....and if none of that works...take it down the road and burn it... :-)

---

