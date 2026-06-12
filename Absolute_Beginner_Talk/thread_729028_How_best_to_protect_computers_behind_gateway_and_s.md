---
title: "How best to protect computers behind gateway and still connect to them"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by greavette on 2008-03-19
Hello,

I'm hoping someone can lead me in the right direction in my search on how to do this.

I'm helping with setting up a secure network for a very small business.  5 computers are being used in this office where 2 are currently connected to the internet.  The other 3 are not connected to the internet.

What I'd like to do is something like this:

Internet > Untangle Gateway > Wireless Router > Ubuntu Box > 5 computers throughout the office.

[LIST]
[*]I will build a computer to run the Untangle Gateway to protect all the other computers.
[*]I will put in place another new computer to run Ubuntu on.
[*]I would like the two computer that currently connect to the internet to still connect (for mail, etc..) but to be protected by the Gateway
[*]I would like the other 3 computers to not connect to the internet.
[*]I would like all computers to be able to connect to each other.
[/LIST]

I live in a different town than the office so what I'm hoping to do is be able to connect into the Ubuntu Box from my house and have the ability to connect into any of the other 5 computers by remote desktop (I've used Hamachi and VNC in the past, but with 3 computers not connected to the internet, I'm not sure how to connect to them?)

Would this setup be possible?  What components do I need to install and setup to make this work?

I know these are loaded questions, but I'm willing to learn and read/teach myself how to set this up.  I'm hoping someone can point me in the direction of where to start.

Thanks in advance for any help you might have.

Charles.

---

### Post by Golem XIV on 2008-03-19
If I understand your setup correctly, you have 3 routers one after the other: the gateway, the wireless and then the Ubuntu box (as a server?).  Maybe even a 4th one, if your ISP gave you one.

Untangle Gateway has VNC access for remote setup, so you can work directly on it.  Unless your office systems absolutely need wireless, I would get rid of it.  If your office systems don't need wireless but you need it just for the odd "guest" that wants Internet access every now and then, i would put the wireless out of the loop by plugging it in directly to your ISP's router (if you were given one) and have the "guests" worry about their own security.

So, the setup would be:

ISP's router -> Untangle Gateway -> Office systems (protected by Untangle) and
ISP's router -> Wireless router (no protection).

About connecting to non-internet systems from home:

I've never heard about Untangle Gateway until now, but all these systems are configurable.  What you do is allow the 2 systems connection to the Internet (according to certain rules) and set the other 3 to "block all".  If you want to access one of the blocked systems, log into Untangle via VNC, unblock the system you want to work on, log into it, do your work, log out, log onto Untangle again and re-block the system (whee! I hope that's clear!)

About the wireless:

They are notorious for having security holes and exploits.  If you put one **inside** your network, you're ripping a big hole in your security.  That's why I said leave it on a parallel connection, outside of the protected zone.

If you absolutely must have the wireless inside the protected network, make sure that you change all settings from default (passwords, default IP addresses, etc.), use the best encryption (WPA2), disable broadcast, enable MAC filtering, etc. etc.  Most of these (MAC filtering and disabling broadcast) won't do much and are almost trivial to break, but every little bit helps.

Oh, and I would recommend to use static IPs for the networked systems.

Good luck!

---

### Post by greavette on 2008-03-20
Thanks very much for the response Golem!

I wasn't planning on using the Ubuntu box as a router (but now that I look at the diagram, that does seem to show that).  I was planning on using the Ubuntu box to remote into from home, and once on the Ubuntu box, I would remote into the other PC's.  I was also planning on using the Ubuntu box to store all backed up data from the 5 other PC's (using rysync) and then sending that data for offsite backup to my house (instead of going to each PC and getting the data, the Ubuntu box would get all the data for me and then I'll get all the data from one PC only).   Since Untangle already has VNC access, I probably won't need the Ubuntu box for remoting into the other PC's.  Should I use the Untangle box to store backed up data as well?

The owner wants to have these 5 PC's setup together because one is a database to store data and the other 4 are used to input the data.  To save on wires going between each PC, the owner wants a wireless setup.  I knew wireless is less secure, but didn't think it would be such a weak link.  I thought that by using the Untangle gateway at the front of the network, using wireless behind it would be more safe.  I don't think the owner will budge on not using wireless unfortunately.

