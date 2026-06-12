---
title: "Is Ubuntu/Linux at risk with closed ports?"
date: 2006-04-08
forum: Absolute Beginner Talk
---

### Post by wasp on 2006-04-08
I went to a port testing site, and it said the ports were closed (better than open) but weren't stealthed (better than closed I guess, since it makes the port seem like it doesn't exist).

In Linux, can closed ports be found and hacked into like they apparently can in Windows? And if so, is there a way to stealth them?

I tried to get Firestarter, but I'm running Dapper, and it doesn't seem to have made it's way there yet. I heard Firestarter is basically just a GUI for iptables, so is there a way to stealth ports with that? And even should I?

---

### Post by angkor on 2006-04-08
By default Ubuntu doesn't listen to any port, so you're pretty safe.

But you know what they say, the only invulnerable computer is unplugged and buried in concrete. ;)

Just make sure you have strong passwords and use your common sense.

Edit: I just scanned my common ports at:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

and they were all stealthed on a default Dapper Drake installation. Are you behind a router / hardware firewall?

---

### Post by wasp on 2006-04-08
[QUOTE=angkor]

Edit I just scanned my common ports at:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

and they were all stealthed on a default Dapper Drake installation. Are you behind a router / hardware firewall?[/QUOTE]

I went to that same site, on a default Dapper install, and it listed all my ports as closed. Odd.

No I don't have a router.

---

### Post by angkor on 2006-04-08
[QUOTE=wasp]No I don't have a router.[/QUOTE]

That's probably the difference. My modem / router acts as a hardware firewall.

---

### Post by erniewinner on 2006-04-08
i'm running flight 5 with firestarter. whats your problem with it?

---

### Post by wasp on 2006-04-08
Does anyone know if there is any way to configure iptables to stealth unused ports and/or allow specific applications access to a given port, much like Zonealarm does for Windows?

I looked through the wiki, and played around with iptables through the command line, (a little challenging for a Linux newbie) and was also able to get Firestarter in Dapper, with the uni/multiverse repositories. It seemed to be all or nothing, though. Either port 80 for example, was open or it wasn't. I didn't see a way to allow Firefox, but deny say, Opera...

Is this is possible? Either with the command line, or with a firewall app?

---

### Post by 5-HT on 2006-04-08
[quote= wasp] Does anyone know if there is any way to configure iptables to stealth unused ports and/or allow specific applications access to a given port, much like Zonealarm does for Windows?

I looked through the wiki, and played around with iptables through the command line, (a little challenging for a Linux newbie) and was also able to get Firestarter in Dapper, with the uni/multiverse repositories. It seemed to be all or nothing, though. Either port 80 for example, was open or it wasn't. I didn't see a way to allow Firefox, but deny say, Opera...

Is this is possible? Either with the command line, or with a firewall app?[/quote] Firestarter, as you said, is pretty much all-or-nothing on each port (but it should stealth closed ports).

As to a application-based firewall (for allowing/disallowing certain applications from communicating on the network), I'm not sure if one currently exists for linux. I'm not sure if iptables could do this either.

Just as an aside, stealthed ports do not add any real security benefit. In silently dropping packets, stealthed ports are like  black holes from which no response is forthcoming. By not sending back a 'destination unreachable' response, someone knows that you are there. Stealthed ports may actually attract more attention as people get curious as to what might be behind them that is so precious. In addition, the moment any data leaves your computer, you are no longer stealthed and any packet sniffer could determine this.

---

### Post by erniewinner on 2006-04-08
oh sorry i thought you meant you couldn't get it working. i'm no expert but it seems most people think linux doesn't carries the kind of risks that merrits such measures? i think firestarter is as complex as it gets after all there isn't that much history of such nasty things happening on linux. i appreciate what your saying coming from windows it sure makes you worry... i've got a nat router as an added precaution that stealths me, cheap too... but no app control. i shall watch your thread with interest!

---

### Post by dcstar on 2006-04-08
[QUOTE=wasp]I went to that same site, on a default Dapper install, and it listed all my ports as closed. Odd.

No I don't have a router.[/QUOTE]

So you plug your Ubuntu PC directly into the Internet (not via a NAT device) with a "real" IP address assigned to the Ubuntu box?

