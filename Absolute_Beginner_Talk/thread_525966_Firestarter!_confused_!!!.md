---
title: "Firestarter! confused !?!?!"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-08-14
So i installed firestarter but everytime the firewall is turned on and i open firefox i get server not found.  I did the standard configuration upon installation but i believe the part i'm going wrong with is adding policies. During the firestarter setup i specified eth0.   Can someone help me to understand how to use firestarter and if any alterations are required explain the purpose behind them as i am still learning about ubuntu.

This is how i connect to the internet:

open terminal and type: pon dsl-provider.  I have an ethernet cable to modem to phone jack in my wall.  

this is what my network file looks like:

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#Wiface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet 

Can anyone help me out with this and explain wat exactly must be further configured and also with any  chagens you specify could you please explain why you would do them.

Thanks in advance, Alain

---

### Post by ramjet_1953 on 2007-08-14
The first question that needs to be asked here is why do you need to change iptables with Firestarter?

Do you need to do any port forwarding?

If not, you don't even need Firestarter, as all ports are closed and your system is secure.

Remember the old saying, "If it isn't broken, don't try to fix it".

Firestarter IS NOT a firewall, it is merely a GUI for your built-in forewall which is iptables.

Regards,
Roger :cool:

---

### Post by S15_88 on 2007-08-14
ic wasn't aware of that, networking/security is my weakness i'm more of a programmer.  i thought firestarter was an actual firewall not just a GUI to manage iptables.  well don't i feel silly haha so just to make sure i understand this correctly ubuntu has a built in firewall to prevent unauthorized access, now if i wanted to run my laptop as a server and a client for remote desktop i would need to modify my iptables correct?

---

### Post by ramjet_1953 on 2007-08-14
If you want to set up a server, you almost certainly will need to have a look at customizing iptables.

There are plenty of scripts out there and also tutorials on setting things up.

Just search these forums and also the web for more info.

It's probably a good idea to have a clear picture of exactly what you want to do with the firewall, before plunging in. iptabels is extremely flexible and powerful and complexity comes along with that.

In other words, do you homework well and all should be fine.

Regards,
Roger 8)

---

### Post by nowshining on 2007-08-15
actually yes they are closed ,BUT solicited connections are allowed which is NOT secure.. Firestarter will help hide these and stealth them, an example on my Not secure is the port is the same when I do P2p (i had to re-install so i gotta re-set that up), and open up a port it allows anything to come in accepting connections to it.. Which is Not secure with at least with comodo firewall when I had XP It would become stealth AFTER i quit the p2p program which is not the case in ubuntu linux which it just goes to closed.. again I highly suggest firestarter---

Did you make sure to chose (op) the DHCP option if not to back into the wizard and make sure it's check... to do that  Firewall-run wizard..

edit: here's the output without firestarter of what grc.com (go to shields up link down the second page after the auto-forward page) gives me:

[FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=1][COLOR=#000060]**Solicited TCP Packets: [FONT=Arial][COLOR=#cc0000]RECEIVED (FAILED)[/COLOR][/FONT]** &#8212; As detailed in the port report below, one or more of your system's ports actively responded to our deliberate attempts to establish a connection. It is generally possible to increase your system's security by hiding it from the probes of potentially hostile hackers. Please see the details presented by the specific port links below, as well as the various resources on this site, and in our extremely helpful and active [user community]("https://www.grc.com/discussions.htm").
[IMG]https://www.grc.com/image/transpixel.gif[/IMG]
[IMG]https://www.grc.com/image/graypixel.gif[/IMG]
[IMG]https://www.grc.com/image/transpixel.gif[/IMG]
**Unsolicited Packets: [FONT=Arial][COLOR=#006600]PASSED[/COLOR][/FONT]** &#8212; No Internet packets of any sort were received from your system as a side-effect of our attempts to elicit some response from any of the ports listed above. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system remained wisely silent. (Except for the fact that not all of its ports are completely stealthed as shown below.)
[IMG]https://www.grc.com/image/transpixel.gif[/IMG]
[IMG]https://www.grc.com/image/graypixel.gif[/IMG]
[IMG]https://www.grc.com/image/transpixel.gif[/IMG]
**Ping Reply: [FONT=Arial][COLOR=#cc0000]RECEIVED (FAILED)[/COLOR][/FONT]** &#8212; Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.[/COLOR][/SIZE][/FONT][IMG]https://www.grc.com/image/transpixel.gif[/IMG]

edit2: of course I HAD to set some rules for that in firestarter which is easy to do..

edit3: and here's the output WITH firestarter started: (see next post)

---

### Post by nowshining on 2007-08-15
[IMG]https://www.grc.com/image/transpixel.gif[/IMG]
[IMG]https://www.grc.com/image/graypixel.gif[/IMG]
[IMG]https://www.grc.com/image/transpixel.gif[/IMG][FONT=Verdana,Arial,Helvetica,Sans-Serif,MS Sans Serif][SIZE=-1][COLOR=#000060]Your system has achieved a **perfect** "TruStealth" rating. **Not a single packet** &#8212; solicited or otherwise &#8212; was received from your system as a result of our security probing tests. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests). From the standpoint of the passing probes of any hacker, this machine does not exist on the Internet. Some questionable personal security systems expose their users by attempting to "counter-probe the prober", thus revealing themselves. But your system wisely remained silent in every way. Very nice.[/COLOR][/SIZE][/FONT]

---

### Post by Paul820 on 2007-08-15
That's exactly why i use it, i even use the same site to check. I want my computer full stealth on the internet and without having firestarter to set everything it wouldn't be. If my computer can be detected on the net, what's stopping someone from trying to get in. I would rather have it in stealth so no-one knows i'm on the net. Guess i'm just paranoid but it makes me feel more secure. :)

---

