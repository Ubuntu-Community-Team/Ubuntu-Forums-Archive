---
title: "Internet Access Trouble"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by Zoglarfy on 2005-09-02
Man, you guys are really awesome.  The forum is full of us poor newbies desperately trying to get the system working, and yet you patiently show up and help.  That's really cool!

Anyways, onto my dilemma.  Brand new Linux guy here.  Everything about this OS is pretty much new to me.  I installed Ubuntu on my Thinkpad T21 laptop and am having problems accessing the internet.  I'm using a DSL modem that is connected to my laptop using the built-in Ethernet device.  I should note that I'm dual-booting XP and Ubuntu, and have no network/internet problems on Windows.  So, I'm leaning away from my "faulty hardware" theory.

First of all, I initally had problems where the system didn't recognize my network card.  Doing a bit of research, I found [this](http://www.thinkwiki.org/wiki/Problem_with_3Com_10/100_Ethernet_card_not_being_recognized) webpage.  Not knowing how to modify kernel parameters, I opted to try the setpci solution.  I copied the Perl script, made it into a file, and ran it with success.  After I did that, the system finally recognized the card and I was able to activate it.  But it still wouldn't let me access the internet.

I set the IPs and DNS servers to what they are in Windows.  This gives me a slightly different error.  Firefox can lookup a website now, but it can't connect to it.  I find that I CAN connect the my DSL modem's configuration utility, which is... umm... well, accessed through a web browser (the documentation tells you to type in an IP address, and that takes you to the configuration page).  

