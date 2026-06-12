---
title: "Firestarter firewall setup"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by AngelBreath on 2007-07-07
When i enable firestarter i m loosing the internet connection. Is there something i have to do? I use an ethernet D-Link adsl modem. I didnt setup nothing in firestarter no policies not anything yet.

---

### Post by mattze on 2007-07-07
firestarter has 2 different modes
whitelist(blocks all but) and blocklist(blocks only whats on the list)
might that be the issue?

---

### Post by oilchangeguy on 2007-07-07
you really don't need firestarter. it's not a firewall. it's the gui, for the already installed firewall, iptables.

---

### Post by atria on 2007-07-07
> you really don't need firestarter. it's not a firewall. it's the gui, for the already installed firewall, iptables.

Yes yes it sure is a gui for iptables, but do you realize that iptables is disabled by default?
And unless you know how to configure iptables properly, there will always be a need for frontend tools like firestarter.
[edit]I'm sorry that i was a little harsh there. But try not to post irrelevant nonsense like this.[/edit]

In any case, your problem might be due to
1) firestarter might be blocking everything except the entries you have configured in your white list. In this case you'll have to change it to the black list mode as mentioned by mattze.

2) Your computer might not be fast enough for firestarter to flush and reload the firestarter policies, thus resulting in timing outs of existing connections. In this case try to reduce your system load when you plan to start/restart firestarter.

The above list is by no means comprehensive, there are other reasons why it might happen. Do you mind describing your problem further? Like, are existing connections dropped as soon as firestarter is started? Does internet connection work at all after a system reboot with firestarter started?

Hope that helps

---

### Post by ramjet_1953 on 2007-07-08
Atria, iptables IS NOT disabled by default.

The default setup is for ALL ports to be closed and your system is VERY secure.

As stated earlier, you do not need Firestarter, unless you specifically need to open ports for port forwarding.

The Golden Rule applies here. "If it's not broken, don't try to fix it".

Go to the Shields Up website and check your system, if you do not believe me.

Regards,
Roger :)

---

### Post by Malibu Illusion on 2007-07-08
Ports are closed by default, firewall or no firewall.  Closed ports only signify that there is no daemon listening on that particular port, not that anything is particularly responsible for closing them, per-se.

Daemons, typically, are responsible for listening on the outside network for connections.  You're only as secure as the software controlling that.  Ubuntu comes with no daemons listening by default unless you have set them up.  This is why it it is secure.  OSs like Windows come with a multitude of unsecure daemons listening right out of the box, which causes a problem.

---

### Post by mcduck on 2007-07-08
> **ramjet_1953 said:**
> Atria, iptables IS NOT disabled by default.

The default setup is for ALL ports to be closed and your system is VERY secure.

As stated earlier, you do not need Firestarter, unless you specifically need to open ports for port forwarding.

The Golden Rule applies here. "If it's not broken, don't try to fix it".

Go to the Shields Up website and check your system, if you do not believe me.

Regards,
Roger :)
It's not disabled, but it doesn't do anything unless you use some script or tool to give it rules to work with.

The reason why all ports in default Ubuntu install show as closed is that there is no program responding to  incoming traffic in any port. So as long as you don't have any open servers running you don't need a firewall.

---

### Post by AngelBreath on 2007-07-08
Even trying the outbond policie to setup blacklist either whitelist still the same problem. Internet connection AND firestarter cant work together.

---

### Post by namealreadytaken on 2007-07-08
AngelBreath,

Bearing in mind I am a complete novice to Ubuntu, I changed my firewall settings from erth0 to erth1 and was able to activate the firewall, not sure why it made a difference.

For what it is worth

---

### Post by AngelBreath on 2007-07-09
namealreadytaken

 Actually thsnk my friend. This worked for me too. I guess there is no firewall enable now ,but at least i dont have to start firestarter and disable it in every boot. 

Thanks a lot

---

### Post by ushills on 2007-07-09
There appears to be something that Firestarter adds to the firewall scenario, if you do a test of your ports with a firewall scanner like [shields up]("http://www.grc.com/") without Firestarter all ports will be listed as closed, however, with Firestarter installed the ports report as stealthed.

This difference basically means that to the outside world your machine doesn't exist when Firestarter is installed.

Does this make a difference with ubuntu, I do not know.

---

### Post by kittyhawk63 on 2007-07-19
I ran Shields Up  [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) and found that iptables was not working fully. I installed and ran Firestarter and made a minimal amount of configurations. I reran Shields Up and everything passed perfectly.
kh

I made these Firestarter settings : (just two)
Network Setting: selected: "Enable DHCP for the local network"
ICMP Filtering: I checked "Enable ICMP Filtering". *I did not check anything else here*.

---

### Post by fusionisthefuture on 2007-07-21
hi.

i am extremely happy with the way that ubuntu's iptables is configured, except when i want to use a torrent program.  for this i got firestarter, and told it to open some ports.  is it possible to set profiles, or get it to some way NOT start firestarter every time i start the OS, so that iptables uses its default rules, except when i have firestarter turned on manually?

thanks,
-arne

---

