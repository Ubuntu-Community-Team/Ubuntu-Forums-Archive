---
title: "Ubuntu security"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Unreal223linux on 2007-06-15
What kind of security measures do I need to do now that I'm running ubuntu.
I know that spyware, viruses, ect really aren't something linux users worry about but what do I need to do to make sure my system is secure? 

Do I need a firewall? And if so is there one out there like the xp firewall that just blocks incoming stuff on its own with zero config?

---

### Post by chiefboats on 2007-06-15
Its not zero config but close. Install firestarter with synaptic. Can walk you through it if needed.

---

### Post by starcraft.man on 2007-06-15
> **Unreal223linux said:**
> What kind of security measures do I need to do now that I'm running ubuntu.

None other than what you already have.

> I know that spyware, viruses, ect really aren't something linux users worry about but what do I need to do to make sure my system is secure? 
Spyware doesn't exist for linux to my knowledge. Viruses have been created as concept, they aren't wild though and even if they were you have to get them on your system and you'd have to actively do that with the firewall in place, like a transfer.

> Do I need a firewall?
IPtables is a firewall already installed and built right in. You don't need to do anything else other than boot up to be protected with it. Firestarter is just a GUI frontend for configuring it. Unless you plan on port forwarding or modifying the set up, don't bother and leave IPtables completely secured.

> And if so is there one out there like the xp firewall that just blocks incoming stuff on its own with zero config?
IPtables does that... everything is locked down unless you say otherwise.

[Read this please.]("http://www.psychocats.net/ubuntu/security") Don't worry about it is bottom line.

---

### Post by ramjet_1953 on 2007-06-15
Unless you need to alter iptables for port forwarding, you don't need to install Firestarter.

Firestarter is not a firewall, it is a graphical configuration tool for iptables.

Iptables, by default has closed all ports and your installion is very secure.

Do not get caught-up in fiddling with iptables, or having Firestarter running in your taskbar.

This is very dangerous, as Firestarter requires root privileges to run and by doing so, you are shooting yourself in the foot, by creating a security risk in running an application on your desktop with root privileges.

What is the old saying ? "If it's not broken, don't try to fix it".

Regards,
Roger :cool:

---

### Post by Unreal223linux on 2007-06-16
Thanks for the help then. :)
I use public wifi networks a lot and just wanted to make sure I wasn't leaving my computer wide open for someone to just start browsing through my files.(I don't really do anything major on them just browse but I still have stuff I would rather not have people steal.) 

Thanks for the answers! :)

---

### Post by chiefboats on 2007-06-16
While all the above is true, ther are problems with Ubuntu's default iptables configuration. The majority of your ports do show as closed but this in effect tells whomever may be trying to reach your box that it does esist by answering any outside request that you are there but closed for business for the moment. Your box even answers "ping" requests. Firestarter can stop this by setting iptables to silently drop those network packets rather than sending back the closed status.

To each his own.

---

### Post by Unreal223linux on 2007-06-16
So the ports aren't stealthed?(to use grc terms. :P)
Is firestarter something I have to have running all the time or can I just install it, configure, and then close it and keep the improvements?

---

### Post by starcraft.man on 2007-06-16
> **chiefboats said:**
> While all the above is true, ther are problems with Ubuntu's default iptables configuration. The majority of your ports do show as closed but this in effect tells whomever may be trying to reach your box that it does esist by answering any outside request that you are there but closed for business for the moment. Your box even answers "ping" requests. Firestarter can stop this by setting iptables to silently drop those network packets rather than sending back the closed status.

To each his own.

This is true, most firewalls close ports rather than stealth. I of course have had this solved for a very long time with a NAT router configured for stealth. I don't think though that it poses that much of a risk answering pings... I'd be more concerned frankly with using public wifi networks and losing important data... 

Oh and unreal, I see your a security now listener. Steve's a bit paranoid when it comes to security... I mean for some odd reason he runs with an almost crippled IE6 on his old machines rather than firefox with no script. I don't get it... Anyway, as ya like. I'd just stick with regular IPtables, its not worth hassle.

---

### Post by chiefboats on 2007-06-16
No, the ports are not stealthed and the ICMP ping is accepted and answered. Firestarter must be running to work but there are ways of editing the iptables rule set that are permanent and do not require it to run. I am working on that now but can't help you with it as I am in the process of teaching myself how to do it.

---

### Post by starcraft.man on 2007-06-16
> **chiefboats said:**
> No, the ports are not stealthed and the ICMP ping is accepted and answered. Firestarter must be running to work but there are ways of editing the iptables rule set that are permanent and do not require it to run. I am working on that now but can't help you with it as I am in the process of teaching myself how to do it.

Just curious, what makes you so concerned about being pinged/stealthed? Think theres a hacker stalking you? I mean I do it, and I do prefer it when I can, but I don't think its absolutely necessary for security nor always 100% practical.

---

### Post by chiefboats on 2007-06-16
Just seems like the thing to do after being in security work for most my life, physical security not the IT type. If anything can be made more secure, and theres nothing more secure than not being there (stealthed), then I feel it should be.

To each his own.

---

### Post by starcraft.man on 2007-06-16
> **chiefboats said:**
> Just seems like the thing to do after being in security work for most my life, physical security not the IT type. If anything can be made more secure, and theres nothing more secure than not being there (stealthed), then I feel it should be.

To each his own.

True. But don't you find that most attacks now a days have nothing to do with ports. I mean most seem now to occur due to the users own active participation. Take the OO bad bunny virus/exploit (recent thing, was over hyped). You have to actively by some means get that infected file on your PC and then open it with Writer, then of course it executes and messes you up through OO. That hasn't got anything to do with being stealthed or not, its on your pc and you opened it.

I mean there are lots of other examples, browsers exploits have been a pain on windows for a long time, like the ANSI thing that windows xp and Vista had a while ago. Then theres the newer cross site scripting flaws... it just doesn't seem like secured ports are the biggest problem anymore, or even on the radar. IMO, the browser is the most insecure and likely vector for attack on any PC (including Linux), it has direct interaction with the net and has lots of features tied directly to your computer.

Anyway, thats me. Make what you will of all this OP, I don't think stealthed ports is that important... being mobile introduces a lot more concerns IMO.

---

### Post by chiefboats on 2007-06-16
I see your point and have no silver bullet reply. The more you exposure you have the higher your risk is a concept that applies to all things, not just PCs. I think we are pretty much in agreement, I want as much security as I can get while still being able to do the things I need, or want, to do. You are right in that the more public exposure one has the greater risk they assume, no way around that. Have a good day as I'm going to move on to other things now.

---

