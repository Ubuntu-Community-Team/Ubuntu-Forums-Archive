---
title: "How good is Windows 7s Firewall?"
date: 2011-10-26
forum: Any Other OS
---

### Post by NattyLight on 2011-10-26
Passable? This is just for home use so I don't need it to be super hardcore but if the firewall is a joke than I will probably DL Comodo Firewall for it.

---

### Post by Dangertux on 2011-10-26
Firewalls are probably one of the most misunderstood network security applications out there. 

Most firewalls will provide at least the minimum functionality (windows firewall included)

- Stateful Packet Inspection
- Ability to drop, reject or accept packets (based on a variety of factors, some give more options than others)
- Ability to limit packet traffic based on rate.
- Ability to forward traffic to a computer (Routing)

Those are the 4 most commonly used applications for a firewall, some firewalls like iptables include some extra functionality like tarpit. However, that is an advanced use case and not really pertinent to your initial question.

If you want a simple response to your question, quite simply yes (despite the hate for MS on this forum) Windows Firewall, if properly configured is adequate protection. If you wish to increase the protection offered by the Windows security suite I would highly recommend installing [Microsoft Security Essentials ]("http://www.microsoft.com/en-us/security_essentials/default.aspx")(it's free)

Now if you wish to know WHY Windows Firewall is adequate please continue reading.

First Windows Firewall does provide Stateful Packet Inspection. While not the best in the world, it is certainly preferable to a stateless firewall. It's important to understand what SPI is, since many often confuse SPI with Deep Packet Inspection, which is something entirely different. Stateful Packet Inspection is a process that makes sure connections are legitimate in that they are behaving the way a connection should. IE: They will not allow a TCP connection to be established with ACK. Since the first packet must have the SYN flag or it will be considered anomalous. This is just a small example, however it can limit the use of some exploitation methods as well as some types of denial of service (particularly reflective types). Conversely a Deep Packet Inspection firewall can be likened to an Intrusion Prevention System, as it is going to examine the contents of the packet to determine if its intent is malicious, and drop or reject it appropriately.

In addition to this and standard control over both TCP and UDP ports Windows firewall does allow fairly fine grained control on a by application basis. While it doesn't quite provide as many options in terms of limiting as iptables, for the average home use case the Windows Firewall is actually quite adequate. In fact in its infancy (circa windows XP) the firewall was rather immature, a lot like the GUFW front end is now. However, in my opinion it is equal in terms of functionality with UFW. Though, UFW does not allow access to some of iptables' finer grained controls so it remains slightly behind the curve there. However, if you factor in Windows Firewall's intended audience it doesn't particularly need those controls, much like UFW does not.

I hope that this helps you make your decision easier.

---

### Post by ubupirate on 2011-10-26
[delete, Dangertux answered all before me lol]

---

### Post by satanselbow on 2011-10-26
@Dangertux:

Do you have any comment on the Comodo Internet Security Suite? It is my preferred Windows firewall/av client like the OP.

My biggest problem with the Windows Firewall (out of the box) is it's lack of control of traffic leaving a machine (outbound). Given that Windows is awash with software regularly phoning home - this is something WFW does not cater for :(

Not trying to catch you out ;) Just interested on the opinion of someone with a more indepth knowledge than myself :popcorn:

---

### Post by NattyLight on 2011-10-26
> **Dangertux said:**
> Firewalls are probably one of the most misunderstood network security applications out there. 

Most firewalls will provide at least the minimum functionality (windows firewall included)

- Stateful Packet Inspection
- Ability to drop, reject or accept packets (based on a variety of factors, some give more options than others)
- Ability to limit packet traffic based on rate.
- Ability to forward traffic to a computer (Routing)

Those are the 4 most commonly used applications for a firewall, some firewalls like iptables include some extra functionality like tarpit. However, that is an advanced use case and not really pertinent to your initial question.