---

### Post by wasp on 2006-04-08
> **5-HT]Firestarter, as you said, is pretty much all-or-nothing on each port (but it should stealth closed ports).

As to a application-based firewall (for allowing/disallowing certain applications from communicating on the network), I'm not sure if one currently exists for linux. I'm not sure if iptables could do this either.

Just as an aside, stealthed ports do not add any real security benefit. In silently dropping packets, stealthed ports are like  black holes from which no response is forthcoming. By not sending back a 'destination unreachable' response, someone knows that you are there. Stealthed ports may actually attract more attention as people get curious as to what might be behind them that is so precious. In addition, the moment any data leaves your computer, you are no longer stealthed and any packet sniffer could determine this.[/QUOTE]

Ports came back as stealth under Firestarter, but still replied to ping requests so therefore "failed". Being new to Linux, I don't know how big of a deal that is, (I'm guessing not much) but it gave me pause, since everything was stealthed _**and **_ignored ping requests under the Windows firewall. If I didn't know any better, I might think Windows was the more secure environment. :p (I do know better, though)

I wonder why it is that no Linux firewalls have application-specific rules. That seems to be common in the Windows world, as it's not only fairly powerful, but user friendly as well. (Not that Linux has to be like Windows, I'm just saying...  said:**
> oh sorry i thought you meant you couldn't get it working. i'm no expert but it seems most people think linux doesn't carries the kind of risks that merrits such measures? i think firestarter is as complex as it gets after all there isn't that much history of such nasty things happening on linux. i appreciate what your saying coming from windows it sure makes you worry... i've got a nat router as an added precaution that stealths me, cheap too... but no app control. i shall watch your thread with interest!

No, at first I couldn't install it all. I tried sudo apt-get install firestarter , which didn't work. Then I figured out it was in the uni/multiverse repositories. At least for Dapper, anyway.

And yes, coming from Windows is EXACTLY what it is. Less than a week ago, I had a firewall to which I didn't dare connect Windows to the internet without. It's hard to believe that I can run Ubuntu with a laid back attitude to a firewall, or maybe not even really need one at all. :)

---

### Post by wasp on 2006-04-08
[QUOTE=dcstar]So you plug your Ubuntu PC directly into the Internet (not via a NAT device) with a "real" IP address assigned to the Ubuntu box?[/QUOTE]

Yes, I think so. Is that bad?

---

### Post by 5-HT on 2006-04-08
[quote=wasp]Ports came back as stealth under Firestarter, but still replied to ping requests so therefore "failed". Being new to Linux, I don't know how big of a deal that is, (I'm guessing not much) but it gave me pause, since everything was stealthed and ignored ping requests under the Windows firewall. If I didn't know any better, I might think Windows was the more secure environment.  (I do know better, though) [/quote] 
In Firestarter, if you go to edit > preferences > firewall > ICMP filtering > Allow ICMP filtering you can block responses to pings. If "allow ICMP filtering" is checked, any of the options that are unchecked are blocked, and any that are checked are allowed.
[quote= wasp]
I wonder why it is that no Linux firewalls have application-specific rules. That seems to be common in the Windows world, as it's not only fairly powerful, but user friendly as well. (Not that Linux has to be like Windows, I'm just saying... ) [/quote] 
Yeah, I definitely agree with you. It would be nice to have application-specific rules. Maybe in time though.
[quote= wasp]
And that is good to hear if stealthed ports don't add much security. I have only a basic understanding of how all of that works, I've just heard hackers can try to get into a closed port, while a stealthed one seems like it doesn't even exist. I guess if you can tell a port is stealthed, it makes sense it might attract curiousity, though..
[/quote] For a casual attacker, stealth can be good depending on if they are simply looking for a response or not. If someone is determined though, it doesn't really add any protection.

If you want, you can change Firestarter to either stealth (drop packets silently) or close (reject with error message) ports in the 'advanced options' section.

If you don't have any world-listening services running (which there aren't any by default), such as a mailserver for example, I really wouldn't worry too much. This is the major difference between Ubuntu and Windows, in Windows there are many world-listening services running by default (and in secret). It's always nice to have a firewall for extra piece of mind though.

---

