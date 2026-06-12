---
title: "[SOLVED] what does ntop show??"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by duruttye on 2007-11-22
Hey guys!
I've been seeing some strange activities in my network, so I installed ntop.

I'm seeing an uknown IP address and heavy activity, all time connection.
In the attached screenshot I'll show you the address. Every time I refresh the page, the last time seen time is refreshed too, so, i'm guessing, that this some connection.

I'm completely lost.
Please advice.
Thanx!

---

### Post by duruttye on 2007-11-22
Forgot  the screenshot...

---

### Post by Dr Small on 2007-11-22
I would first like to see this screenshot ;)

---

### Post by Dr Small on 2007-11-22
Well, here is the Whois Page for it:
[http://whois.domaintools.com/116.0.216.51](http://whois.domaintools.com/116.0.216.51)

Hmm. If you check your firewall, is it being blocked, or is he accessing one of your services over an open port ?

---

### Post by duruttye on 2007-11-22
This is what I know:
He uses this port:
2712  Axapta Object Communication Protocol - on his PC

42710 - and this is mine, there is no data about it on grc.com

How can I check if it is opened?
I have install firestarter, but there is activity even when it is locked...

---

### Post by duruttye on 2007-11-22
Hm, this is odd, the shields up, from grc.com, says, that this port on my PC is in stealth mode...

---

### Post by duruttye on 2007-11-22
How could I just kick him out of there?
Is there a way to restrict access for specific IP addresses?

---

### Post by seachnasaigh on 2007-11-22
If you're using IPTABLES, just put in a quick rule to block his IP, or his entire address block if you don't do business with Japan. Then forget about him.

vim your firewall, then near the bottom, put in a line that looks like this:

$IPTABLES -A INPUT -s 116.0.216.0/32 -j DROP

Then restart your firewall and go on about your business. 
Of course, if you do business with Japan, you'll want to modify the address to block him specifically, but I'd just block his ISP's /24 or /32 or /20 or whatever they have and let it go at that. I'm assuming here that he's DHCP and he's using a range of addresses within his ISP's assigned block. You can remove (or better: comment out) the line in 30 days or so when he's picked another victim.

Good luck!

ckr

---

### Post by duruttye on 2007-11-23
Well, when I saw the "victim" expression, I shut down the laptop and went to bed>:)

I'm not exactly sure what I should do with that command you wrote down for me, I would greatly appreciate some help no this.

I'm curious what happened.
Did he hack in my laptop? Should I change my passwords? or what exactly happened?

It looks for the moment that it's gone, but this was going on for 4-5 days now...

Thanx!

---

### Post by seachnasaigh on 2007-11-23
Sorry, didn't mean to frighten you.

Apologies again, I suppose that I was making a few assumptions ... that you have a firewall, that you're using IPTABLES, etc. The command I gave you is an iptables rule ... rules are processed in order, and I advised initially putting it near the bottom of your ruleset. Essentially that command says that any traffic from the source (-s) IP range to your machine should be dropped by the rule (-j DROP) regardless the port, the type of traffic, etc. It's a freeze-out rule. It returns no response to the source IP at all; their traffic or probe or whatever simply "falls into a black hole" so to speak, from their perspective.

I didn't do a lot of analysis of the traffic; I don't have your logs available and the snippet from ntop isn't terribly enlightening as to what the traffic was. Looking at it again, it could be any number of things but is most likely a probe rather than an actual hack. The port on your machine is a high non-assigned port, meaning it could be assigned all sorts of traffic if you wish. The port on his machine may have been chosen to disguise his probe or to look legitimate. The stealth bit just means it's open but not broadcasting its status. Open a terminal and do a netstat; you'll see lots of that sort of thing.  Google up the findings; you'll worry yourself sick otherwise looking at suspicious-sounding things that are actually pretty normal.  

Our boy from Japan there could be an apprentice hacker just learning how to probe open ports, or it could be a script simply looking for something to exploit. Most of both of these don't know if they're dealing with a Linux or Windows machine, and once they find out it's Linux, usually move on. It could be someone more sophisticated in Russia or Brazil using a spoofed Japanese address or even using a compromised Japanese box as a relay; we really don't (and won't) know for sure. Unless you're a security professional or looking to become one, don't worry about it; just freeze them out and go on using your computer. If you don't have any suspicious bandwidth usage outbound and haven't heard from them in a while, you might not even need to do that. 

Do a bit of research on iptables, check out the details of your firestarter program, and the code line I gave you will make more sense. IPTABLES firewalls are basically scripts that are run; that line is just one rule in a script. IPTABLES itself is not an editable file; the firewall scripts are. You can build that script graphically in fwbuilder (sudo apt-get install fwbuilder rc fwbuilder-doc) or any number of other front ends for IPTABLES. It sounds, however, like you don't have a lot to worry about. Cheers!

ckr

---

### Post by duruttye on 2007-11-23
Thank you, that cleared my mind!

Yesterday night I managed to block the traffic with firestarter and haven't heard from there since, so it is probably they gave up.
Just for my peace of mind, I changed my passwords, and I have alway an open tab in firefox for ntop :)
I'm just wondering what they can do with a windows machine, 'cause I have seen a few of them with wide opened ports... They don't even need to probe anything, just walk in, like an invitation.
Why do people use windows anyway????? It's a mystery for me....

Thanx for the replies, and once again you made me believe in The Ubuntu Forum!! 
Great support for those who are new to linux!!!

Thanks again for the help!
Take care!!

---

### Post by seachnasaigh on 2007-11-23
That's an excellent way to handle it, and you're very wise to be using a Linux system.

Windows users are very trusting souls; they prefer convenience over security every time, until they're hacked. You're aware, and that's good. Just don't frighten yourself unnecessarily over too many things that are everyday on the internet. There are a lot of bad guys, script kiddies, and 'bots out there probing nearly every machine on the internet for an exploit. Most of our systems are pretty secure. Linux is both harder to hack and less prevalent than Windows, and most of the cheap criminals out there are looking for an easy victim. You're not. Keep an eye out for bad stuff on your machine but be aware that this sort of probing is pretty common. Most Windows users aren't even aware it's happening, and that puts you way ahead of all of them.

I think Microsoft's products are the past; I think Linux is the future. I think one day MS products will be either so easy to exploit that they'll be unviable (XP) or so difficult to use that they're unusable (Vista). We may have seen the turning point in the computing world ... and it's us.

Cheers!

ckr

---

### Post by Mithrilhall on 2007-11-23
Another great program for monitoring traffic is iftop. I can't live without it.

---

