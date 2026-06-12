---
title: "Help Me Build My Network, Please"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by tikbjamin on 2006-05-19
Problem situation:
Windows XP Slow on Machine 1, don't have full control of my mouse on slow Windows ME on machine 2
Opportunity:  Install Ubuntu 5.10 on Machine 2, put in second network card, use as server; reinstall XP on machine one, connect to machine 2

So far so good with Ubuntu machine, connects to the Internet, been surfing, etc. for over a week now.  Except for being unable to update to java5, to format and save to floppies and CD's, I am happy.  Firestarter firewall is installed and working fine.

Followed thread headlined HOWTO Share an Internet Connection posted by anaoum.  Still unable to let the machines talk to each other.

From my XP machine, pinging anything returns "Destination host unreachable"

Form my Ubuntu machine #ifconfig returns

eth0      Link encap:Ethernet  HWaddr 00:04:5A:5B:F6:04
          inet addr:xx.xxx.xxx.xxx  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::204:5aff:fe5b:f604/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:236417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:22360226 (21.3 MiB)  TX bytes:1426692 (1.3 MiB)
          Interrupt:9 Base address:0xd800

eth1      Link encap:Ethernet  HWaddr 00:14:BF:55:C8:37
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bfff:fe55:c837/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:2 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4626447 (4.4 MiB)  TX bytes:4626447 (4.4 MiB)

Please help because I should normally be running my XP machine for work, but I was supposed to be taking a break this week.  What a break!!

Further, I don't know computing or networking so please be gentle.

Thanks.

---

