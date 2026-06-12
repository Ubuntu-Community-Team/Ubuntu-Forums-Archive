---
title: "2 NIC but no connection through ADSL"
date: 2005-09-05
forum: Absolute Beginner Talk
---

### Post by coolfinch on 2005-09-05
Hi all,

I feel depressed: I am a new Ubuntu 5.04 user and here are my wired network cards:
1) Realtek RTL-8139 integrated to the motherboard 
2) SMC networks EZ 10/100 (SMC 1244TX)
I have an ADSL connection through an ADSL modem (9T with NeufBox in France) which works perfectly well on my other computer that runs WinXP SP2.

During Ubuntu installation, the system is not able to find DHCP and do the appropriate configuration. 
Then in the device manager onlt the Realtek NIC appears (eth0). In network tool, the eth0 is not available. In system/administration/network I activated eth0 and it was OK.
But it's impossible to configure my ADSL connection with pppoeconf (no access concentrator detected). I guess I am not connected bcause I can not reah any webpage with Firefox.

How could I add my SMC card (as eth1)?
What should I do for at least 1 NIC to connect to my provider DHCP, and get the connection?

Any idea might help. After long hours of reasearch and many unsuccessful tries, I am almost resignated. I really want to install a linux system though.

Thanks in advance

an exhausted linux newbie

---

### Post by rafakl on 2005-09-05
hello!!!
welcome to linux!!!

did you tried this:

[http://ubuntuguide.org/#rp-pppoe](http://ubuntuguide.org/#rp-pppoe) 

???

---

### Post by coolfinch on 2005-09-05
Thanks for your answer.
I have installed the rp-pppoe. Everything goes well but when I launch the Applications/internet/rp-pppoe, I type in my password and then I get the following error message:

failed to run /opt/rp-pppoe-3.5/go-gui
child terminated with 1 status

Any idea what could have gone wrong?

---

### Post by bratwurst on 2005-09-22
[QUOTE=coolfinch]Thanks for your answer.
I have installed the rp-pppoe. Everything goes well but when I launch the Applications/internet/rp-pppoe, I type in my password and then I get the following error message:

failed to run /opt/rp-pppoe-3.5/go-gui
child terminated with 1 status

Any idea what could have gone wrong?[/QUOTE]
 hi there ...

did you install gcc with synaptic ???

you need to install synaptic as the go-gui needs it !
works this way on my box !

---

