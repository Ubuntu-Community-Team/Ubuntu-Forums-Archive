---
title: "Firestarter Worries"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by BigRon on 2008-02-10
Hello People! I am new to Ubuntu and Firestarter. When running Firestarter I have noticed it's counted 25 serious inbound events.

I've only been online an hour or so, and there's a list of blocked connections as long as your arm, is this normal?

I am not a computer expert and have had 2 nightmarish experiences of trojans in the past (using windows of course) and was told that I wouldn't need a Firewall with Ubuntu because I have no interest in file sharing or anything. However I've installed one anyway just to be on the safe side and it looks as if all hell is breaking loose despite everything running fine.

There have been blocked connections from the following services: Unknown, Samba(SMB), Traceroute, DCOM-scm, Webadmin, Microsoft ds, Radmin port and God knows what else.:confused:

Do any of the above sound familiar? Are they anything to worry about?

I know I'm pretty clueless, but some advice would be much appreciated.

Cheers

---

### Post by lespaul_rentals on 2008-02-10
I wouldn't be too worried.  Are you behind a NAT or a router?  Look at it this way, Firestarter is working for you.  ;)

---

### Post by misfitpierce on 2008-02-10
Exactly its helping protect you... Perhaps a port you use is closed but if everything is still functioning and your ports are closed just means your safe from stuff that shouldnt have reached you. :)

---

### Post by zvacet on 2008-02-10
> had 2 nightmarish experiences of trojans in the past 

Ubuntu(or any other linux) is solution for your nightmares,because malware are made to harm windows.That means that malware can not be run in linux because of different exe files.If you want to be secure read [this](http://ubuntuforums.org/announcement.php?f=73).

---

### Post by PeterJS on 2008-02-10
Linux security is based on an entirely different paradigm. Windows security is based on the idea of containing and fixing problems after they crop up, AV, firewalls, etc. While linux security is based on rendering threats inert, no open ports, permissions, separation of user and admin. No need to worry about something that wasn't a threat in the first place.

The ubuntu security guide:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by hyper_ch on 2008-02-10
peter: ubuntu ships with ports open - but with no listening applications.

---

### Post by PeterJS on 2008-02-10
> **hyper_ch said:**
> peter: ubuntu ships with ports open - but with no listening applications.

Really? I might have got the terminology mixed up, but I thought that bit was a point of pride.

I guess it all comes down to how useful an open port with nothing listening on it is. If a tree falls in the forest and no one is around to hear it, does it make a sound?

---

### Post by CasperRed on 2008-02-10
I'm guessing what you are seeing from Firestarter are people looking for a Windows system to get into. Since you don't have Windows, you shouldn't worry.

---

### Post by BigRon on 2008-02-10
Thanks very much to all for explaining this to me. I am impressed everyone has replied so quickly and been so helpful.

---

### Post by lespaul_rentals on 2008-02-10
> **CasperRed said:**
> I'm guessing what you are seeing from Firestarter are people looking for a Windows system to get into. Since you don't have Windows, you shouldn't worry.

I would disagree with this.  Ubuntu allows for Windows services to be set up.  Think of Samba, printer shares, etc.  If they try an attack against port 139 for example, sure, they are intending to attack a Windows machine.  But if it somehow hits a Linux machine running Samba, the effect will be the same.

Now, I know you've got your problem resolved, BigRon, so don't get worried again.  Are you behind a router or a NAT?  If so, you are fairly safe.  Just make sure you don't have any unnecessary ports forwarded to your machine.  This is a good rule whether you are using Windows or Linux.  DSL/Cable routers are probably one of the greatest things to happen to home network security.  Back in the days of dial-up, computers had an IP address and were directly connected to the wall, with no separation between the outside world and their computer.  Now that we have NATs commonplace in broadband home networks, your computer doesn't have a public IP address, say 71.276.90.82.  If a hacker or script-kiddie got a hold of that, he could attack your IP directly.  But if you are behind a router or a NAT, your computer's IP is something like 192.168.1.2.  If the hacker attacks the public IP, he will be attacking the router, a smart device, that will usually not allow him to get through to your private computer.

If this sounds like Greek to you, my apologies.  I just want to explain why routers are a great thing.  ;)

Also, if you have Windows computers on your network, you may get "hack" attempts by the nosy Windows computers, which have a tendency to probe around for services to share.  These are not necessarily malicious, but because of the sheer number of request packets that Windows computers send, it can seem that way.  I once used Wireshark (a packet sniffer) to study what kind of packets were bogging down my network.  Note that my dad and I are smart and use Linux, so there are only two Windows computers for my mom and sister to use.  These two Windows computers were sending request packets for all kinds of services, over and over.  Note that they were not infected either!

So, I would not be worried.  You should be fine.  :)  Feel free to post if you have any more questions.

---

