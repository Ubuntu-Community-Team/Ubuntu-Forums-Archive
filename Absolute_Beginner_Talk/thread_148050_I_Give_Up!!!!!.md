---
title: "I Give Up!!!!!"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2006-03-21
Hello everyone,

Sadly, i cannot waste any more time with this project.  I am forced to admit defeat and go back to my old life with Windows.  It's a shame really, Ubuntu looked so promising.  in fact, I was ready to convert.  Despite two weeks of fiddling, loads and loads of reading help forums and postings to this forum, I still cannot connect to the internet.  

I can successfully ping google, ebay and my service provider through the terminal, I can even change settings on my ADSL router via the browser, but will it connect to the internet...NO!  I know the router works cos I'm typing this live.  Please please, if anyone can help I will greatly appreciate it, otherwise it's back to Bill Gates for me!  

Please save me from eternal misery  :cry:

---

### Post by Brunellus on 2006-03-21
trivial.  specify the IP address of your router (should be something like 192.168.1.1) as the default gateway in the networking setup gui for Ubuntu.)

Then rock and roll.

---

### Post by Norfolk 'n' Good on 2006-03-21
Hi

If you mean under 'administration', 'networking' (unfortunately I'm having to switch between operating systems so I cannot remember the correct headings), then in properties, when eth0 is highlighted there is a section for DNS.  I have entered that exact IP number there.

---

### Post by noswal on 2006-03-21
This is what I did, maybe it will be of help

[http://ubuntuforums.org/showthread.php?t=141461](http://ubuntuforums.org/showthread.php?t=141461)

---

### Post by localzuk on 2006-03-21
Can you explain how you ping google? Do you ping it by IP or by the domain name? Also, is it Firefox you are trying to use?

Does your pc connect have a static IP or dhcp assigned one? Is it a wired or wireless card?

When you say you have entered that exact IP, is that IP the actual IP of your router?

---

### Post by Buffalo Soldier on 2006-03-21
Have you checked your DNS server settings?

---

### Post by Norfolk 'n' Good on 2006-03-21
I pinged Google through the terminal using both the IP address and [www.ggogle.com](www.ggogle.com).  On both occasions this was successful.  The browser I have been trying to connect with is Mozilla Firefox.  My IP address is DHCP assigned.  It connects to the router via an RJ 45 cable. Finally, the DNS adress I enterd was 192.168.1.1 .  By entering this number into my browser address bar I can (if I want to) edit the settings on my router.  So I know the browser can see the router, but it doesn't appear to see beyond that.

I hope that helps and thanks for your help.

---

### Post by m.musashi on 2006-03-21
Brunellus is right. I had the same problem and as I clicked on various tabs I added my router IP as a gateway. Suddenly everthing worked just fine. True, it would be nice if that was somehow a more automated process but on the plus side I learned a bit more about networking. However, I can't remember how I did it. I don't think you can add a gateway address under the properties menu if you are set to use DHCP. If you put in a static IP address you can.

EDIT: woops, took too long to post. Anyway, the router IP 192.168.1.1 is NOT your DNS address. It would go in as your gateway (or perhaps the IP of your modem which for me was 192.168.0.1). Your DNS address is assigned by your ISP. I actually had to call them to find out what it was and then entered it under the DNS tab.

---

### Post by Norfolk 'n' Good on 2006-03-21
I think I tried that (using the static IP), but just to make sure I'll give it another go.  If I don't reply for a short while it's because I have booted into Ubuntu.

---

### Post by _simon_ on 2006-03-21
System -> Administration -> Networking -> DNS

In there I removed the IP that was entered and entered my ISP Domain Name Servers (DNS).

That worked for me... have you tried that?

---

### Post by localzuk on 2006-03-21
The fact that you can ping google.com via the terminal indicates that there may be an issue elsewhere (other than DNS settings). Do you have a firewall installed?

---

### Post by Norfolk 'n' Good on 2006-03-21
I tried the static IP address entering 192.168.1.1 and the subnet mask 255.255.255.0, but this did not help.  In fact, I was unable to ping anything after that.  I put everything back as it was and again I am able to ping Google with both its IP address and www. name.  As far as having a firewall installed, I don't know if ubuntu installs with one ( I suspect not) and there is one on the router, which I have tried turning off, but again it has no effect.  I'm absolutely baffled!!

---

### Post by Brunellus on 2006-03-21
point your primary DNS to your router (192.168.1.1) and see what happens.

---

### Post by krusbjorn on 2006-03-21
Make sure that you didnt tell your router only to work with a computer that has a certain internal IP. You might not have the same IP in linux as in XP. 

Also, I have had to have a static internal IP since breezy, DHCP never worked, though it should have.

---

### Post by Norfolk 'n' Good on 2006-03-21
Sorry for my apparent ignorance, but how do I point my primary DNS at my router, which is as you stated 192.168.1.1?

---

### Post by Brunellus on 2006-03-21
[QUOTE=Norfolk 'n' Good]Sorry for my apparent ignorance, but how do I point my primary DNS at my router, which is as you stated 192.168.1.1?[/QUOTE]
should be an item for that in the network setup gui.  I'm at work (on win2k, blech) so I can't remember exactly where it is.

---

### Post by Norfolk 'n' Good on 2006-03-21
krusbjorn appears to have a good point... how do I find an IP address in Linux, instead of the one XP uses?

---

### Post by krusbjorn on 2006-03-21
type "ip address" in a terminal.
> 
1: lo: <LOOPBACK,UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:11:d8:b1:a5:c8 brd ff:ff:ff:ff:ff:ff
    inet **192.168.0.109**/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::211:d8ff:feb1:a5c8/64 scope link
       valid_lft forever preferred_lft forever
3: sit0: <NOARP> mtu 1480 qdisc noop
    link/sit 0.0.0.0 brd 0.0.0.0

---

### Post by al108 on 2006-03-21
[QUOTE=Norfolk 'n' Good]I tried the static IP address entering 192.168.1.1 and the subnet mask 255.255.255.0, but this did not help.  In fact, I was unable to ping anything after that.  I put everything back as it was and again I am able to ping Google with both its IP address and www. name.  As far as having a firewall installed, I don't know if ubuntu installs with one ( I suspect not) and there is one on the router, which I have tried turning off, but again it has no effect.  I'm absolutely baffled!![/QUOTE]

The reason that one didn't work is because your ip address 192.168.1.1 was the same as you router's ip. So if you want to specify static ip on your Ubuntu machine it should be something like 192.168.1.101 (make sure other computers on your network are not using it). Also make sure if you go static IP that your default gateway is 192.168.1.1, and add it to you DNS list. Check that eth0 (I assume) is active, and selected as default gateway device. To add 192.168.1.1 to your DNS go into Administration > Network Settings > highlight eth0 and click on DNS tab.

If you don't mind also give us an output of this :
dmesg | grep eth

---

### Post by Online Gamer on 2006-03-21
Hi
This is only my second post so bear with me. One quick question are you as new to Linux as me and only using the graphical interface like windows .

If so I'll talk you through what I have for my ADSL modem in the UK. It might not be the same but it sounds close. The IP address of 192.168.1.1 is your router mines 192.168.2.1. Let me know and I'll try. I got mine working after some messing around, but before Firefox wouldn't get on the net.

---

### Post by Online Gamer on 2006-03-21
Nice one youve just explained what I've got with mine  I made my DNS 192.168.2.1    and my IP address as 192.168.2.2 and it worked.

---

### Post by Iowan on 2006-03-21
Correct me if I'm wrong (again), but a DNS address of 192.168.x.x will only work if there's a machine at that address with a connection to a REAL DNS server.  My router has a caching DNS server, so my clients can be set up to ask it for DNS information - It has the address of my ISP DNS.
  If your routher has no DNS server, it MIGHT work to specify your ISP DNS on the client, and the router address as a gateway.

---

### Post by m.musashi on 2006-03-21
[QUOTE=Iowan]If your routher has no DNS server, it MIGHT work to specify your ISP DNS on the client, and the router address as a gateway.[/QUOTE]
I think that is what you would want to do in this case. Contact or otherwise lookup the DNS address(es) for your ISP and put them in the DNS tab. Set the static IP address to the address assigned by the router (ifconfig from a terminal should show this) and then set the gateway to either your router IP (192.168.1.1) or your modem IP. I believe my is set to my modem IP but I'm not sure what is actually correct.

---

### Post by tuxinvader on 2006-03-21
This is very strange. 

If he can ping [www.google.com](www.google.com) by name and IP the problem can't possibly be routing or DNS!?!?

What ISP are you with? It could be ECN (Explicit Congestion Notification). I've had problems communicating with sparcs (running Solaris 9) with ECN enabled in the past. Perhaps your isp runs a transparent proxy on sparcs?

Open a console and type "cat /proc/sys/net/ipv4/tcp_ecn"
If it's 0, then this ECN isn't the problem.

The only other thing I can think of is the MTU. You could try manually lowering it for testing initially. If it is the problem you need to allow icmp to get back to your linux box, but before we get into that. Try this:

Open a console and run "sudo ifconfig eth0 mtu 1000"

This lowers the Maximum Transmission Unit to 1000, it's usually 1500. If you're not using an ethernet adapter (eg wireless) then use your interface instead of eth0

HTH

---

### Post by Online Gamer on 2006-03-21
Sorry about this guys but I'm new to linux, only had this about 5 days and wasn't that good with windows. Iowan yep youv'e jogged my memory in the UK I set my router to dns set by provider automatically (it was a tick box) in the router set up.
Then pointed my Ubuntu dns to the router IP and added one to that and set it as my machine IP. This was done via my ISP helpline. I was lucky enough to find a Linux speaking helpline person who could use Ubuntu.

With the person askings name as Norfolk and Good I assumed he was in the UK as that's UK slang. My ISP helpline told me that all UK ADSL providers    provide the DNS automatically for this situation.

---

### Post by Norfolk 'n' Good on 2006-03-21
Sorry guys, I had to get dinner going before my wife gets home otherwise there would be trouble.  I'm now going to reboot into Ubuntu and try out a few ideas you guys have very kindly suggested.  I know it must be difficult to help some-one remotely, particularly with a finnicky task like this.  What makes it more difficult is I don't really understand all the terms and how one machine looks at another using DNS, IPs and so forth.  But thank you anyway.

---

### Post by tatimmer on 2006-03-21
I am such a new user that I havent received my Ubuntu cd yet.  But I did look thru the list of programs supplied with the standard cd and did not see the program "chat" listed.  

I have an "internet connect how-to" available from [www.ticon.net/~tatimmer](www.ticon.net/~tatimmer) that shows how to manually configure a modem to connect using ppp and chat.   Hope it helps. 

Good Luck.

TomT

---

### Post by Norfolk 'n' Good on 2006-03-21
I now talk to you from my Ubuntu operating system... success at last!!  The answer was very simple, thanks a particular suggestion.  The IP address in the DNS section was 192.168.1.1... the same as the IP address for my router.  I simply added a new IP number 192.168.1.2 and hey presto. 

I was very close to quiting Ubuntu, but all your help has not only allowed me to finally get connected, it has shown me what a great community you all are.  Thank you all very very much for all your suggestions and help.  I hope by this posting some-one else is also able to resolve their connection issues.

Thank you  :-D

---

### Post by Papa-san on 2006-03-21
I thought it kind of ironic that someone else beat me to this post!
I am going to try a clean re-install, and barring some sort of actual progress, I am burying my laptop ceremoniously in the dumpster... (I said I wouldn't do windows again, and meant it...) I'll check back in a few years...lol

---

### Post by Online Gamer on 2006-03-21
Glad your sorted mate, I've been on linux for 5 days and was mediocre in windows, so keep at it and anything you need just ask on the forums. thats all I do. Most of the time search the forum and someone else has already asked. This is a fantastic community for learning about Ubuntu and Linux.

Welcome onboard
Online Gamer

---

### Post by Iowan on 2006-03-21
[QUOTE=Papa-san]... I am burying my laptop ceremoniously in the dumpster...[/QUOTE] I'd be willing to provide the dumpster (or reasonable facimile thereof)... but I'd rather help solve the problem :D

---

### Post by AndrewCaul on 2006-03-21
[QUOTE=Norfolk 'n' Good]
I was very close to quiting Ubuntu, but all your help has not only allowed me to finally get connected, it has shown me what a great community you all are. [/QUOTE]
It would be foolish to quit Ubuntu just because of that. You can run into the same problem in Windows if you're not careful. It's because it's not an OS-based issue.

---

