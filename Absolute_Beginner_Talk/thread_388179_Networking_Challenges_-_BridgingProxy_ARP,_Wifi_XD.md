---
title: "Networking Challenges - Bridging/Proxy ARP, Wifi XDMCP...How to? Or impossable?"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by cic007 on 2007-03-19
Hey folks,

I'm trying to realise an ideal network dream here - one which eliminates windows and uses Ubuntu.

The attached image is a diagram of the way I'd like my network to be.

Please note:

1. The 'Modded Xbox' is configurable just like any other device. I've got it using static IP and looking for connection on 198.168.0.1 (which works). The Modded Xbox requires an internet connection which must be supplied via one of my laptops (really just a low footprint desktop for all intents and purposes) running ubuntu. I can make it work on windows (it's duel boot) using Internet connection Sharing (i.e. wireless to ethenet bridging). I have sofar been unable to get it working in Ubuntu. I've glemed that either (a) I can bridge the connection (I have installed bridge-utils) or (b) I can have my laptop function as a router (proxy ARP?). I don't know how to set up either or any additional packages I need.

2. I wish to be able to control that laptop turned desktop from my other laptop via remote login over XDMCP. I tried enabling it on the other machine (and desktop sharing as well....if that's different kind of gathered it may just be XDMCP all over again). Being signed in on my other laptop is useful because I like to leave that one signed in and because it allows me to connect to the wirless network (using a script I wrote which basically restarts the dhcp client to talk to our wirless router, specifies the ESSID and WEP key). The fact that I need to run this before I'm connected means that I have no network connction when sitting at the longin screen until such a time as I set it up....I was kind of hoping XDMCP would be able to start another session.

3. About using the other laptop to conenct: The way I attempt to obtain a wifi connection at the login of the other laptop is a little easier. I'm runing Kubuntu so I log into KDE, It connects to the wireless network (pretty much automagically) then I start a new session and use the options ----> XDMCP---->Search for servers/referesh (or whatever it is!).

The problem: nothing is seen.

Any help on these two issues would be much appreciated folks!

[LIST=1]
[*]How do I set my Modded Xbox up to access the net?
[*]Should I use Bridging or ProxyARP/Router? Does it matter which? Which is easiest? and how do I do it?
[*]How do I go about facilitating XDMCP connection with my other laptop over our local wireless network?
[/LIST]

Thanks everyone!

---

### Post by alamba on 2007-03-19
Your internet sharing bit might be solved by by installing firestarter and a few clicks to get internet sharing started. However, I'm not sure if it'll work in your case since it probably does a NAT on the network behind the box and might not accept both interfaces with the same IP scheme. 

Unless I've misunderstood the setup here.

A

---

### Post by cic007 on 2007-03-19
Thanks for that :-)

I'll give it a shot when I get back home in a couple of hours and let you know how it goes.

Anyone got any ideas about the XDMCP questions?

---

### Post by cic007 on 2007-03-19
Just installed Firestarter on my 'desktop' laptop. Install was nice and easy with apt-get.

Then I opened it and the wizard started. When I got to the ICS page it seemed like biss and I set it up.

Now I'm being met with the following error on enabling the firewall:

''The Device eth0 is not ready.

Please check your network device settings and make sure your internet connection is active'

eth0 is my ethernet card (wired). Eth1 is my internet.

I'm typing form that laptop now so the internet part is ok.....

So the problem must be on the ethernet side.

Anyone any troubleshooting ideas that might solve this?

Thanks again folks!


PS - in case it's helpful:

My laptop is set to:

eth1 (wireless): DHCP (to the wireless router)

eth0 (static IP): 192.168.0.1
Subnet Mask: 255.255.255.0
Gateway: none.

Modded Xbox (media station):

Static IP: 192.168.0.25
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1 (the 'desktop' laptop)

DHCP is disabled.

---

### Post by cic007 on 2007-03-19
oooh. I've changed the gateway on the eth0 device of the 'desktop'

to be 192.168.0.25......

now I can ping 192.168.0.25 and it works again......

Also that firestarter nolonger gives the error.....

Only problem now is the conspicuous lack of internet on the xbox.............


ideas?

---

### Post by cic007 on 2007-03-19
Bag of popcorn for the most useful advice :popcorn:

---

### Post by cic007 on 2007-03-19
please? :-)

---

### Post by alamba on 2007-03-20
Buddy...the solution isn't trivial here. Firstly, you need to be in a different subnet for your Xbox (e.g. 192.168.2.x). Since both the interfaces on the laptop are on the same subnet, it can't route packets. 

Once that is done, you will need to add routes on the X-box to be able to get online with it. I'm not sure if you can do that on your box.

We can setup a chat session if you need hand holding. Also, this is the solution I'm envisaging, not neccessarily the only or the best or the easiest solution out there.

A

---

### Post by cic007 on 2007-03-20
Thanks so much for your help here alabama, I really appreciate it :-)

I'll have a shot at playing with the subnets tomorrow to see if I can make it work without troubling you....

Failing that I'll probably take you up on your offer of help over IRC.

Have a bag of popcorn: :popcorn:  You've earned it.

;)

---

### Post by alamba on 2007-03-21
lol...good luck!

---

### Post by cic007 on 2007-03-22
Still getting nowhere.....perhaps it's time to ask for help via MSN/IRC Alabama :)

---

### Post by alamba on 2007-03-23
Alamba buddy...not Alabama! Short for Akshay Lamba. Anyways...you can catch me on MSN, Yahoo, Google Talk, etc. etc. See the contact me page on my website for the ID's. Website address is in my signature.

A

---

### Post by dalziel_86 on 2007-04-03
Okay, the best solution for your network is bridging.

Router*---wifi---*Laptop1<---ethrnet--->Xbox
*
|
|
Wifi
|
|
*
Laptop2

This is what we're working with.

If you set up bridging on Laptop 1, this will bridge the Xbox to the router, making it act like it's connected to the router via wireless. Bridging is actually fairly simple. You set up the bridge as a new interface, zero the IPs of the ethernet and wifi interfaces and bring them up, then add them to the bridge, give it an IP and bring it up. The bit that took me ages to work out was that you have to add the default gateway (your router, presumably 192.168.0.1) for the bridge in the routing table if you want Laptop 1 to get Internet access. I can give you bash commands for all this if you want, but it's relatively easy to work out.

Once you have this set up, the Xbox and Laptop 1 will both act like they're connected directly to the router. It's worth noting, however, that the wireless between Laptop 1 and the router becomes shared between the two, so if you're downloading on one, that'll slow the other's access.

As far as the XDMCP stuff, I'm stuck on that myself. Sorry I can't help you there. :)

---

