---
title: "Website"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by AnLGP on 2007-11-24
I want to start a website soon and I have a few questions.

1)  How do I host it from my own computer?
2) What security features should I install, if any?  (I hear ubuntu/linux is good for this)
3) I still have XP installed (am going to get rid of it if I can figure out how to work rosegarden) and would like to know if this would effect question # 2.
4) Any advice on this?

Anything I can do to clarify?

Thanks,
Steve

---

### Post by atomkarinca on 2007-11-24
First of all, you should install a web server. My suggestion is XAMPP because it not only includes Apache Web Server but also MySQL, PHP and Perl. You can find the howto [here]("http://www.apachefriends.org/en/xampp-linux.html").

Next, if your computer doesn't have a static ip, then you should have dyndns account and client. The address is [this]("http://www.dyndns.com/") and the client is [here]("http://www.dyndns.com/support/clients/unix.html").

---

### Post by wolfen69 on 2007-11-24
[http://www.pcstats.com/articleview.cfm?articleID=1774](http://www.pcstats.com/articleview.cfm?articleID=1774)  may be of some help

---

### Post by AnLGP on 2007-11-24
Thanks to you both.  

I have installed LAMP.  Would you recommend that I install XAMPP?  I do not know if my computer has a static IP.  How do I find this out?  Thanks for that link wolfen I'm reading it now.

---

### Post by Daveski on 2007-11-24
The point is if your ISP has given you a static address or a dynamic one. You need to use dyndns or similar if your public IP is dynamic. Check your account or call your ISP to clarify.

Also, if you are using a NAT router (rather than just a modem), then you will need to set up port forwarding to point any incoming connections on port 80 to the local IP address of the web server.

---

### Post by daengbo on 2007-11-25
Speaking from experience, hosting your own server will require a lot of maintenance time. I'd recommend you look at hosting unless you can't afford it or are doing this for educational pruposes.

Next, get an Ubuntu Server CD and install a LAMP setup. I don't suggest going with XAMPP because you'll have to update that manually.

Next, install a good firewall (I recommend Shorewall), an IDS (Intrusion Detection System) like Snort and/or Portsentry, and a rootkit detector.

If you don't have a static IP, you'll need to get a Dynamic DNS account and install a management program like EasyIP. Search the repositories for "Dynamic DNS." You may need to set up port forwarding on your router.

I'd recommend using web apps from the repos whenever possible so that exploits are patched easily. An unpatched web app is an invitation for web defacement or worse.

Good luck on your new endevor.

---

### Post by jcsteele on 2007-11-25
You might also want to look into the legal agreement you have between you and your ISP.  Many do not allow running server(s) and they define what is and is not permitted to run on their network.

I just wanted to mention it so you do not get all of this setup and working great, then find out your ISP has cancelled your service due to violation of their terms for service.  I know it sounds frivolous, but a public accessible http server is a fairly easy thing for them to find on their network, and I would surmise they have automated tools that take care of the job for them as well.

//jcs

---

### Post by carlosjuero on 2007-11-25
Another thing: You need to find out if your ISP blocks port 80 (inbound) on your connection; many ISP's block this by default to stop people from hosting websites at home (and thus sucking up bandwidth - or whatever their excuse is). I know that my ISP (Optimum Online, Cablevision) blocks port 80 unless you get their upgraded 'Boost' package (which gives you 30Mbit/s down and 15Mbit/s up) which allows you to open up ports 80 & 25 to allow hosting a web site from the home (it is even specified and supported in their ToS - in fact they give you a free domain name and a DDNS client to go with it - proprietary DDNS client, but a fully qualified domain name for nothing).

The best way to find out, if you don't want to alert your ISP or get some sort of brush off answer, is to set up the site through DynDNS.org [if you have a dynamic DNS] and then going somewhere else (off your IP/Internet connect) to test out the URL - if you cannot connect (timeout) then likely the port is blocked; otherwise it should be fine and dandy.

---

