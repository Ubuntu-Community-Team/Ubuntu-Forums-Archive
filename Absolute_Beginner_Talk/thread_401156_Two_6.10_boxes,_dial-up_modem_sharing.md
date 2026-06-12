---
title: "Two 6.10 boxes, dial-up modem sharing?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by whein on 2007-04-04
So close and yet so far...
I have two boxes running Edgy at home.  One has an external dial-up modem to connect to the internet, which works great (but obviously slow).  We'll call this Computer A.  The other one has only a networking card, and we'll call it Computer B.  Last night I got the two computers to recognize each other over the network and share files using (I think) a Samba share.  I'm trying to get Computer B to be able to access the internet when Computer A is dialed in.

 I followed the instructions on the Firestarter website [http://www.fs-security.com/docs/connection-sharing.php](http://www.fs-security.com/docs/connection-sharing.php) but took the path of static IPs instead of mucking around with a DHCP server.  _Almost_ everything works.  I'm using IPs of 192.168.0.1 for Computer A and 192.168.0.2 for Computer B.  I can ping each one from the other and get a response.  As mentioned above, Computer B was able to copy files from a shared folder on Computer A.  So for the most part, networking works.  In the Firestarter preferences panel I have the "Internet connected network device" set to the modem (PPP0) and the "Local network connected device" set to the networking card (ETH0).  Internet connection sharing is checked, and the DHCP is diabled (not checked).

Now, here's the question: what do I need to do on Computer B to let programs such as Firefox, Synaptic, etc. see the big bad intarweb-hicky?  They just sort of sit there twiddling their thumbs and saying no connection found.  The more detailed the instructions, the better.   Screenshots are good.  :)  I spent all night hunting the web for answers and they were all hand-wavy and vague.  
](*,)
-Will

---

### Post by mikeyphi on 2007-04-04
I'm a bit slow - so just to be sure of the question...could you post the settings for Firestarter for each computer?

---

### Post by oilchangeguy on 2007-04-04
my question to you is, why when you live in a major US city would you use dial up? if you had a broadband connection it would be so much simpler to network the computers. most phone and cable companies have lower level packages available with prices near dial up. and much faster speeds.

---

### Post by whein on 2007-04-04
mikeyphi:
I only have Firestarter installed on Computer A, the one with the modem connected to the internet.  It didn't seem useful to put a firewall on the other computer since it was (I assume) already behind one by proxy.

oilchangeguy:
Complicated, but the main reasons are
 - I already have a dial-up account.  It may be slow, but it gets the job done.  For big stuff, ISO images, etc. I use the fast connection at my work and carry it home on a USB flash drive.
 - I don't live in a major US city. I live in the next county over.  I cannot get DSL, sattellite has too high a lag for the price, and cable might be an option down the road, but right now is too pricey as well.  Dial-up is $7 a month.  Cable is >$40.  I'm a cheap *******, proud of it.  ;)
 - I have a strong hunch I will run into the same problems with any type of connection using the above network topology.  My hunch is the problem lies in the settings on Computer B, not on Computer A.
 - And lastly, I want to learn more.  Networking is very new to me and still a "black magic" kind of thing.  Back in my Windoze days it was even more confusing.  Time to earn my geek credentials.

-Will

---