One more thing to note.  I had noticed the [Router and DNS problems thread](http://ubuntuforums.org/showthread.php?t=5690) mentioned in the Warty 4.10 Hardware Help forum, but can't figure out how to activate the universe mirrors.  I don't even know if it's the same problem that is being described in that thread, but it seemed similar enough I thought I'd give it a try.  

I apologize for the long post.  I had hoped to give you as much information as possible.  If anyone else has any ideas, I thank you in advance for them.

---

### Post by davmac on 2005-09-02
Zoglarfy,

I used to get the router and dns problem with 4.10, but haven't had the problem since I shifted to 5.04 so I can only assume this issue was resolved with it. It does sound like some sort of DNS problem though.

What are the contents of your resolv.conf file and what output do you get from the command "ifconfig"? Can you ping an IP address? Try "ping 158.152.1.58".

I used to get a problem where I'd set the DNS addresses and things would work fine for a short while and then stop. Looking at the resolv.conf and they'd been reset to something else. It hasn't troubled me for a while now - but I'm somewhat of a clueless eejit and couldn't figure out what was causing it

BTW: You must have read [http://catb.org/%7Eesr/faqs/smart-questions.html](http://catb.org/%7Eesr/faqs/smart-questions.html) because that is one of the best written questions I've seen for ages!

Regards,

Dave Mac

---

### Post by Zoglarfy on 2005-09-02
[QUOTE=davmac]Zoglarfy,

I used to get the router and dns problem with 4.10, but haven't had the problem since I shifted to 5.04 so I can only assume this issue was resolved with it. It does sound like some sort of DNS problem though.

What are the contents of your resolv.conf file and what output do you get from the command "ifconfig"? Can you ping an IP address? Try "ping 158.152.1.58".

I used to get a problem where I'd set the DNS addresses and things would work fine for a short while and then stop. Looking at the resolv.conf and they'd been reset to something else. It hasn't troubled me for a while now - but I'm somewhat of a clueless eejit and couldn't figure out what was causing it

BTW: You must have read [http://catb.org/%7Eesr/faqs/smart-questions.html](http://catb.org/%7Eesr/faqs/smart-questions.html) because that is one of the best written questions I've seen for ages!

Regards,

Dave Mac[/QUOTE]
Alright, the results of ifconfig give me this:
eth0	Link encap: Ethernet HWaddr 00:00:86:49:79:BF
	inet addr:###.###.#.# Bcast:###.###.#.### Mask: 255.255.255.0
	inet6 addr: fe80::200:86ff:fe49:79bf/64 Scope: Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:39 errors:0 dropped:0 overruns:0 frame:0
	TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
	collisions: 0 txqueueln: 1000
	RX bytes: 6941 (6.7 KiB) TX bytes: 8324 (8.1 KiB)
	Interrupt: 11           Base address: 0x1800

It also gives lo information, but I didn't think that was relevant.

Attempting to ping the address you supplied gave me:
  connect: Network is unreachable

And finally, I couldn't find resolv.conf.  I apparantly have a manual file for it, but not the actual file itself.  Thinking on it now though, I'm sure I've seen it.  Does it not turn up in the search function unless you're logged in as root or su?  Hmm...

---

### Post by davmac on 2005-09-03
In a terminal windows, type "cat /etc/resolv.conf".

---

### Post by UbuWu on 2005-09-03
[QUOTE=davmac]
I used to get the router and dns problem with 4.10, but haven't had the problem since I shifted to 5.04 so I can only assume this issue was resolved with it. It does sound like some sort of DNS problem though.
[/QUOTE]

I still have these problems even with breezy. Somehow managed to fix it for hoary, now trying to fix it for breezy again. I think I removed dhcp3 and installed dhcpcd.

---

### Post by fongalong on 2005-09-03
Hi all:

I have the exact same problem as Zogarfly so I hope no one minds that I jump in here. My specs are different: Asus M6r notebook with built-in RealTek Ethernet card.

Unlike Z, Ubuntu had no problem recognizing the ethernet card. Or at least I don't think it does - the card is listed in the Device Manager. However, the adapter is there embedded under an unknown device - my ATI controller I think. I believe I might need a driver for that. 

My internet woes are the same as Z:I'm connected to a network with DHCP but there is no detection of configuration. As suggested by someone, I typed:

cat /etc/resolve.conf 

and I received this:

nameserver 129.173.1.100
nameserver 129.173.1.103

I can't ping, can't connect to web sites, etc. 

Please help. Thanks.

---

### Post by Zoglarfy on 2005-09-04
Heh, found the file.

Mine contains the same thing as fongalong's, but with different IP addresses, obviously.  It also includes:

search domain.actdsltmp

That's the very first line in the file.  Any ideas, anyone?

---

### Post by fongalong on 2005-09-05
Hey Zoglarfy:

I'm wondering if you have the same problem that I do. I've noticed, during installation, that my internet connection works when I have acpi turned on. It stalls later on, but that's another story.

With boot: acpi=off, my network fails altogther. I'm also wondering if it's an ide controller issue. There's a link in my other post to a discussion of the problem that I have. You may find it useful.

---

### Post by sanneman on 2005-09-05
Hi all,

another joiner. 
I saw your conversation when I was looking for other people with network problems. No solutions, but another similar question. Hope you don't mind I'm joining. 

My connection was working, both in XP and Ubuntu, which I installed recently. Today I removed a router that was in between the Cable-modem and the computer. As I feared, XP didn't have any problems, but my connection in Ubuntu is lost. I've tried several things:

I inserted the Install-cd, up to the point that it looks for the network automatically, this works, it finds the network automatically using the computername and DHCP. Because I didn't want to reinstall Ubuntu (because I have important data on the disk), I aborted the installation. 

So I tried to get Ubuntu to search for the connection, but I don't know how. I've used System, administration, networking from the menu. Then I deactivated and activated the connection, unsuccesfully. I have also looked at the tab 'general', but the computername is correct, and the under the TAB 'properties' DHCP is still used. 

any ideas? 
thanks, greetings,
Sanne

---

### Post by davmac on 2005-09-05
Zoglarfy and Fongalong,

Are those IP addresses the correct ones for the DNS that you'd expect? This is where my problem was. I'd set the correct DNS addresses and then next time I looked they were gone.

Dave Mac

---

### Post by Zoglarfy on 2005-09-05
[QUOTE=davmac]Zoglarfy and Fongalong,

Are those IP addresses the correct ones for the DNS that you'd expect? This is where my problem was. I'd set the correct DNS addresses and then next time I looked they were gone.

Dave Mac[/QUOTE]
Yeah, the IP addresses where the same ones that Windows used.  I don't seem to have any problem with them disappearing though.  How strange.  

fongalong, our problems seem similar.  My Thinkpad uses a 3com 10/100 Mini PCI Ethernet Controller.  I was lucky enough to find a perl script that would reset the card without having to turn off acpi.  Without running that script, linux doesn't even recognize the card.  Perhaps you'll be able to find a similar script for your RealTek card.

sanneman, are you on a laptop or a regular computer?  Or, perhaps more relevantly, what network card are you using?

---

### Post by fongalong on 2005-09-05
Zoglarfy:

Linux does recognize the ethernet adaptor - it works to retrieve data from the ubuntu websitie when I'm installing for the first time. The problem is booting after installation, esp. when loading ACPI modules. 

But even when I boot with acpi=off and I do get into ubuntu, my realtek adaptor still shows up in my device manager. However, it's embedded in an "unknown" controller. 

I think I might have to find a driver for my ATI controller because linux is recognizing my realtek ethernet adaptor fine. Just can't do anything with it. 

F

---

### Post by fongalong on 2005-09-07
*bump*

---