If you want a simple response to your question, quite simply yes (despite the hate for MS on this forum) Windows Firewall, if properly configured is adequate protection. If you wish to increase the protection offered by the Windows security suite I would highly recommend installing [Microsoft Security Essentials ]("http://www.microsoft.com/en-us/security_essentials/default.aspx")(it's free)

Now if you wish to know WHY Windows Firewall is adequate please continue reading.

First Windows Firewall does provide Stateful Packet Inspection. While not the best in the world, it is certainly preferable to a stateless firewall. It's important to understand what SPI is, since many often confuse SPI with Deep Packet Inspection, which is something entirely different. Stateful Packet Inspection is a process that makes sure connections are legitimate in that they are behaving the way a connection should. IE: They will not allow a TCP connection to be established with ACK. Since the first packet must have the SYN flag or it will be considered anomalous. This is just a small example, however it can limit the use of some exploitation methods as well as some types of denial of service (particularly reflective types). Conversely a Deep Packet Inspection firewall can be likened to an Intrusion Prevention System, as it is going to examine the contents of the packet to determine if its intent is malicious, and drop or reject it appropriately.

In addition to this and standard control over both TCP and UDP ports Windows firewall does allow fairly fine grained control on a by application basis. While it doesn't quite provide as many options in terms of limiting as iptables, for the average home use case the Windows Firewall is actually quite adequate. In fact in its infancy (circa windows XP) the firewall was rather immature, a lot like the GUFW front end is now. However, in my opinion it is equal in terms of functionality with UFW. Though, UFW does not allow access to some of iptables' finer grained controls so it remains slightly behind the curve there. However, if you factor in Windows Firewall's intended audience it doesn't particularly need those controls, much like UFW does not.

I hope that this helps you make your decision easier.

 Wow, awesome post, I do already have Microsoft Essentials (one of the first things DLed when I upgraded from XP) before that Avast was the cats meow as far as antivirus goes for XP and lower, but was told the Essentials is better to have for 7 than Avast again.  I have used Comodo when I had XP and it was great, sounds like the firewall for 7 is alright but I will probably DL Comodo again for it, my only concern now however is if Comodo will interfere  with Microsoft Security Essentials somehow? I like Win 7 but I like Ubuntu a lot better lol, I still need the Win side to be safe cause unfortunately, theres no completely getting rid of Windows, especially at my school where *everything* needs to use Windows :(

---

### Post by NattyLight on 2011-10-26
> **satanselbow said:**
> @Dangertux:

Do you have any comment on the Comodo Internet Security Suite? It is my preferred Windows firewall/av client like the OP.

 So do you have Windows 7 as well? Did you notice that having Comodo installed interfered with anything else? Good question however.

---

### Post by ubupirate on 2011-10-26
> **NattyLight said:**
> So do you have Windows 7 as well? Did you notice that having Comodo installed interfered with anything else? Good question however.

If you get the standalone Comodo firewall, I don't think it will interfere with MSE. If you either get the standalone Comodo AV or Comodo IS, then maybe it will.

---

### Post by Dangertux on 2011-10-26
> **satanselbow said:**
> @Dangertux:

Do you have any comment on the Comodo Internet Security Suite? It is my preferred Windows firewall/av client like the OP.

My biggest problem with the Windows Firewall (out of the box) is it's lack of control of traffic leaving a machine (outbound). Given that Windows is awash with software regularly phoning home - this is something WFW does not cater for :(

Not trying to catch you out ;) Just interested on the opinion of someone with a more indepth knowledge than myself :popcorn:

Actually I believe you may be incorrect about outbound controls in Windows Firewall. 

See here : [http://technet.microsoft.com/en-us/library/cc732306%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/cc732306%28WS.10%29.aspx")

Anyways, as far as Comodo Internet Security Suite goes, as I stated in my original post most firewalls that aren't insanely expensive (IE: a physical device you put on your network), are going to offer roughly the same functionality. Maybe a more intuitive interface etc, but it's all going to be the same. If you're really concerned about heuristics based matching of attack patterns you're going to want to move into an IPS or DPI firewall, which as far as I'm aware CIS does not offer (I could be wrong shop around). 

Obviously, a security suite is going to offer more functionality than just a firewall, so I'm not going to factor in the extra functionality there, as we are talking about the firewall aspect. Not anti-malware or browser addons.

Hope that helps answer your question.

---

### Post by NattyLight on 2011-10-26
Thanks for all the responses everyone!

---

### Post by servermonitoring on 2011-10-27
Working fine although you need some good firewall for all protection.

---

### Post by satanselbow on 2011-10-27
> **Dangertux said:**
> Actually I believe you may be incorrect about outbound controls in Windows Firewall. 

See here : [http://technet.microsoft.com/en-us/library/cc732306%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/cc732306%28WS.10%29.aspx")

Thanks again for your thorough answer ;)

Reading the MS link - action is required to manually configure the WFW by the user to block outbound traffic and no notification will be made to the user of traffic leaving their system in it's default state. From realworld experience this does not happen and is beyond the average "Joe Windows User" understanding.

Comodo - whilst configured to be more generous with common web traffic eg browser/email requires case by case (app by app) approval by the user for outbound traffic (updaters/phone-homes)

I would consider this an essential requirement of any fw on my windows boxes - MS obviously consider it as a spoiler on the "windows experience" ;)

@nattylight:

Comodo replaces the default WFW (integrates with the security panel) on installation and does not "interfere" although you will require more manual intervention on installation and 1st runs of apps to allow/block their access to filesystem/registry/internet ;) Comodo also includes a sandbox feature which I disable on installation as I find that feature too intrusion... I also turn off "GeekBuddy" which used to be optional during installation of the suite... you can't win :D

I take in and repair PCs. Anything that comes in with security breaches/virus or requires a reinstall of the OS gets Comodo on before it leaves me. I haven't ever had a Comdo secured machine back with further virus/spyware issues and usually get thanked for saving the user annual subscriptions fees to "A.N Other security Suite" - you know who they are :D 

The current big/popular windows security suite providers are in that position because of the deals they do with OEM and PC retail outlets to get their software on new machines - not because they are actually any good ;) If they were windows spyware/virus reputation problems would have been fixed years ago :lolflag:

---

### Post by BrokenKingpin on 2011-10-27
It is pretty good. That plus Microsoft Security Essentials (which is free) for anti-virus and you are good to go. These are also pretty good on the system resources, unlike other av and firewall software for windows.

---