That's great news that I can block the other PC's from the Untangle gateway and open them up when I need too..thanks for the tip!

So If it was to leave the wireless inside the protected network, would the setup be:

ISP Modem -> Untangle Gateway -> Wireless Router -> Office systems.

I don't believe the ISP modem is a router.
I will definitely use your suggestions for the wireless router.
Would the Untangle gateway dole out a static IP for the networked systems, or would I have to assign a static IP to the Untangle gateway first?

Thanks again for your help!

Charles.

---

### Post by Golem XIV on 2008-03-20
Sorry, I didn't mean to scare you about wireless.  Many people and companies use it and have no problems.  It's just that being in the IT business for 15+ years makes you a bit paranoid, which is a quite desirable trait in this line of business :) 

The problem with wireless is that just about anyone can "listen in" to the data streams.  This is obviously less of an issue if the office is on an umpteenth floor of a tall building or if it's inside concrete walls (the signal is fairly weak and concrete will degrade it a lot).  In a wired system you have to physically connect a sniffer to the network (and that means going through physical security - guards, locks, etc.) while with wireless you can park your car beside the office and use a laptop to capture the data streams and/or to inject malicious content into it.  Of course, to do that you have to break the encryption first, so make sure you use the strongest available.  WEP can be cracked in a matter of minutes so consider using WPA2 Enterprise (you will need a RADIUS server for that, but you can set one up in the Ubuntu box).  WPA Personal is also a decent option, though not so good.

However, I think I should warn you that wireless may be too unreliable for what you want to do.  I had problems with computers disconnecting all the time for a few seconds - for normal office work this was almost unnoticed by the users, but we had a very old database system that was very sensitive to loss of connection so it caused all sorts of problems.  I am assuming that you will be using a more modern database system that supports transactions (i.e. nothing is written to the database unless the data has been confirmed to have arrived correctly to destination) so this may not be an issue, but do make a few experiments first.  I had to install signal boosters all over the place to fix the problem, which turned out to be a lot more expensive than the wiring.  As I said, your best bet is to set up a testing case on-site first (and it would be useful for it to be a "worst-case" scenario, with the system that will be behind most walls and/or farthest away from the wireless station).  If you don't get problems with this setup, chances are the rest will go fine.

In any case, good luck and let us know if you need anything

---

### Post by hyper_ch on 2008-03-20
are the 5 Boxes also connected to the wifi router?

If so, I'd assign each machine a static IP and then install openssh-server on the ubuntu box... that way you can connect through ssh to the ubuntu box and from there you can then connect to the other boxes and you know which one is which because they all have static IPs.

---

### Post by Golem XIV on 2008-03-20
> **greavette said:**
> Thanks very much for the response Golem!

I wasn't planning on using the Ubuntu box as a router (but now that I look at the diagram, that does seem to show that).  I was planning on using the Ubuntu box to remote into from home, and once on the Ubuntu box, I would remote into the other PC's.

When you connect remotely, you connect directly to the system you want.  The path to the system should be completely transparent, and it is your router that decides if and how it should allow access.  In your case, Untangle is acting as router, firewall, intrusion detection system, etc.

> **greavette said:**
> I was also planning on using the Ubuntu box to store all backed up data from the 5 other PC's (using rysync) and then sending that data for offsite backup to my house (instead of going to each PC and getting the data, the Ubuntu box would get all the data for me and then I'll get all the data from one PC only).   Since Untangle already has VNC access, I probably won't need the Ubuntu box for remoting into the other PC's.  Should I use the Untangle box to store backed up data as well?

Sure, as long as the system can handle the requirements as to CPU speed, disk space, RAM, etc.    Gateways/firewalls usually have small requirements, so I don't think it will be a problem.  Many people use obsolete systems (we're talking 486's , even 386's) with old Linux distros just for this purpose.  Tacking on backup should increase system reqs quite a bit, but nothing a fairly modern run-of-the-mill system can't handle.  Once you get to 100+ machines and 500+ users is when you start thinking about heavy-duty dedicated servers.

