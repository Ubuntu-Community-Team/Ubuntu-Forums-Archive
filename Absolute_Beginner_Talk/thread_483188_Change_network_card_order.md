---
title: "Change network card order?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by drifting on 2007-06-24
Can I change the order that Ubuntu gives the network cards?

Reason I ask is that I have a 1gb and 10/100 card, I need the 1GB set to my local network, and the 10/100 to my adsl. Ok I know I could just change the IP's, but I have installed vmware server and have a stack of configured Vm's that are configured.

I have googled and read through quite a few posts, but can find no information on doing it, do know it can be done with Redhat, but not a clue with Ubuntu.

I bet it's simple and I have been googling with the wrong question?

Paul.

---

### Post by Obeleh on 2007-06-24
Are you on a ADSL router or do you want to use your pc as a kind of server that provides the other pc's near you internet?

And what are you trying to do? give your VM's internet or just network acces and no internet?

---

### Post by drifting on 2007-06-25
> **Obeleh said:**
> Are you on a ADSL router or do you want to use your pc as a kind of server that provides the other pc's near you internet?

And what are you trying to do? give your VM's internet or just network acces and no internet?

It was a little incoherent wasn't it ?

Right. What I am trying to do is setup a server with Ubuntu on it, and Vmware. The Ubuntu machine has two network cards, one goes to my local lan the other goes to my ADSL router. The router has a number of fixed IP's available. 

I have a number of pre configured VM's, the main one being an SBS2003 R2 which is configured for two network cards. One local lan the other goes to the router (Using one of the fixed available addresses)

Problem, Ubuntu has set eth0 to be the wrong card, it's a 10/100, the other card is a 10/100/1000 which I would like as my local lan. Now to add insult to injury VM's expect eth0 to be the local lan, and eth1 to be the wan side.

I know I could reconfigure the SBS install (Major pain) or hopefully change the card config round in Ubuntu (Hoping easier)

Does that make any more sense?

Regards Paul.

---

### Post by drifting on 2007-06-29
Anyone?

Perhaps I should reinstall and not put the second card in till the OS is installed?

Suggestions?

Paul.

---

### Post by drifting on 2007-06-29
Found some information, tried it, and it works...cool

[http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)


Using the ifrename tool

Ifrename is a tool specifically designed to (re)name network interfaces based on characteristics like MAC address (wildcards supported), bus information, and hardware settings. It uses a control file (/etc/iftab) to specify rules about how the interfaces will be named. (thanks to Matt Baron for this tip.)

# Example /etc/iftab file
eth2           mac 08:00:09:DE:82:0E
eth3           driver wavelan interrupt 15 baseaddress 0x390
eth4           driver pcnet32 businfo 0000:02:05.0
# wildcard name: pick the lowest available name of air0, air1, air2, etc.
air*           mac 00:07:0E:* arp 1

just changed the order around and it worked a treat.

Paul.

---

### Post by iimre on 2007-10-03
I've just faced to the same problem.
I guess that the best solution is using udev.
More info here: [http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)

---

