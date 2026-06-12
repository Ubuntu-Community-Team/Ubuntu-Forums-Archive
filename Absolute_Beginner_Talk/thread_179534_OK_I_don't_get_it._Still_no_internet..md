---
title: "OK I don't get it. Still no internet."
date: 2006-05-20
forum: Absolute Beginner Talk
---

### Post by JamesD on 2006-05-20
So I'm an idiot right? I don't think so but if I was I wouldn't know.

So OK I had a hard time trying to get on the internet (Breezy B) with my USB modem. Everyone else I found in searches did as well. So fine, I bought a D-link DSL-502T. Why not? $70.00 AUS My wife will sell the old one on Ebay and be happy.

The new modem, router, DHCP server,autologin to my ISP (Dodo in Oz if it matters. It shouldn't) all singing all dancing little cute box. Works fine in XP.

Oh yeah I upgraded my service to a faster one which just happend at the same time (billing period) so my wife thinks the new modem is MUCH faster than the old one. Just luck really. :o) 

Anyway I still can't get on the internet from Ubuntu. I can see the modem.

I have searched and searched. Which is a bit hard because I have to keep logging off XP and logging on to Ubuntu rinse, repeat, over and over and of course I have to type my password into Ubuntu everytime I want to do anything.

I have searched this site and found much. pppoeconf (?) seemed like a good thing but it fails with the usuall error message.  Something else might be using it or some such. It's long.

To me this seems pretty basic stuff and I am suprised that many questions about it seem not to be answered. Well not with much result mostly. And I have spent many hours searching (again) before I asked in here. I would rather be the guy that finds the answer than the guy that asks the question.

But If I can get my wife to use a connection that is not XP and so is not flooded with malware etc every time she clicks the wrong button that would save me a lot of cleaning up.

So the modem works, the modem connects to my ISP from windows, it's ethernet not USB Breezy B can see it. Breezy B says it all looks well.

But Fire fox is a no go.

Should I just re-install with the modem plugged in?

Not much point if it won't help.

Any ideas?

Anyone?

Thanks

JD

---

### Post by skippy81 on 2006-05-20
OK,

DSL-502T is an ADSL router.  Your linux PC should connect to this router with a standard RJ45 patch cable.  

The important part is the network card (NIC) which you use in your linux box.

If you know the exact make and model of your PCs network card, please post it, that would be really helpfull.  If its integrated (ie part of the motherboard) then please post the name and model of the motherboard.  
  
Open a terminal (Applications > Accesories > Terminal) and type the following commands:

> lspci
> lsmod
> ifconfig

Post the results to this forum.  That way we can see whether you ethernet card in the linux PC is being recognised and has drivers loaded,

---

### Post by JamesD on 2006-05-21
Thank you Skip. Tck, Tck, Tck, (translation, No worries Sonny) :o)

No really thanks for replying. I don't think it's what you suggest though and I'll tell you why first. However I did of course do as you recommened and the results (edited for relevence and clarity) are below.

However in Ubutu with Firefox pointed at 10.1.1.1 (the IP addy of the ADSL Router) I can see the setup / config pages for the modem / router OK. I can ping it (of course). I get a DHCP IP addy from it. 10.1.1.2. It is connected by a CAT 5 RG 45 cable only, the USB cable is NOT plugged in and it works fine like that from XP. I'm using it now. So I figure that the Realtek embeded network card on the Asus P5S800-VM mother board is fine. Ubuntu talks through it quite well. The router / modem is programmed to talk to my ISP (Dodo in Oz).  The password etc are correct. It works in XP. No "dialing" required.

Here is the information you suggested I should post with a bit extra Personally I think it's the bit extra that points to the problem. I could be wrong and I don't know exactly what it is pointing at.

lspc

0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. 
RTL-8139/8139C /8139C+ (rev 10)

lsmod

8139too 23552  0
8139cp 18432  0
mii 5248  2 8139too,8139cp

ifconf

eth0 Link encap:Ethernet  HWaddr 00:13:D4:5F:52:65      
inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0      
inet6 addr: fe80::213:d4ff:fe5f:5265/64 Scope:Link     
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1    
RX packets:15 errors:0 dropped:0 overruns:0 frame:0    
TX packets:36 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000  
RX bytes:2355 (2.2 KiB)  TX bytes:3213 (3.1 KiB)     
Interrupt:19 Base address:0xe400

pppoeconf

Sorry I scanned 1 interface,but the Access Concentrator of your 
provider did not respond ... check cables... another pppoe proc 
might be controlling... etc.