> **greavette said:**
> The owner wants to have these 5 PC's setup together because one is a database to store data and the other 4 are used to input the data.  To save on wires going between each PC, the owner wants a wireless setup.  I knew wireless is less secure, but didn't think it would be such a weak link.  I thought that by using the Untangle gateway at the front of the network, using wireless behind it would be more safe.  I don't think the owner will budge on not using wireless unfortunately.

Unless the 5 PCs are very far away from each other, I don't see much savings.  No idea what's teh current price for Cat5 cable but it shouldn't be too much.  Even if the PCs are far from each other, you would need signal boosters for wireless, so the savings would evaporate.  There are 2 much more appealing characteristics that wireless has:  convenience - you can move your PCs around without worrying if there is going to be a network cable available, and the "coolness" factor which may sound dumb, but it's a very important thing for a company that wants to show a high-tech profile to its customers.  So, if he wants wireless, give it to him, but keep in mind what I said before.

> **greavette said:**
> That's great news that I can block the other PC's from the Untangle gateway and open them up when I need too..thanks for the tip!

All of these systems that I know work this way, both software and hardware.  As I said, I don't know Untangle specifically, but it *should* work this way.

> **greavette said:**
> So If it was to leave the wireless inside the protected network, would the setup be:

ISP Modem -> Untangle Gateway -> Wireless Router -> Office systems.

I don't believe the ISP modem is a router.
I will definitely use your suggestions for the wireless router.
Would the Untangle gateway dole out a static IP for the networked systems, or would I have to assign a static IP to the Untangle gateway first?

Thanks again for your help!

Charles.

Yep, that should be it.  About IPs - The Untangle gateway will probably get an IP assigned from the ISP.  Check with the ISP if the IP is dynamic (changes) or static.  If it's static, you just need to log in to that IP.  If it's dynamic, you will have to get a DynDNS or FreeDNS account (they're free) and run their software on the Untangle machine (Maybe Untangle has its own dynamic DNS service).

Both Untangle and the wireless router should come with a DHCP server that assigns IPs on a "first come, first served" basis.  That means that the IP of one PC may be different tomorrow.  To get around this, disable the DHCP servers on both Untangle and the Wireless router and set up static IPs on the PCs themselves.  This way you know which PC is which.

If you have need of DHCP for other computers, you can set up a range of addresses to be used by DHCP and set the static IPs for the 5 PCs outside of that range.  If you absolutely must have DHCP on all PCs, there are ways of "asking" the DHCP server which IP goes to which PC, but this  will slow you down and complicate your remote maintenance of the systems.

Whew!  That should cover it.  I hope it's clear, just let me know if you have any questions.

Good luck!

---

### Post by greavette on 2008-03-21
Thanks for all this information Golem and hyper_ch.  I love this community...these forums are just a wealth of information and everyone here is so helpful.  I'm still new to Linux and have been using Ubuntu since Feisty came out.  The help I get from these forums makes it easier for me to turn my back on windows and keep using Ubuntu!

Currently of the 5 PC's the owner currently owns, 2 are on the net and the other 3 are connected via network cable and are not on the net.  Since the owner wants these 5 to connect to each other (1 being the database and the other 4 being the client input PC's) and doesn't want to use network cables around the office, all 5 will be connected via wireless router.  I had never thought of assigning static IP's to each of the 5 PC's...what a great idea.  

Thanks for the information on wireless.  I will put into place your suggestions to help protect the wireless network.  The owner of this business is located in a sort of remote location (they are about 10 KM's from a larger town and can still get high speed internet) in a very small town so hopefully they won't have a lot of war drivers driving around trying to break into their wireless network.  They will be using a modern database program that was built specifically for their needs...I had never thought of what happens if the wireless connection is momentarily dropped.   I will need to do some more testing with this company they bought the software from to make sure it can handle a wireless network.  

I think I have enough here to have a very good start at building this network!  Thanks again so much for your help!  With forums like this, it makes it so much easier to get friends interested in Ubuntu(Linux) when there is so much help available!

Later,

Charles.

---

