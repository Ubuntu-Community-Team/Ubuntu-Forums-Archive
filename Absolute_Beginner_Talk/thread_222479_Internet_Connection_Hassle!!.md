---
title: "Internet Connection Hassle!!"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-07-25
Hi

Each time I log into Ubuntu (running 32bit Dapper on a 64bit AMD system, connecting to the net via an ADSL router through an RJ45 cable) and need to connect to the internet or download my emails, this is the palaver I have to go through...

**System > Administration > Networking > Ethernet Connection > Properties > Configuration > Static IP address...** here I enter my router's IP and the subnet mask before okaying everything and exiting networking.  

At this point I am still unable to connect.  In order to do that I have to go back through the above routine, **reselecting** DHCP in confuiguration. After okaying it, then I am able to connect.  The Ethernet connection remains active throughout all this and everytime I log into my system.  

Could someone please tell me how I can connect to the internet without going through all this ritual?

Thank you once again in anticipation of your ideas.


Regards

---

### Post by cat on 2006-07-25
could you post your /etc/network/interfaces file?

---

### Post by Norfolk 'n' Good on 2006-07-25
Hi Cat

I'm at work at the moment and will be until around 21:00 tonight (GMT). I will post the requested file on my return.  

Thank you.

---

### Post by richbarna on 2006-07-25
Cat has got the right idea, I think the problem that you have is that your configured "gateway" isn't being saved. I remember that there was a bug report on this last year.

Anyway, to edit the config file :-
> gksudo gedit /etc/network/interfaces 
Check this line (add your gateway), Save & Exit.
> address 192.168.1.110
        netmask 255.255.255.0
[COLOR=Blue]         gateway 192.168.1.1[/COLOR] 
Then start the network with :-
> sudo /etc/init.d/networking restart

---