poff -a

/usr/bin/poff: No pppd is running. None stopped

I had to reformat all that twice so it isn't exactly what came up in the Ubuntu terminal window. Most is a copy and paste The last two about The ppp I typed. I do know what Point to Point Protocol over Ethernet is. But I think it says what you asked for Skip. 

Oh yes I have read the man pages for some of the above. But one problem I have is that I don't know most of the Debian command names to ask about. I know a bit about Solaris, a bit about Red Hat (I did a week long course on Red Hat but it took them four days to tell me something I didn't already know). So thanks for pointing me at some of them which I am sure will be usefull in the future. I am a Noob at Ubutu and I am trying to fast track a bit to get it on the internet. But I am not a total Noob with computers. I do IT support for a large university. I spent my first few years there in the Computer Science Dept using a Solaris account on big SUN boxen and trying to keep the CS students (who knew more than me supposedly) from breaking the network. But no, I was not an admin on the Solaris system. Just a user. I was an admin on the Windows domain and the Novell NDS network. Due to a re-structure I do a different job now. Mostly XP desk top and Novell support. And yes, yes, I am an MCSE, sorry about that. Please don't hold it against me. The Uni paid for it. Pretty useless qualification if you ask me. If you want to know why I think that send me a private message. But basically what they teach you sort of works sometimes in the real world. Ya gotta be better than that to make the stuff work.

Enough rant.

I still ain't got no internet in Ubuntu.

Any ideas anyone? Don't worry. I'm looking for clues in all the wrong places as well. I WILL make it work. And of course then I will tell all to anyone I can.

But do I really need to re-invent the wheel? I see a lot of questions in my searching about this sort of stuff. But very few answers. So far none that work for me. Oh well maybe I will get lots of beans 'cos I'll be the guy that works it out? ;0)

Or maybe somebody already knows? Or maybe Ubuntu just isn't ready yet for the great unwashed (I did have a shower last week, I've been busy OK!)

:0)

James

---

### Post by manicka on 2006-05-21
You don't need to configure pppoed if you have a router, you just need to get your eth0 card talking properly to the router and using it properly. In my experience there are some issues with the cheaper d-link routers and using dhcp. With my d-linbk router I have to enter my network settings manually, particularly the dns settings, to get it to connect properly. Using dhcp the router will telll ubuntu to use itself for dns rather than your providers dns details. which doesn't work with these d-link routers.

first go to System--> Administration-->Networking to bring up the networking control panel.

Choose the ethernet connection then click on 'properties' and change it to a 'static ip address' and enter your network settings manually.

[IMG]http://img236.imageshack.us/img236/7977/screenshot1kc.png[/IMG]

click on OK, then click on the DNS 'tab'

remove your router address if it is shown there and replace it with your providers dns settings. You should be able to get these from your routers web interface in the 'status' section. When you've added these click on ok to apply them.

All going well you'll now be on the net. :)

HTH

P.S. Don't forget to disable ipv6 in Firefox.

In the address bar for firfox type - about:config

In the filter section type ipv6

then toggle 'network.dns.disableipv6' from false to true

---

### Post by JamesD on 2006-05-21
Oh, thank you, thank you.

Actually it will be a while before I try it. My wife wants to surf. The web!

But yes that is VERY GOOD advice.

Actually I did try to set a static IP as suggested. No go. But it never occured to me to turn off IPv6. I'll try that.

But really the magic word was DNS, if that's a word.

Doh!

I won't post anything about host files or such like because I want to appear as a Noob but not stupid. But just to explain as to how I am a total idiot. I think I saw a similar problem at work last week in Solaris.

So who knows were the "Hosts file" is located and what it is called in Ubuntu?

I'll bet a buck that it's a DNS problem. Everything else is working.

Doh! I'm an idiot I should have looked at that first thing. Well second or third thing.

But Thank you Mancika I suspect you have given me a very important part of the puzzle.

My thanks go out to you.

James

---

### Post by Jimmey on 2006-05-21
[QUOTE=JamesD]So who knows were the "Hosts file" is located and what it is called in Ubuntu?[/QUOTE]

I do :)

It's /etc/resolv.conf

Type the IP address of your router, and use that as a DNS address.

---

### Post by manicka on 2006-05-21
[QUOTE=Jimmey]

Type the IP address of your router, and use that as a DNS address.[/QUOTE]

the problem in this case is that some d-link routers do not handle dns properly if you use them directly. You are better off to enter the dns settings of your provider with these routers

---

