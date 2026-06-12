---
title: "Networking in ubuntu 7.04"
date: 2007-08-06
forum: Absolute Beginner Talk
---

### Post by Eniac on 2007-08-06
Hi,

i just installed Ubuntu 7.04 as a dual boot on my PC. 

(me) <- (absolute beginner)

At first glance everything is fine. i was able to install ubuntu, i got sound, video and network too. but for some reason, i have no access to the internet or even to my router.

How would i troubleshoot was is going on with my network ? i tried going in the network tools but, not knowing too much about network, i cannot guess where is the problem.

the windows XP counterpart is working fine (otherwise i couldnt write this :p)

---

### Post by shearn89 on 2007-08-06
Open a termianl (Applications -> accessories -> terminal), and type "lspci", then post output here, and we'll see what we can do.

---

### Post by sputn1k on 2007-08-06
Also show us the output of ifconfig. Open a terminal and enter ifconfig

---

### Post by Eniac on 2007-08-06
Here you are. lspci and ifconfig.

if its worth anything, i got 3 lan card in there, 2 i dont use because they're onboard and i had problems with them in past. the third one is one i bought and installed myself. I tried connecting my cable in 2 of them, without success.

---

### Post by sputn1k on 2007-08-07
Thanks,

from you posted ifconfig.txt I can see that eth0 does not get an IP. Is eth0 you internal NVidia NIC? Which one have you disabled as you also have a Marvel GigNic and a Realteak NIC (which one of this three cards get used in your Windows System?, you can find it out if you watch the net traffic in a dos box via ipconfig ). I would also disable the avahi daemon (in services -> uncheck Multicast DNS service discovery. Also have a look for the settings in /etc/network/interfaces as you only need one card which gets the IP via DHCP e.g: 
auto eth0 
iface eth0 inet dhcp

the rest can be out commented except the lo interface. Please also post which kernel modules are loaded (lsmod) as I forgot to ask in my first message. That's all for now.

---

### Post by ropateviliame on 2007-08-07
:confused:I have read this thread with great interest - I too have a very similar problem.
I am running Ubuntu on a dual boot with XO (shudder,shudder!) and have no internet connection working.
I have tested Kubuntu - no problem, Edubuntu, the system kept going on and off; however with Ubuntu there is no connection or recognition of the LAN on my modem(DSL Broadband). I have found out that our Fijian IP, Connect, do not support Linux from a technical point of view, but that should not prevent a connection nor has it with Kubuntu.
I attach ifconfig, lspci, and lsmod. They are in word pad as I have to communicate through XP.:(
Please help this newbie!!

---

### Post by sputn1k on 2007-08-07
Hi ropateviliame

Does your system have one network card or two? As in your lspci output I can only see a RealTek card but there are two network drivers loaded (8139cp, 8139too). If you have only the RealTek nic please unload one of the two drivers as (in a termina): sudo rmmod 8139cp && rmmod 8139too && ifdown eth0 && insmod 8139too && ifup eth0 (in this example both drivers get unloaded, the net interface eth0 get should down, then the 8139too driver get loaded and the net inface eth0 get switched on).

You could also post the output of lspci, ifconfig + the output of /var/log/dmesg of the working kubuntu system. But as you have previous posted it works with Kubuntu so the problem must be small and should be fixable :-).

---