### Post by macdo on 2006-05-19
On your XP PC: Make sure the firewall is disabled.
Connect using 192.168.0.1 as gateway and DNS.
On the Ubuntu box: have a close look at Firestarter; make sure that it knows about the second PC and isn't blocking anything. I **think** that there's a forwarding option, actually. Have a poke round. (I'd be more precise, but I got rid of Firestarter when I got my router/firewall.)

Consider buying a router - it's not at all expensive (I heard $30.00 somewhere on these forums) and you'll save yourself a lot of hassle in the long run. 

If you're really stuck, give me a shout (gtalk option on the sidebar, pm, whatever), and I'll duplicate your set-up here and see if I can work it out.

---

### Post by macdo on 2006-05-19
Your question intrigued me - so I installed Firestarter. Run the wizard in Firestarter, (Firewall -> Run Wizard) and input the right values for your set-up in the share internet connection screen:
eth0 to the internet, eth1 to local network.
Let us know if that works...

---

### Post by tikbjamin on 2006-05-19
macdo:
Thanks for your prompt response.  There is no improvement.

I had done a bunch of checks in Firestarter to ensure that it was not blocking "redundant entries" like my cricket website cricinfo.com which refreshes every 90 seconds.  The eth0 is set to DHCP and eth1 has a static IP as above.

I know the router is the simple solution. (I actually had a router which got shot because I had connected it to the wrong power adapter after changing locations).  However, part of the alllure of Ubuntu, to me, comes from:

1. my small way of sticking it to the mon(opoly)
2. the perception of greatly improved security, and
3. the challenge of learning something new - building the network, moving files between the two computers, etc.

I still want to build the network.  I need to to have a fast computer setup to handle downloads of tons of megabits of realtime data and computation.  If I can avoid having to deal with the increased risk of intrusions and viruses, the time spent will be well worth it.  I didn't want to have my XP machine directly exposed at all, though.

Are you suggesting that a router is just as, or more secure than Ubuntu + firewall?

---

### Post by tikbjamin on 2006-05-19
Actually, don't know if this helps, but when I do
Places>  Network Servers  >   I see a Windows Network icon.  Is this good news?

---

### Post by macdo on 2006-05-19
Re your router question: It's my understanding that a hardware router/firewall is inherently more effective than a software firewall. Somebody once put it into layman's terms for me by explaining that any malicious person has to work through a hardware firewall, but only needs to go round a software one...

A lot of routers use linux, by the way...

I don't know if the Network Share is a good sign; what happens if you try to click on it? (share a folder or two on your WinXP box first, though...) My guess is that that means that your linux box is seeing your windows box on the network, and using Samba to access it, but I could be wrong.

---

### Post by dmizer on 2006-05-19
humm ... not sure, but that may just always be there.  but if you can click on the windows network and browse to a shared folder on your windows machine, then that will mean you have your network at least connected and ip routing configured correctly.

if you can browse to your shared windows folders from linux, then it just means that you will need to configure firestarter with the correct parameters.

i wouldn't say that a router is more secure than a linux box, but it is a fair compromise.  it most certainly is easier.

if you want to set up a local file sharing LOCAL network though, your best bet is to have an ics/firewall setup as it is more secure.

---

### Post by tikbjamin on 2006-05-21
macdo, when I clicked on the Windows Network Icon, there was nothing in the folder.  

It seems from the above that I need to have Samba installed for the filesharing to work, right?  I just have samba-common and smbclient packages installed, probably not enough, right?

dmizer:  yeah, what I want to do is set up local file sharing LOCAL network, so I will hold off on the router option for the next couple of weeks.  I can still hold on to the network card I just bought and installed.

---

### Post by macdo on 2006-05-21
Try this howto: page 4 and 5 are what you need, I think. [http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)

And yes, you do need to install samba (sudo apt-get install samba) to serve files. At the moment, you've only got a client, not a server.

---

### Post by tikbjamin on 2006-05-21
Ok, macdo, so I read the howto, not that I understand it, but does this address my main problem of no connection between the XP and the Linux box?  Are these steps designed to make the machines talk to each other?

---

### Post by macdo on 2006-05-21
Sorry, I got distracted by the Samba question. 

You should be able to ping from one computer to another. Can you ping from Ubuntu to WinXP? 
What about the cable? It should be a crossover cable, if the computers are connected directly. Is there any way to test it, make sure that it works? It's not a 100 yard cable coiled up, is it? (Cat 5 cables **hate** that.)
Does XP have an IP address? (I think the command for that is ipconfig, but I'm not sure...)

---

### Post by tikbjamin on 2006-05-22
No, I cannot ping the XP machine from Ubuntu, the former has no IP adddress.   ipconfig at the DOS prompt returns a media disconnected message from the XP machine.  I will have to research at the MS website how to solve this.  I knew there were some driver problems for the network card from my reinstall of XP, but I thought that there wasn't any now.

Also, I am using the wrong cables.  I will have to get the crossover cables you mentioned.

Thanks for your help so far.

---

### Post by tikbjamin on 2006-05-31
[QUOTE=macdo]Sorry, I got distracted by the Samba question. 

You should be able to ping from one computer to another. Can you ping from Ubuntu to WinXP? [/QUOTE]

I can now ping from XP to Ubuntu.  Edit:  Opening up my Windows firewall for my LAN connection, I can now ping from Ubuntu to XP.

[QUOTE=macdo]What about the cable? It should be a crossover cable, if the computers are connected directly.[/QUOTE]
Yeah, once I changed the cable, internet connection was up and running.

[QUOTE=macdo]Does XP have an IP address? (I think the command for that is ipconfig, but I'm not sure...)[/QUOTE]:-D 

Now, I just have to do something with Samba so that I can share files.  Thanks. 

Will let you know what happens with  my efforts there.

---

### Post by tikbjamin on 2006-12-21
> **tikbjamin said:**
> Problem situation:
Windows XP Slow on Machine 1, don't have full control of my mouse on slow Windows ME on machine 2
Opportunity:  Install Ubuntu 5.10 on Machine 2, put in second network card, use as server; reinstall XP on machine one, connect to machine 2

So far so good with Ubuntu machine, connects to the Internet, been surfing, etc. for over a week now.  Except for being unable to update to java5, to format and save to floppies and CD's, I am happy.  Firestarter firewall is installed and working fine.

Followed thread headlined HOWTO Share an Internet Connection posted by anaoum.  Still unable to let the machines talk to each other.

Further, I don't know computing or networking so please be gentle.

Thanks.

So I built my network and now I want to undo this.

I got a router.  Windows XP machine connects fine and programs configured.   I am now up to Edgy on the Ubuntu box, but I am unable to connect to the Internet.  I know I need to undo something we did before, but what?  Now I need some help in configuring this one.  Can you guys please help me out again?

I disabled eth1 and put the ip address from the router in System>Administration>Networking.  Removed Firestarter.  Various combinatins of the foregoing, nothing works.

Ifconfig gives:


eth0 Link encap:Ethernet HWaddr 00:04:5A:5B:F6:04
inet addrx.xxx.xxx.xxx Bcast:xx.xxx.xxx.xxx Mask:255.255.255.0
inet6 addr: fe80::204:5aff:fe5b:f604/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:945 errors:0 dropped:0 overruns:0 frame:0
TX packets:3158 errors:1 dropped:0 overruns:0 carrier:2
collisions:0 txqueuelen:1000
RX bytes:84828 (82.8 KiB) TX bytes:84828 (129.7 KiB)
Interrupt:9 Base address:0xd800


lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2321 errors:0 dropped:0 overruns:0 frame:0
TX packets:2321 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:182992 (178.7 KiB) TX bytes:182992 (178.7 KiB)

---

