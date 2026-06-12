---
title: "Firestarter, PPPoE and Wireless Internet Sharing: The Good, The Bad and The Ugly"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by gaelfx on 2007-07-16
I would like to start by saying that I am posting here because all the Firestarter topics I have read are over my head and seem to assume I know something about Firestarter that I don't: I am in China and I fear that they have blocked [http://www.fs-security.com](http://www.fs-security.com) .

As previously mentioned, I am in China, and in China ADSL is the connection everywhere, which means I must use PPPoE for my internet connection. I want to share this connection with my iBook (running 10.4.10 on a G4 PPC processor), however, firestarter seems to do me no good for starting up internet sharing. I get connected to ADSL without a problem (eth0 has the ethernet cable hooked up to the screwy Chinese modem), but the firewall doesn't start. this may sound familiar from other posts, however the other posts never clearly describe how to set up the wireless card to work with Firestarter.

 So I tried connecting to a computer-to-computer network set up by my mac to resolve this "device is not ready " problem, . The wireless tries to connect for a long time, starts to look good and then I get a message saying that the device has connected to the wired network. When I first try connecting to the wireless, it says it disconnects from the wired network, though it actually does not, which is why I thought this is what I am supposed to do, but it fails every time and automatically reconnects to the eth0. 

What is a boy to do? EXACTLY what do you need to do to get Firestarter to properly share internet connection from one device (or in this case 2: ppp0 and eth0) to another (eth1, the wireless card)?

If you need more info, I will gladly post it. Please help!

---

### Post by Wim Sturkenboom on 2007-07-16
You don't have problems when you stop the firewall in firestarter?

---

### Post by gaelfx on 2007-07-16
I can run the PPPoE connection just fine, but the problem is that the firewall won't ever start because it says that eth1 device is not ready.

---

### Post by Wim Sturkenboom on 2007-07-16
And according to the system eth1 is ready? Has an IP address, can ping other computers in the network etc.

---

### Post by gaelfx on 2007-07-16
Well, you see, that's why I'm posting this problem in this forum, I have no idea how to check/cause those particular facts. so could you tell me:
1.How to check this
2.How to make it so
(No, I'm not a Trekkie)

---

### Post by xpod on 2007-07-16
[http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php)

Can you not see that page ???

I share a cable broadband  connection with firestrater ok although i dont have wireless or even a router so i`m not sure how those fit into the equation i`m afraid.I`m a bit lost with just what you mean too i think
Do you actually have a wireless router because you dont need firestarter to share the internet if you do surely???

I dont even know if you can even share the connection with two other devices like that through firestarter?
I have internet coming in on eth0 which i share to eth1, then if i want i can connect a hub etc to that and add more pc`s.

If i had a router though that would all be surplus to requirements i think.

---

### Post by Wim Sturkenboom on 2007-07-16
As far as I understand it, there is an Ubuntu PC with both a wired (eth0/ppp0) and a wireless (eth1) connection. That PC connects to the internet.
Topic starter now needs to get his mac connected to the network using the wireless.

If I'm incorrect, please correct me.

The check if eth1 (wireless) is up, it should show up in something related to network in the gnome menus (not sure exactly where). Or you can run ifconfig to see if eth1 has an ip address.

---

### Post by gaelfx on 2007-07-16
OK, I'll try to make what I want to do clearer:

I have two laptops, one is running Ubuntu, the other is Mac OS X 10.4.10. I have the Ubuntu box hooked up to a DSL router using PPPoE. I want the Ubuntu box to share its internet connection with the Mac using the wireless card built-in to the machine.

Does that make sense or am I just totally inept at describing my situation?

Also, no, I cannot see that page. I am almost certain that fs-security is a banned domain in China. I will try the ifconfig program now though. Thanks for replying!

---

### Post by the.phantom on 2007-07-16
hi
you say that firestarter is not starting


you do know that it is just a GUI ( graphic interface) and it is running
the only time you need to see it is when you want to change something


believe me your firewall is running ! 
your firewall is iptables and the gui is just a easy way to configure it


don't know but have you checked out your firewall?

say go to 
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

and check it out?

---

### Post by gaelfx on 2007-07-16
OK, for one, firestarter was not starting because, as Wim stated correctly, my eth1 had no IP. I fixed this with ifconfig, but the issue at hand is that I want to use Firestarter to SHARE my internet connection via wireless with another laptop. I now have firestarter running, but the second laptop is not seeing any kind of wireless network to connect to.

I made the IP address for the ubuntu box 192.168.1.1 and on the mac box I set the airport to run TCP/IP off of manual settings, so I made the router address and the DNS server address the same as eth1 from my ubuntu box. I even used iwconfig to set the ESSID of my Ubuntu box to something like "UbuntuBook" (because I'm a dork). Was using iwconfig the wrong way to go?

I also manually set the IPv6 router address on my mac, and then did
```
sudo iwconfig eth1 mode Master
```
which resulted in the mac box recognizing some strange wireless network ("BRCM_TEST_SSID" or something like that, reminiscent of Broadcom (my wireless card's chipset) and ESSID) for the entire ten seconds that eth1 actually remained on Master mode. I kept typing "iwconfig" in the term trying to figure out how long it took before the settings on it reverted to Managed. Is it possible that my wireless card can't act as a wireless router of sorts, or is that just poppycock? I'm really in the dark here.

P.S. I'm going to bed, so I won't reply so quickly

---

### Post by Wim Sturkenboom on 2007-07-16
Good morning,

So switch the firewall off in firestarter (your Ubuntu box will still be quite safe) and see if you can connect. If so, it's the iptables commands that firestarter creates that blocks the traffic. If you still can not do what you want, it's something else that you need to fix first.

Firestarter is a GUI frontend for iptables and not a tool to share internet connections.

---

### Post by gaelfx on 2007-07-17
OK, perhaps you are correct that Firestarter is unnecessary to what I'm doing. I probably just got really excited when I found a window that had a checkbox next to "Enable Internet Sharing." 

So can you tell me how I can share my internet via my wireless card? I'm guess there is something I will have to do specifically for/to my mac in order for this to work, but how does one get the ethernet card to stay connected while the wireless is running? You see, anytime I try to start up my wireless, the wired network disconnects (or at least says it does), and then the wireless fails to create a new network (and the wired network reconnects).

Not that I refuse to hear the advice, but I would really prefer not to reinstall. Any solution? Do I need to post my lspci output or what?

---

### Post by xpod on 2007-07-17
> Firestarter is a GUI frontend for iptables and not a tool to share internet connections.


It`s certainly a tool that "helps" me share my internet conenction thank you very much:)

> OK, perhaps you are correct that Firestarter is unnecessary to what I'm doing. I probably just got really excited when I found a window that had a checkbox next to "Enable Internet Sharing."


Life would certainly be a bit more complicated if i didn`t have that little check box i can tell you.
I know firestarter is but a front end to iptables but when you dont have a clue about iptables then firestarter sure makes life a bit easier.:)

---

### Post by Wim Sturkenboom on 2007-07-18
I might have been mistaken with regards to all options of firestarter, sorry for that. As I don't share internet and I don't use wireless, I can't help further.

---

