---
title: "I'm having problems accessing my cable internet"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-12-19
I have a cable modem set up for my desktop.  There is only one button which can activate or go on standby.  With this, my desktop can access the internet.  When I take the ethernet cable from my desktop and connect it to my laptop, my laptop is not able to access the internet.  I have tried to reboot with the cable connected to the laptop, went to System>Adminstration>Networking and activated my eth0.  Still doesn't work.  Before I upgraded to breezy, my laptop worked without a glitch when I connected the cable to it.  What can be the problem?

I am running Breezy on a IBM Thinkpad R50

---

### Post by bscbrit on 2005-12-19
Is your laptop configured to use the cable modem?  If it is an ethernet modem it has an IP address.  Your laptop needs to know this address for its gateway.  

On a commandline, try the following:

ping -c5 [www.ubuntuforums.org](www.ubuntuforums.org)

and let me know what you get.

---

### Post by racermike1967 on 2005-12-19
I get the following reply:
ping: unknown host [www.ubuntuforums.org](www.ubuntuforums.org)

---

### Post by bscbrit on 2005-12-19
OK, please print the results of the following command:

ifconfig

Do you know the IP address of your modem?

---

### Post by racermike1967 on 2005-12-19
I do not know the IP address of my modem.

The results of the command ifconfig are:

ath0   Link encap:Ethernet HWaddr 00:05:4E:44:65:FD
         inet6 addr: fe80::205:4eff:fe44:65fd/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:118 dropped:0 overruns:0 frame:118
         TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
         collisions:0 txquelen:200
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
         Interrupt:11 Memory:d0ba0000- d0bb0000

lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436  Metric:1
        RX packets:37963 errors:0 dropped:0 overruns:0 frame:0
        TX packets:37963 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:2849660 (2.7 MiB)  TX bytes:2849660 (2.7 MiB)

Sorry for taking so long,  I have to type every result and connect/disconnect my cable ethernet.

---

### Post by bscbrit on 2005-12-19
I thought you might be switching the cable back and forth.....  It doesn't look like your network card is configured.

Firstly, on your _desktop_

System -> Adminstration -> Networking -> Connections

Select eth0 (or whichever network card the desktop uses).  Select Properties and note the values in each of the fields.  

Then move across each of the tabs of the Networking dialog making note of each of the settings.

Change over to your laptop, and mirror the settings.  Although both your desktop and laptop will have the same IP numbers it will not matter because they do not connect at the same time.

Once the values have been inputted, activate the network card in your laptop and make sure that it is also selected as the default gateway at the bottom of the dialogue.

Try using your browser - if it works, then you are sorted.  If not, then we will have to look a bit further.

---

### Post by racermike1967 on 2005-12-19
I'm sorry, I forgot to mention that my desktop is running a windows xp home edition.

My desktop is assigned the ip address, subnet mask, and gateway address by DHCP.  If I select DHCP on my laptop, I am unable to enter any data into the IP address, subnet, and gateway fields.  Should I switch over to static IP address?

---

### Post by bscbrit on 2005-12-19
I'm going to have to go offline in a few minutes - but I will be back on tomorrow evening if you are still having problems.

---

### Post by bscbrit on 2005-12-19
OK - I'm now racking my brain to try to remember the XP dialogue names!  I'll try and do this from memory but you will have to interpret my instructions quite freely to get a result - stand by, back in a second.

---

### Post by bscbrit on 2005-12-19
Control panel - networking. Your network card should be shown.  I cannot remember the precise labelling of the tabs but you should be able (somewhere!) to highlight  TCP/IP and then select properties.  That should give you various IP addresses e.g. 192.168.0.1, although the actual figures may be completely different. Make a note of all of the values.  If this is not helping, then tomorrow night I will fire up both breezy and XP on adjacent machines and go through it then in slow time.  
Sorry about this - but my life outside of the computer is calling.....  She is reasonably tolerant but there are limits!

---

### Post by ertai on 2005-12-19
Doesn't your provider select allowed computers?? Some providers need to have the mac-address correctly to be able to connect.. some need the computername to be correctly. Maybe it is souch a problem

(sorry for my bad english)

---

### Post by bscbrit on 2005-12-19
OK we can make it use DHCP but we will still have to point the laptop at your DHCP server which could be local in your modem or your ISP.  CU2morrow

---

### Post by harisund on 2005-12-19
[QUOTE=racermike1967]
ath0   Link encap:Ethernet HWaddr 00:05:4E:44:65:FD
         inet6 addr: fe80::205:4eff:fe44:65fd/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:118 dropped:0 overruns:0 frame:118
         TX packets:0 errors:1 dropped:0 overruns:0 carrier:0
         collisions:0 txquelen:200
         RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
         Interrupt:11 Memory:d0ba0000- d0bb0000
[/QUOTE]

Did you type ath0 by mistake or is really ath0? Just wondering

---

### Post by Biased turkey on 2005-12-19
Maybe the cable modem stores some parameters of your desktop into his non volatile memory ( maybe the mac adress for example ).
So I would try the following:
1) unplug your cable modem off for about 10 seconds
2) connect your laptop to the cable modem
3) turn your cable modem on
4) boot your laptop

That tip was given to me by a support technician working for my cable internet provider.

---

### Post by racermike1967 on 2005-12-19
Thank you very much for your help, I appreciate it very much.  I will continue to try to solve this problem.

Have a good day.

---

### Post by racermike1967 on 2005-12-19
[QUOTE=ertai]Doesn't your provider select allowed computers?? Some providers need to have the mac-address correctly to be able to connect.. some need the computername to be correctly. Maybe it is souch a problem

(sorry for my bad english)[/QUOTE]

I am not sure.

---

### Post by racermike1967 on 2005-12-19
[QUOTE=harisund]Did you type ath0 by mistake or is really ath0? Just wondering[/QUOTE]

No, It is ath0.  Why, is that a problem?

---

### Post by harisund on 2005-12-19
[QUOTE=racermike1967]No, It is ath0.  Why, is that a problem?[/QUOTE]

Just for the fun of it, as long as your wires are all in place

ifconfig ath0 down
ifconfig ath0 up
dhclient ath0

Then post the content of ifconfig ath0 again? 

Just wondering.. works for me when my wired connection is at eth0

---

### Post by racermike1967 on 2005-12-19
[QUOTE=harisund]Did you type ath0 by mistake or is really ath0? Just wondering[/QUOTE]

My mistake, I had eth0 as well as ath0.  I am sorry.

---

### Post by racermike1967 on 2005-12-19
[QUOTE=Biased turkey]Maybe the cable modem stores some parameters of your desktop into his non volatile memory ( maybe the mac adress for example ).
So I would try the following:
1) unplug your cable modem off for about 10 seconds
2) connect your laptop to the cable modem
3) turn your cable modem on
4) boot your laptop

That tip was given to me by a support technician working for my cable internet provider.[/QUOTE]


I just did what you had suggested.  I worked.  thank you.  Do you know what happens when I disconnect my cable and connect it back to the desktop?  Will the desktop now have internet access?  Will I have to turn off my cable modem for 10 seconds everytime I switch between the desktop and the laptop?

---

### Post by harisund on 2005-12-19
Ah. Thought so. ath0 is your wireless, right? 

Anyway, try the same for your eth0.

Before that disable your ath0 by 
ifconfig ath0 down

---

