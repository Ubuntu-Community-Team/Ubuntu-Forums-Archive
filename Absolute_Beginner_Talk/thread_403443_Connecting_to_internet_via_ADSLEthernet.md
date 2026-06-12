---
title: "Connecting to internet via ADSL/Ethernet"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by mcteethinator on 2007-04-07
Howdy. I brought a new computer today, and I thought this would be the best time to install Ubuntu. I'm just running it off the Live CD at the moment just in case. I'm trying to get on the internet via my wireless D-link DSL-G604T modem. This new computer doesn't have a wireless card so I'm plugging it in via Ethernet. It says that the Ethernet cable is plugged in + working and all the appropriate lights are on that says the modem is working (Obviously it is because I'm typing this from my MacBook). I'm also able to successfully get on the internet via Windows XP just by plugging Ethernet in. Yet I can't get on the internet on Ubuntu. What do I need to do to get it working?

---

### Post by alkat on 2007-04-07
Maybe it has to do with the ethernet card on your PC. 

Use the following command from a terminal to see if the card is working or not:

$ sudo ifconfig

It should display the network cards that Ubuntu can see on your system.
If  no card is displayed then I think you should load the modules for your card, provided it's supported by Linux.

The following commands will show you the hardware installed on your machine:

$ sudo lspci

and

$ sudo lshw

They should give you information also on the ethernet card. When you discover the model of your card, google for it or write here to see which module is needed to make it work. Once you know the name of the module, load it with:

$ sudo modprobe name_of_module

Then pull up the card with:

$ sudo ifconfig eth0 up  <-- eth0 may change on your system and be eth1 for instance

And try to connect to the network again, maybe just pinging your router at first.

Hope this helps.
Ale.

---

### Post by mcteethinator on 2007-04-07
Well the Ethernet thing is "MCP51 Ethernet Controller nVidia Corporation". I don't know anything about modules + I can't find what module to do on Google. How do I ping my router?

---

### Post by alkat on 2007-04-07
> **mcteethinator said:**
> Well the Ethernet thing is "MCP51 Ethernet Controller nVidia Corporation". I don't know anything about modules + I can't find what module to do on Google. How do I ping my router?

Are you running Ubuntu Edgy or any previous version? It seems your card was not well supported in Ubuntu - if you can read Spanish, here are a couple of discussions on the topic (the only solution being to upgrade to Edgy): 
[http://foros.ubuntu-cl.org/viewtopic.php?p=5143](http://foros.ubuntu-cl.org/viewtopic.php?p=5143)
[http://www.ubuntu-es.org/index.php?q=node/26583](http://www.ubuntu-es.org/index.php?q=node/26583)

What's the output of the ifconfig command? Can you post it here?


To ping an IP (such as the one of your router) you just need to issue the command:

$ ping ip_to_ping

To ping my router I use the following (the IP changes according to the router you have):

$ ping 192.168.0.1

---

### Post by benson444 on 2007-04-08
I've got that ethernet controller on my Asus a8n-vm motherboard. The module, for me, is 'forcedeth'.

sudo modprobe -r forcedeth
sudo modprobe forcedeth
sudo ifdown eth0
sudo ifup eth0

Very rarely, mine will not connect automatically and I have to ifup eth0 to kick-start it. I haven't had any real problem with it since Ubuntu 5.10 though. I was dual booting it with XP and every time I went back to Ubuntu from XP I'd have to shut down the PC and turn it off at the mains to stop all power to the MB. Otherwise Ubuntu wouldn't be able to get control of the onboard ethernet. I highly doubt you'd need to do that now though.

---

### Post by HereInOz on 2007-04-08
This could be a DNS issue.  If you can ping 64.233.161.104 alright, but you are unable to ping [www.google.com](www.google.com), then the problem is DNS.

If it is the problem, go in to System > Administration > Networking and click on your Ethernet adaptor and then click on Properties.  Set the IP address as a static IP in the same subnet as your router - you are going to have to find out what the internal IP address of your router is.  Being a D-Link, it is probably 10.1.1.1, but that is a guess.

You then set the gateway address to the IP address of your router (see above).

Then go to the DNS tab in Networking, and set the DNS addresses to the ones provided to you by your ISP.

Click OK and all that sort of stuff, and if the problem was a DNS issue, then it should work.

By the way, it is a good idea to set the static IP outside of the range of IP addresses provided by DHCP, just to ensure that you don't confuse the issue too much.

Hope this helps.

---

### Post by chemtut on 2007-04-08
my ethernet connection only works when it is plugged in at boot
have you tried that

---

### Post by zvacet on 2007-04-08
Do all things that HereInOz told you to do and after that 
```
pppoeconf
```

---

