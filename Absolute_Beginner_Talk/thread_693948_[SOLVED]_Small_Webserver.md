---
title: "[SOLVED] Small Webserver"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-02-11
Hey everyone, I could use alot of direction right now regarding building a Websever.

I have two churches that want me to build a webpage for them which is the easy part but they rather not host it with an outside service and asked me if I could host it.  They're both willing to chip in money for the box but the only webserver I have ever built was through Windows Enterprise 2003 (which pretty much automated the installation lol)   

I want to build this server from the ground up on Linux and need help...It needs to be able to host 2 Domains..
[LIST=1]
[*]I have business class cable, should I ditch my router and setup up a cheapo DHCP server to alleviate network traffic or am I fine with just a regular router?  (I think I eventually want to get a hardware firewall)
[*]Being that I'm only familiar with Enterprise 2003's GUI, is the software offered by Ubuntu only strictly terminal or is it like Ubuntu's Desktop version where its mixed?
[*]Where do I start and what should I be aware of?
[/LIST]
Thanks for any help...  and on a side note, I would prefer to run DHCP... I feel you have better control with policies and whatnot /shrugs  maybe I'm completely wrong.....

---

### Post by dstew on 2008-02-11
> I have business class cableDoes your agreement with your ISP allow you to host a website? You should check first.

---

### Post by Dr Small on 2008-02-11
Check out XAMMP, it's simple to install and use, and is powerful :)
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

---

### Post by Aysah on 2008-02-11
> **dstew said:**
> Does your agreement with your ISP allow you to host a website? You should check first.

yes it does... they provide me with a static IP and open port 80 and 25 for these purposes...

---

### Post by Aysah on 2008-02-11
> **Dr Small said:**
> Check out XAMMP, it's simple to install and use, and is powerful :)
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

so am I installing Ubuntu Desktop and adding this in and then stripping down all the extra programs OR am I installing Ubuntu Server and then adding this in for additional functionality?

---

### Post by Dr Small on 2008-02-11
> **Aysah said:**
> so am I installing Ubuntu Desktop and adding this in and then stripping down all the extra programs OR am I installing Ubuntu Server and then adding this in for additional functionality?
Either or will work, but it mainly depends upon you.
If you don't have a feel for the command line yet, then the server edition may seem daunting to you.

If it was my server (it would have to be my second one :) ) I would install the Server Edition, but that's just my personal prefference :)

Dr Small

---

### Post by Aysah on 2008-02-11
> **Dr Small said:**
> Either or will work, but it mainly depends upon you.
If you don't have a feel for the command line yet, then the server edition may seem daunting to you.

If it was my server (it would have to be my second one :) ) I would install the Server Edition, but that's just my personal prefference :)

Dr Small

definitely something to consider... I think for the time being I'm going to go with option 1 to get things going a little quicker and then setup a Pentium II dummy server and experiment with Server Edition.  

[LIST=1]
[*]Also, what should I do for security??  recommend any firewalls?
[*]And, should I stick with a home router or setup a DHCP server?  And if I should go DHCP, would it be unwise to throw everything on one server or should I leave DHCP on its own?
[/LIST]

---

### Post by LeChacal on 2008-02-11
For security I would look at building a hardware firewall that splits up your network traffic between the server(s) and the rest of your network then put the router behind the firewall for DHCP or put in a switch and let the firewall do DHCP. There are a lot of Linux distros out there for firewalls take a look, I like [Ipcop]("http://ipcop.org/") it is easy to setup and and doesn't take that powerful of a PC to run on and you get a lot of options with it and if and option doesn't come built in there are add-ons other have built or you can build your own.

---

### Post by Dr Small on 2008-02-11
1. iptables comes installed by default on Ubuntu, that is your firewall. If you wish to configure it and open / close ports, you would need Firestarter, the GUI tool for Iptables.

2. I have never had much traffic on my server, so I do not know what would be best for you here. I simply run a D-Link router which is enough for all my needs, and it should be for you too.

---

### Post by Aysah on 2008-02-11
> **LeChacal said:**
> For security I would look at building a hardware firewall that splits up your network traffic between the server(s) and the rest of your network then put the router behind the firewall for DHCP or put in a switch and let the firewall do DHCP. There are a lot of Linux distros out there for firewalls take a look, I like [Ipcop]("http://ipcop.org/") it is easy to setup and and doesn't take that powerful of a PC to run on and you get a lot of options with it and if and option doesn't come built in there are add-ons other have built or you can build your own.

so basically we're saying..

---> ISP MODEM --->  Ipcop w/ DHCP capability ---> Switch ---> Personal Computers & WebServer ???

Not trying to sound redundant if I am; I just want to make sure I follow what you're saying...

---

### Post by LeChacal on 2008-02-11
Yes, basically that is what I am saying, my comment is that when you setup the firewall (be it Ipcop) you can split it up into multiply networks so that the server(s) is on one network and the other PCs are on a different network. This would help protect the rest of you network because someone can't connect to your server then jump over to a different PC because they will be on separate networks.

--> ISP MODEM ---> Ipcop (split)

network #1  DHCP capability ---> Switch/Router --->PersonaComputers 
network #2  static IP ---->  WebServer

---

### Post by Aysah on 2008-02-11
> **LeChacal said:**
> Yes, basically that is what I am saying, my comment is that when you setup the firewall (be it Ipcop) you can split it up into multiply networks so that the server(s) is on one network and the other PCs are on a different network. This would help protect the rest of you network because someone can't connect to your server then jump over to a different PC because they will be on separate networks.

--> ISP MODEM ---> Ipcop (split)

network #1  DHCP capability ---> Switch/Router --->PersonaComputers 
network #2  static IP ---->  WebServer


Sorry for asking so many questions but I think I almost understand this...

I now understand why I should assign my WebServer with a unique IP outside of the Address Pool of my personal home network.  Now when assigning "network #1" and "network #2" are they both physically connected to the Ipcop computer??  In that case I need 3 NIC cards??  (one for the modem, another for the switch and yet another going straight to my webserver?)

Again I'm sorry for all mayhem of questions lol..

---

### Post by LeChacal on 2008-02-11
> In that case I need 3 NIC cards?? (one for the modem, another for the switch and yet another going straight to my webserver?)


Yes this is exactly what you need and with Ipcop you can have more then three, say you also wanted to set up a wireless network and have it split off from the other two you put in another NIC and have that go to a wireless appliance. When you run the setup you see all this, it is easy, you might just want to read some of the help manuals also.

---

### Post by Aysah on 2008-02-11
> **LeChacal said:**
> Yes this is exactly what you need and with Ipcop you can have more then three, say you also wanted to set up a wireless network and have it split off from the other two you put in another NIC and have that go to a wireless appliance. When you run the setup you see all this, it is easy, you might just want to read some of the help manuals also.

wow.... that's some pretty interesting stuff... Thanks alot for all the help man!  I'm going to read up on all this and start fiddling around with this tonight..

---

