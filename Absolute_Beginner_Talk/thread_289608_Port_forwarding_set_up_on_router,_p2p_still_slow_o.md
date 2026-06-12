---
title: "Port forwarding set up on router, p2p still slow or dead"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by Zeke73SG on 2006-10-31
I've been trying to figure this out for days and I'm about to pull my beard out. I have read a multitude of posts on various forums about this and the answer is invariably "go to your router and enable port forwarding for such-and-such!" and I have done this many times over. I bypassed the router for troubleshooting and the situation didn't change. It's a Netgear wireless router and I am physically plugged into the LAN. For some reason I don't trust this router, probably because it's my girlfriend's and I didn't buy it myself. So I tried Firestarter for awhile but again, nothing changed, so I go rid of it and went with this guide:
[http://doc.gwos.org/index.php/IptablesFirewall]("http://doc.gwos.org/index.php/IptablesFirewall")
Still torrent downloads never top 2KB/s and don't find seeders unless I force update, and then they gradually fall off. When connecting to servers in aMule the client always returns an error saying the port is not available, even though the ports specified in the firewall script match the ports in preferences and they are being forwarded, according to the router. I am really unsure about my firewall script, mostly because I don't quite follow what it's doing. Is there a way to see what the firewall is rejecting/dropping/allowing? I'm going through the router again because other people in the house need it and it doesn't seem to be the problem. I have an ADSL connection and my ISP is Isomedia in Washington state. I have not read anything about them blocking or limiting common p2p ports, in fact I have specifically read that they don't, plus I used a variety of ports for aMule and none of them returned anything different. I'm guessing that I did something wrong or I've overlooked something. I'm also just guessing that the problems with aMule and the torrent clients are rooted in the same cause, but it would seem to be the case. I really need to stop working on this and go to bed. If you need more info from me I'll be up to check this around the crack of noon PST. Any insight on this would be much appreciated. Thanks in advance.

---

### Post by TheWizzard on 2006-10-31
looks like a firewall problem

> So I tried Firestarter for awhile
what did you do with firestarter? open the ports needed by amule and bittorent? 
there's a lot of information on the emule website on routers and firewalls. 

> s there a way to see what the firewall is rejecting/dropping/allowing?
yes, one of the tabs in firestarter shows you.


NB firestarter is not a firewall, but a gui to configure your firewall (iptables).

---

### Post by Zeke73SG on 2006-10-31
I opened the ports with firestarter, and aMule was still returning the port not available error, and I hadn't messed with bittorrent yet when I was using Firestarter. It seemed to me that you have more direct control over the firewall with the script, and aMule does have some rather involved instructions (at least for me) on their wiki. I am thinking I need to find a new firewall script, something I can wrap my head around, and add what the aMule wiki prescribes, word for word.

---

### Post by skymt on 2006-10-31
Just don't use a firewall. Really. Most home users don't need one, and they can cause problems with P2P and the like.

Also, if aMule is telling you that the port isn't available, that usually means one of two things:

1. You may have more than one aMule open at once. That's a Bad Thing. Run "killall amule", then try again.

2. You may have told aMule to use a port below 1024. That range of ports is restricted to programs running with superuser privileges. Set all ports to above 1024.

---

### Post by iamnafets on 2006-10-31
> **Zeke73SG said:**
> I opened the ports with firestarter, and aMule was still returning the port not available error, and I hadn't messed with bittorrent yet when I was using Firestarter. It seemed to me that you have more direct control over the firewall with the script, and aMule does have some rather involved instructions (at least for me) on their wiki. I am thinking I need to find a new firewall script, something I can wrap my head around, and add what the aMule wiki prescribes, word for word.

Are you sure your network even supports such a thing?  A lot of networks nowadays are blocking P2P ports, and I happen to be under some sort of NAT network where the IP they give me is actually part of a subnetwork and the real internet IP is shared by a lot of people.  Check in your router what it gets for its "internet IP" or "WLAN IP" and make sure it matches up with something like [www.whatismyip.com](www.whatismyip.com).  Just thoughts...

---

### Post by TheWizzard on 2006-11-01
> **Zeke73SG said:**
> I opened the ports with firestarter, and aMule was still returning the port not available error, and I hadn't messed with bittorrent yet when I was using Firestarter. It seemed to me that you have more direct control over the firewall with the script, and aMule does have some rather involved instructions (at least for me) on their wiki. I am thinking I need to find a new firewall script, something I can wrap my head around, and add what the aMule wiki prescribes, word for word.

if you open firestarter, you can diable the firewall and see if amule works. if it doesn't work with the firewall disabled, your problem is somewhere else. firestarter gives you perfect control over your firewall. 

also read the help wiki of **e**mule [http://www.emule-project.net/home/perl/help.cgi?l=1](http://www.emule-project.net/home/perl/help.cgi?l=1)

---

### Post by Zeke73SG on 2006-11-01
I think I've narrowed the problem down to my modem. It's a Zoom X3 and I've found out that it uses NAT as well, so I am trying to figure out how to enable IP passthrough, or bridging, or half bridging, or DMZ mode, or whatever it is that will allow the router to be assigned an IP from the ISP, thus disabling the routing function of the modem. I'm not sure which method is correct and I'm not finding a lot of information specific to my hardware/issue. It is not an Ubuntu problem though, I am almost sure of that.

---

### Post by TheWizzard on 2006-11-02
> **Zeke73SG said:**
> I think I've narrowed the problem down to my modem. It's a Zoom X3 and I've found out that it uses NAT as well, so I am trying to figure out how to enable IP passthrough, or bridging, or half bridging, or DMZ mode, or whatever it is that will allow the router to be assigned an IP from the ISP, thus disabling the routing function of the modem. I'm not sure which method is correct and I'm not finding a lot of information specific to my hardware/issue. It is not an Ubuntu problem though, I am almost sure of that.

good that you found the problem.
i think the easiest setup is to let your modem allow everything and do firewallin, port forwarding, etc with your router.

good luck!

---

### Post by Zeke73SG on 2006-11-03
I figured it out. It was definitely a problem with the firewall/routing function of the modem. I had to shoot an email to Zoom technical support and they explained how to configure the modem to pass the IP to the router. All I had to do was enable bridging and disable DHCP on the modem, and the router was already DHCP enabled, so now things are working the way I want them to. The first thing I did to test it out was start aMule and I recieved a highid on the first try. Anyone who is having trouble with p2p/bittorrent, and has already configured the Linux firewall and the port forwarding on the router should take a look at their modem. I didn't even know there was a way to access the modem's configuration [type [http://10.0.0.2](http://10.0.0.2) in a browser, for mine at least] until this problem popped up. You learn something new everyday. Thanks.

---

### Post by TheWizzard on 2006-11-03
> **Zeke73SG said:**
> I figured it out. It was definitely a problem with the firewall/routing function of the modem. I had to shoot an email to Zoom technical support and they explained how to configure the modem to pass the IP to the router. All I had to do was enable bridging and disable DHCP on the modem, and the router was already DHCP enabled, so now things are working the way I want them to. The first thing I did to test it out was start aMule and I recieved a highid on the first try. Anyone who is having trouble with p2p/bittorrent, and has already configured the Linux firewall and the port forwarding on the router should take a look at their modem. I didn't even know there was a way to access the modem's configuration [type [http://10.0.0.2](http://10.0.0.2) in a browser, for mine at least] until this problem popped up. You learn something new everyday. Thanks.

congratulations! but don't forget to setup the firewall of your router and pc!

---

### Post by markelhas on 2006-11-13
Hi ppl i've the same problem with my kubuntu, simple i've very very slow speed in p2p clients. I've look for some problems with my router and linux but, nothing.

My router is a Linksys wag54g. Any tips to help me out!?
Just for remark, in windows the same router, client and port forward works just fine!

---

### Post by TheWizzard on 2006-11-13
> **markelhas said:**
> Hi ppl i've the same problem with my kubuntu, simple i've very very slow speed in p2p clients. I've look for some problems with my router and linux but, nothing.

My router is a Linksys wag54g. Any tips to help me out!?
Just for remark, in windows the same router, client and port forward works just fine!

please give us a bit more information
- is this windows on the same computer? 
- are the ports forwarded to the correct computer?
- did you try disabling the firewall?

---

### Post by markelhas on 2006-11-13
please give us a bit more information
- is this windows on the same computer?
- are the ports forwarded to the correct computer?
- did you try disabling the firewall?


Hello,
I've test it on the same machine and other one, in windows the p2p clients and portt frw works just fine and to the correct ip address. I've no firewall at the kubuntu, also disable the router firewall. The problem of low performance over p2p steel there. ](*,)

---

### Post by TheWizzard on 2006-11-14
> **markelhas said:**
> please give us a bit more information
- is this windows on the same computer?
- are the ports forwarded to the correct computer?
- did you try disabling the firewall?


Hello,
I've test it on the same machine and other one, in windows the p2p clients and portt frw works just fine and to the correct ip address. I've no firewall at the kubuntu, also disable the router firewall. The problem of low performance over p2p steel there. ](*,)

sorry, but this is not exactly the information needed to help you.
can you please give the output of ```
ifconfig
``` and a screenshot of the port forwarding page on your linksys router? 

in (k)ubuntu the iptables firewall is installed by default and i think the amule ports are closed by default. but i'm not sure about this. 
you can configure iptables with a gui like firestarter.

---

### Post by markelhas on 2006-11-14
I'm tired of trying to solve this question, thanks for trying to help me out, but tomorrow I'll reinstall windows on the desktop.

I'll use kubuntu only on my laptop. For client p2p and Internet sharing for me didn't help using kubuntu.

---

### Post by TheWizzard on 2006-11-15
> **markelhas said:**
> I'm tired of trying to solve this question, thanks for trying to help me out, but tomorrow I'll reinstall windows on the desktop.

I'll use kubuntu only on my laptop. For client p2p and Internet sharing for me didn't help using kubuntu.

sorry to hear you didn't succeed in running p2p. 

are you very sure you forward the amule ports to the correct computer **and** to only one computer?

---

### Post by markelhas on 2006-11-15
I'm at work right now. I'll change the os to night, i simply can't imagine what's wrong.

And yes i'm sure about the port fwd. Another reason to be sure about it is that when i used a windows machine with the same router config the emule works just fine. I've used Azureus in windows and kubuntu sames ports complete diferent speeds performances.

I'll post the ifconfig output and one pic of my router settings before removing kubuntu. Them i'll wait for some tips.

Thnks

---

### Post by TheWizzard on 2006-11-16
> **markelhas said:**
> I'm at work right now. I'll change the os to night, i simply can't imagine what's wrong.

And yes i'm sure about the port fwd. Another reason to be sure about it is that when i used a windows machine with the same router config the emule works just fine. I've used Azureus in windows and kubuntu sames ports complete diferent speeds performances.

I'll post the ifconfig output and one pic of my router settings before removing kubuntu. Them i'll wait for some tips.

Thnks

ok.
if you're sure you never touched the iptables settings or used something like firastarter, it can't be ubuntu blocking ports. 

another thing? did you udate the serverlist in amule? the default list is not very good. replace with this one: 
[http://ocbmaurice.no-ip.org/pl/slist.pl/server.met?download/server-best.met](http://ocbmaurice.no-ip.org/pl/slist.pl/server.met?download/server-best.met)

---

### Post by markelhas on 2006-11-16
> **TheWizzard said:**
> ok.
if you're sure you never touched the iptables settings or used something like firastarter, it can't be ubuntu blocking ports. 

another thing? did you udate the serverlist in amule? the default list is not very good. replace with this one: 
[http://ocbmaurice.no-ip.org/pl/slist.pl/server.met?download/server-best.met](http://ocbmaurice.no-ip.org/pl/slist.pl/server.met?download/server-best.met)

Yestarday i've used several tools to config the iptables and now i'm not sure of anything. Can we talk in the irc ubuntu channel tonight!?

---

### Post by TheWizzard on 2006-11-16
> **markelhas said:**
> Yestarday i've used several tools to config the iptables and now i'm not sure of anything. Can we talk in the irc ubuntu channel tonight!?

ok, then install firestarter. next run firestarter and click  "stop firewall". now try to get amule working. 
if you still have problems it's either your amule configuration or your router settings. therefore i'd like to see your ifconfig and a screenshot of the port forwarding page on your linksys router. 
i'm not on the irc ubuntu channel. sorry.

---

