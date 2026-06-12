---
title: "Apache....ip = timeout ...localhost OK"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by astra2000 on 2007-05-17
hello dudes, 
i'm new here, and my english is not so good, but here i go...

I install in my ubuntu php5, mysql, phpmyadmin, and apache2

so i create a webpage and in localhost runs ok, but if i try make my ip on the firefox adress bar than give me a timeout...

it's weird because i dont have a firewall and because my router its listen the port 80 to the server...

someone can give-me somme ideas???

tnks in advanced


(my english suks... i know):(

---

### Post by DaveyG on 2007-05-17
> **astra2000 said:**
> hello dudes, 
i'm new here, and my english is not so good, but here i go...

I install in my ubuntu php5, mysql, phpmyadmin, and apache2

so i create a webpage and in localhost runs ok, but if i try make my ip on the firefox adress bar than give me a timeout...

it's weird because i dont have a firewall and because my router its listen the port 80 to the server...

someone can give-me somme ideas???

tnks in advanced


(my english suks... i know):(

Hi there! are you referring to your private (lan) ip address i.e 192.168.2.10 or  the ip your ISP gave you i.e 85.21.7.03?

If you are running through a router try enabling dmz for your ip

Davey

---

### Post by astra2000 on 2007-05-17
> **DaveyG said:**
> Hi there! are you referring to your private (lan) ip address i.e 192.168.2.10 or  the ip your ISP gave you i.e 85.21.7.03?

If you are running through a router try enabling dmz for your ip

Davey


hello, tnks 4 the quick answer..

i'm talking about my external ip... like... 80.142.222.222  (isp ip)

i go try now with dmz

---

### Post by astra2000 on 2007-05-17
> **astra2000 said:**
> hello, tnks 4 the quick answer..

i'm talking about my external ip... like... 80.142.222.222  (isp ip)

i go try now with dmz

with dmz still the same :(

---

### Post by DaveyG on 2007-05-17
are you using a router? if so please could post the make and possibly the model as each router has different settings

---

### Post by astra2000 on 2007-05-17
> **DaveyG said:**
> are you using a router? if so please could post the make and possibly the model as each router has different settings

yes.. i'm using a router linksys WRT54G   it's is a wireless router and i'm conected now with wireless

---

### Post by DaveyG on 2007-05-17
> **astra2000 said:**
> yes.. i'm using a router linksys WRT54G   it's is a wireless router and i'm conected now with wireless

hmm, i just set up the same router at my data center to try out and i don't seem to be able to enable dmz on wireless... have you tried wired? also were you enable dmz it should show some numbers so you can have your ip go to a specific machine

Davey

---

### Post by astra2000 on 2007-05-17
> **DaveyG said:**
> hmm, i just set up the same router at my data center to try out and i don't seem to be able to enable dmz on wireless... have you tried wired? also were you enable dmz it should show some numbers so you can have your ip go to a specific machine

Davey


i dont have any probleme with the dmz on wireless... i just give the ip adress from my wireless machine and no problem...


but still give me a timeout on my ip.

i go now trying wired

---

### Post by esoterica on 2007-05-17
Your problem is in your router, not your Apache install, your trying to send packets into your network and it's seeing these as requests from an external source, you don't have your router properly configured so it doesn't know what to do with those packets being sent to it from the public side of it so it just drops them.

It's hard to understand if you even have the Apache web server set in the DMZ of your router settings or not, this will make it publicly accessable, you say you aren't using a Firewall but you are, your router is acting as a firewall, this is why you need to place the web server in the DMZ so your firewall doesn't block incoming requests to it.

I'd suggest you look up and read the documentation for your router, it will probably have the exact steps and configurations on the router you need to make in order to get it to work for you. Another important reason to read the documentation is because it will also likely contain very important security steps that you are going to want to be aware of.

Also be aware that many ISP's are not going to be very happy with what your trying to do here. Most people get away with it with no problems as long as traffic is low and it doesn't send up any red flags to alert your ISP that your doing this. If they see hi volumes of incoming traffic to your IP address though they may clip your connection. Usualy they do this because they want you to pay for the higher priced commercial or business accounts they probably offer.

---

### Post by astra2000 on 2007-05-17
> **esoterica said:**
> Your problem is in your router, not your Apache install, your trying to send packets into your network and it's seeing these as requests from an external source, you don't have your router properly configured so it doesn't know what to do with those packets being sent to it from the public side of it so it just drops them.

It's hard to understand if you even have the Apache web server set in the DMZ of your router settings or not, this will make it publicly accessable, you say you aren't using a Firewall but you are, your router is acting as a firewall, this is why you need to place the web server in the DMZ so your firewall doesn't block incoming requests to it.

I'd suggest you look up and read the documentation for your router, it will probably have the exact steps and configurations on the router you need to make in order to get it to work for you. Another important reason to read the documentation is because it will also likely contain very important security steps that you are going to want to be aware of.

Also be aware that many ISP's are not going to be very happy with what your trying to do here. Most people get away with it with no problems as long as traffic is low and it doesn't send up any red flags to alert your ISP that your doing this. If they see hi volumes of incoming traffic to your IP address though they may clip your connection. Usualy they do this because they want you to pay for the higher priced commercial or business accounts they probably offer.

very weird... i tryed wired and now works :D


but if try wireless dont works... it's dont  mather, if works wired, dann i leave it wired:lolflag:

tnks one mor time...

:guitar:

---

