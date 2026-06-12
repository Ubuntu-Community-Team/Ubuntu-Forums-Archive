---
title: "free firewall and anti-virus software?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by todd_k on 2007-03-19
Can someone recommend a reliable and free firewall and anti-virus software?

---

### Post by thomas576 on 2007-03-19
hey im new here but from what i have used with unix before,  there is no need for a virus scanner, theres few viruses out there that run in linux , and as far as a firewall, the system is pretty locked down if you wish to see what open ports you have on your system you should look into ubuntu ip config setup it pretty nifty from 1st glance.

thomas

---

### Post by raja on 2007-03-19
Firestarter is a graphical frontend to the firewall that you can get from the repositories. Similarly clamAV is there in the repositories, though the only reason to use one may be if you are sharing files with a windows machine.

---

### Post by oilchangeguy on 2007-03-19
while no operating system is totally imune to these things, they're mainly a windows problem. i've got two computers running ubuntu with nothing other than the built in firewall, and no problems.

---

### Post by airtonix on 2007-03-19
this is how it is : 

you have no listening services by default....
so you dont need to block packets
ergo...why you dont have a gui for the already installed firewall pre-installed....
becuase you are already protected by not having software waiting for anoymous incoming requests.


unlike windows....

where local filsharing is already running on ports 137-139...and other ones too but since this software on windows is waiting for packets on this port....it will need to have all the data filtered...only letting through the ones you allow.


but since most windows people how just switched to ubuntu will obviously like to share files with some of their (assuming here) already existing windows machines via samba....

which in this case its best to install firestarter and allow only the ip addresses of your local computers to access ports 137-139 on either computers.

---

### Post by astrolabio on 2007-03-19
As the others said for the firewall Firestarter is good.

I just want to highlight something that confuse newbes. 

Firestarter is just a configurator utility for your firewall. This means that if you close firestarter is NOT like closing Zone Alarm in windows. It means also that is not necessary to start Firestarter as soon as you start your pc to be protected.

The actual firewall is not Firestarter and will be running all the time. You use firestarter just to easily tweak it.

If you need something like PeerGuardian instead look for moblock.

---

